---
title: "fstab mounts incorrect device for DVD and i can't use it"
date: 2008-07-12
forum: General Help
---

### Post by Koobi on 2008-07-12
Hi,
I've been using Ubuntu since 2005 and I just upgraded to 8.04.1 the other day.

Just today, I realized I can't access my DVD drive.

example:
```

$ mplayer dvd://1
(output truncated for readability)
Couldn't open DVD device: /dev/dvd

```

```

$ ls -lah /dev/dvd
ls: cannot access /dev/dvd: No such file or directory

```


this is my fstab:
```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=04ede31b-9431-4208-92a3-51efd7216432 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=59f0b182-ddd0-4254-bcdb-20ff49a70180 /boot ext3 defaults 0 2
# /dev/sda9 -- converted during upgrade to edgy
UUID=ac7eae95-4789-428f-a708-65dc3c8a0434 /home ext3 defaults 0 2
# /dev/sda11 -- converted during upgrade to edgy
UUID=4840-3EF4 /media/fat32 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda12 -- converted during upgrade to edgy
UUID=8f46fcb0-f8c0-4ade-b5a3-4f66434ff0a8 /media/store ext3 defaults 0 2
# /dev/sda8 -- converted during upgrade to edgy
UUID=0bc7a993-2dbb-4ba6-8c2b-8b3e0b77fd61 /opt ext3 defaults 0 2
# /dev/sda6 -- converted during upgrade to edgy
UUID=351f11dd-00d6-4118-bd84-54ce2111b921 /usr ext3 defaults 0 2
# /dev/sda7 -- converted during upgrade to edgy
UUID=66869866-d53a-4ea1-9213-140ccfd9c256 /var ext3 defaults 0 2
# /dev/sda10 -- converted during upgrade to edgy
UUID=483cf5ff-1d88-41a6-aaa6-3a87944c8af7 none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```


is UUID usual? i noticed that change the last time I upgraded to edgy.



as you can see, my DVD is mounted from /dev/hdd but this doesn't exist:
```

$ ls /dev/hdd
ls: cannot access /dev/hdd: No such file or directory

```

apparently the new kernel mounts devices differently, right?


well I believe scd0 is the device I should mount from:
```

$ ls -lah /dev/scd0 
brw-rw----+ 1 root cdrom 11, 0 2008-07-10 23:54 /dev/scd0

```


but even an fstab entry like this:
```

/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
still gives me those mplayer errors.





any idea what I could do to resolve the issue? my DVD worked fine before I upgraded.



here's some additional info in case you find it useful:
```

##### mtab
$ cat /etc/mtab 
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-386/volatile tmpfs rw 0 0
/dev/sda5 /boot ext3 rw 0 0
/dev/sda9 /home ext3 rw 0 0
/dev/sda11 /media/fat32 vfat rw,utf8,umask=007,gid=46 0 0
/dev/sda12 /media/store ext3 rw 0 0
/dev/sda8 /opt ext3 rw 0 0
/dev/sda6 /usr ext3 rw 0 0
/dev/sda7 /var ext3 rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/scd0 /media/CRAZY_DET iso9660 ro,nosuid,nodev,uhelper=hal,uid=1000,utf8 0 0





##### fdisk
$ sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b08fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         392     3148708+  83  Linux
/dev/sda2             393       19457   153139612+   5  Extended
/dev/sda5             393         522     1044193+  83  Linux
/dev/sda6             523        1829    10498446   83  Linux
/dev/sda7            1830        2481     5237158+  83  Linux
/dev/sda8            2482        3134     5245191   83  Linux
/dev/sda9            3135        5745    20972826   83  Linux
/dev/sda10           5746        6006     2096451   82  Linux swap / Solaris
/dev/sda11           6007        6659     5245191    b  W95 FAT32
/dev/sda12           6660       19457   102799903+  83  Linux





##### df
$ df -Th
Filesystem Type    Size Used Avail Use% Mounted on
/dev/sda1     ext3    3.0G  628M  2.2G  22% /
varrun       tmpfs    347M  236K  347M   1% /var/run
varlock      tmpfs    347M     0  347M   0% /var/lock
udev         tmpfs    347M   68K  347M   1% /dev
devshm       tmpfs    347M  816K  347M   1% /dev/shm
lrm          tmpfs    347M   40M  308M  12% /lib/modules/2.6.24-19-386/volatile
/dev/sda5     ext3    956M   99M  806M  11% /boot
/dev/sda9     ext3     20G   15G  4.4G  77% /home
/dev/sda11    vfat    5.0G  4.6G  488M  91% /media/fat32
/dev/sda12    ext3     97G   92G  496M 100% /media/store
/dev/sda8     ext3    5.0G  823M  3.9G  18% /opt
/dev/sda6     ext3    9.9G  8.2G  1.3G  87% /usr
/dev/sda7     ext3    5.0G  2.1G  2.6G  45% /var
/dev/scd0  iso9660    4.4G  4.4G     0 100% /media/CRAZY_DET

