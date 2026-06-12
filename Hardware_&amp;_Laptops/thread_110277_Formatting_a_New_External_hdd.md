---
title: "Formatting a New External hdd?"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by shane2peru on 2005-12-30
I bought a 160 GB Western Digital hdd.  I have a laptop and want to use it to back up and store things on.  I plugged it in and windows XP has many issues with detecting an unformated USB hdd.  So I turned to faithful Ubuntu.  I opened qparted and can see it there.  It has nothing on it, and has NEVER been formatted.  It wouldn't let me format it.  It doesn't give an error message or anything, it simply says, "It was not possible to make a new partition table." 

Here is my sudo fdisk -l
```

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2493    20024991    7  HPFS/NTFS
/dev/hda3            3826        4864     8345767+   5  Extended
/dev/hda4            2494        3825    10699290    b  W95 FAT32
/dev/hda5            4313        4373      489951   82  Linux swap / Solaris
/dev/hda6            3826        4312     3911764+  83  Linux
/dev/hda7            4374        4864     3943926   83  Linux

Partition table entries are not in disk order

[b]Disk /dev/sda: 168.6 GB, 168631950848 bytes
255 heads, 63 sectors/track, 20501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes[/b]

Disk /dev/sda doesn't contain a valid partition table

```

I highlighted the part about the new usb hdd.  How can I format this?  Any help would be greatly appreciated.  

Shane

---

### Post by abovett on 2005-12-30
Hi.

Is the HDD an IDE one in a USB caddy? If so, can you connect it directly to a PC via an IDE cable to partition it?

Not got much experience with USB drives so if not I'm not sure I can be of much help.

Andy B

---

### Post by shane2peru on 2005-12-30
Andy, 

   Thanks for the response.  No I don't have any way of connecting it directly with the IDE cable.  It is an IDE harddrive and it is in an external enclosure.  I can connect it with a USB cable or a 1394 Firewire. 

Shane

---

### Post by shane2peru on 2006-01-04
FYI,

   I got it.  It took some time and effort, but I got it.  Let me say that I tried with both OS, and thought that I had formatted it correctly several times only to find that it didn't work.  Let me say also that "they" said it couldn't be done with a laptop since it was an external NEW (never formatted) IDE hdd.  Ok, to boil it down.  
     Once I figured the jumper settings out I booted off the Ubuntu Install disk.  I went all the way to the disk partitioner.  My **external** hdd was listed so I formatted 2 partitions in fat32 in the **external** hdd.  It is important that you **do not touch your existing insternal hdd YOU WILL LOOSE EVERYTHING!**  (If you are only trying to format your external hdd.)  I wrote the changes to the hdd about 2 minutes later I ABORTED the installation, and exited.  I booted normally into Ubuntu, and both partitions were accessible with rw permissions.  I copied two files to both partitions.  exited and booted into XP, and was able to use both partitions.  That was it.  That simple.  
     Hope this helps someone.  I had tried repeatedly with QTParted and got the error message above.  I had tried with the Disk Management part of XP multiple times only to get simple error messages.  This may not be the best way, but did seem the simplest way for me.  I didn't have to mess with permissions afterward either.  I don't know if this had to do with the way it was formatted or not.  Hope this helps!  :D 

Shane

---

### Post by Claus7 on 2007-05-08
I know that this is already an old forum, yet this might help:
[http://ubuntuforums.org/showthread.php?p=2614591#post2614591](http://ubuntuforums.org/showthread.php?p=2614591#post2614591)

Regards!

---

