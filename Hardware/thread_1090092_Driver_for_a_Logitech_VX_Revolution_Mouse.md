---
title: "Driver for a Logitech VX Revolution Mouse"
date: 2009-03-07
forum: Hardware
---

### Post by Dragon Smaug on 2009-03-07
Can a Logitech VX Revolution Mouse work with Ubuntu?  How do I find out?  I'm on 8.10.

Thanks you for any help.

---

### Post by Dragon Smaug on 2009-03-07
Hey it actually working now, don't know why it wasn't before.  The additional buttons don't work, will search around the internet...

---

### Post by zeddock on 2009-03-25
It actually does not fully work.  I would like to see the zooms and other buttons work too.

Any help?

zeddock

---

### Post by dentharg on 2009-05-22
Also interested in this.

---

### Post by juamez. on 2009-06-01
Can't you assign functionality to the custom buttons through the keyboard shortcuts menu in System - Preferences - Keyboard Shortcuts? I reckon the custom buttons won't work because the their functionality is added by the logitech software, which is unfortunately not available for linux.

I'd say: try it out and tell it here. ;)

edit: I found this: [http://www.terminally-incoherent.com/blog/2007/11/01/logitech-vx-revolution-in-dapper/](http://www.terminally-incoherent.com/blog/2007/11/01/logitech-vx-revolution-in-dapper/)

It's old (dapper drake is like 3 years old) but it might help, who knows.

I'm actually thinking of buying one myself, since the current mouse I have tends to get crazy and warps the mouse pointer all the way up to the upper left or lower right corner. This is my cry for quality!

---

### Post by kprzysowa on 2009-07-25
Hi, I am having problems with getting my logitech thumbs buttons of VX Revolution to work.
I have followed this HOW TO:
[http://ubuntuforums.org/showthread.php?t=277388](http://ubuntuforums.org/showthread.php?t=277388)

My:
cat /proc/bus/input/devices
 > 
I: Bus=0003 Vendor=046d Product=c521 Version=0111
N: Name="Logitech USB Receiver"                  
P: Phys=usb-0000:00:1a.0-1/input0                
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input5
U: Uniq=                                                               
H: Handlers=mouse1 event5                                              
B: EV=17                                                               
B: KEY=ffff0000 0 0 0 0                                                
B: REL=143
B: MSC=10
sudo gedit /etc/udev/rules.d/19-local.rules
> 
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", SYSFS{../phys}=="usb-0000:00:1a.0-1/input0", NAME="input/event9"
sudo gedit /etc/X11/xorg.conf
 > 
Section "InputDevice"
    Identifier        "VX Rev"     #VX Rev users can type "VX Rev"
    Driver            "evdev"
    Option            "Device" "/dev/input/event9"
    Option            "Protocol" "auto"
    Option            "CorePointer"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "VX Rev"
EndSection
I have tried as well btnx, but:
> 
 kprzysowa@larix:~$ sudo btnx
 btnx: uinput modprobed successfully.
 btnx: Opening config file: /etc/btnx/btnx_config_Default
 btnx: Could not read the config file: No such file or directory
 btnx: Configuration file error.
> 
kprzysowa@larix:~$ sudo btnx-config
/usr/share/btnx-config/btnx-config.glade
Warning: configuration file for configuration "Default" does not exist. Deleting configuration.
Aborted
Only right, left and wheel with middle button fuction are working.
The goal is to remap the big thumb button as a middle button.
Once thumb button will be recognised the mapping will be fixed by xmodmap 
Please help...

---

