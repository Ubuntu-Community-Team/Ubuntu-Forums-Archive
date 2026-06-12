---
title: "Wacom on Fujitsu T902"
date: 2012-09-04
forum: Hardware
---

### Post by TabletUbuntu on 2012-09-04
Just got a new Fujitsu T902 and everything works out of the box with latest Precise except for the pen (stylus).  

lsusb returns 

Bus 001 Device 004: ID 056a:0101 Wacom Co., Ltd 

but all of the following return nothing

fgrep -i wacom /var/log/Xorg.0.log
xsetwacom --list devices
xinput | grep -i wacom

Any ideas where to start?  

Thanks.

---

### Post by Favux on 2012-09-05
Hi TabletUbuntu,

Very interesting.  That appears to be Fujitsu's first USB tablet PC.  Prior to it they have been producing serial tablet PCs or ISDv4 devices as the Linux Wacom Project calls them.  Lenovo switched to USB with the Thinkpad X220t.

Is this pen only or does it have touch too?  If it has touch how many finger touch?

I do not recognize the Product ID in the lsusb line:  PID = 0101.  It isn't yet in the wacom_wac.c or wcmUSB.c.  So a new entry has to be made for it.  Which isn't too difficult if the usb packet protocol is already one that is defined.  If it is new then a developer would definitely have to do it.

I don't know if they're aware of this model digitizer yet.  I suggest you post on the linuxwacom-discuss mailing list.  That should get you the fastest results.
[http://sourceforge.net/mailarchive/forum.php?forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?forum_name=linuxwacom-discuss)

---

### Post by TabletUbuntu on 2012-09-05
> **Favux said:**
> Hi TabletUbuntu,

Very interesting.  That appears to be Fujitsu's first USB tablet PC.  Prior to it they have been producing serial tablet PCs or ISDv4 devices as the Linux Wacom Project calls them.  Lenovo switched to USB with the Thinkpad X220t.

Is this pen only or does it have touch too?  If it has touch how many finger touch?

I do not recognize the Product ID in the lsusb line:  PID = 0101.  It isn't yet in the wacom_wac.c or wcmUSB.c.  So a new entry has to be made for it.  Which isn't too difficult if the usb packet protocol is already one that is defined.  If it is new then a developer would definitely have to do it.

I don't know if they're aware of this model digitizer yet.  I suggest you post on the linuxwacom-discuss mailing list.  That should get you the fastest results.
[http://sourceforge.net/mailarchive/forum.php?forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?forum_name=linuxwacom-discuss)

Hi Favux,

Thanks for the reply.  I will try posting to the linuxwacom-discuss mailing list.  It is pen and multitouch.  When I find out anything more, I will report back here.

---

### Post by TabletUbuntu on 2012-09-05
Signed up twice and posted four messages, but sourceforge replies that I am not allowed to post to the list.  Ridiculous.  As much as I want this to work, I simply do not have to time for such foolishness and will have to wait until my issue resolves itself. It is very disappointing.

---

### Post by Favux on 2012-09-05
Sounds like SourceForge is just flakey at the moment.  Did you get an e-mail confirmation that you were signed up?

I'd just wait a while before trying again.

---

### Post by Cobuntu on 2013-03-11
Current Fujitsu T902 10-Finger Multitouch with Dual-Touchscreen have a different touchscreen: 
lsusb returns Bus 001 Device 005: ID 056a:010d Wacom Co., Ltd 
instead of before 
Bus 001 Device 004: ID 056a:0101 Wacom Co., Ltd  

This device was unknown to linuxwacom-discuss but Stephan Frank (thank you!) found out that it works with the same driver than the older one, they will soon be added to the linuxwacom-Repository. For the meantime he adjusted all necessary files for the different ID, they can be downloaded here and work for 13.04 with 3.8.0.9-generic:
 [http://www.cs.tu-berlin.de/~sfrank/input-wacom.tar.bz2](http://www.cs.tu-berlin.de/~sfrank/input-wacom.tar.bz2) 
[http://www.cs.tu-berlin.de/~sfrank/xf86-input-wacom.tar.bz2](http://www.cs.tu-berlin.de/~sfrank/xf86-input-wacom.tar.bz2)  [B]

The following is valid for 3.8.0-9-generic, for newer kernel versions you have to adjust:[/B] 
1. download and unpack both of them (in my case to /home/USERNAME/Desktop) 

2. # cd /home/USERNAME/Desktop/input-wacom 
# sudo cp 3.7/wacom.ko /lib/modules/3.8.0-9-generic/kernel/drivers/input/tablet 
(replace the '3.8.0-9-generic' part with the one shown with # uname -r) 

3. #sudo gedit /etc/modules put 'wacom' into this file 

4.  
# sudo apt-get build-dep xf86-input-wacom  
# cd /home/USERNAME/Desktop/xf86-input-wacom 
# make 
# sudo make install # sudo update-initramfs -u -k all 

5. Restart, Pen and Touch should then be working!  [B]

After kernel update [/B]**(here to 3.8.0-12-generic) ****you have to update both drivers manually:** 
 
6. #cd /home/USERNAME/Desktop/input-wacom 

7. # ./autogen.sh 

8. # sudo cp 3.7/wacom.ko /lib/modules/3.8.0-12-generic/kernel/drivers/input/tablet 
(replace the '3.8.0-12-generic' part with the one shown with # uname -r) 

9.  
# sudo apt-get build-dep xf86-input-wacom  
# cd /home/USERNAME/Desktop/xf86-input-wacom 
# ./autogen.sh 
# sudo update-initramfs -u -k all 

10. Restart, Pen and Touch should then be working!

---

