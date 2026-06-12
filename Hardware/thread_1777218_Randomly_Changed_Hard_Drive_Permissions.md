---
title: "Randomly Changed Hard Drive Permissions"
date: 2011-06-07
forum: Hardware
---

### Post by cyberhood on 2011-06-07
Before the problem: my external hard drive plugged into my computer via USB and everything worked just fine for years. 

The problem: Just a few days ago the external drive suddenly became read only whenever I plug it in. I'm still using the same Ubuntu version as before, didn't do any updates or make any changes. Right now I can see and open files which are on the drive just fine. However I am not allowed to add new files or edit/delete old ones.

The first thing I tried: I immediately downloaded Storage Device Manager (SDM) from Synaptic and played around with it, but I can't find out how to change to permissions of the drive using this program. I'd prefer to learn how to do it with SDM before having to mess around in the terminal and text editor. I knooow, I'm a n00b.

Errors: 
1. Whenever I plug the drive in this error pops up:
“Unable to mount [name of drive]
Error mounting: mount exited with exit code 1: helper failed with:

mount: only root can mount /dev/sdb1 on /media/sdb1”

2. After messing around with SDM I get this error when I start up the machine, just before the log in screen:
“The disk drive for /media/sdb1 is not ready yet or not present.
Continue to wait; or Press S to ski mounting or M for manual recovery”

any help would be appreciated,
thanks in advance

---

### Post by cyberhood on 2011-06-08
It's been 24 hours

TTT

anyone?

---

### Post by matt_symes on 2011-06-08
Hi

Plug the device in and the open a terminal and type

```
dmesg | tail -n 40
```

Post the results back here. It may be a hardware issue if nothing has changed on your system.

Kind regards

---

### Post by cyberhood on 2011-06-08
Thanks Matt...

```
:~$ dmesg | tail -n 40
[   32.487914] Registered led device: iwl-phy0::radio
[   32.487938] Registered led device: iwl-phy0::assoc
[   32.487996] Registered led device: iwl-phy0::RX
[   32.488033] Registered led device: iwl-phy0::TX
[   32.500801] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.502459] r8169: eth0: link down
[   32.502582] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   40.328360] ppdev: user-space parallel port driver
[   45.352162] padlock: VIA PadLock not detected.
[   50.925056] CE: hpet increasing min_delta_ns to 15000 nsec
[   54.121589] wlan0: direct probe to AP 00:02:cf:b9:62:fe (try 1)
[   54.121636] wlan0: deauthenticating from 00:02:cf:b9:62:fe by local choice (reason=3)
[   54.121686] wlan0: direct probe to AP 00:02:cf:b9:62:fe (try 1)
[   54.124943] wlan0: direct probe responded
[   54.124948] wlan0: authenticate with AP 00:02:cf:b9:62:fe (try 1)
[   54.129457] wlan0: authenticated
[   54.129482] wlan0: associate with AP 00:02:cf:b9:62:fe (try 1)
[   54.131861] wlan0: RX AssocResp from 00:02:cf:b9:62:fe (capab=0x471 status=0 aid=2)
[   54.131865] wlan0: associated
[   54.133282] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   65.040020] wlan0: no IPv6 routers present
[  598.580194] usb 1-4: new high speed USB device using ehci_hcd and address 3
[  598.715347] usb 1-4: configuration #1 chosen from 1 choice
[  599.426583] Initializing USB Mass Storage driver...
[  599.426859] scsi4 : SCSI emulation for USB Mass Storage devices
[  599.427040] usb-storage: device found at 3
[  599.427044] usb-storage: waiting for device to settle before scanning
[  599.427065] usbcore: registered new interface driver usb-storage
[  599.427071] USB Mass Storage support registered.
[  604.424489] usb-storage: device scan complete
[  604.425164] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[  604.428397] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  604.429740] sd 4:0:0:0: [sdb] 15679488 512-byte logical blocks: (8.02 GB/7.47 GiB)
[  604.432836] sd 4:0:0:0: [sdb] Write Protect is off
[  604.432844] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  604.432850] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  604.436144] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  604.436154]  sdb: sdb1
[  604.540622] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  604.540633] sd 4:0:0:0: [sdb] Attached SCSI removable disk
```

---

### Post by matt_symes on 2011-06-08
Hi

Your drive is being recognised, so that is not the problem.

Next thing to look at. 

What is the filing system on your hard drive ?

```
sudo blkid
```

If it extX file system then run fsck on it. If you need instruction on how to do this then post back. Make sure the device is not mounted.

Kind regards

---

### Post by cyberhood on 2011-06-09
> **matt_symes said:**
> Hi

Your drive is being recognised, so that is not the problem.

Next thing to look at. 

What is the filing system on your hard drive ?

```
sudo blkid
```

If it extX file system then run fsck on it. If you need instruction on how to do this then post back. Make sure the device is not mounted.

