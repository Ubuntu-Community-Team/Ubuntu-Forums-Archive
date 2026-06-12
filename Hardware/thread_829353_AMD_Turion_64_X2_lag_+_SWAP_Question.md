---
title: "AMD Turion 64 X2 lag + SWAP Question"
date: 2008-06-14
forum: Hardware
---

### Post by David Benjamin on 2008-06-14
Hello, I currently own a Acer Aspire 5104 WLMI Laptop. With a AMD Turion 64 X2 1,8 Gigahertz TL-56 processor and 2048 DDR2 SoDimm Ram (2x 1024). 

Now basicly, I am having some lag, this also occured in windows since I doubled the ram. A very strange thing, anyway in Linux this never was a problem. Till now, I am having a strange lag again. And maybe the SWAP has nothing to do with it, it does attract my attention that the SWAP is almost been used by Ubuntu, the swap partition is 10 gigabyte because I have too much space. 

The only operating system I have installed on my laptop currently is Ubuntu 8 (latest one). Before I had Ubuntu 7 installed, worked very good. 

Help is appreciated.

Thank you

---

### Post by lavinog on 2008-06-14
I would reduce the swap space to 2gigs or less.
Are you running ubuntu 64 bit or 32?

Maybe you should run memtest since this seems to be ram related.

And what do you mean by lag? is the computer sluggesh?

what does free report
```
free -m
```

---

### Post by David Benjamin on 2008-06-15
```
             total       used       free     shared    buffers     cached
Mem:          2025        780       1245          0         16        367
-/+ buffers/cache:        396       1629
Swap:         9538          0       9538
```

The computer runs Vista etc. fine with a score above the standards (4/5). Anyway Ubuntu 7 seemed to run faster though.

---

### Post by lavinog on 2008-06-15
are you running 32bit ubuntu? I think there could be a problem if your swap is larger than 4gigs.
[I]"Swap partitions don't need to be any larger than 2X your system ram. And, the sum of system ram and swap shouldn't exceed 4 Gig. If it does, reduce the swap partition size to get back to 4 Gig. or less. If you have 4 Gig. of ram on a 32 bit system like Mint, make a very small swap partition anyway, as the kernel expects to have a swap partition available. Not having a swap partition slows the kernel down in certain situations. For this purpose, there is no need for the swap partition to be over 256 KB at most."
[/I]Quoted from post #5 on this thread [http://ubuntuforums.org/showthread.php?t=815547]("http://ubuntuforums.org/showthread.php?t=815547")
You may want to consider switching to 64bit ubuntu if you are not already.

also 
what video card do you have?
what happens if you run glxgears

---

### Post by David Benjamin on 2008-06-15
I have a ATI Radeon Mobility X1300 and when I run glxgears I get the following:

```
david@Acer:~$ glxgears
6751 frames in 5.0 seconds = 1347.867 FPS
7974 frames in 5.0 seconds = 1593.541 FPS
9596 frames in 5.0 seconds = 1919.057 FPS
9630 frames in 5.0 seconds = 1925.846 FPS
9708 frames in 5.0 seconds = 1941.538 FPS
9574 frames in 5.0 seconds = 1912.716 FPS
7641 frames in 5.0 seconds = 1528.094 FPS
7146 frames in 5.0 seconds = 1429.176 FPS
8469 frames in 5.0 seconds = 1693.737 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 83253 requests (83252 known processed) with 0 events remaining.
david@Acer:~$ 

```

And yes, I used to run Ubuntu 7.10 on 64 Bit. However the main problem was installing my Atheros 5007EG WiFi card on 64 Bit linux. That is a pain in the *** and it does work propperly on 32 bit.

---

### Post by lavinog on 2008-06-15
> **David Benjamin said:**
> 
And yes, I used to run Ubuntu 7.10 on 64 Bit. However the main problem was installing my Atheros 5007EG WiFi card on 64 Bit linux. That is a pain in the *** and it does work propperly on 32 bit.

Well then that might be the problem then...but I don't know about the windows side of it though, unless you manually configured your VM size.

---

