---
title: "Ubuntu 7.10 on ps3  HP printer problem &amp; lsusb"
date: 2008-08-09
forum: General Help
---

### Post by dogdaynoon on 2008-08-09
Hi, I am kinda new to linux.
 I installed kernel 2.6.22 on my ps3 then upgraded to 2.6.24 .
I have installed ALL the updates that came in on the automatic updates tab.

My promblem is this.
  $lsusb     =   NO OUTPUT
 
Also I have installed hplip from here [http://hplip.sourceforge.net/downloads.html]("http://hplip.sourceforge.net/downloads.html")
I still get the error of nothing plugged in when i try to install printer through $sudo hp-setup .
can find my keyboard and mouse here
$nano proc/bus/devices   OUTPUT = 

I: Bus=0003 Vendor=046d Product=c00e Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-sb_05-2.2/input0
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=0b38 Product=0003 Version=0110
N: Name="USB-compliant keyboard"
P: Phys=usb-sb_05-2.3/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=0b38 Product=0003 Version=0110
N: Name="USB-compliant keyboard"
P: Phys=usb-sb_05-2.3/input1
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2
B: EV=1f
B: KEY=37fff00ac3027 bf00444400000000 1fe3 c040a37c000 267bfad941dfed 9e0000000$
B: REL=143
B: ABS=100000000
B: MSC=10

So at some point they installed.
What can I do to make lsusb work so that I can try and get my printer up and running.
Thanks,
BO


EDIT :  
I got lsusb working: Here is the fix:
$sudo nano /etc/fstab
#added this to make usb bus mount.
none          /proc/bus/usb        usbfs             defaults      0         0
Then  CNTL + X
Y  Enter
Enter
Now the bus mounts on boot and lsusb works fine.....
Yay!!!!

---

