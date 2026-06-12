---
title: "compact flash usb drive"
date: 2006-05-17
forum: Hardware &amp; Laptops
---

### Post by CameronCalver on 2006-05-17
Hey i have a compact flash usb drive and i would like to know how to mount it and what i will put in my fstab

---

### Post by Sutekh on 2006-05-17
Open a Terminal (Applications -> Accessories) and enter this command, which will wait for something to happen, at which point messages will appear, something like plugging a USB drive in
```
tail -f /var/log/messages
``` Then plug in the USB drive.  You are looking for a line like this
```
Attached scsi removable disk [COLOR=Blue]sdd [/COLOR]at scsi5, channel 0, id 0, lun 0
``` Meaning that your USB is given the device node[COLOR=Red] [COLOR=Blue]**/dev/sdd **[COLOR=Black](of course your output may be different)[/COLOR][/COLOR][/COLOR]

Next use the fdisk command to find out what devices are attached, the partition node, and format they use
```
sudo fdisk -l
``` You might find something like this
```
Disk [COLOR=Blue]/dev/sdd[/COLOR]: 129 MB, 129740800 bytes
4 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 248 * 512 = 126976 bytes

   Device Boot      Start         End      Blocks   Id  System
[COLOR=Blue] /dev/sdd1[/COLOR]   *           1        1021      126573    6  FAT16

``` Meaning in this case, the USB device has a FAT partition; [COLOR=Blue]/dev/sdd1[/COLOR].  If your USB is formatted different, you will need different options in the next steps

OK, halfway there.

Now you need to edit the fstab.  This code makes a backup of the file and opens it for editing
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` (You could also use gedit, if you find nano hard to use)

When the fstab opens, you need to add an entry for it like this one.
```
[COLOR=Blue]/dev/sdd1[/COLOR]  [COLOR=Red] /usbdisc[/COLOR]   [COLOR=Green]vfat[/COLOR]   [COLOR=DarkOrchid]iocharset=utf8,umask=0000[/COLOR]   0   0
```  - [COLOR=Blue]/dev/sdd1[/COLOR] - is the location of the FAT partition

 - [COLOR=Red]/usbdisc[/COLOR] - this is the folder where the partition will be mounted. If this folder doesn't exist you will need to create it yourself ```
sudo mkdir [COLOR=Red]/usbdisc[/COLOR]
``` **Note** you don't have to use [COLOR=Red]/usbdisc[/COLOR], its up to you

 - [COLOR=Green]vfat[/COLOR] - this specifies the filesystem as VFAT (virtual FAT?)

 - [COLOR=DarkOrchid]iocharset=utf8,umask=0000[/COLOR] - these options set the character encoding to utf8 (for special chars) and sets the **umask**.  [COLOR=DarkOrchid]umask=0000[/COLOR] allows read, write and execute access to the partition.

Then save the file (Ctrl +O) and exit (Ctrl +X) and then you can mount the USB with
```
sudo mount /usbdisc
``` or
```
sudo mount -a
```

---

### Post by CameronCalver on 2006-05-17
Hey thanks for the great response thats one of the best responses i have ever had so quickly but nothing ocmes up when i do that first thing so i think there is something wrong with my flash drive can you help me connect my logitech quickcam express
when i plug it in afteri typed that thing it comes up all this stuff lke 

usb -2 new full speed usb device using ohci_hcd address 3 
registered device  /dev/video0

---

### Post by Sutekh on 2006-05-17
No problem.

If nothing comes up from the tail message, then there may be something wrong.  It should do *something*.  This is not a card reader is it?  If so, you may find it needs a card inserted.

As for the camera, that could more tricky.  I haven't tried doing this sort of thing with a webcam.  There are plenty of threads about getting webcams (in particular Logitech) working.  See what you can find with a search.

Here might be helpful

[Ubuntu Forums - HOWTO: Making ICM532 chipset based webcams work on breezy]("http://www.ubuntuforums.org/showthread.php?t=75284")

---

### Post by CameronCalver on 2006-05-18
Hey yes it is a compact flash card reader and ill check that link but thanx for the great post i am not going to use it but i bet alot of people will use it so it was not a waste

---

### Post by theboatashore on 2006-05-21
I have a Toshiba CF card that I haven't been able to get working under Kubuntu for a while now.  Thanks a ton for your post, it's solved my problem.

---

### Post by groundpounder on 2006-05-22
I have a PNY thumb drive that was working fine.  I would plug it in, and an icon would appear on my desktop, I could browse, read write, etc., no problem.  Today, I did a kernel udate that came up as an automatic update, and now, it still detects the thumb drive (although no icon appears on the desktop anymore), but it won't mount.  I get the following when I double click on it in nautilus:
> Unable to mount the selected volume. 
The volume is probably in a format that cannot be mounted.

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount


---