```

I don't understand how fstab has /dev/hdd defined as the DVD (and that's the wrong entry) but df shows me /dev/scd0.



any help would be appreciated.
Thanks.

---

### Post by VMC on 2008-07-12
Try inserting a "#" in fron of your fstab entry of the /dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

Then add something like this:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

Maybe you will need a remount "mount -a" afterwards.

---

### Post by Koobi on 2008-07-12
> **VMC said:**
> Try inserting a "#" in fron of your fstab entry of the /dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

Then add something like this:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

Maybe you will need a remount "mount -a" afterwards.

thanks for the reply.

i gave that a go:
```

$ cat /etc/mtab  | grep scd0
/dev/scd0 /media/cdrom0 udf ro,nosuid,nodev,utf8,user=koobi 0 0

```

user 'koobi' is my login user and his id is 1000.


i still get this error:
```

$ mplayer dvd://1
Couldn't open DVD device: /dev/dvd

```

also, i can't open certain DVD's, however, this has been a problem since i upgraded.



i also noticed this:
```

$ dmesg | tail
[ 1858.166974] Buffer I/O error on device sr0, logical block 13
[ 1858.166983] Buffer I/O error on device sr0, logical block 14
[ 1858.166986] Buffer I/O error on device sr0, logical block 15
[ 1858.166990] Buffer I/O error on device sr0, logical block 16
[ 1858.166993] Buffer I/O error on device sr0, logical block 17
[ 1858.166996] Buffer I/O error on device sr0, logical block 18
[ 1858.166999] Buffer I/O error on device sr0, logical block 19
[ 1858.167002] Buffer I/O error on device sr0, logical block 20
[ 1858.167006] Buffer I/O error on device sr0, logical block 21
[ 1858.167009] Buffer I/O error on device sr0, logical block 22

```


thanks.

---

### Post by mc4man on 2008-07-12
Run ```
sudo lshw -C disk 
```to get the logical names of your drive.
also maybe the contents of /etc/udev/rules.d/70-persistent-cd.rules

to run mplayer from cli where the device is not the mplayer default of /dev/dvd go
 > mplayer -dvd-device /dev/dvd1 dvd://1
where 'dvd1' is set to the logical name of your device whatever it may be

---

### Post by Koobi on 2008-07-12
> **mc4man said:**
> Run ```
sudo lshw -C disk 
```to get the logical names of your drive.
also maybe the contents of /etc/udev/rules.d/70-persistent-cd.rules

to run mplayer from cli where the device is not the mplayer default of /dev/dvd go
 
where 'dvd1' is set to the logical name of your device whatever it may be



```

$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: MAXTOR STM316021
       vendor: Maxtor
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 6PT2HH9P
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000b08fa
  *-cdrom
       description: DVD-RAM writer
       product: DRW-1608P3S
       vendor: ASUS
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.06
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1

```

so /dev/scd0 is a valid device, right?




```

$ cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# ASUS_DRW-1608P3S (pci-0000:00:0f.1-ide-0:1)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-0:1", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-0:1", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-0:1", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-0:1", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# DRW-1608P3S (pci-0000:00:0f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"

```

what does that file do btw? does it map the drives or something? never came accross this file until now.



i've tried that mplayer command before as well...but i'm beginning to wonder if the upgrade messed with mplayers DVD options...either way, i can't seem to access the files via CLI:
```

$ ls -lah /media/cdrom0/VIDEO_TS
ls: reading directory /media/cdrom0/VIDEO_TS: Input/output error
total 0

```


here the full output of mplayer:
```

$ mplayer -dvd-device /dev/scd0 dvd://1
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.66GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
Can't open VMG info!
No stream found to handle url dvd://1


Exiting... (End of file)

```




my libdvd library sems to be in order so mplayer should be accessing DVD's as usual:
```

