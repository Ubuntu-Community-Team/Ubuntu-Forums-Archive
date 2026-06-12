---
title: "help needed from the experts and techs"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by abh83 on 2007-02-26
Hey there,

During the installation phase of ubuntu edgy a couple days ago  i received an error message (see screen shot "install1" below).

But the installation continued normally and it seems ubuntu is running fine. I haven't really noticed any serious issues.

However, when i start up my computer, at the ubuntu startup screen were the progress bar loads it seems to take a long time to load. The progress bar progresses halfway and then stops for about a minute or two.

Also when i press cntrl-alt-f1 i see another error message (see screen shot "startup2" below).

help is greatly appreciated!
ABH

---

### Post by abh83 on 2007-02-26
[SIZE="4"][COLOR="Red"]i also forgot to mention that at the first start up right after the installation of ubuntu i recieved the error messaged: failed to initialize HAL![/COLOR][/SIZE]

---

### Post by Dylnuge on 2007-02-26
Start Ubuntu in Recovery Mode (Select it from the GRUB menu).

From there, type gdm.

Login as usual.

Post the results of an lspci and a fdisk -l

Don't post screenshots of your error messages, just type them out. Its eaiser to read and saves space.

---

### Post by abh83 on 2007-02-26
I appreciate your help!

> **Dylnuge said:**
> Start Ubuntu in Recovery Mode (Select it from the GRUB menu).

From there, type gdm.

Login as usual.

Post the results of an lspci and a fdisk -l

Don't post screenshots of your error messages, just type them out. Its eaiser to read and saves space.

firstly: after loging into Recovery mod i got all sorts of error message such as:
-CPU frequency scaling unsupported ...
-Can't acess ACPI events /var/run/acpid. socket! ...
-failed to initialize HAL!

secondly, here is the lspci and fdisk -l info
lspci:
> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d7 (rev a1)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)


fdisk -l:
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10729    86180661    7  HPFS/NTFS
/dev/sda2           10730       14432    29744347+  83  Linux
/dev/sda3           14433       14593     1293232+   5  Extended
/dev/sda5           14433       14593     1293201   82  Linux swap / Solaris


hope this helps

ABH

[COLOR="Red"]EDIT: corrected minor mistakes[/COLOR]

---

### Post by abh83 on 2007-02-27
help anyone?

---

### Post by Dylnuge on 2007-02-27
Ok, sorry that I can't reply immediatly always, but don't worry because I am watching your thread.

I need you to post a copy of your /etc/fstab file. It looks as if something is mounting at boot that may be causing the problem. Remove all USB devices, CD-ROMs, DVD-ROMs and floppy disks.

Next, reload and run this command:
```
less /etc/fstab

```

And post the results. Also, make sure that the DBUS service is active. Type this command:
```
less /var/run/dbus 
```
And if the file does not exist, then post that here. (If it does, there is no need to post its contents).

If you need your computer ASAP, you will need to run this command, unfortunatly:
```
sudo aptitude remove hal
```

Make a list of every dependancy it removes with HAL, so you can reinstall them if you get it fixed.

---

### Post by abh83 on 2007-02-27
Hey no probs!

I&#8217;m currently writing to you from my windows xp partition since the desktop in ubuntu has been deinstalled.

> If you need your computer ASAP, you will need to run this command, unfortunatly:

Did you by any chance mean if you _don&#8217;t_ need...? :D

Anyway,

1st part:

Less /etc/fstab:
> 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b3e3241a-a6e8-47cb-8cd2-c0923698a9f7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4d83e36a-354d-461b-a2b6-374f12eb6faf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
~
~
~
(END)



2nd part:


dbus folder exists.
> 
/var/run/dbus is a directory


3rd part

> sudo aptitude remove hal applied!

I'm no pro but it looks somewhat faulty to me. Let me know if i should post it here.

thx
ABH

---

### Post by Dylnuge on 2007-02-27
> **abh83 said:**
> Did you by any chance mean if you _don’t_ need...? :D

No, I mean that that command will remove some very nice features from your computer-if you are having extreme problems that should fix some stuff.

Fstab looks right, assuming thats your partitioning layout.

Removing HAL should help...you did get a list of depandancies that will be removed with it, correct? If not, I can always get one.

