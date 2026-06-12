---
title: "Samsung SCX-4200 scanner does not work on Ubuntu 8.04 Hardy Heron"
date: 2008-04-21
forum: Hardware
---

### Post by tayroni on 2008-04-21
Summary: I have installed the samsung unified driver in gutsy and on hardy. The scanner works on gutsy but NOT on HARDY.

Description: I've installed the driver first using the script provided by samsung, and manually. The manual installation was done because that the script allows /etc read and write by users (I really want to know the name of the programmer who did this mess!)

In both ways: installation by script or manually, the driver for the printer and scanner works on a clean install of gutsy. The same don't happen for hardy: the printer works but the scanner is not recognized by xsane.

Output of sane-find-scanner (both Gutsy and Hardy). Using sudo scanimage -L, the scanner is found on gutsy, but not on hardy.
_______________________________________________________________________________________________________________________________________________________
found USB scanner (vendor=0x04e8 [Samsung], product=0x341b [SCX-4200 Series]) at libusb:002:003
_______________________________________________________________________________________________________________________________________________________


On GUTSY (sudo xsane and sudo scanimage -L WORKS), the relevant lines of /var/log/syslog are
_______________________________________________________________________________________________________________________________________________________
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules 
Apr 21 19:14:25 galileu kernel: [ 1263.159257] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu kernel: [ 1263.246583] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.246596] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.246662] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.352916] lp0: using parport0 (interrupt-driven).
Apr 21 19:14:25 galileu kernel: [ 1263.394944] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules 
Apr 21 19:14:25 galileu kernel: [ 1263.450626] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.450638] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.450702] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.564420] lp0: using parport0 (interrupt-driven).
_______________________________________________________________________________________________________________________________________________________


On HARDY (sudo xsane DOESN'T WORK and sudo scanimage -L don't find the scanner) the relevant lines of /var/log/syslog are
_______________________________________________________________________________________________________________________________________________________
Apr 21 19:11:46 kepler kernel: [ 1166.177485] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.236853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.253490] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.257871] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.275009] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632'). 
Apr 21 19:11:46 kepler rmmod: ERROR: Module ppdev does not exist in /proc/modules 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.282338] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.287454] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632'). 
Apr 21 19:11:46 kepler kernel: [ 1166.453319] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.511863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.516347] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.562628] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.567925] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.589722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.594256] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632'). 
Apr 21 19:17:01 kepler /USR/SBIN/CRON[7696]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
_______________________________________________________________________________________________________________________________________________________


So, please, help me to figure out what's happening with the samsung scx-4200 scanner on hardy. Any help is welcome.


PS: To install the driver manually (best way), only for reference: 

1) Download 20070720152943906_UnifiedLinuxDriver.tar.gz from samsung, extract the files, go to new directory cdroot and type these commands
cp Linux/noarch/at_root/etc/sane.d/smfp.conf /etc/sane.d/
cp -r Linux/noarch/at_opt/share/ppd/* /usr/share/ppd/custom/
cp Linux/i386/at_root/usr/lib/libmfp.so.1.0.1 /usr/lib/
cp Linux/i386/at_root/usr/lib/sane/libsane-smfp.so.1.0.1 /usr/lib/sane/
cp Linux/i386/at_root/usr/lib/cups/backend/mfp /usr/lib/cups/backend/
cp Linux/i386/at_root/usr/lib/cups/filter/* /usr/lib/cups/filter/
cd /usr/lib
ln -s libmfp.so.1.0.1 libmfp.so.1
ln -s libmfp.so.1.0.1 libmfp.so
cd sane
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so.1
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so

2) Edit /etc/sane.d/dll.conf and add the line "smfp" to the end of file. Add yourself to the groups lp and scanner.

3) Reboot

---

### Post by tayroni on 2008-04-24
I DID IT!!!!! The SAMSUNG SCX-4200 now works on HARDY HERON!!!!!!

The problem was the driver software by SAMSUNG looks for the usb device on

/proc/bus/usb/00*/00*

