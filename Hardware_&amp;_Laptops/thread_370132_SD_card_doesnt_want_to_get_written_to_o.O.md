---
title: "SD card doesnt want to get written to o.O"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by 9a3eedi on 2007-02-25
Hi.

I've been using a USB 6-in-1 card reader in order to read and write to my microSD card which I connect to one of those SD card adapters...

anywho

I was copying a few video files to it. After that I wanted to copy some more stuff, but it told me that the disk is read only. Strange. The lock wasn't on. I thought this could be because of the adapter, so I tried using another SD card and I get teh same issue. Then I tried an MMC card, which doesnt even have a lock, but it still tells me that it's write protected. 

I then connected a Memory Stick PRO to the card reader, and I was able to write and read to it. Strange

I then connected the card reader to a Windows box. Writing to SD cards, including my microSD worked fine with no problems.

What's causing this o.O


I'm using gnome on a kubuntu install on a laptop centrino 1.7 ghz on edgy x86

---

### Post by 9a3eedi on 2007-02-26
um.. bump



oh ya.. forgot to mention.. I tried mounting it in the terminal.. like this
```

mount -o user,rw,exec,umask=000 /dev/sda1 /media/usbdisk 

```

so that any user can gain access to it. I still wasnt able to write to it, nor was root able to either. 

The filesystem is FAT16 .. that's fully supported by linux right?

The interesting thing is that Windows was able to write to the same SD card using the same adapter.. so there must be something wrong with the configuration in linux, especially since it used to work fine.

---

### Post by Tom Tiger on 2007-02-26
you can try sudo mount.

I've had almost the same problem on a SDcard of 1GB, which simply refused to write after some time, which was odd since it allways worked before, it was also a fat16 and could also be written under w2k.  I reformatted it to vfat (fat32) and never had the problem again.  It's worth a try.

---

### Post by 9a3eedi on 2007-02-26
well of course I tried sudo mount :P how can I mount otherwise?

Anyway, I was thinking of the same thing.. formatting it. But I had doubts about it. So I try it out, and see what I'll get..

---

### Post by 9a3eedi on 2007-02-26
I found the source of the problem.

Apparently the filesystem had errors.. This was apparent when I ran qtparted on console. It wasn't formatting.. it was giving me an error in the console

```
Fatal: Bad FAT: unterminated chain for \MSMETA~1.  You should run dosfsck or scandisk.
```

so I ran dosfsck -a /dev/sda1

fixed everything. Though when I opened the SD's mount point, I found lots of files that were apparently created by dosfsck (due to them being called dosfsckxxxx.rec, where the x is a number) Deleted those, no problem. And now I'm able to copy stuff back and forth to my microSD

Thanks a lot ^________^

---

