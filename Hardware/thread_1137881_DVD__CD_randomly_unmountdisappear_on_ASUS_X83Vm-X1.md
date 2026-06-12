---
title: "DVD / CD randomly unmount/disappear on ASUS X83Vm-X1"
date: 2009-04-26
forum: Hardware
---

### Post by dreamingdarkness on 2009-04-26
Fairly straightforward, as the subject reads, Ubuntu 8.10 issue that I don't replicate when sorrowfully running Vista so I can watch a movie or listen to a CD on this laptop.
DVDs or CDs randomly unmount/disappear on ASUS X83Vm-X1.
This happens consistently with the DVD or CD, or it does not happen at all. 


What happens:
1. Insert DVD or CD
2. Select program to access it with
3. Program hangs or dies (VLC, Totem, Mplayer, Audio Extractor, AcidRip, etc)
4. Force-quit program and manually kill runaway CPU-sucking processes (at least for Audio Extractor)
5. .....
6. Fail

To retrieve the CD or DVD, I have to:
1. Shut down
2. Once BIOS comes up, I have to shut down AGAIN
3. Restart
4. During boot up, eject the CD/DVD

I have tried manually re-mounting or re-discovering the CD or DVD and it does not work, many variants on sudo mount, never finds it.
It looks like I don't A) Have an FSTAB or MTAB entry for the CD/DVD drive.

FSTAB:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda7
UUID=424ae514-ea70-4162-a73e-2ee32a621f7f     /               ext3        defaults,errors=remount-ro    0   0
# /dev/sda6
UUID=8EA863F7A863DBE9       /media/drv0       ntfs-3g         defaults      0   0
# /dev/sda8
UUID=25987d86-2484-43a1-838a-7c953172e569      none            swap        sw          0   0

```

Sudo of lshw, only entry I found that might apply:
```
           *-cdrom
                description: DVD-RAM writer
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: status=open
```

If anyone has any thoughts, I would appreciate it. The CD ROM thinks it's open, for some reason, unless I misread the lshw, and thinks that until the reboot clears the status.

With a DVD in the drive, one of the ones that doesn't "fail":
```
*-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T50L
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/1000036992
                version: SR04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/1000036992
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted
```


Any thoughts on this would be welcome, even if you can definitively say, "You are Out of Luck, I tried it myself" because its frustrating never knowing if your media will work, or be temporarily 'eaten'.

---

### Post by mikeric on 2009-05-17
Does anyone have anymore info on this? I am having the same exact problem with mine.

---

### Post by rusty.hinge on 2009-05-30
I see no new word on this.  I have an ASUS A8V-VM SE with similar issues runing Jaunty 9.04.  When I boot with a CD or DVD in my Drives they mount correctly I can see them listed in the "Places" drop down menu. I can Open the drive and look at the contents even change disks and all remounts correctly.  

ted@Grayhound:~$ sudo lshw -C disk

*-cdrom:0
       description: DVD reader
       product: DVD-ROM DDU1615
       vendor: SONY
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/Roxio11
       version: FYS3
       capabilities: removable audio dvd
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/Roxio11
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted

After some period of time, and not long, the drives disappear or becomes unresponsive.  They are visible to the file system but unmoutable.  Any attempt to access the drive yields a "Unable to mount location, no media in the drive " Error.  

Now lshw -C disk reads for the same drive as:  

  *-cdrom:0
       description: DVD reader
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio dvd
       configuration: status=open

I've noted that the system no longer knows the product nor vendor information for the drive as well as the status=open when the doors are not.  Is this a mother board issue, gnome, linux, or ...? 

Any guidance would be greatly appreciated.

---

### Post by mikeric on 2009-06-12
Anyone have any new news on this?

---

### Post by dreamingdarkness on 2009-09-25
Solved at last, with a firmware update!
Had to ```
sodu lswh | grep DVD
```
Then find the firmware for it (mine is a GSA-T50L), then boot Windows, download the firmware.
In my case, downloaded 5 versions from diff sides, tried to MD5sum compare, none matched, and just took the risk - the HP firmware update failed to install, too! So I had to go with an un-verified one from a forum. Bleh.
But the DVD drive no longer fails every time I try to use the darn thing. Makes a huge difference in my ability to stick to Linux on this laptop - except the part where the firmware required booting to Windows to install.
WHOOT.

---

### Post by rusty.hinge on 2011-08-28
The SOLVED comment above never worked for me.  Upgraded to 11.04 awhile ago.  Been watching my DVD/CD ROM drives closely.  Be it the newest Kernel or 11.04 whichever but my drives are now remembering who they are and I am happy again.

---

### Post by mike1312 on 2011-11-12
*t*[I]hen boot Windows
[/I]Hey! thats not the solution!I dont have windows and dont want to install it.

I have the same problem with ubuntu 11.04 11.10 on Asus K50IN
```
sudo lshw
...
                product: DVD-RAM UJ890AS
                vendor: MATSHITA
....
```So the question is how can i change my firmware under linux?
This guys
[http://ubuntuforums.org/showthread.php?t=1695462](http://ubuntuforums.org/showthread.php?t=1695462)
[http://ubuntuforums.org/showthread.php?t=1750285](http://ubuntuforums.org/showthread.php?t=1750285)
 might want to know too.

---

