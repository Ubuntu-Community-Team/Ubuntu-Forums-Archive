---
title: "Unable to unmount modem 3G"
date: 2011-04-12
forum: Hardware
---

### Post by bach on 2011-04-12
I was running Ubuntu 10.04 until yesterday on my notebook (DELL Latitude E6510), and my Huawei modem 3G worked flawlessly. The usb-modeswitch and usb-modeswitch-data packages are installed. 

After I upgraded to 10.10, however, I am no longer able to unmount my modem. When I plug it in (usb) it shows up in Network Manager and I can establish a connection using it. No problem there. However, when I try to "safely remove" it (Places -> Computer, then right click on HUAWEI MMC STORAGE and choose "Safely Remove Drive") I get the following message:

------------------

Unable to stop drive

Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory

------------------

The output of lsmod |egrep "usb|option" is:

usb_storage            54050  0 
usbhid                 48035  0 
option                 25324  0 
hid                    91696  1 usbhid
usb_wwan               20552  1 option
usbserial              43106  2 option,usb_wwan
btusb                  18712  2 
bluetooth              74660  9 rfcomm,sco,bnep,l2cap,btusb

Additionally, I am running the same kernel I was running under 10.04:

cribari@darwin:~$ uname -a
Linux darwin 2.6.38-997-generic #201104011244 SMP Fri Apr 1 12:49:23 UTC 2011 x86_64 GNU/Linux

I also notice that the modem icon does not show up in my Desktop (unlike what happened in 10.04). 

Suggestions are welcome.

---

### Post by bach on 2011-04-12
More info: 

cribari@darwin:~$ lsusb | grep Huawei
Bus 002 Device 013: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem



cribari@darwin:~$ dmesg | grep modem
[   94.609399] USB Serial support registered for GSM modem (1-port)
[   94.609552] option 2-1.3:1.0: GSM modem (1-port) converter detected
[   94.609790] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB0
[   94.609803] option 2-1.3:1.1: GSM modem (1-port) converter detected
[   94.609916] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB1
[   94.609950] option: v0.7.2:USB Driver for GSM modems
[  103.958886] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  103.959844] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  104.535545] option 2-1.3:1.0: GSM modem (1-port) converter detected
[  104.535669] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB1
[  104.686059] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  109.385285] option 2-1.3:1.0: GSM modem (1-port) converter detected
[  109.385424] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB0
[  109.385590] option 2-1.3:1.1: GSM modem (1-port) converter detected
[  109.385677] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB1
[  475.213578] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  475.213813] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  773.325573] option 2-1.3:1.0: GSM modem (1-port) converter detected
[  773.325714] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB0
[  773.325886] option 2-1.3:1.1: GSM modem (1-port) converter detected
[  773.325985] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB1
cribari@darwin:~$

---

### Post by bach on 2011-04-12
More info: 

cribari@darwin:~$ dmesg | grep sdb
[   46.976958] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[   62.060290] sd 15:0:0:0: [sdb] Attached SCSI removable disk

cribari@darwin:~$ sudo eject -v /dev/sdb
eject: device name is `/dev/sdb'
eject: expanded name is `/dev/sdb'
eject: `/dev/sdb' is not mounted
eject: `/dev/sdb' is not a mount point
eject: `/dev/sdb' is a multipartition device
eject: trying to eject `/dev/sdb' using CD-ROM eject command
eject: CD-ROM eject command failed
eject: trying to eject `/dev/sdb' using SCSI commands
eject: SCSI eject succeeded

cribari@darwin:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cribari/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cribari)

---

### Post by bach on 2011-04-12
More info: 

[IMG]http://www.de.ufpe.br/~cribari/modem.png[/IMG]

---

### Post by bach on 2011-04-12
More info: The same error happens in Ubuntu 11.04 Beta 1 (which I run from the live CD).

---

### Post by bach on 2011-04-13
More info: The same happens with kernel 2.6.39 RC3:

cribari@darwin:~$ uname -a
Linux darwin 2.6.39-020639rc3-generic #201104120912 SMP Tue Apr 12 09:16:19 UTC 2011 x86_64 GNU/Linux

---

