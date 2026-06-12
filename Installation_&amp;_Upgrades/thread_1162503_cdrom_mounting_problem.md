---
title: "cdrom mounting problem"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by rcayea on 2009-05-17
hey everyone,

i have a problem where i can't mount my second cdrom drive (as opposed to my first dvdr drive which is working well)....

i tried to mount with the following command: mount /dev/cdrom and i received the following error message....

"mount: can't find /dev/cdrom in /etc/fstab or /etc/mtab"

I am a bit paranoid about messing up my fstab file so can someone maybe give me an exact example of what I should enter into my fstab? 

Thanks for the help. Below is my fstab file I copy/pasted...


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=41b014ab-7997-4f87-b183-42beababb0d1 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=7e454671-7a9e-466d-9cfe-f4f057b6795d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by logos34 on 2009-05-17
gksudo gedit /etc/fstab

you should have this:

> 
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

*or maybe /dev/sr0

verify it's being detected, by checking the BIOS and running this

sudo lshw -C disk

don't forget: 

sudo mkdir /media/cdrom1

in case mount doesn't exist

if you continue to have problems, post back with output of the following:

ls -l /dev | grep dvd

ls -l /dev | grep cd

cat /etc/udev/rules.d/70-persistent-cd.rules

---

### Post by Greyfox_75 on 2009-05-17
There is an entry in your fstab for your primary cdrom drive but your second one is not in there.

/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

Running mount /dev/cdrom it uses that line which only access /dev/scd1  This leaves you with 2 options make a new fstab line like this

pathToSecondDrive /media/newFolderYouCreate udf,iso9660 user,noauto,exec,utf8 0 0
mount /media/newFolderYouCreate

I don't have 2 cd drives so you will have to find out what your second cdrom is in /dev for the pathToSecondDrive part.

Second option is a temporary command 

mount pathToSecondDrive /media/newFolderYouCreate

This should autodetect your filesystem type but you may have to specify it like this

mount -t iso9660 pathToSecondDrive /media/newFolderYouCreate

---

### Post by rcayea on 2009-05-17
Thanks for the help. I'll see what happens and report back. 

Randy

---

### Post by rcayea on 2009-05-17
It appears that my cdrom drive in question was not listed in the fstab file. So, as I go there and try to add in the appropriate line, I am told I can't edit it. I tried sudo -s from the command line thinking that owuld then allow me to edit, but I can't still. I am not sure what to type from the command line to do the editing. Any ideas?

Thanks,
Randy

---

### Post by logos34 on 2009-05-17
> **rcayea said:**
> It appears that my cdrom drive in question was not listed in the fstab file. So, as I go there and try to add in the appropriate line, I am told I can't edit it. 

you could edit it if you'd type in the command I gave you top of my reply (#2 above)

---

### Post by rcayea on 2009-05-17
I tried as you suggested. I received the same message about not being able to save. Here is the ouput from the following command: 
ls -l /dev | grep dvd

ls -l /dev | grep cd

cat /etc/udev/rules.d/70-persistent-cd.rules


output:


rcayea@randycomputer:~$ ls -l /dev | grep dvd
lrwxrwxrwx  1 root   root             3 2009-05-17 16:50 dvd1 -> sr1
lrwxrwxrwx  1 root   root             3 2009-05-17 16:50 dvdrw1 -> sr1
drwxr-xr-x  2 root   root            60 2009-05-17 16:50 pktcdvd

rcayea@randycomputer:~$ ls -l /dev | grep cd
lrwxrwxrwx  1 root   root             3 2009-05-17 16:50 cdrom -> sr0
lrwxrwxrwx  1 root   root             3 2009-05-17 16:50 cdrom1 -> sr1
lrwxrwxrwx  1 root   root             3 2009-05-17 16:50 cdrw1 -> sr1
drwxr-xr-x  2 root   root            60 2009-05-17 16:50 pktcdvd
lrwxrwxrwx  1 root   root             3 2009-05-17 16:50 scd0 -> sr0
lrwxrwxrwx  1 root   root             3 2009-05-17 16:50 scd1 -> sr1
crw-rw----+ 1 root   cdrom      21,   1 2009-05-17 16:50 sg1
crw-rw----+ 1 root   cdrom      21,   2 2009-05-17 16:50 sg2
brw-rw----+ 1 root   cdrom      11,   0 2009-05-17 16:50 sr0
brw-rw----+ 1 root   cdrom      11,   1 2009-05-17 16:50 sr1

rcayea@randycomputer:~$ cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# CD-ROM_SC-148C (pci-0000:00:1f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
# DVDRAM_GH22LS40 (pci-0000:00:1f.2-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-0:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-0:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-0:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-0:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"



Thanks logos34. I feel fortunate someone with much depth in knowledge has decided to give me some special attention with my problem tonight. 

Thanks again,
Randy

---

### Post by logos34 on 2009-05-17
well, /dev looks perfect...all the symlinks are there pointing to the correct targets

> **rcayea said:**
> I tried as you suggested. I received the same message about not being able to save. 

hmm, odd.  Try

sudo nano /etc/fstab

Paste (Ctrl+Shift+V) this at bottom:

> /dev/sr0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sr1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

or use /dev/scd0 and scd1--the /dev I see has symlinks to sr0/1, so it really shouldn't matter

any luck?

---

### Post by logos34 on 2009-05-17
you forgot

sudo lshw -C disk

---

### Post by rcayea on 2009-05-18
No luck. I'll keep trying with your suggestions and let you know if and what I do to succeed to pass on to others in the future.

Thanks,
Randy

---

### Post by rcayea on 2009-05-18
I was able to open and save my fstab file using the following command:

gksudo gedit fstab


Now to see if my cdrom drive is yet recognized...

---

### Post by ruehara on 2009-05-18
Have you confirmed that the CD drive actually appears in your device table?

It should look something like

root@fred-desktop:/dev# l scd*
brw-rw----+ 1 root cdrom 11, 0 2009-05-19 09:40 scd0
brw-rw----+ 1 root cdrom 11, 1 2009-05-19 09:40 scd1

If you have both devices listed, you could try creating a directory in /mnt called say 'CD1', then from the command line type 'sudo mount /dev/scd1 /mnt/CD1'. You should then be able to access the drive by referring to it as /mnt/CD1.

---

### Post by rcayea on 2009-05-27
I will check the device table. 

thank you,
Randy

---