and 8.04 drops support to /proc/bus/usb/00*/00* and port all software to look only on /dev/bus/usb/00*/00*

To reenable support on /proc/bus/usb I edited

/etc/init.d/mountdevsubfs.sh

and modify the lines

#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

to

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

and reboot.

ONE CAVEAT: Using patched /usr/lib/libmfp.so.1.0.1 from [http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian) allows me to use xsane with normal user.

---

### Post by sylvaticus on 2008-06-24
Works like a shame! Thanks!

[OT]How to activate the "thanks" feature of this forum??[/OT]

---

### Post by roccivic on 2008-06-25
Worked perfectly, thank you!

Rouslan

---

### Post by jackbox on 2008-07-05
How do you edit the LDP to /dev/usb.lp0 to use the modified libmfp.so.1.0.1 file so that the scanner works with a normal user?

---

### Post by Benic on 2008-09-17
Yeah ! Finally works ! Thanks

---

### Post by jack frost on 2008-09-21
> **tayroni said:**
> Summary: I have installed the samsung unified driver in gutsy and on hardy. The scanner works on gutsy but NOT on HARDY.

Description: I've installed the driver first using the script provided by samsung, and manually. The manual installation was done because that the script allows /etc read and write by users (I really want to know the name of the programmer who did this mess!)

In both ways: installation by script or manually, the driver for the printer and scanner works on a clean install of gutsy. The same don't happen for hardy: the printer works but the scanner is not recognized by xsane.

Output of sane-find-scanner (both Gutsy and Hardy). Using sudo scanimage -L, the scanner is found on gutsy, but not on hardy.
_______________________________________________________________________________________________________________________________________________________
found USB scanner (vendor=0x04e8 [Samsung], product=0x341b [SCX-4200 Series]) at libusb:002:003
_______________________________________________________________________________________________________________________________________________________


On GUTSY (sudo xsane and sudo scanimage -L WORKS), the relevant lines of /var/log/syslog are
_______________________________________________________________________________________________________________________________________________________
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules 
Apr 21 19:14:25 galileu kernel: [ 1263.159257] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu kernel: [ 1263.246583] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.246596] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.246662] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.352916] lp0: using parport0 (interrupt-driven).
Apr 21 19:14:25 galileu kernel: [ 1263.394944] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules 
Apr 21 19:14:25 galileu kernel: [ 1263.450626] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.450638] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.450702] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.564420] lp0: using parport0 (interrupt-driven).
_______________________________________________________________________________________________________________________________________________________


On HARDY (sudo xsane DOESN'T WORK and sudo scanimage -L don't find the scanner) the relevant lines of /var/log/syslog are
_______________________________________________________________________________________________________________________________________________________
Apr 21 19:11:46 kepler kernel: [ 1166.177485] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.236853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.253490] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.257871] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.275009] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632'). 
Apr 21 19:11:46 kepler rmmod: ERROR: Module ppdev does not exist in /proc/modules 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.282338] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.287454] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632'). 
Apr 21 19:11:46 kepler kernel: [ 1166.453319] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.511863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.516347] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.562628] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.567925] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.589722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632'). 
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.594256] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632'). 
Apr 21 19:17:01 kepler /USR/SBIN/CRON[7696]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
_______________________________________________________________________________________________________________________________________________________


So, please, help me to figure out what's happening with the samsung scx-4200 scanner on hardy. Any help is welcome.


PS: To install the driver manually (best way), only for reference: 

