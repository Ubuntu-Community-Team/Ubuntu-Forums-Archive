---
title: "Swapping to video ram"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by apfsdsdu on 2006-12-03
I found an article about using video ram as a block device and decided to try using some of the 64 megabytes that my Ati Rage 128 has. I configured Xorg to use 4096 k of video ram. The block device works when I use a very small amount (less than 10 MB) of memory, but when using more, the data seems to go where the actual graphics are and the screen goes all weird. The computer doesn't crash or anything, and the screen goes back to normal after removing the slram and mtdblock modules.  I think I have the memory addresses wrong, but I don't know how or why.

The article is here: [http://www.linuxnews.pl/_news/2002/09/03/_long/1445.html](http://www.linuxnews.pl/_news/2002/09/03/_long/1445.html)

Because of udev, I didn't create the device nodes myself. They appear automatically after modprobing the mtdblock module. This is what I did:

Get the memory addresses:
```

$ cat /var/log/Xorg.0.log | grep frame
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(--) R128(0): Linear framebuffer at 0xe0000000

```
Insert the modules:
```

$ sudo modprobe slram map=VRAM,0xe0400000,+0x03b00000

$ sudo modprobe mtdblock

```
At this point the /dev/mtdblock0 device appears. Everything seems to be ok. To test the new device, I created a vfat filesystem on it and mounted it and copied stuff on it. When the files are written on the device, they replace the picture on the screen. I've tried different memory addresses, but only the ones that start at 0xe0400000 work, and only when the device is about 10 MB or smaller. So does anyone have any ideas about how I could use the 60 megabytes that aren't used by X?

---

### Post by apfsdsdu on 2006-12-05
I tried this on a different computer with a Radeon 9200SE with 128 MB of ram. On that the memory trick works just like it should. I still can't get it to work on the computer that has the older graphics card.

---

