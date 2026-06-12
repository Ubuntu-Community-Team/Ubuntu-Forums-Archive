---
title: "Files being deleted randomly."
date: 2013-01-26
forum: Hardware
---

### Post by nhkim on 2013-01-26
Hi, 

I'm using an SD card for additional storage/backup for my documents. Today, a bunch of my files got deleted from one of the folders inside the SD card. This happened before, but the files later re-emerged. I can't get the files to do that again, and I'm wondering wtf is going on. 

Thanks for any help.

---

### Post by sudodus on 2013-01-26
Good question :P

I think that the file system (FAT32 I guess) is damaged. The best way to check and if possible repair it is to run
```
chkdsk /f
``` in a Windows computer.

If you pull out the SD card too quickly, before it has finished writing, the file system might be damaged. You probably know already to always 'unmount' or 'eject' the drive or partition before disconnecting. But you need to wait until it finishes, and that can be checked with the terminal window command ```
sync
``` Wait until it returns to prompt!

---

### Post by nhkim on 2013-01-31
How do I check to make sure the volume was properly ejected? I click eject or unmount, but I still see the drive on my desktop. (It's transparent though, and I assume this means it isn't mounted). I want to make sure 100% that it's been completely unmounted.

On a different note. My SD Card is incredibly slow. I formatted it to fat32 (is there a better one that I can use on Linux, Windows, and Mac?) and the file transfer is very very slow. When I move files to my internal (SSD) from a USB drive, it is about 10 times faster. No exaggeration. A video file taking 47 minutes to move into the SD took only about 5 mins when moving directly to the internal (both from a USB). 

Is that normal?

---

### Post by fdrake on 2013-01-31
> **nhkim said:**
> How do I check to make sure the volume was properly ejected? I click eject or unmount, but I still see the drive on my desktop. (It's transparent though, and I assume this means it isn't mounted). I want to make sure 100% that it's been completely unmounted.



in the terminal ```

mount -l

```
will list the mounted filesystems

> 
On a different note. My SD Card is incredibly slow. I formatted it to fat32 (is there a better one that I can use on Linux, Windows, and Mac?) and the file transfer is very very slow. When I move files to my internal (SSD) from a USB drive, it is about 10 times faster. No exaggeration. A video file taking 47 minutes to move into the SD took only about 5 mins when moving directly to the internal (both from a USB). 

Is that normal?
fat32 or ntfs are your best choises. when you format it (gparted) it will ask you for quick or slow format: (choose the slow format option) I do believe that the quick format doea not co mpletely erase your data just formats the disk blocks wiht the spec file sys you have selected: anyone correct me if I am wrong..

---

### Post by ahallubuntu on 2013-01-31
Understand that an internal card reader on a PC is basically attached to a USB port internally.  So if you copy USB to SD card, you're basically copying USB to USB which would generally be really slow.  Also, SD cards themselves can use very slow flash technology - varies by the card.

Definitely make sure you do safe eject/unmount before physically removing the card, otherwise the filesystem could be corrupted for sure.

If the card is 4GB or smaller, stick with FAT32, because then a Mac will be able to deal with it automatically.  NTFS is better and allows files larger than 4.1GB (obviously not an issue if the card is 4GB or smaller).  Ubuntu works great with NFTS but Macs may not be able to write to NTFS automatically.

---

### Post by nhkim on 2013-01-31
Thanks everyone.

Last question: is it possible to name my drive when I format on gparted? I looked and it just formats and names the drive itself. I also don't remember it ever asking me if I wanted to do a quick or slow format.

---

### Post by fdrake on 2013-01-31
> **nhkim said:**
> Thanks everyone.

Last question: is it possible to name my drive when I format on gparted? I looked and it just formats and names the drive itself. I also don't remember it ever asking me if I wanted to do a quick or slow format.

when you delete the partition first and select creat a new on it will give you the "label" input. that's the name you give to your device. It will appear when you creat a new partition from an unloccated one not from an existing one. So you have to delete the whole partition first then create a new one in order to change the name.

---

### Post by Mark Phelps on 2013-02-01
Sorry to say this, but that is likely to be the USB reader device.

I've had repeated failures of the same nature and they stopped when I went out and replaced the built-in card reader with a USB-plugged card reader.

Size and speed of the SD card didn't really make any difference.  Encountered the errors ranging from class 2 256MB up to class 10 32 GB.

---