Kind regards
*Note* I plugged this drive into another machine running Ubuntu last night and it worked just fine with all the permissions. All my other external hard drives started having the same problem at the same time on the first machine. They all work fine on the other machine. I'm assuming then that there's no problem with my drives. This is my thumb drive that I'm experiencing the same problems with:

```
sudo blkid
/dev/sdb1: LABEL="KINGSTON" UUID="3433-3231" TYPE="vfat"
```

I don't think any of the drives are extX; I bought them and formatted them all back in the day when I was using Windows.

cheers

---

### Post by matt_symes on 2011-06-09
Hi

You might want to run chkdsk.exe on the drive to be sure if you have windows handy.

What happens if you mount it manually from the terminal bypassing gvfs ? Is the drive read only then ?

Kind regards

---

### Post by cyberhood on 2011-06-09
> **matt_symes said:**
> Hi

You might want to run chkdsk.exe on the drive to be sure if you have windows handy.
Don't have Windows.

> **matt_symes said:**
> What happens if you mount it manually from the terminal bypassing gvfs ? Is the drive read only then ?
Don't know how to mount manually.

sorry again for the n00bitute

---

### Post by matt_symes on 2011-06-11
Hi

Plug in the drive in.

From a terminal....

Umount it.

```
sudo umount /dev/sdb1
```Enter your password. It will not be echoed to the screen.

Create a new mount point.

```
sudo mkdir /media/vfat_drive
```Mount the drive.

```
sudo mount -t vfat -o iocharset=utf8,umask=000 /dev/sdb1 /media/vfat_drive
```Create a temp file on the drive.

```
touch /media/vfat_drive/test
```Does the file get created correctly ?

Unmount again.
[FONT=monospace]
[/FONT]```
sudo umount /media/vfat_drive
```Kind regards

---

### Post by cyberhood on 2011-06-11
OK, so I followed all of those commands and it seems to work with full permissions and everything! THANK YOU!!! Now I'm going to try with the other drives. A couple of questions though...

Do I need to make the directories for the other drives with names other than "vfat_drive" so that they don't get mixed up? (eg. "vfat_drive2", "vfat_drive3", etc.)?

Will the drives work like this as plug and play immediately from now on, or is this just a temporary fix?
I mean, will I have to manually mount them from now on, or is there a way to make it permanent so that they just work like they used to? 

Any ideas on why this occurred? 

thanks for stickin' with me Matt! gotta love this community!
cheers

---

### Post by matt_symes on 2011-06-13
Hi

> **cyberhood said:**
> OK, so I followed all of those commands and it seems to work with full permissions and everything! THANK YOU!!! Now I'm going to try with the other drives. A couple of questions though...

Do I need to make the directories for the other drives with names other than "vfat_drive" so that they don't get mixed up? (eg. "vfat_drive2", "vfat_drive3", etc.)?

Will the drives work like this as plug and play immediately from now on, or is this just a temporary fix?
I mean, will I have to manually mount them from now on, or is there a way to make it permanent so that they just work like they used to? 

Any ideas on why this occurred? 

thanks for stickin' with me Matt! gotta love this community!
cheers

Sorry for the delay. I have been very busy the last couple of days.

This was more of a test to see if you could write to the drives when they are manually mounted.

It's not something you want to be doing all the time (only because it's a pain) but it does eliminate some things. 

So lets check some other things. Can you post the output of

```
cat /etc/fstab
```

and also post the output of (when the drive is plugged in)

```
cat /etc/mtab
```

Kind regards

---

### Post by cyberhood on 2011-08-20
> **matt_symes said:**
> Hi



Sorry for the delay. I have been very busy the last couple of days.

This was more of a test to see if you could write to the drives when they are manually mounted.

It's not something you want to be doing all the time (only because it's a pain) but it does eliminate some things. 

So lets check some other things. Can you post the output of

```
cat /etc/fstab
```

and also post the output of (when the drive is plugged in)

```
cat /etc/mtab
```

Kind regards
matt-
Forgive me for dropping off the face of cyberspace for a couple of months, but I needed a break. I hope you will forgive me, and I hope the mods don't kill the thread. (mods: Please don't kill this thread, this isn't a senseless revival; the problem is still not solved, the fix was only temporary.)

```
:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=c0f23444-211c-42e5-8f56-e5f42c075d95  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=1bbd780c-b837-4e84-8814-1f4b7e3c372a  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  vfat  defaults             0  0  
/dev/sdc1                                  /media/sdc1  vfat  defaults             0  0  

:~$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/home.Private /home ecryptfs ecryptfs_check_dev_ruid,ecryptfs_sig=ae1c0355f2e2c849,ecryptfs_fnek_sig=ce3c24bd87e815ec,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs 0 0
gvfs-fuse-daemon /home/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=alien 0 0
/dev/sdb1 /media/vfat_drive vfat rw,iocharset=utf8,umask=000 0 0

```
Thanks in advance matt, if you're still there to help me...
or thanks to anyone else brave enough to save this n00bsel in distress!

---

