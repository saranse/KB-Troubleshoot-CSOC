### **Policy ที่ต้องทำ**

**Source ip private** ของเครื่องนั้นๆ

\----------

**Destination IP** ตามด้านล่าย

"Public DNS Name: ts01-gyr-maverick.cloudsink.net"

IPs:

35\.162.224.228

35\.162.239.174

50\.112.129.218

50\.112.130.23

50\.112.131.18

52\.25.223.26

52\.33.193.184

52\.35.11.124

52\.35.162.27

54\.68.92.116

54\.71.43.66

100\.20.76.137

Public DNS Name: lfodown01-gyr-maverick.cloudsink.net"

IPs:

34\.209.79.111

34\.210.186.129

34\.209.165.130

35\.80.210.147

35\.160.213.193

35\.166.20.122

52\.10.219.156

52\.27.205.162

100\.20.144.105

\----------

**Port**

443 , 53

**กรณีที่ไม่อยากออกไปขา inter ให้ชี้มายัง INET**

edr-proxy.inet.co.th

203\.154.196.91

**Port**

3128

ขั้นตอนการ install

1\.Check Support Kernal

```
uname -r
```

2\.Download EDR สำหรับ install ของ OS Version นั้นๆ ด้วย Command

* Ububtu : [http://203.151.249.125/index.php/s/esDTjtqA9wPSsaf/download/falconsensor](http://aeynextcloud.inet.co.th/index.php/s/esDTjtqA9wPSsaf/download/falcon-sensor)*\_Ubuntu*\_7.03.0-15805_amd64.deb
* Centos : [http://203.151.249.125/index.php/s/42B3oqxWnQ5ZobD/download/falcon-sensor](http://aeynextcloud.inet.co.th/index.php/s/42B3oqxWnQ5ZobD/download/falcon-sensor)\_*CentOS7-7.03.0-15805.el7.x86*64\.rpm

> ตัวอย่างการ Download ผ่าน command

```
wget ตาม Link ที่ต้องการจะ Download ด้านบน
```

3\.ตรวจสอบดูว่า File install EDR Download มาหรือยัง

```
ls
```

จะแสดงชื่อ File ที่ Download มา

> *\- ถ้าเป็น Ubuntu ชื่อ File จะเป็น falcon-sensorUbuntu7.03.0-15805_amd64.deb*
>
> *\- ถ้าเป็น Centos ชื่อ File จะเป็น falcon-sensorCentOS7-7.03.0-15805.el7.x8664.rpm*

4\.ให้ Perminsion แก่ File ให้มีสิทธิ์ในการ Run ได้

```
สำหรับ centos
chmod 555 falcon-sensorCentOS7-7.03.0-15805.el7.x8664.rpm  
สำหรับ ubuntu
chmod 777 falcon-sensorUbuntu.03.0-15805.el7.x8664.deb
[เพิ่มสิทธิ์ไฟล์] ชื่อโปรแกรมขึ้นอยู่กับ Version Linux
```

5\.Install Agent

```
สำหรับ centos
rpm -i falcon-sensorCentOS7-7.03.0-15805.el7.x8664.rpm
สำหรับ ubuntu
dpkg -i falcon-sensorUbuntu.03.0-15805.el7.x8664.deb   
[Install Agent]
```

6\.ใส่ cid

```
/opt/CrowdStrike/falconctl -s --cid=00F79DE8BE94463D8482591A1A4B5AF2-85  [ใส่ cid ของ license]
ปัจจุบัน cid ที่ใช้จะเป็น 00F79DE8BE94463D8482591A1A4B5AF2-85
```

7\.install Token EDR

```
sudo /opt/CrowdStrike/falconctl -s --provisioning-token=1AB187BC
ปัจจุบัน Token เป็น 1AB187BC หมดอายุเดือน 5 ( Token มีระยะเวลาจะหมดอายุ )
สามารถเปิด Case ขอจากทีม Endpoint ได้
```

8\.start service

```
service falcon-sensor start [start service]
หรือ
systemctl falcon-sensor start [start service]
```

9\.เปิดการทำงาน sensor

```
systemctl enable falcon-sensor [เปิด sensor]
```

10\.ตรวจสอบ starus

```
service falcon-sensor status [ตรวจสอบ starus] 
หรือ
systemctl falcon-sensor status [ตรวจสอบ starus]
```

11\.นำ Host name ไปตรวจสอบบน Portal CrowdStrike

---

# จบ