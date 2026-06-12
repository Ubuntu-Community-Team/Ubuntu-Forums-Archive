---
title: "T61p Trackpoint not working at all"
date: 2008-07-26
forum: Hardware
---

### Post by phazon. on 2008-07-26
Hi

Can anyone help me enable the trackpoint? All the posts I can find seem to be about either disabling it, or making the middle button work, whereas mine is not working at all. This is a new install of 8.04.

For some reason I seem to have no /etc/trackpoint directory, nor any of the expected files under /sys/devices/platform/i8042/serio1/serio2/ (ie Sensitivity etc)

Thanks

---

### Post by tesna on 2008-07-26
do you have something like 
```

[   25.864574] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   25.775540] input: TPPS/2 IBM TrackPoint as /class/input/input10

```

in dmesg?

Have u tried to disable trackpoint in the bios, boot to ubuntu, then reboot and enable it again in bios? 

Mine is T61 and my trackpoint and trackpad working fine. For files in /etc/trackponint I think that one will be available if you install trackpoint-settings . Maybe [this]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61") can help you

---

### Post by phazon. on 2008-07-27
The BIOS trick worked, thank you for your quick reply

---

### Post by erpan on 2008-08-21
> **tesna said:**
> do you have something like 
```

[   25.864574] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   25.775540] input: TPPS/2 IBM TrackPoint as /class/input/input10

```

in dmesg?

Have u tried to disable trackpoint in the bios, boot to ubuntu, then reboot and enable it again in bios? 

Mine is T61 and my trackpoint and trackpad working fine. For files in /etc/trackponint I think that one will be available if you install trackpoint-settings . Maybe [this]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61") can help you

I have tried this with no success lenovo t61. what can i do as thinkwiki doesnt give much help as im new at this. 
To change x11 you must be root i assume you should use the terminal then but what commands do i use?

---

### Post by linux_tech on 2008-08-21
Make a backup 1st-
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

To edit:
```
sudo gedit /etc/X11/xorg.conf
```
then replace the "Configured Mouse" section in /etc/X11/xorg.conf with Trackpoint info 
from: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#TrackPoint](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#TrackPoint)



Also if you have any issues with losing the trackpad you may want to reset trackpad:

backup menu.ls:
```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup  
```

edit menu.lst
```
 sudo gedit /boot/grub/menu.lst   
```

Add the following to your kernel line -

```
 locale=fr_FR i8042.reset 
```

for example: 

title		Ubuntu, kernel 2.6.20-15-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-386 locale=fr_FR i8042.reset
initrd		/boot/initrd.img-2.6.20-15-386
quiet

---

