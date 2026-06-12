---
title: "eeepc 4G flash reader"
date: 2010-10-19
forum: Hardware
---

### Post by emptyvestage on 2010-10-19
[SIZE=3]I've installed the latest version of netbook 10 and while I am enjoying the new OS I havent been able to find my flash card reader.  With just enough memory to run the OS I was using the card (16 gig) as a hard drive.  There has been no sign of the music, photos or video no matter where I look. I checked the bios and the boot sequence and hdd list is in order and still no card.  Any help would be appreciated.

Thanks 

Miles
[/SIZE]

---

### Post by chessnerd on 2010-10-19
I'm not sure I understand what the problem is. Is it that the system isn't detecting the card after it is inserted or that the card appears to have no data on it?

---

### Post by sgosnell on 2010-10-19
Have you tried removing and reinserting the card?

---

### Post by emptyvestage on 2010-10-19
The netbook doesn't even admit that the card exists. I have tried all the different apps that I could think of.  I have tried inserting and removing the card and the hdd light doesn't even fizz.

Thanks

Miles

---

### Post by chessnerd on 2010-10-19
Hmmm... Could you give us the output of the mount command? 
```
mount
```

That way we can see if it is actually mounting and other programs are recognizing it or if the computer is truly ignoring it.

EDIT: Also, give the output of ls /dev/disk/by-id and ls /dev/disk/by-label
```
ls /dev/disk/by-id

ls /dev/disk/by-label
```

---

### Post by sgosnell on 2010-10-19
The HDD light only operates when the internal SSD is accessed, not when the SD card is accessed.  I don't use the netbook remix, so I don't know exactly how it's set up, but you should be able to open the file manager and see what drives are available.  The SD card should be mounted at /media/somethng, so opening a terminal and entering 'ls /media' should show what is there, if anything.

---

### Post by emptyvestage on 2010-10-19
[SIZE=3]I'm afraid that the terminal/console is going to take me a while to master.  Been years since I've typed any command (dos 3.5 I believe) and previous to that it was punch cards.  The disk utility shows only the 4 gig built in memory, there is no mention of the card or reader.  If I use the card and a reader dongle there is no problem reading the card.[/SIZE]  [SIZE=3]When I checked the dev/id or path and uuid all I could find were references to the usb reader and silicon motion 4 gig hdd.

Thanks

Miles
[/SIZE]

---

### Post by emptyvestage on 2010-10-20
[SIZE=3]The mount command produced:

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
gvfs-fuse-daemon on /home/miler/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=miler)
/dev/sdc1 on /media/PHONE CARD type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)



Most of this doesn't mean a lot to me but I don't see any mention of the card or reader.  The dongle has another card in it for this occasion.

Thanks again

Miles
[/SIZE]

---

### Post by sgosnell on 2010-10-20
Assuming the PHONE CARD is in a card reader, there seems to be no /dev/sdb, which should be the card reader.  Can you remove/replace the SDHC, then post the output of dmesg?  (dmesg is a command typed in the terminal).  I've heard of this problem being fixed by disabling the SD card reader in BIOS, starting the system, then shutting down and re-enabling the reader in the BIOS.  There are several threads on the forum about EEE-PCs not recognizing SD cards, some with solutions and some without.

---

### Post by emptyvestage on 2010-10-20
[SIZE=3]The by id and by path commands produced:

miler@miler-701:~$ ls /dev/disk/by-id
ata-SILICONMOTION_SM223AC_31424686201506061952
ata-SILICONMOTION_SM223AC_31424686201506061952-part1
ata-SILICONMOTION_SM223AC_31424686201506061952-part2
ata-SILICONMOTION_SM223AC_31424686201506061952-part5
scsi-SATA_SILICONMOTION_S31424686201506061952
scsi-SATA_SILICONMOTION_S31424686201506061952-part1
scsi-SATA_SILICONMOTION_S31424686201506061952-part2
scsi-SATA_SILICONMOTION_S31424686201506061952-part5
usb-Generic_STORAGE_DEVICE_000000009407-0:0
usb-Generic_STORAGE_DEVICE_000000009407-0:0-part1
miler@miler-701:~$ ls /dev/disk/by-label
PHONE\x20CARD

I see no sign of the flash card or drive, I think.


Thanks again

Miles

[/SIZE]

---

### Post by chessnerd on 2010-10-20
Well, the computer is apparently seeing a card. That's good.

[QUOTE=emptyvestage]/dev/sdc1 on /media/PHONE CARD type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000, shortname=mixed,dmask=0077,utf8=1,showexec,flush)[/QUOTE]
[QUOTE=emptyvestage]usb-Generic_STORAGE_DEVICE_000000009407-0:0
usb-Generic_STORAGE_DEVICE_000000009407-0:0-part1[/QUOTE]
[QUOTE=emptyvestage]PHONE\x20CARD[/QUOTE]

Those are your card, or at least, that should be it. Does this command show you the files on your card?
```
nautilus /media/PHONE\ CARD
```

If not, then what is PHONE CARD?

NOTE: If your file manager isn't Nautilus, replace nautilus with your file manager. If you don't know what that is, just replace nautilus with ls and see what that brings up.

---

### Post by emptyvestage on 2010-10-20
[SIZE=3]Phone card is in the usb flash reader. Used it only to show that usb ports work.  The card I'm looking for is an internal sd card reader.  The sd card has been in the reader since I completed the install.  I have removed it and reinserted it to see if it was a physical problem but that's  it.

Thanks

Miles
[/SIZE]

---

### Post by Jechem on 2010-11-14
I think I have a similar problem. My card reader suddenly stopped working. When I first installed 10.04 it worked. Tried to disable it in the BIOS and reboot and enable it again and rebooted but no fix. Used EEE control and EEE applet but it didn't help. I tried creating a mount point in the fstab but its still not detected. In diskutil it is not detected. I tried booting from the SD card and it booted the ubuntu live cd on it so its not a hardware problem. I've searched the net for a fix but unfortunately I haven't found any. The card reader icon is present but there's no option to mount it. 

EDIT:
I did right click on the card reader icon and clicked on safely remove drive and rebooted then it worked again. I pulled out the SD card that was inserted and put it in again and it won't work again. Had to do it all over just to get it working. How can you make a mount option on the menu? or just have it auto mount?

SOLUTION:
Downgraded hal from 0.5.14-0ubuntu6 to 0.5.14-0ubuntu5.
My SD card reader works fine now

---