What do you mean by "looks somewhat faulty." The desktop or the error message or something else?

OK, I need to narrow this problem down. These questions should help:

1. Did you have Ubuntu running successfully at any time on your computer?
2. Did you make any changes to your computer recently, excepting installation of Ubuntu?

---

### Post by abh83 on 2007-02-28
This is a brand new notebook. When i first got it i installed dapper to test. I can't recall seeing the same error messages. However, back then the hdd was in FAT32 format and had a copy of windows preinstalled on it. Then i reformatted the whole thing into ntfs and installed my own copy of winxp and edgy.

Both OS work fine only edgy gives me the error message (second screen shot in 1st post) and loads very slwoly. However, after it is done loading it seems to work fine.

I haven't upgraded my system in anyway or form. No new hardwares added. I have a removable 5-in-1 card reader which i use occasionally to copy data on my (mobile phone's) memory stick. I have a typhoon usb optical mouse attached and an external hdd which i only turn on when i need it.

this seems faulty:

sudo aptitude remove hal:
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done     
The following packages are BROKEN:
  gnome-power-manager gnome-volume-manager hal-device-manager
  hwdb-client-common network-manager ubuntu-desktop update-notifier
The following packages will be REMOVED:
  hal
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 1139kB will be freed.
The following packages have unmet dependencies:
  network-manager: Depends: hal (>= 0.5.0) but it is not installable
  gnome-power-manager: Depends: hal but it is not installable
  ubuntu-desktop: Depends: hal but it is not installable
  update-notifier: Depends: hal but it is not installable
  hwdb-client-common: Depends: hal but it is not installable
  gnome-volume-manager: Depends: hal (>= 0.5.7.1-0ubuntu4) but it is not installable
  hal-device-manager: Depends: hal but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
gnome-power-manager
gnome-session
gnome-volume-manager
hal-device-manager
hwdb-client-common
hwdb-client-gnome
network-manager
network-manager-gnome
ubuntu-desktop
update-notifier

Leave the following dependencies unresolved:
apport-gtk recommends update-notifier
gnome-control-center recommends gnome-session
gnome-panel recommends gnome-session
Score is -4060

Accept this solution? [Y/n/q/?]

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  gnome-power-manager gnome-session gnome-volume-manager hal-device-manager hwdb-client-common
  hwdb-client-gnome network-manager network-manager-gnome ubuntu-desktop update-notifier
The following packages will be REMOVED:
  gnome-power-manager gnome-session gnome-volume-manager hal hal-device-manager hwdb-client-common
  hwdb-client-gnome network-manager network-manager-gnome ubuntu-desktop update-notifier
0 packages upgraded, 0 newly installed, 11 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 20.4MB will be freed.
Do you want to continue? [Y/n/?]

Writing extended state information... Done
(Reading database ... 147809 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing gnome-session ...
Removing gnome-power-manager ...
Removing gnome-volume-manager ...
Removing update-notifier ...
Removing network-manager-gnome ...
Removing network-manager ...
 * Stopping NetworkManager daemon                                                                 [ ok ]
 * Stopping NetworkManager dispatcher                                                             [ ok ]
Removing hal-device-manager ...
Removing hwdb-client-gnome ...
Removing hwdb-client-common ...
Removing hal ...
 * Stopping Hardware abstraction layer hald                                                       [ ok ]
 * Reloading system message bus config                                                            [ ok ]



hope this helps

thx
ABH

---

### Post by abh83 on 2007-03-01
*bump*

---

### Post by Dylnuge on 2007-03-01
I am sorry to say that I have never seen this kind of problem before. Are you still experiancing difficulties after removing HAL?

What is the model of your computer? Ex. Dell XPS M1710.

---

### Post by Dylnuge on 2007-03-03
You still there?

---

### Post by abh83 on 2007-03-05
Hey there Dylnuge,

thanks for your time and effort!! But i decided to reinstall Ubuntu and start fresh. I think the error message in the first post (1st screen shot: install1.jpg) is related to my SATA hdd and matrix storage controllers which are also causing me problems in Windows. And the slow start-up issue relates to my cooling pad which i had plugged into the usb when i first installed Ubuntu.

Currently every thing seems stable.... i hope! ;)

thx
ABH

---