$ aptitude search libdvd
i   libdvdcss2                                                                                  - Library for accessing DVDs like block device usind deCSS if needed                                   
p   libdvdnav-dev                                                                               - The DVD navigation library, development package                                                      
i   libdvdnav4                                                                                  - The DVD navigation library                                                                           
p   libdvdread-dev                                                                              - library for reading DVDs (development)                                                               
i A libdvdread3                                                                                 - library for reading DVDs                                                                             
v   libdvdread3-dev

```



thanks for the help so far.

---

### Post by mc4man on 2008-07-12
no it would be mplayer -dvd-device /dev/dvd1 dvd://1
you can easily fix your setup, your drive is listed twice read here 
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)
_any questions ask first_, it's very easy to do
You can adjust your fstab afterwards if you choose to straighten things out as in the link

---

### Post by Koobi on 2008-07-12
> **mc4man said:**
> no it would be mplayer -dvd-device /dev/dvd1 dvd://1
you can easily fix your setup, your drive is listed twice read here 
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)
_any questions ask first_, it's very easy to do
You can adjust your fstab afterwards if you choose to straighten things out as in the link

using the mplayer command you gave me gave me that same error.


i followed your link.
i vim'd the rules file, just commented the top half away and remove the 1's where necessary.


i then found the files i needed to remove:
```

$ ls -lah /dev | grep ^l
lrwxrwxrwx   1 root   root           4 2008-07-12 21:10 cdrom1 -> scd0
lrwxrwxrwx   1 root   root           4 2008-07-12 21:10 cdrw1 -> scd0
lrwxrwxrwx   1 root   root          11 2008-07-12 21:10 core -> /proc/kcore
lrwxrwxrwx   1 root   root           4 2008-07-12 21:10 dvd1 -> scd0
lrwxrwxrwx   1 root   root           4 2008-07-12 21:10 dvdrw1 -> scd0
lrwxrwxrwx   1 root   root          13 2008-07-12 21:10 fd -> /proc/self/fd
lrwxrwxrwx   1 root   root          13 2008-07-12 21:10 MAKEDEV -> /sbin/MAKEDEV
lrwxrwxrwx   1 root   root          24 2008-07-12 21:10 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx   1 root   root           4 2008-07-12 21:10 sr0 -> scd0
lrwxrwxrwx   1 root   root          15 2008-07-12 21:10 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root   root          15 2008-07-12 21:10 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root   root          15 2008-07-12 21:10 stdout -> /proc/self/fd/1

```



and removed them:
```

$ sudo rm cdrom1 dvd1 cdrw1 dvdrw1 sr0

```


i rebooted and this is what i now have in /dev
```

$ ls -lah /dev | grep ^l
lrwxrwxrwx   1 root   root           4 2008-07-13 00:02 cdrom -> scd0
lrwxrwxrwx   1 root   root           4 2008-07-13 00:02 cdrw -> scd0
lrwxrwxrwx   1 root   root          11 2008-07-13 00:02 core -> /proc/kcore
lrwxrwxrwx   1 root   root           4 2008-07-13 00:02 dvd -> scd0
lrwxrwxrwx   1 root   root           4 2008-07-13 00:02 dvdrw -> scd0
lrwxrwxrwx   1 root   root          13 2008-07-13 00:02 fd -> /proc/self/fd
lrwxrwxrwx   1 root   root          13 2008-07-13 00:02 MAKEDEV -> /sbin/MAKEDEV
lrwxrwxrwx   1 root   root          24 2008-07-13 00:02 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx   1 root   root           4 2008-07-13 00:02 sr0 -> scd0
lrwxrwxrwx   1 root   root          15 2008-07-13 00:02 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root   root          15 2008-07-13 00:02 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root   root          15 2008-07-13 00:02 stdout -> /proc/self/fd/

```



this is what i get when i run mplayer:
```

$ mplayer dvd://1
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.66GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 2 titles on this DVD.
There are 13 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Invalid title IFO (VTS_01_0.BUP).
Cannot open the IFO file for DVD title 1.
No stream found to handle url dvd://1


Exiting... (End of file)

```

that DVD has worked for me on mplayer before this.

totem ran as soon as i popped in my DVD and it gave me this error:
> 
Could not open location; you might not have permission to open the file.




note that my fstab had this when i rebooted:
```

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```

i changed that to:
```

/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

and did `sudo mount -a` and i still have the same problem.


have i dont something wrong? i think we've at least identified the problem so thats great.


thanks.

---

