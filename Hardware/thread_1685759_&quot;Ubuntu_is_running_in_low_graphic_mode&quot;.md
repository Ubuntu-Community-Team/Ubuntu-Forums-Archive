---
title: "&quot;Ubuntu is running in low graphic mode&quot;"
date: 2011-02-11
forum: Hardware
---

### Post by pareLi on 2011-02-11
Suddenly when i restarted my computer i got this messenge: 

"Your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself."

So, now i can't really do anything besides going into the console, i get some options after i click ok on the error, but none of them works. Only "exit to console"-

And also; I'm a newbie on liunx, so i dont really know any commands..

Anyone has any info on what i can do?

I got a nvidia grahpic card and I'm on a aspire 8920g laptop running dual boot ubuntu 10.10 and xp64.

---

### Post by grahammechanical on 2011-02-11
Watch out that your graphic card is not overheating. This happened on my machine (a desktop) and the OS could not determine the correct settings of the monitor. First, Ubuntu loaded in low resolution mode, a little later it would dump me to a command line prompt. The live CD would not install the OS. Then the Live CD would not run. I was able to install a 2007 version of Mandriva because it allowed me to set the monitor screen resolution during the install process. I eventually replaced the graphic card.

I hope that in your case it is not time for a new graphic card.

Regards.

---

### Post by komputes on 2011-02-11
You can hold down shift at boot to get the boot menu (this is tricky for some). From the boot menu, there are usually two entries for each kernel version. Select the second option (recovery mode). From recovery mode (menu with blue background) you can do any of the following to see if it helps. If you get stuck at a terminal press Ctrl-D to return to the menu.

```
netroot - this will get you an IP address.
dpkg - this will update your packages
root - this will return you to a terminal

```Once in a terminal you can run any of the following commands to see if it helps with the nvidia card.

```
# mv /etc/X11/xorg.conf /etc/X11/xorg.nvidia.backup
```The command above moves/renames the xorg (video) config file.

```
# jockey-text
```The command above will walk you through enabling your nvidia card's binary/restricted driver. It's pretty self explanatory. Once the drivers are downloaded/installed simply run the "reboot" command to reboot. The resolution issue should be corrected. If not, use the following command in a terminal to report a bug:

```

$ ubuntu-bug xorg
```

---

### Post by pareLi on 2011-02-13
> You can hold down shift at boot to get the boot menu (this is tricky for some). From the boot menu, there are usually two entries for each kernel version. Select the second option (recovery mode). From recovery mode (menu with blue background) you can do any of the following to see if it helps. If you get stuck at a terminal press Ctrl-D to return to the menu.

Since i have dual boot i get a boot menu with about 8 different choices, this would be the boot menu you walk about right? When going for the recovery choice on this menu I end up with a console (no menu with blue background).. and if i use it just auto types EXIT and then i'm back to root@xxxx~#

> ```
netroot - this will get you an IP address.
dpkg - this will update your packages
root - this will return you to a terminal

```Once in a terminal you can run any of the following commands to see if it helps with the nvidia card.

Output of those commands:

```
netroot: command not found.
root: can't figure out display. Set it manually.
```

I did not figure out how to use dpkg and can't i use apt-get update instead?

> ```
# mv /etc/X11/xorg.conf /etc/X11/xorg.nvidia.backup
```The command above moves/renames the xorg (video) config file.

What's the point of doing this? Tried it though.

After typing in locate xorg.conf i get this:

```
root@xxxxx:~# locate xorg.conf
/etc/X11/xorg.conf-backup-110211114654
/etc/X11/xorg.conf.failsafe
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/X11/xorg.conf.d/60-magictrackpad.conf
/usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf
/usr/share/man/man5/xorg.conf.5.gz
```

The /etc/X11/xorg.conf-backup-110211114654 file is empty...
Why is it empty?

And the xorg.conf.failsafe contains:


```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fbdev"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

> ```
# jockey-text
```The command above will walk you through enabling your nvidia card's binary/restricted driver. It's pretty self explanatory. Once the drivers are downloaded/installed simply run the "reboot" command to reboot. The resolution issue should be corrected. If not, use the following command in a terminal to report a bug:

When typing in jockey-text in the recovery console i get this:

```
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init_.py:57: GtkWarning: could not open display warning.warn(str(e), _gtk.Warning)

Searching for avilable drivers...

root@xxxxx:~#
```

But when i'm in a x-session and i type jockey-text i only get:

```
Searching for avilable drivers...
```

In x-session i think i found out that none of the nvidia drivers was not installed. System - Administration - Additional drivers.
2 Nvidia drivers came up and none of them where activated, now i can't activate one since i don't have internet.

Yet another speedbumb...

I have never connected to a wifi through terminal before so i dont know what i have done wrong.

/etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet DHCP
wireless-essid GIGABYTE
wireless-key s:1234567891
```

Trying to connect:

```
root@xxxxx:~# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
There is already a pid file /var/run/dhclient.wlan0.pid with pid 2065
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:1d:e0:a6:30:2f
Sending on   LPF/wlan0/00:1d:e0:a6:30:2f
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:1d:e0:a6:30:2f
Sending on   LPF/wlan0/00:1d:e0:a6:30:2f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]


```

What do i do know? There should be no problem with the card.

I would appreciate any help anyone can give me.

---

### Post by pareLi on 2011-02-15
Excuse my English but please, i really need some input on the matter.

---

### Post by pareLi on 2011-02-16
I solved the wireless problem:

[http://ubuntuforums.org/showthread.php?t=1689102](http://ubuntuforums.org/showthread.php?t=1689102)

---

