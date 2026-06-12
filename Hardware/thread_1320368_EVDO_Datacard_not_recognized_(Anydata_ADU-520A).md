---
title: "EVDO Datacard not recognized (Anydata ADU-520A)"
date: 2009-11-09
forum: Hardware
---

### Post by golgot04 on 2009-11-09
Dear All,

I used to connect my computer with a EVDO data Card (Anydata ADU 520A) without problem on 9.04

Since update to 9.10, the datacard is not recognized and it's not possible anymore to connect.

Can you provide help?

Regards

---

### Post by Nickolay Ihalainen on 2010-05-10
> **golgot04 said:**
> I used to connect my computer with a EVDO data Card (Anydata ADU 520A) without problem on 9.04

Hi, golgot04!
Probably this howto works not only with 10.04, but also with 9.10
Edit system udev rules file:
```
sudo gedit /lib/udev/rules.d/61-option-modem-modeswitch.rules
```and comment the line with #:
```
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="1000", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"
```install special usb-cdrom to usb-modem mode switching software:
```
sudo apt-get install usb-modeswitch usb-modeswitch-data
```create a new kernel driver parameter file 
```
sudo gedit /etc/modprobe.d/usbstor.conf
```and plache this text into:
```
options usb-storage option_zero_cd=2 delay_use=5
```Reboot the system (or umount all flash drives plus execute a command: modprobe -r usb_storage;modprobe usb_storage).
Plug AnyData 520A device into usb port wait about 10-20 seconds, check /dev/ttyUSB* devices / or NetworkManager Mobile broadband device)

---

### Post by pradeepthundiyil on 2010-05-20
Hi, 
This is wat i did for my reliance.. 
change baud rate according to evdo.. 


1.Install wvdial & gnome-ppp

2. sudo chmod 777 /etc/wvdial.conf

3. sudo gedit /etc/wvdial.conf 

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
PPPD Path = /usr/sbin/pppd
Modem = /dev/ttyUSB0
ISDN = 0
; Phone = <number>
; Password = <passwrd>
; Username = <usrnam>

4. sudo pppconfig

in the new (below) window select Create and give ok... 
 
Type provider name (say reliance) and give ok 
 
Select Dynamic and give ok 
 
Select PAP and give ok 
 
Enter your Reliance Number and give ok 
 
Password is same as your Reliance Number, enter it and give ok 
 
Select Tone and give ok 
 
Enter #777 and give ok 
 
Enter yes 
 
Now all set. Ensure Everything is fine. Select Finished then ok 
 
Finally in the last wind select Quit and give ok


5. sudo chmod a+x /usr/sbin/pppd
6.$ sudo chmod a+rw /etc/ppp/pap-secrets
7. $ sudo chmod a+rw /etc/ppp/chap-secrets

sudo gedit /etc/ppp/options

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
ipcp-max-failure 30

Code:
gksudo gedit /etc/ppp/options
Add this line and save:

replacedefaultroute

if this is done then replace the # in front of the

replace the # in front of the " ipcp-max-failure 30 " do not use both lines


configure gnome-ppp, with ur username & password.. 

Reboot and click connect in gnome-ppp
:guitar:

---