1) Download 20070720152943906_UnifiedLinuxDriver.tar.gz from samsung, extract the files, go to new directory cdroot and type these commands
cp Linux/noarch/at_root/etc/sane.d/smfp.conf /etc/sane.d/
cp -r Linux/noarch/at_opt/share/ppd/* /usr/share/ppd/custom/
cp Linux/i386/at_root/usr/lib/libmfp.so.1.0.1 /usr/lib/
cp Linux/i386/at_root/usr/lib/sane/libsane-smfp.so.1.0.1 /usr/lib/sane/
cp Linux/i386/at_root/usr/lib/cups/backend/mfp /usr/lib/cups/backend/
cp Linux/i386/at_root/usr/lib/cups/filter/* /usr/lib/cups/filter/
cd /usr/lib
ln -s libmfp.so.1.0.1 libmfp.so.1
ln -s libmfp.so.1.0.1 libmfp.so
cd sane
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so.1
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so

2) Edit /etc/sane.d/dll.conf and add the line "smfp" to the end of file. Add yourself to the groups lp and scanner.

3) Reboot
not sure if you want do; but I installed xp virtual machine and just used the scanner that way and just move doc over to shared folder.  To get the usb devices to be seen in virtual machine via virtualbox I found this:

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

I already had virtual box installed so I skipped further down in the how to part once virtual box was already installed.  I would like to use it inside my host os 8.04; but it says the patch for the scanner can make the system unstable. (not sure if that is true or not)

---

### Post by unicko on 2008-09-27
This is me problem:

[INDENT][FONT="Courier New"]  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04e8 [Samsung], product=0x341b [SCX-4200 Series]) at libusb:001:006
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.[/FONT][/INDENT]


But i can't use the scanner... please, help me.

Note: I use the driver software by samsung, i edited /etc/init.d/mountdevsubfs.sh and finaly use the this [fix]("http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian").

---

### Post by rht22696 on 2008-10-16
hi guys iam very new at this can you pls explain in lamins term
how to get my samsung scx-4200 working

i cant even install the driver manually sorry 

i have dl the driver from same samsung and extracted but don't know how to install it

thanks for any help 

jimmy@jimmy-laptop:~$ cp Linux/noarch/at_root/etc/sane.d/smfp.conf /etc/sane.d/
cp: cannot stat `Linux/noarch/at_root/etc/sane.d/smfp.conf': No such file or directory
jimmy@jimmy-laptop:~$ 

this is what i get..??

---

### Post by rht22696 on 2008-10-16
help pls i got the printer to work but how to i call up the script to edit??

in the terminal. i really new at ubuntu and linux for that fact. 

thanks for any help 

jimmy@jimmy-laptop:~$ /etc/init.d/mountdessubfs.sh
bash: /etc/init.d/mountdessubfs.sh: No such file or directory
jimmy@jimmy-laptop:~$ /proc/bus/usb
bash: /proc/bus/usb: is a directory
jimmy@jimmy-laptop:~$ usb edit
bash: usb: command not found
jimmy@jimmy-laptop:~$ /etc/init.d/mountdevsubfs.sh
Warning: mountdevsubfs should be called with the 'start' argument.
jimmy@jimmy-laptop:~$ stat /etc/init.d/mountdevsubfs.sh
  File: `/etc/init.d/mountdevsubfs.sh'
  Size: 1465      	Blocks: 8          IO Block: 4096   regular file
Device: 805h/2053d	Inode: 337106      Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2008-10-16 13:34:26.000000000 -0400
Modify: 2008-04-19 01:05:36.000000000 -0400
Change: 2008-10-13 10:54:46.000000000 -0400
jimmy@jimmy-laptop:~$ 


tell me what i doing wrong..???

---

### Post by EckyBrazzz on 2008-11-05
Hi,

I had the same problem, but resolved it in 8.10 x64

Solution :
```

sudo gedit /etc/fstab

```
and add after the last line
```

none /proc/bus/usb usbfs devgid=1000,devmode=664 0 0

```

Hope it helps someone

Regards,

EckyBrazzz

---

### Post by tayroni on 2008-11-06
I solved doing this:

The same manual for hardy cannot be followed by intrepid because
/etc/init.d/mountdevsubfs.sh was updated.

To reenable support on /proc/bus/usb/00*/00*, add yourself to the groups lp, lpadmin and scanner:

sudo adduser your_login_here lp
sudo adduser your_login_here lpadmin
sudo adduser your_login_here scanner

and edit the file /etc/init.d/mountdevsubfs.sh. ADD THE LINES:

#
# Magic to KEEP /proc/bus/usb working
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

right below the line

domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE

Finally, reboot.

---