### Post by mc4man on 2008-07-12
lets back track 1 sec so you can separate mounting issues from the ability to playback encrypted dvds
R. click on the the dvd icon -> properties -> volume, Does it show mount point /media/cdrom0 ?

---

### Post by Koobi on 2008-07-12
> **mc4man said:**
> lets back track 1 sec so you can separate mounting issues from the ability to playback encrypted dvds
R. click on the the dvd icon -> properties -> volume, Does it show mount point /media/cdrom0 ?


i can mount them...but i'm not sure if the permissions are correct.

i watched another DVD which i watched the night before i upgraded. let me know if you want me to check using that.



Properties > Volume shows:
Mount Point: /media/cdrom0
File System: udf (the other DVD uses the ISO option)
Mount Options: ro nosuid nodev noexec



all of the DVD's complain of permissions in the Properties > Permissions tab.

---

### Post by mc4man on 2008-07-12
Leave your fstab alone for the moment it's fine though I'd use 
> /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
I think your only issue now is enabling proper playback
What you could do is run thru these commands and then ck. If _you know_ you have medibuntu for hardy enabled as a source then skip the first 2 code boxes, _run the third_ and optional stuff if wished, if anything is redundant no harm.
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)
(don't worry about the xubuntu heading)
After that try a dvd again, for the moment start mplayer from the gui, either run gmplayer from terminal or open mplayer from applications menu.
For any further troubleshooting vlc opened from terminal is best

edit; > all of the DVD's complain of permissions in the Properties > Permissions tab.
don't worry that, normal to see

---

### Post by Koobi on 2008-07-12
> **mc4man said:**
> Leave your fstab alone for the moment it's fine though I'd use 

I think your only issue now is enabling proper playback
What you could do is run thru these commands and then ck. If _you know_ you have medibuntu for hardy enabled as a source then skip the first 2 code boxes, _run the third_ and optional stuff if wished, if anything is redundant no harm.
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)
(don't worry about the xubuntu heading)
After that try a dvd again, for the moment start mplayer from the gui, either run gmplayer from terminal or open mplayer from applications menu.
For any further troubleshooting vlc opened from terminal is best

edit; 
don't worry that, normal to see



that was a little surprising. apparently some things like msttcorefonts had been removed.

anyway, your instructions led my Ubuntu to install msttcorefonts ubuntu-restricted-extras and upgrade w32codecs.

it also upgraded ffmpeg libavcodec-dev libavcodec1d libavformat-dev libavformat1d libavutil-dev libavutil1d libpostproc1d libswscale1d.



here's why i think there could be something wrong with the mounting:
```

$ ls -lahR /media/cdrom0
/media/cdrom0:
total 10K
dr-xr-xr-x 4 4294967295 4294967295  136 2006-03-19 02:57 .
drwxr-xr-x 7 root       root       4.0K 2008-07-13 00:03 ..
dr-xr-xr-x 2 4294967295 4294967295   40 2006-03-19 02:57 AUDIO_TS
dr-xr-xr-x 2 4294967295 4294967295  664 2006-03-19 02:57 VIDEO_TS

/media/cdrom0/AUDIO_TS:
total 4.0K
dr-xr-xr-x 2 4294967295 4294967295  40 2006-03-19 02:57 .
dr-xr-xr-x 4 4294967295 4294967295 136 2006-03-19 02:57 ..
ls: reading directory /media/cdrom0/VIDEO_TS: Input/output error

/media/cdrom0/VIDEO_TS:
total 0

```


that's a little odd isn't it?


also, dmesg shows this:
```

$ dmesg | tail
[ 5111.264445] sr 1:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 5111.264452] end_request: I/O error, dev sr0, sector 1068
[ 5120.697828] sr 1:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5120.697840] sr 1:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[ 5120.697845] sr 1:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 5120.697853] end_request: I/O error, dev sr0, sector 1068
[ 5128.059052] sr 1:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5128.059063] sr 1:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[ 5128.059069] sr 1:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 5128.059076] end_request: I/O error, dev sr0, sector 1068

```



and here's the VLC output the moment i tried to open the disc:
```

^Lioctl(): Input/output error
[00000295] vcdx access error: error reading Info sector (150)
[00000295] vcd access error: no movie tracks found
[00000295] access_file access error: file /dev/scd0 is empty, aborting
[00000302] main private error: cannot pre fill buffer
[00000305] cdda access error: could not read block 0 from disc
[00000305] cdda access error: cannot read sector 0
[00000305] cdda access error: could not read block 1 from disc
[00000305] cdda access error: cannot read sector 1
[00000305] cdda access error: could not read block 2 from disc
[00000305] cdda access error: cannot read sector 2
[00000305] cdda access error: could not read block 3 from disc
[00000305] cdda access error: cannot read sector 3
[00000305] cdda access error: could not read block 4 from disc
[00000305] cdda access error: cannot read sector 4
[00000305] cdda access error: could not read block 5 from disc
[00000305] cdda access error: cannot read sector 5

```



do i have to run an fsck or something?

thanks for taking the time to help.

---

### Post by mc4man on 2008-07-12
I got to run out for a bit but this looks like a drive  issue
for comparison here's same command for me
```
doug@doug-desktop:~$ ls -lahR /media/cdrom0
/media/cdrom0:
total 12K
dr-xr-xr-x 4 4294967295 4294967295  136 2007-08-10 22:13 .
drwxr-xr-x 5 root       root       4.0K 2008-07-12 16:31 ..
dr-xr-xr-x 2 4294967295 4294967295   40 2007-08-10 21:51 AUDIO_TS
dr-xr-xr-x 2 4294967295 4294967295 2.9K 2007-08-10 21:50 VIDEO_TS

/media/cdrom0/AUDIO_TS:
total 4.0K
dr-xr-xr-x 2 4294967295 4294967295  40 2007-08-10 21:51 .
dr-xr-xr-x 4 4294967295 4294967295 136 2007-08-10 22:13 ..

/media/cdrom0/VIDEO_TS:
total 7.0G
dr-xr-xr-x 2 4294967295 4294967295 2.9K 2007-08-10 21:50 .
dr-xr-xr-x 4 4294967295 4294967295  136 2007-08-10 22:13 ..
-r--r--r-- 1 4294967295 4294967295  26K 2007-08-10 21:36 VIDEO_TS.BUP
-r--r--r-- 1 4294967295 4294967295  26K 2007-08-10 21:36 VIDEO_TS.IFO
-r--r--r-- 1 4294967295 4294967295 137M 2007-08-10 21:36 VIDEO_TS.VOB
-r--r--r-- 1 4294967295 4294967295  78K 2007-08-10 21:36 VTS_01_0.BUP
-r--r--r-- 1 4294967295 4294967295  78K 2007-08-10 21:36 VTS_01_0.IFO
-r--r--r-- 1 4294967295 4294967295  59M 2007-08-10 21:36 VTS_01_0.VOB
-r--r--r-- 1 4294967295 4294967295 1.0G 2007-08-10 21:37 VTS_01_1.VOB
-r--r--r-- 1 4294967295 4294967295 1.0G 2007-08-10 21:37 VTS_01_2.VOB
-r--r--r-- 1 4294967295 4294967295 1.0G 2007-08-10 21:38 VTS_01_3.VOB
-r--r--r-- 1 4294967295 4294967295 1.0G 2007-08-10 21:38 VTS_01_4.VOB
-r--r--r-- 1 4294967295 4294967295 1.0G 2007-08-10 21:39 VTS_01_5.VOB
-r--r--r-- 1 4294967295 4294967295 306M 2007-08-10 21:39 VTS_01_6.VOB
-r--r--r-- 1 4294967295 4294967295  18K 2007-08-10 21:39 VTS_02_0.BUP
-r--r--r-- 1 4294967295 4294967295  18K 2007-08-10 21:39 VTS_02_0.IFO
-r--r--r-- 1 4294967295 4294967295 478K 2007-08-10 21:39 VTS_02_0.VOB
-r--r--r-- 1 4294967295 4294967295  13M 2007-08-10 21:39 VTS_02_1.VOB
-r--r--r-- 1 4294967295 4294967295  18K 2007-08-10 21:39 VTS_03_0.BUP
-r--r--r-- 1 4294967295 4294967295  18K 2007-08-10 21:39 VTS_03_0.IFO
-r--r--r-- 1 4294967295 4294967295 478K 2007-08-10 21:39 VTS_03_0.VOB
-r--r--r-- 1 4294967295 4294967295 746K 2007-08-10 21:39 VTS_03_1.VOB
-r--r--r-- 1 4294967295 4294967295  24K 2007-08-10 21:39 VTS_04_0.BUP
-r--r--r-- 1 4294967295 4294967295  24K 2007-08-10 21:39 VTS_04_0.IFO
-r--r--r-- 1 4294967295 4294967295 478K 2007-08-10 21:39 VTS_04_0.VOB
-r--r--r-- 1 4294967295 4294967295 186M 2007-08-10 21:39 VTS_04_1.VOB
-r--r--r-- 1 4294967295 4294967295  24K 2007-08-10 21:39 VTS_05_0.BUP
-r--r--r-- 1 4294967295 4294967295  24K 2007-08-10 21:39 VTS_05_0.IFO
..........clipped, not needed

```
What's not good is this
>  5111.264445] sr 1:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)

