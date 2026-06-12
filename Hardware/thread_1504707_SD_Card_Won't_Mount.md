---
title: "SD Card Won't Mount"
date: 2010-06-08
forum: Hardware
---

### Post by Th3Blaze on 2010-06-08
Hi!
I have an SD card and a reader, but the SD card won't mount.
It has mounted before and through the same reader.
I am on Lucid btw and it is:
Sandisk 128mb normal SD card.
Any help on this prob?

---

### Post by Th3Blaze on 2010-06-08
Please help!
Any other needed information?

---

### Post by unmole on 2010-06-08
Could you post the output of
```
dmesg |tail
``` here please?

---

### Post by Th3Blaze on 2010-06-08
Here you go!

```
[21975.172035] usb 2-7: device not accepting address 6, error -62
[21975.348038] usb 2-7: new full speed USB device using ohci_hcd and address 7
[21975.756038] usb 2-7: device not accepting address 7, error -62
[21975.756074] hub 2-0:1.0: unable to enumerate USB device on port 7
[22356.940533] operapluginwrap[14185]: segfault at 4a4 ip 0150ba05 sp bfb9aae0 error 4 in libflashplayer.so[1196000+994000]
[22628.613639] operapluginwrap[14653]: segfault at 4a4 ip 06501a05 sp bfd9fac0 error 4 in libflashplayer.so[618c000+994000]
[22641.893702] operapluginwrap[14696]: segfault at 4a4 ip 044c8a05 sp bf97d8a0 error 4 in libflashplayer.so[4153000+994000]
[23271.376762] operapluginwrap[14750]: segfault at 4a4 ip 04f52a05 sp bfffdbb0 error 4 in libflashplayer.so[4bdd000+994000]
[23281.684960] operapluginwrap[14770]: segfault at 4a4 ip 05d2ea05 sp bffba1d0 error 4 in libflashplayer.so[59b9000+994000]
[23802.439705] operapluginwrap[14822]: segfault at 4a4 ip 03de8a05 sp bffb5870 error 4 in libflashplayer.so[3a73000+994000]

```

---

### Post by dabl on 2010-06-08
Google turns up a lot of hits on that "usb 2-7: device not accepting address 7, error -62" error.

Have you tried rebooting your system without the card reader in it, and then (with the SD card already in the reader) just plug it into the running system?  That's how I use my card reader, and I've not seen this problem.

FYI, that's a nasty problem with Opera's plugin wrapper, too.

---

### Post by Th3Blaze on 2010-06-08
I might know why.
My wii formatted it using this program
So that should be the cause.
Is this fixable?
I can't reset otherwise someone will have to put the password on, which I don't know and they probably won't.

---

### Post by Th3Blaze on 2010-06-08
I'm really trying to press on so does anybody else know a possible way to do this?

---

### Post by dabl on 2010-06-08
Try running GParted, and see if the card shows up as a storage device/partition.  If yes, you can "format to" FAT32 filesystem type.

EDIT:  If wii screwed with the partition table, then you'll need to set a new partition table first, in GParted, before formatting.

---

### Post by Th3Blaze on 2010-06-08
Sorry, but I fixed it.
I used Disk Utility and formatted the volume to FAT.
Thanks anyway.
Btw, I can't administrate the computer anymore now.
I have come up with a new problem.
I am trying to copy a file named "data.bin" into a folder, but it says there is an input/output error.
I have downloaded it twice and neither worked

Couldn't help notcing but:
85 Views
8 Replies

Come on. Please!

---

### Post by dabl on 2010-06-08
> **Th3Blaze said:**
> 

Btw, I can't administrate the computer anymore now.



New problem.

Needs a new thread.

---

