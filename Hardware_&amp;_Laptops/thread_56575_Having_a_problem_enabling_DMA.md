---
title: "Having a problem enabling DMA"
date: 2005-08-13
forum: Hardware &amp; Laptops
---

### Post by Dolphin on 2005-08-13
Ubuntu is installed on a 200GB SATA drive, which seems fine.
I also have a 200GB ATA storage drive and a Pioneer A09 DVDRW, both of which I cannot seem to enable DMA on.

```
dolphin@ECHO:~$ sudo hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

dolphin@ECHO:~$ sudo hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
dolphin@ECHO:~$                             
```

I did this for both my DVDRW and my HD, both with the same result.
I also tried editting hdparm.conf to enable DMA on startup:

```
   /dev/hdc {
   dma = on
   }
```

Nothing has yet worked.
What am I doing wrong?

---

### Post by heimo on 2005-08-13
Do you know which motherboard, and more specifically, which chipset you're using? You probably need to load module for that (edit /etc/modules and /etc/hdparm.conf) and reboot. Loading correct module with modprobe after boot didn't work for me. Correct module name depends on the chipset, for my Via based motherboard it was  via82cxxx.

See these threads:
[http://www.ubuntuforums.org/showthread.php?t=30949](http://www.ubuntuforums.org/showthread.php?t=30949)
[http://www.ubuntuforums.org/showthread.php?p=93238#post93238](http://www.ubuntuforums.org/showthread.php?p=93238#post93238)

---

### Post by Dolphin on 2005-08-13
ASUS A8V Deluxe
VIA K8T880 Chipset
VIA SATA Controller

---

### Post by heimo on 2005-08-13
run:
 ```
lspci  | grep -i ide
``` 

I get:
```
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
```

---

### Post by FLeiXiuS on 2005-08-13
I've been having the same problem and I'm still looking for a solution, I'll let you know if I find one.

---

### Post by tseliot on 2005-08-13
Which kernel are you using?

If you don't know, just type "uname -r" in Terminal or Konsole.

If it is 2.6.10 then maybe installing 2.6.11 could do the trick for you (it is in Universe repositories, read the Unofficial Ubuntu Starter guide if you don't have them in you /etc/apt/sources.list)

Otherwise, if it didn't work you should compile a new kernel and disable the function "Enable DMA only for disks" (use this as your last resort).

Let me know if it works

---