I just finished working on something with that exact same error
read the first couple of posts here (was fixed with a new,proper ide cable)
[http://ubuntuforums.org/showthread.php?t=855535](http://ubuntuforums.org/showthread.php?t=855535)
I believe your ...rules, fstab , /dev links ect. are all good, we could double ck. fool with fstab, ect. but  ck. the error in the link. (will ck .back in hr. or so)

Edit; also run this 
```
sudo hdparm -i /dev/scd0
```

---

### Post by Koobi on 2008-07-13
> **mc4man said:**
> 
I just finished working on something with that exact same error
read the first couple of posts here (was fixed with a new,proper ide cable)
[http://ubuntuforums.org/showthread.php?t=855535](http://ubuntuforums.org/showthread.php?t=855535)
I believe your ...rules, fstab , /dev links ect. are all good, we could double ck. fool with fstab, ect. but  ck. the error in the link. (will ck .back in hr. or so)

Edit; also run this 
```
sudo hdparm -i /dev/scd0
```


sorry for the late reply. i'm in Asia so it was late night when you replied :)

so what exactly is the matter? is it the way my data is being transferred or my drive itself? i doubt it could be physical because everything worked fine right up until i upgraded.

unless of course the kernel requires that different type of cable you mentioned since it sees everything as a SCSI.

i dont know what else i could try in fstab. any suggestions? i've also tried using exec and switching the ISO option with the UDF.


here's the output for the command you asked me to run:
```

$ sudo hdparm -i /dev/scd0

/dev/scd0:

 Model=ASUS    DRW-1608P3S                     , FwRev=1.06    , SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode

```

---

### Post by mc4man on 2008-07-14
Your drive is set to udma4 which is as good as it gets for an optical drive but the error in dmesg > Logical unit communication CRC error (Ultra-DMA/32) is indicating some problem there. In the other case it was resolved by replacing the ide cable being sure to use an 80 wire cable.

As far as the fstab I think it's probably fine as you had it. What I was going to suggest to ck. if fstab was involved is to take it out of the picture for the moment. To do that is either comment the line for /dev/scd0 out (#) or better yet just delete it. (You could copy it to a text file to paste back in later or use the scd1 line as guide)
With no fstab entry for the device the media will be mounted by default to /media/<volume name>. You could look for it at that location and or point vlc to it, ie. file -> open disk, change the  default device to /media/<volume name>
If still no go I'd look to try a different cable

Try grepping your logs for DMA and see if anything unexpected turns up
 ```
grep ' DMA' /var/log/syslog

 grep ' DMA' /var/log/dmesg
```

---

### Post by Koobi on 2008-07-14
> **mc4man said:**
> Your drive is set to udma4 which is as good as it gets for an optical drive but the error in dmesg  is indicating some problem there. In the other case it was resolved by replacing the ide cable being sure to use an 80 wire cable.

As far as the fstab I think it's probably fine as you had it. What I was going to suggest to ck. if fstab was involved is to take it out of the picture for the moment. To do that is either comment the line for /dev/scd0 out (#) or better yet just delete it. (You could copy it to a text file to paste back in later or use the scd1 line as guide)
With no fstab entry for the device the media will be mounted by default to /media/<volume name>. You could look for it at that location and or point vlc to it, ie. file -> open disk, change the  default device to /media/<volume name>
If still no go I'd look to try a different cable

Try grepping your logs for DMA and see if anything unexpected turns up
 ```
grep ' DMA' /var/log/syslog

 grep ' DMA' /var/log/dmesg
```



i deleted that fstab entry. then i cat'd mtab:
```

/dev/scd0 /media/CRAZY_DET iso9660 ro,nosuid,nodev,uhelper=hal,uid=1000,utf8 0 0

```

it still has trouble playing via mplayer and accessing the video folder of the DVD.


i'll try and look for an 80 wire cable tomorrow. it's just odd that all this happenned right after i upgraded.

grepping syslog gave me nothing.
however,:
```

$ grep ' DMA' /var/log/dmesg
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0

```


i'm starting to find this interesting. how did you learn about this stuff? by just doing or did you take a course in Linux or read up about it?



i'm not too familiar with VLC but i started it up via CLI and went to File > Open Disc.

in the Disc tab, i selected "DVD (menus)" first and then tried the "DVD" option. for both options, i changed "Device name" to "/media/CRAZY_DET" 
but in both cases, i got errors similar to this:
```

libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdread: Invalid IFO for title 1 (VTS_01_0.BUP).
[00000294] dvdread demuxer error: fatal error in vts ifo
[00000294] dvdread demuxer error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[00000296] vcdx access error: fread (): Is a directory

```


so i guess i should give a new cable a go? if i can't find a cable, can't i downgrade the kernel? because i live in Sri Lanka, i'm not sure how available such cables are around these parts.


thanks a lot for your help so far.

---

### Post by mc4man on 2008-07-15
Other than trying an new cable or a fresh viewpoint arriving I don't know.
> i'm not sure how available such cables are around these parts
If that's an issue pm me.
what might be interesting is to see in the meantime is if you could copy a disk to hdd and attempt playback from there. Copying is a bit more tolerant of data transfer then playback which expects the data in a timely fashion. If you can copy than successful playback gives a little more weight to a hardware issue.  One way 
```
dd if=/dev/scd0 of=cd.iso
```
There's 2 potential issues with this method. 
If the disk is encrypted the .iso will be also. To decrypt you would need the keys to have been read and stored previously by a player in home dir. -> .dvdcss. They're stored in individual folders under the disks volume name. (with proper dvds usually quite recognizable) if they're not there don't bother with a dd.
The other issue may be if a sector is unreadable the copy will fail, to get around you need to go (IIRC, ck. man or --help)
```
dd conv=noerror,sync if=/dev/scd0 of=cd.iso
``` or try 
```
dd_rescue -n -b 2048 /dev/scd0 movie.iso
```
Note; i believe the partial .iso may be 'playable' to some extent depending where the failure occured.

The second way would be to try to rip to a volume name dir. in a video_ts folder. (will be in home)
For that install vobcopy and run
```
vobcopy -v -m -F 16 
``` Assumes that your using  /media/cdrom0 drive, otherwise you'd append comm. with <space> /media/cdrom1 (or /media/whatever)
If vobcopy starts getting alot of read retries, forget it unless they're of a limited number of sectors.(blocks) In that case let me know and we can modify the source. (Vopcopy defaults to 10 read tries per sector )

If vobcopy is successful or even semi- successful that would show your whole libdvdcss thing is good.
If you can copy don't be surprised if it is slow, normally a dvd9 would take 10-12 min. with vobcopy.
If vobcopy fails the after reading the disk structure try losing the -F 16 parameter. 
Vobcopy needs a proper dvd structure, dd doesn't.
In either case if you do get a copy with read errors (skipped blocks) you should get some form of playback with glitches where info is missing, though if there is too much who knows. I'd try a commercial disk in excellent condition if possible.

Edit: 
a search on that error line doesn't turn up alot, and most concern burning, not reading (some very recent - ubuntu 8.04) but many focus on the cable, possible incompatible drives on same cable, positioning on drive(s), ect.
If possible can you open the case and see what the hook up for your dvd drive is? Is it on it's _own cable separate from the hdd and hooked up to end connector_? Also you can easily tell if the cable is 40 or 80 wire - if you see the wires from a distance it's 40.
You might try reseating the cable connector in the back of drive

---

### Post by Koobi on 2008-07-15
i managed to find a 60-conductor cable and it works fine, thanks :)
so i have one SATA connection to my hard disk. and my primary IDE is connected via 80-conductor wire to my DVD drive.

i still can't play via mplayer though. i'm not sure why...althought VLC plays it but access time is a lot slower. i can however, cd into the folder and then play a file directly.

but neither of the following work:


* playing a DVD directly:
```

$ mplayer dvd://1
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.66GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
Couldn't open DVD device: /dev/dvd
No stream found to handle url dvd://1


Exiting... (End of file)

```




* specifying the DVD device as /dev/dvd
```

$ mplayer -dvd-device /dev/dvd dvd://1
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.66GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
Couldn't open DVD device: /dev/dvd
No stream found to handle url dvd://1


Exiting... (End of file)

```




* specifying the DVD device as /dev/dvd.
this works fine:
```

$ mplayer -dvd-device /dev/scd0 dvd://1

```





looks like some links are still askew huh?
do you know if i can fix this? i could use a bash alias, i guess, but ideal solution would be to fix it.


here's the verbose output of mplayer:
```

$ mplayer -v dvd://1
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.66GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/koobi/.mplayer/codecs.conf'
Reading /home/koobi/.mplayer/codecs.conf: Can't open '/home/koobi/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --target=i586-linux --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-arts --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-libamr_nb --enable-libamr_wb --enable-faac --enable-gui --enable-mencoder
CommandLine: '-v' 'dvd://1'
init_freetype
get_path('font/font.desc') -> '/home/koobi/.mplayer/font/font.desc'
font: can't open file: /home/koobi/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/koobi/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/koobi/.mplayer/input.conf'
Can't open input config file /home/koobi/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('1.conf') -> '/home/koobi/.mplayer/1.conf'

Playing dvd://1.
get_path('sub/') -> '/home/koobi/.mplayer/sub/'
URL: dvd://1
Couldn't open DVD device: /dev/dvd
No stream found to handle url dvd://1

vo: x11 uninit called but X11 not inited..

Exiting... (End of file)

```



btw, do you have a blog or something? you should write a few mini tutorials on this stuff. you seem to know a lot on the subject.



thanks.

---

### Post by Koobi on 2008-07-15
this is weird:
```

$ ls -lah /dev/dvd
ls: cannot access /dev/dvd: No such file or directory

```

but /dev/dvd existed in [post #7 of this thread.](http://ubuntuforums.org/showpost.php?p=5371937&postcount=7)


so i just did:
```

$ cd /dev && sudo ln -s /dev/scd0 dvd

```

and now the following works:
```

$ mplayer dvd://1

```


i should probably create a symlink for cdrom, cdrw, dvdrw and sr0


strange that /dev/dvd disappeared but it appears the problem is solved, thanks to you. thanks for your time. it was a big help :)


:edit
also, these seem to have appeared:
```

$ ls -lah /dev | grep ^l | grep scd0
lrwxrwxrwx   1 root   root           4 2008-07-15 19:24 cdrom2 -> scd0
lrwxrwxrwx   1 root   root           4 2008-07-15 19:24 cdrw2 -> scd0
lrwxrwxrwx   1 root   root           9 2008-07-16 01:49 dvd -> /dev/scd0
lrwxrwxrwx   1 root   root           4 2008-07-15 19:24 dvd2 -> scd0
lrwxrwxrwx   1 root   root           4 2008-07-15 19:24 dvdrw2 -> scd0
lrwxrwxrwx   1 root   root           4 2008-07-15 19:24 sr0 -> scd0

```

but if its not harmful to my system, i can live with it.

---

### Post by mc4man on 2008-07-15
If things are working good then _you can leave alone_. Because of the improper cable your drive was probably detected 2 or even 3 times hence the 1 upped dev links. Definitely when you changed the cable created a new entry. (the other possibility is that you inserted a microcryzer or similar usb thumb drive at some point before changing the cable. Thumb drives like that are given an entry in ....rules.) If you were to look at your ...rules file you'll see what I mean.
 You could, if you choose, do the process again, remove the entries and reboot and you'll get 1 @ scd0 with links of dvd dvrw cdrom cdr sr0

> i should probably create a symlink for cdrom, cdrw, dvdrw and sr0
you could do that also . Any link you create in /dev that _conflicts_ with what's in ..rules will only last till a reboot so no harm in trying

---

### Post by Koobi on 2008-07-16
ok i removed the links and fixed my CD rules and rebooted and everything works great.


would this be a result of the whole kernel SCSI issue?:
```

$ cat /var/log/fsck/checkfs 
Log of fsck -C3 -R -A -a 
Wed Jul 16 19:05:39 2008

fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda11: 10 files, 1184047/1308735 clusters
/dev/sda5: clean, 54/522240 files, 166931/1044193 blocks
/dev/sda9: clean, 72755/2606080 files, 4050702/5242880 blocks
/dev/sda12: clean, 11617/12861440 files, 24291991/25699975 blocks
/dev/sda8: clean, 16/656000 files, 231284/1311297 blocks
/dev/sda6 contains a file system with errors, check forced.
Error reading block 1311165 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  

/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
/dev/sda7: clean, 32124/655360 files, 594852/1309289 blocks
fsck died with exit status 4

Wed Jul 16 19:06:30 2008
----------------

```


or is that a separate issue?

---

