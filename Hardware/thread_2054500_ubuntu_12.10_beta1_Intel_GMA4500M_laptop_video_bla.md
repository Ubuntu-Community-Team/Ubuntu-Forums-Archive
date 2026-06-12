---
title: "ubuntu 12.10 beta1 Intel GMA4500M laptop video black screen problem"
date: 2012-09-07
forum: Hardware
---

### Post by anandv21 on 2012-09-07
** kubuntu / ubuntu 12.10 Intel GMA 4500M Black screen problem **

   
   Installed the latest Kubuntu 12.10 on my Acer Aspire 4736Z laptop.  However, the display is blank/black. The OS seems to have started  correctly (keystrokes result in expected results, albeit flying blind)  but only display is blank.

This has been the case with (k)ubuntu 12.04 and 11.10 too. I remember  the same laptop used to work just fine earlier (9.10 probably?)


Google search led me to the following forums threads:
[http://ubuntuforums.org/showthread.php?t=1237873](http://ubuntuforums.org/showthread.php?t=1237873)
[http://forums.gentoo.org/viewtopic-t-892206-start-0.html](http://forums.gentoo.org/viewtopic-t-892206-start-0.html)

User cach0rr0 on the Gentoo forum mentions that setting  /sys/class/backlight/acpi_video0/brightness to value 8 and rebooting  immediately (say Ctrl-Alt-Del) retains the value and the display works  fine. There should not be a power off/on sequence in between, since that  destroys the value we have written into the register.

So, I thought I could automate the same

I modified my /etc/rc.local to detect the setting and if "wrong" set it  to 8 and reboot. If the value is 8, the system completes the bootup and  is ready for user login.

The only "problem" with this trivial fix is that when powering on the laptop, it reboots automatically once.

Suspend/Resume seems to work fine for me.


[FONT=&quot]catroot@asp4736-k1210:~# cat /etc/rc.local [/FONT]
[FONT=&quot]#!/bin/sh -e[/FONT]
[FONT=&quot]#[/FONT]
[FONT=&quot]# rc.local[/FONT]
[FONT=&quot]#[/FONT]
[FONT=&quot]# This script is executed at the end of each multiuser runlevel.[/FONT]
[FONT=&quot]# Make sure that the script will "exit 0" on success or any other[/FONT]
[FONT=&quot]# value on error.[/FONT]
[FONT=&quot]#[/FONT]
[FONT=&quot]# In order to enable or disable this script just change the execution[/FONT]
[FONT=&quot]# bits.[/FONT]
[FONT=&quot]#[/FONT]
[FONT=&quot]# By default this script does nothing.[/FONT]

 [FONT=&quot]d=`date`[/FONT]
[FONT=&quot]bv=`cat /sys/class/backlight/acpi_video0/brightness`[/FONT]
[FONT=&quot]if [ $bv != "8" ];then[/FONT]
[FONT=&quot]  echo 8 >/sys/class/backlight/acpi_video0/brightness [/FONT]
[FONT=&quot]  echo "$d: acpi_video0 brightness is $bv so rebooting" >>/var/log/acpi_brightness.txt[/FONT]
[FONT=&quot]  reboot[/FONT]
[FONT=&quot]else[/FONT]
[FONT=&quot]  echo "$d: acpi_video0 brightness is $bv" >> >>/var/log/acpi_brightness.txt[/FONT]
[FONT=&quot]fi[/FONT]
[FONT=&quot]exit 0[/FONT]
[FONT=&quot]root@asp4736-k1210:~#[/FONT]

[FONT=&quot]root@asp4736-k1210:~# lspci 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
07:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
07:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
root@asp4736-k1210:~# [/FONT]

---

### Post by vinyvat on 2012-12-18
Solved my intel G4000 + backlight problems on Dell XPS 12 with the following:

With kernel prior to 3.7, requires using kernel boot parameter "nomodeset". With kernel 3.7 and later, add "i915.invert_brightness=1" to the kernel boot

Using 3.7 kernel and other xorg-drivers ontop of 12.10 from [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) 

When running with with "nomodeset", backlight adjustment doesn't work, xrandr doesn't work. with "i915.invert_brightness=1" set, everything works great !

Installation with Ubuntu 12.10 tricky because the graphical install did not seem to pass "nomodeset" to the live cd. Had to install with Ubuntu 12.10 server, manually install into /lib/firmware all the intel wifi firmware drivers, got wifi working. Then installed Xubuntu from command line.

---

