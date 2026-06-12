---
title: "help insatlling ZTE 636 HSDPA  on Ubuntu 9.10"
date: 2009-11-04
forum: Hardware
---

### Post by superpal on 2009-11-04
Dear Ubuntu experts
 
Im trying to install ZTE 636**HSDPA on my Toshiba laptop, I red too much on this forum and I treid too much but nothing.**
 
I already did this 
 
sudo gedit /etc/usb_modeswitch.conf 
 
to delete the # and ; infront of ZTE 636 configuration lines
 
i did this command
 
sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf
 
to change 19d2:2000 to 19d2:0031 by using the comand lsusb
 
so far so good.
 
i did this command to make this file 
sudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf626.fdi 
 
and fill it with 
 
<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
<!-- ZTE MF626 HSDPA USB Modem -->
<match key="@info.parent:usb.vendor_id" int="0x19d2">
<match key="@info.parent:usb.product_id" int="0x0031">
<match key="@info.parent:usb.interface.number" int="3">
<append key="modem.command_sets" type="strlist">GSM-07.07</append>
<append key="modem.command_sets" type="strlist">GSM-07.05</append>
<append key="info.capabilities" type="strlist">modem</append>
</match>
</match>
</match>
</device>
</deviceinfo> 
 
 
so far so good
 
i did this command to create this file 
 
**sudo gedit /etc/udev/rules.d/90-zte.rules**
 
**and fill it with the following configuration**
 
ACTION!="add", GOTO="ZTE_End"
 
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"
 
LABEL="ZTE_ZeroCD"
RUN+="/usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf"
 
LABEL="ZTE_End"
 
 
i created the file ttyUSB by it is command 
 
for the **wvdial.conf** i found many configurations and i used this conifguration
 
[Dialer Default]
Modem= /dev/ttyUSB0
Modem Tybe = Analog Modem 
ISDN = 0
New PPPD = yes 
Baud = 9600
Username = user
Password = pass
Phone = *99#
Stupid Mode =1
Init1 = ATZ
I
nit2 = AT&Q0 V1 W1 S0=0 &C1 &D2 +FCLASS=0
Init3 =AT+CGDCONT=1,"IP", "internetg"
 
when i run the wvdial by the command sudo wvdial i get this answer
 
command not found
 
 
and the system can not connect with the modem 
 
plzzzzzzzzzzzzzzzzzzzzzzzz
 
help
 
Thank u very mcuh

---

