---
title: "Can not mount htc hero as usb mass storage device in karmic"
date: 2009-11-01
forum: Hardware
---

### Post by bernie9998 on 2009-11-01
The htc hero smart phone (android based) is capable of being used as a usb mass storage device in order to access the memory card within.  This has been working fine with ubuntu upto and including ubuntu karmic-beta with the kernel 2.6.31-12.  However, this is no longer working on the released version of karmic with kernel version 2.6.31-14.

The phone itself does not behave as a usual mass storage device, which could be the reason why this ubuntu version is having trouble.  Normally, it is not immediately detected as a mass storage device when the phone is first plugged in, however it is detected after this mode is enabled on the phone.

The dmesg output when the phone is successfully detected is below.
When the phone is first plugged in:
```

[  370.230083] usb 1-1: new high speed USB device using ehci_hcd and address 6
[  370.396460] usb 1-1: configuration #1 chosen from 1 choice
[  370.422056] scsi3 : SCSI emulation for USB Mass Storage devices
[  370.422517] usb-storage: device found at 6
[  370.422520] usb-storage: waiting for device to settle before scanning
[  375.421929] usb-storage: device scan complete
[  375.424371] scsi 3:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[  375.425304] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  375.446274] sd 3:0:0:0: [sdb] Attached SCSI removable disk

```
Once plugged in, the phone is then manually set to usb mass storage mode and the kernel detects the partitions:
```

[  444.525895] sd 3:0:0:0: [sdb] 3862528 512-byte logical blocks: (1.97 GB/1.84 GiB)
[  444.531263] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  444.540270] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  444.540277]  sdb: sdb1

```

After this point, the device is detected and can be mounted like a normal usb mass storage device.

With the released version of ubuntu karmic, the partition detection does not automatically occur when the phone is switched to mass storage mode.  Partition detection can be done manually with sudo fdisk -l /dev/sdb, after which it can be mounted by root, however when done in this way the device can not be mounted by a non-root user by the usual method, e.g. through the device notifier in kde, etc.

If I can get some assistance in getting my cell phone detected automatically, it would be greatly appreciated.

---

### Post by duartemolha on 2010-03-16
I have the same problem in 10.04.

It was working fine in 9.04 but now only sudo mounting works and I cannot delete or write files to the mounted sd card of the htc hero on nautilus...

Can anyone help?

Cheers

Duarte

---

### Post by AnthonyBeldt on 2010-03-16
i can mount and unmount, but when i try to shutdown the computer, it shows unmount is not possible. I did not face any problem till now but is this a error?

---

### Post by ben.walker on 2010-03-22
> **AnthonyBeldt said:**
> i can mount and unmount, but when i try to shutdown the computer, it shows unmount is not possible. I did not face any problem till now but is this a error?

I just purchased a 4gb Pen Drive of Iball. When i connect it , it asking for format? I formatted the pen drive several time. Whenever i connect it to pc, it asking for format? what is the problem?

---

### Post by joeoshawa on 2010-03-22
i don't know if i am supposed to be posting this here but still figuring out this site so here goes i have been working on mounting my cell phone in linux it is the samsung rant sph-m540 through telus. I have gotten somewhere i believe but i tried mounting it as hdb1 and it is not working this is the message i get on it in dmesg. 
[    1.748951] Initializing USB Mass Storage driver...
[    1.755057] scsi4 : SCSI emulation for USB Mass Storage devices
[    1.755189] usb-storage: device found at 2
[    1.755191] usb-storage: waiting for device to settle before scanning
[    1.755202] usbcore: registered new interface driver usb-storage
[    1.755205] USB Mass Storage support registered.
 i am a linux newbie but as far as i can see linux is seeing my phone and my phone is seeing linux but i just am not mounting it properly if someone could help it would be greatly appreciated

---

### Post by Chame_Wizard on 2010-03-23
Try:```
sudo dmesg|tail
```

```
fdisk -l
```

```
df -h
```

And see what is said!

---

### Post by joeoshawa on 2010-03-23
thanks for the reply 
joe@gator:~$ sudo dmesg|tail
[ 1307.902510] Buffer I/O error on device fd0, logical block 0
[ 1317.301585] end_request: I/O error, dev fd0, sector 0
[ 1317.301600] Buffer I/O error on device fd0, logical block 0
[ 1326.701531] end_request: I/O error, dev fd0, sector 0
[ 1336.102561] end_request: I/O error, dev fd0, sector 0
[ 1345.490014] end_request: I/O error, dev fd0, sector 0
[ 1345.490029] Buffer I/O error on device fd0, logical block 0
[ 1354.881499] end_request: I/O error, dev fd0, sector 0
[ 1354.881513] Buffer I/O error on device fd0, logical block 0
[ 1364.281349] end_request: I/O error, dev fd0, sector 0
joe@gator:~$ fdisk -l
joe@gator:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/nvidia_dcdbddia5
                      459G   37G  399G   9% /
udev                 1005M  256K 1005M   1% /dev
none                 1005M  5.2M 1000M   1% /dev/shm
none                 1005M  276K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw

thanks

---

### Post by peter.hopkins on 2010-03-28
> **Chame_Wizard said:**
> Try:```
sudo dmesg|tail
``````
fdisk -l
``````
df -h
```And see what is said!

Thanks, i have also similar type problem. Your guidance help me to sort out the issue.

---

### Post by lord_nougat on 2010-08-04
I encountered a similar issue; the resolution came as quite a surprise to me though!

I occasionally carry my phone in my pocket, and in my pocket there is sometimes pocket lint... well, there was a truly tenacious bit of pocket lint packed tightly into the very deepest recesses of the device's USB port, barely visible under a most powerful lamp. After wasting a lunch break carefully fishing out tiny fragments of lint with a staple, it now mounts with no difficulty at all.

---

