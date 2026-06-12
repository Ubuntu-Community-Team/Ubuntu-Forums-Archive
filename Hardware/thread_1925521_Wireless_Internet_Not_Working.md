---
title: "Wireless Internet Not Working"
date: 2012-02-14
forum: Hardware
---

### Post by Texasgirl833 on 2012-02-14
I think I am having a problem with broadcom wireless chip.  I have the b43 driver installed.
The wireless wasn't working and then I installed the firmware.  It worked until I shut down the computer.  When I restarted it, the wireless doesn't work again.

I checked and the driver and firmware are still installed.

Can anyone help me with this?

I am running Ubuntu 11.10.

---

### Post by Bucky Ball on 2012-02-14
Welcome, Texasgirl833. In 'Additional Drivers' is the B43 still enabled?

---

### Post by ThomasAndersn on 2012-02-15
well, are u WiFi card is supported by ubutu to check, first u have to identify the your wifi card/driver of your computer or laptop.
Open the terminal type the following command:
lspci -vvnn | grep 14e4

check the exact model of ur wifi card. Supported models are:
BCM4301 BCM4306/2, BCM4306/3, BCM4311, BCM4312, BCM4318, BCM4320 

If u found the wifi model in the list & still have connection problem, then type the following command in terminal:

~$ sudo mount -o loop /host/ubuntu/install/.fuse_hidden0000000400000001 /mnt
~$ cd /mnt/pool/main/b/b43-fwcutter/
~$ sudo apt-get install b43-fwcutter
~$ sudo dpkg -i b43-fwcutter*
~$ cd /mnt/pool/main/p/patch/
~$ sudo apt-get install b43-fwcutter
~$ sudo umount /mnt
 Now download the following firmware:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

copy the downloaded files to the HOME folder & execute the following commands:
~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

Now restart ur system. I hope it will solve ur problem.


_______________________
[Virus Removal](http://antivirus.igennie.net/virus-removal.html)

---

### Post by ajukilibodin on 2012-02-15
What is your card model? I am running on a 4313rev1 and the drivers in the repos don't work for me, the Additional Hardware drivers have very poor performance. Try the Linux STA drivers, follow [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) this guide. Let me know how that works out.

---

### Post by Texasgirl833 on 2012-02-15
Thanks for the help so far.  I checked the Additional Drivers, and it doesnt show up at all.  I can enable the b43 driver from the terminal with modprobe b43.  After enabling it, I checked additional drivers again, and it still wasn't listed, but I was able to connect to the internet.  
 
Ive been looking around at posts with similar problems, and many people suggest "adding the driver to startup", but I am not real clear on how to accomplish this.  Any suggestions?? Thanks.

---

### Post by Yellow Pasque on 2012-02-15
If you just need the b43 module to load at start, then insert 'b43' (on its own line. obviously) in /etc/modules

---

### Post by wildmanne39 on 2012-02-15
Hi, the b43 driver does not show up in additional drivers it sounds like the driver just is not loading on start up so please do:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thanks

---

### Post by Texasgirl833 on 2012-02-17
Thank you so much for all the help!  Wireless is working now.

---

### Post by wildmanne39 on 2012-02-17
Hi, your welcome!
Enjoy

---

