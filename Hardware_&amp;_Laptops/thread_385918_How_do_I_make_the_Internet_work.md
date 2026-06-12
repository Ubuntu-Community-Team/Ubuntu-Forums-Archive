---
title: "How do I make the Internet work?"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by jmagick07 on 2007-03-16
On my laptop (Gateway) I have a build-in Wi-Fi thing, I can't seem to get Ubuntu to detect it and connect to a Wi-Fi connection to get online.

Any help?

**[COLOR="Red"]Edit:  Problem solved, thanks everyone for your help :)[/COLOR]**

---

### Post by jmagick07 on 2007-03-16
I entered the SSID (It says ESSID on ubuntu, but my router labels it as SSID, unless those are different?) and the Hex password, but it won't connect. :(

---

### Post by IcemanV9 on 2007-03-16
It would be great if you can install [[COLOR="Orange"]**Network-Manager**[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/NetworkManager"). It will help you with wifi stuff.

```
sudo aptitude install network-manager
```

---

### Post by ssavelan on 2007-03-16
Perhaps you can get a wired connection so that you can use the synaptic package manager to acquire the packages that you might need.

Another choice, that I have had great luck with is:

sudo apt-get install knetworkmanager

I usually like gnome and xfce for everything, but the knetworkmanager (kde0 is a big exception.  It is the most carefree and easy that I have found.

Good Luck!

---

### Post by jmagick07 on 2007-03-16
> **ssavelan said:**
> sudo apt-get install knetworkmanager

When I enter stuff like that and hit enter, and it asked for password, the keyboard doesn't work.  Like it won't let me enter it.

When I first installed ubuntu, I could, recently it doesn't let me and I dunno why.  It won't even let me paste stuff in.

---

### Post by Motoxrdude on 2007-03-16
just type in your password and hit enter. Nothing will show up btw when typing in passwords, but it is actually typing. It's a security thing.

---

### Post by ssavelan on 2007-03-16
> **jmagick07 said:**
> When I enter stuff like that and hit enter, and it asked for password, the keyboard doesn't work.  Like it won't let me enter it.

When I first installed ubuntu, I could, recently it doesn't let me and I dunno why.  It won't even let me paste stuff in.

yeah, no stars or anything come up.  you just have to type and hit enter.

You can also do it with the synaptic package manager.... or possible add/remove..

---

### Post by jmagick07 on 2007-03-16
ok well I tried that and it didn't work.

I did a search for the network card I got on here, and found [this post](http://ubuntuforums.org/showthread.php?t=197102) (got the same one they mention in that post).  Tried the steps, and couldn't get it to work :(

---

### Post by ssavelan on 2007-03-17
> **jmagick07 said:**
> ok well I tried that and it didn't work.

I did a search for the network card I got on here, and found [this post](http://ubuntuforums.org/showthread.php?t=197102) (got the same one they mention in that post).  Tried the steps, and couldn't get it to work :(

*that* meaning putting in your password or using knetworkmanager?

---

### Post by ssavelan on 2007-03-17
Did you do anything before following the instructions from compwiz?

---

### Post by jmagick07 on 2007-03-17
> **ssavelan said:**
> Did you do anything before following the instructions from compwiz?

I tried a whole bunch of stuff to get it to work.  I have my laptop on a wired connection right now so I could copy/paste the log.

> Log of echo Script version: 0.1.2 
Sat Mar 17 09:26:37 2007

Script version: 0.1.2

Sat Mar 17 09:26:37 2007
----------------
Log of lspci 
Sat Mar 17 09:26:37 2007

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:06.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
01:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Sat Mar 17 09:26:37 2007
----------------
Log of echo /etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e 
Sat Mar 17 09:26:37 2007

/etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e

Sat Mar 17 09:26:37 2007
----------------
Log of cat /etc/issue 
Sat Mar 17 09:26:37 2007

Ubuntu 6.10 \n \l


Sat Mar 17 09:26:37 2007
----------------
Log of ps -e 
Sat Mar 17 09:26:37 2007

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 migration/1
    6 ?        00:00:00 ksoftirqd/1
    7 ?        00:00:00 watchdog/1
    8 ?        00:00:00 events/0
    9 ?        00:00:00 events/1
   10 ?        00:00:00 khelper
   11 ?        00:00:00 kthread
   14 ?        00:00:00 kblockd/0
   15 ?        00:00:00 kblockd/1
   16 ?        00:00:00 kacpid
   17 ?        00:00:00 kacpi_notify
  107 ?        00:00:00 kseriod
  146 ?        00:00:00 pdflush
  147 ?        00:00:00 pdflush
  148 ?        00:00:00 kswapd0
  149 ?        00:00:00 aio/0
  150 ?        00:00:00 aio/1
  774 ?        00:00:00 kirqd
 1736 ?        00:00:00 khpsbpkt
 1744 ?        00:00:00 khubd
 1753 ?        00:00:00 knodemgrd_0
 1825 ?        00:00:00 kjournald
 1907 ?        00:00:00 logd
 2053 ?        00:00:00 udevd
 2815 ?        00:00:00 shpchpd
 2915 ?        00:00:00 kpsmoused
 2927 ?        00:00:00 pccardd
 3206 ?        00:00:00 wrap_wq
 3207 ?        00:00:00 ndis_wq
 3696 tty1     00:00:00 getty
 3697 tty2     00:00:00 getty
 3699 tty3     00:00:00 getty
 3701 tty4     00:00:00 getty
 3702 tty5     00:00:00 getty
 3703 tty6     00:00:00 getty
 3955 ?        00:00:00 acpid
 4084 ?        00:00:00 dd
 4086 ?        00:00:00 klogd
 4160 ?        00:00:00 gdm
 4161 ?        00:00:00 gdm
 4177 tty7     00:00:24 Xorg
 4225 ?        00:00:00 hpiod
 4243 ?        00:00:00 python
 4295 ?        00:00:00 dbus-daemon
 4310 ?        00:00:02 hald
 4311 ?        00:00:00 hald-runner
 4317 ?        00:00:00 hald-addon-acpi
 4320 ?        00:00:00 hald-addon-keyb
 4324 ?        00:00:00 hald-addon-keyb
 4334 ?        00:00:00 hald-addon-keyb
 4338 ?        00:00:00 hald-addon-keyb
 4341 ?        00:00:00 hald-addon-keyb
 4359 ?        00:00:00 hald-addon-stor
 4376 ?        00:00:00 dhcdbd
 4393 ?        00:00:00 NetworkManager
 4407 ?        00:00:00 NetworkManagerD
 4433 ?        00:00:00 perl
 4468 ?        00:00:00 ondemand
 4507 ?        00:00:00 hcid
 4515 ?        00:00:00 sdpd
 4527 ?        00:00:00 krfcommd
 4580 ?        00:00:00 atd
 4593 ?        00:00:00 cron
 4721 ?        00:00:00 dhclient
 4765 ?        00:00:00 x-session-manag
 4800 ?        00:00:00 ssh-agent
 4803 ?        00:00:00 dbus-launch
 4804 ?        00:00:00 dbus-daemon
 4806 ?        00:00:00 gconfd-2
 4809 ?        00:00:00 gnome-keyring-d
 4812 ?        00:00:00 gnome-settings-
 4821 ?        00:00:00 sh
 4822 ?        00:00:00 esd
 4829 ?        00:00:03 metacity
 4834 ?        00:00:03 gnome-panel
 4836 ?        00:00:02 nautilus
 4840 ?        00:00:00 bonobo-activati
 4841 ?        00:00:00 gnome-volume-ma
 4849 ?        00:00:00 gnome-vfs-daemo
 4851 ?        00:00:00 update-notifier
 4857 ?        00:00:00 evolution-alarm
 4861 ?        00:00:00 nm-applet
 4865 ?        00:00:00 gnome-cups-icon
 4868 ?        00:00:00 gnome-power-man
 4887 ?        00:00:00 trashapplet
 4902 ?        00:00:00 mapping-daemon
 4920 ?        00:00:00 gnome-netstatus
 4922 ?        00:00:00 mixer_applet2
 4933 ?        00:00:18 firefox-bin
 4944 ?        00:00:00 gnome-screensav
 4976 ?        00:00:00 dhclient3
 5176 ?        00:00:00 cupsd
 5486 ?        00:00:00 syslogd
 5519 ?        00:00:00 notification-da
 5837 ?        00:00:00 gnome-terminal
 5842 ?        00:00:00 gnome-pty-helpe
 5843 pts/0    00:00:00 sh
 5845 pts/0    00:00:00 sh
 5869 pts/0    00:00:00 logsave
 5870 pts/0    00:00:00 ps

Sat Mar 17 09:26:37 2007
----------------
Log of echo Edgy final release detected. 
Sat Mar 17 09:26:37 2007

Edgy final release detected.

Sat Mar 17 09:26:37 2007
----------------
Log of rmmod ndiswrapper 
Sat Mar 17 09:26:37 2007

ERROR: Removing 'ndiswrapper': Operation not permitted
rmmod died with exit status 255

Sat Mar 17 09:26:37 2007
----------------
Log of rmmod bcm43xx 
Sat Mar 17 09:26:37 2007

ERROR: Module bcm43xx does not exist in /proc/modules
rmmod died with exit status 1

Sat Mar 17 09:26:37 2007
----------------
Log of echo Edgy 
Sat Mar 17 09:26:37 2007

Edgy

Sat Mar 17 09:26:37 2007
----------------
Log of apt-get --assume-yes install ndiswrapper-common ndiswrapper-utils-1.8 
Sat Mar 17 09:26:37 2007

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
apt-get died with exit status 100

Sat Mar 17 09:26:37 2007
----------------
Log of ndiswrapper -e bcmwl5 
Sat Mar 17 09:26:37 2007

Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permission denied at /usr/sbin/ndiswrapper-1.8 line 175
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied at /usr/sbin/ndiswrapper-1.8 line 175
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4319.5.conf: Permission denied at /usr/sbin/ndiswrapper-1.8 line 175
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied at /usr/sbin/ndiswrapper-1.8 line 175
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4301.5.conf: Permission denied at /usr/sbin/ndiswrapper-1.8 line 175

Sat Mar 17 09:26:37 2007
----------------
Log of ndiswrapper -e bcmwl5a 
Sat Mar 17 09:26:37 2007

Driver bcmwl5a is not installed.Use -l to list installed drivers

Sat Mar 17 09:26:37 2007
----------------
Log of ndiswrapper -l 
Sat Mar 17 09:26:37 2007

Installed drivers:
bcmwl5		driver installed, hardware present 
ndiswrapper died with exit status 1

Sat Mar 17 09:26:38 2007
----------------
Log of echo You appear to have an i386 system...installing the i386 drivers... 
Sat Mar 17 09:26:38 2007

You appear to have an i386 system...installing the i386 drivers...

Sat Mar 17 09:26:38 2007
----------------
Log of tar -xf drivers-32.tar.gz 
Sat Mar 17 09:26:38 2007

tar: drivers-32.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar died with exit status 2

Sat Mar 17 09:26:38 2007
----------------
Log of ndiswrapper -i bcmwl5.inf 
Sat Mar 17 09:26:38 2007

bcmwl5 is already installed. Use -e to remove it
ndiswrapper died with exit status 255

Sat Mar 17 09:26:38 2007
----------------
Log of modprobe ndiswrapper 
Sat Mar 17 09:26:38 2007


Sat Mar 17 09:26:38 2007
----------------
Log of iwconfig 
Sat Mar 17 09:26:38 2007

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Sat Mar 17 09:26:38 2007
----------------
Log of ifconfig 
Sat Mar 17 09:26:38 2007

eth0      Link encap:Ethernet  HWaddr 00:03:25:2B:CD:E7  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe2b:cde7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2031 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1547609 (1.4 MiB)  TX bytes:316315 (308.9 KiB)
          Interrupt:193 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:45:6D:B0  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:e00f6000-e00f8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


Sat Mar 17 09:26:38 2007
----------------
Log of iwlist scan 
Sat Mar 17 09:26:38 2007

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      No scan results

Sat Mar 17 09:26:38 2007
----------------


---

### Post by ssavelan on 2007-03-17
you might try *gasp* creating a new partition of ubuntu and following compwiz's instructions from a mint install... sometimes you can tangle the system beyond convenient repair....

It's always nice to have a couple of installs in order to experiment without worry.

---

### Post by jmagick07 on 2007-03-17
I did a fresh install, did the instructions.  This time a "Wireless" option isn't even listed in System/Administration/Networking

Here's the new log

> Log of echo Script version: 0.1.2 
Sat Mar 17 23:42:30 2007

Script version: 0.1.2

Sat Mar 17 23:42:30 2007
----------------
Log of lspci 
Sat Mar 17 23:42:30 2007

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:06.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
01:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Sat Mar 17 23:42:30 2007
----------------
Log of echo /etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e 
Sat Mar 17 23:42:30 2007

/etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e

Sat Mar 17 23:42:30 2007
----------------
Log of cat /etc/issue 
Sat Mar 17 23:42:30 2007

Ubuntu 6.10 \n \l


Sat Mar 17 23:42:30 2007
----------------
Log of ps -e 
Sat Mar 17 23:42:30 2007

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 migration/1
    6 ?        00:00:00 ksoftirqd/1
    7 ?        00:00:00 watchdog/1
    8 ?        00:00:00 events/0
    9 ?        00:00:00 events/1
   10 ?        00:00:00 khelper
   11 ?        00:00:00 kthread
   14 ?        00:00:00 kblockd/0
   15 ?        00:00:00 kblockd/1
   16 ?        00:00:00 kacpid
   17 ?        00:00:00 kacpi_notify
  107 ?        00:00:00 kseriod
  146 ?        00:00:00 pdflush
  147 ?        00:00:00 pdflush
  148 ?        00:00:00 kswapd0
  149 ?        00:00:00 aio/0
  150 ?        00:00:00 aio/1
  774 ?        00:00:00 kirqd
 1732 ?        00:00:00 khubd
 1750 ?        00:00:00 khpsbpkt
 1780 ?        00:00:00 knodemgrd_0
 1824 ?        00:00:00 kjournald
 1906 ?        00:00:00 logd
 2052 ?        00:00:00 udevd
 2828 ?        00:00:00 shpchpd
 2836 ?        00:00:00 kpsmoused
 3053 ?        00:00:00 pccardd
 3718 tty1     00:00:00 getty
 3719 tty2     00:00:00 getty
 3721 tty3     00:00:00 getty
 3723 tty4     00:00:00 getty
 3724 tty5     00:00:00 getty
 3725 tty6     00:00:00 getty
 3986 ?        00:00:00 acpid
 4115 ?        00:00:00 dd
 4117 ?        00:00:00 klogd
 4191 ?        00:00:00 gdm
 4208 ?        00:00:00 gdm
 4209 tty7     00:00:01 Xorg
 4232 ?        00:00:00 cupsd
 4257 ?        00:00:00 hpiod
 4277 ?        00:00:00 python
 4327 ?        00:00:00 dbus-daemon
 4342 ?        00:00:02 hald
 4343 ?        00:00:00 hald-runner
 4351 ?        00:00:00 hald-addon-acpi
 4354 ?        00:00:00 hald-addon-keyb
 4358 ?        00:00:00 hald-addon-keyb
 4362 ?        00:00:00 hald-addon-keyb
 4366 ?        00:00:00 hald-addon-keyb
 4369 ?        00:00:00 hald-addon-keyb
 4389 ?        00:00:00 hald-addon-stor
 4407 ?        00:00:00 perl
 4439 ?        00:00:00 ondemand
 4478 ?        00:00:00 hcid
 4486 ?        00:00:00 sdpd
 4498 ?        00:00:00 krfcommd
 4518 ?        00:00:00 anacron
 4532 ?        00:00:00 atd
 4545 ?        00:00:00 cron
 4676 ?        00:00:01 x-session-manag
 4711 ?        00:00:00 ssh-agent
 4714 ?        00:00:00 dbus-launch
 4715 ?        00:00:00 dbus-daemon
 4717 ?        00:00:00 gconfd-2
 4720 ?        00:00:00 gnome-keyring-d
 4723 ?        00:00:00 gnome-settings-
 4742 ?        00:00:00 sh
 4743 ?        00:00:00 esd
 4750 ?        00:00:00 metacity
 4755 ?        00:00:01 gnome-panel
 4757 ?        00:00:02 nautilus
 4761 ?        00:00:00 bonobo-activati
 4762 ?        00:00:00 gnome-volume-ma
 4770 ?        00:00:00 gnome-vfs-daemo
 4772 ?        00:00:00 update-notifier
 4778 ?        00:00:00 evolution-alarm
 4788 ?        00:00:00 gnome-cups-icon
 4795 ?        00:00:00 gnome-power-man
 4800 ?        00:00:00 trashapplet
 4819 ?        00:00:00 mapping-daemon
 4826 ?        00:00:00 gnome-netstatus
 4828 ?        00:00:00 mixer_applet2
 4844 ?        00:00:00 gnome-screensav
 4852 ?        00:00:00 dhclient3
 5106 ?        00:00:00 gnome-terminal
 5111 ?        00:00:00 gnome-pty-helpe
 5112 pts/0    00:00:00 bash
 5453 ?        00:00:00 syslogd
 5470 pts/0    00:00:00 sh
 5496 pts/0    00:00:00 logsave
 5497 pts/0    00:00:00 ps

Sat Mar 17 23:42:30 2007
----------------
Log of echo Edgy final release detected. 
Sat Mar 17 23:42:30 2007

Edgy final release detected.

Sat Mar 17 23:42:30 2007
----------------
Log of rmmod ndiswrapper 
Sat Mar 17 23:42:30 2007

ERROR: Module ndiswrapper does not exist in /proc/modules
rmmod died with exit status 1

Sat Mar 17 23:42:30 2007
----------------
Log of rmmod bcm43xx 
Sat Mar 17 23:42:30 2007


Sat Mar 17 23:42:30 2007
----------------
Log of echo Edgy 
Sat Mar 17 23:42:30 2007

Edgy

Sat Mar 17 23:42:30 2007
----------------
Log of apt-get --assume-yes install ndiswrapper-common ndiswrapper-utils-1.8 
Sat Mar 17 23:42:30 2007

Reading package lists...
Building dependency tree...
Reading state information...
E: Couldn't find package ndiswrapper-common
apt-get died with exit status 100

Sat Mar 17 23:42:30 2007
----------------
Log of ndiswrapper -e bcmwl5 
Sat Mar 17 23:42:30 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Sat Mar 17 23:42:30 2007
----------------
Log of ndiswrapper -e bcmwl5a 
Sat Mar 17 23:42:30 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Sat Mar 17 23:42:30 2007
----------------
Log of ndiswrapper -l 
Sat Mar 17 23:42:30 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Sat Mar 17 23:42:30 2007
----------------
Log of echo You appear to have an i386 system...installing the i386 drivers... 
Sat Mar 17 23:42:30 2007

You appear to have an i386 system...installing the i386 drivers...

Sat Mar 17 23:42:30 2007
----------------
Log of tar -xf drivers-32.tar.gz 
Sat Mar 17 23:42:30 2007


Sat Mar 17 23:42:30 2007
----------------
Log of ndiswrapper -i bcmwl5.inf 
Sat Mar 17 23:42:30 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Sat Mar 17 23:42:30 2007
----------------
Log of modprobe ndiswrapper 
Sat Mar 17 23:42:30 2007


Sat Mar 17 23:42:30 2007
----------------
Log of iwconfig 
Sat Mar 17 23:42:30 2007

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


Sat Mar 17 23:42:30 2007
----------------
Log of ifconfig 
Sat Mar 17 23:42:30 2007

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5140 (5.0 KiB)  TX bytes:5140 (5.0 KiB)


Sat Mar 17 23:42:30 2007
----------------
Log of iwlist scan 
Sat Mar 17 23:42:30 2007

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


Sat Mar 17 23:42:30 2007
----------------


---

### Post by ssavelan on 2007-03-18
instead of iwconfig, I would use knetworkmanager (from a fresh install).

sudo apt-get install knetworkmanager

It will be in the apps drop-down.  I have no experience with the ndiswrapper.  I have a friend that does though.  I'm going to shoot him this thread and see if he can help.

I don't think that you should have a problem.  I've set a few laptops up and... fortunately (although I don't know anything about wireless because of it) knetworkmanager has always made it too easy.

The last person I helped out with this simple advice was here:

"
WickedAwsome has just replied to a thread you have subscribed to entitled - Wireless Issues! supported hardware noot working - in the Hardware & Laptops forum of Ubuntu Forums.

This thread is located at:
[http://ubuntuforums.org/showthread.php?t=385106&goto=newpost]("http://ubuntuforums.org/showthread.php?t=385106&goto=newpost")

Here is the message that has just been posted:
***************
yep, this network manager works great, and im running in in Gnome, which I prefer to kde after trying both.  the apt-get install ipconfig returned that no package was listed under that name.  So, I guess I wont worry about it as It seems that kde's tool works good.

Thanks everyone for your help, UF has been great in helping me make the transition to linux
***************
"

---

### Post by jmagick07 on 2007-03-19
compwiz18 helped me with [this post](http://ubuntuforums.org/showpost.php?p=2321456&postcount=1222) :)

problem solved

---

### Post by ssavelan on 2007-03-19
> **jmagick07 said:**
> compwiz18 helped me with [this post](http://ubuntuforums.org/showpost.php?p=2321456&postcount=1222) :)

problem solved

Sweet!  I'm going to send that link to my ndiswrapper friends..

Thanks a bunch.

---

