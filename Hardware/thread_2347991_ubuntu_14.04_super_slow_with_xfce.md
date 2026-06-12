---
title: "ubuntu 14.04 super slow with xfce"
date: 2016-12-30
forum: Hardware
---

### Post by matt18 on 2016-12-30
So the system that i have is running supper slow. Youtube just crawls and skips like non other. It is driving me crazy. 


```

             total       used       free     shared    buffers     cached
Mem:          1981       1623        357         13        298        792
Low:           858        761         97
High:         1122        862        259
-/+ buffers/cache:        533       1447
Swap:         2014        182       1832

```
you can see how much memory is being used. But system moniter says only 516mb is being used.... 

I am running a pentium 3.3 ghrz hyper threaded cpu(nothing special) and xfce desktop environment and onboard video.

Thanks

Would like to at least get youtube running faster.

---

### Post by ajgreeny on 2016-12-30
You are misreading the free output which shows your computer is actually using 533 MB ram and has 1447 available.
Linux manages memory quite differently from Windows as it does not release everything sitting in memory immediately but only when more memory is needed by the system.
```
-/+ buffers/cache:        533       1447
```is the important line of that output.

Are you using flash or html5 for youtube?
You can tell that by going to [https://www.youtube.com/html5](https://www.youtube.com/html5) to see what your personal settings are; if not html5 at the moment change the setting to use it as it is much better in my opinion.

If still using flash, what version? This site will tell you that.
[http://www.adobe.com/uk/software/flash/about/](http://www.adobe.com/uk/software/flash/about/)

---

### Post by poorguy on 2016-12-30
> **matt18 said:**
> So the system that i have is running supper slow. 
I am running a pentium 3.3 ghrz hyper threaded cpu(nothing special) and xfce desktop environment and onboard video.

Thanks
Is the processor a Pentium 4? 
If it is I would recommend using Lubuntu 16.04 (32bit) as it is designed to run on older less powerful hardware.

Lubuntu 16.04.1 download link.
[http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/)

This may also help.
[https://ubuntuforums.org/showthread.php?t=2130640](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by matt18 on 2016-12-30
yes its a P$ and i am using html 5. let me double check which version of ubuntu i am using....... yup its 14.04

thanks for the links. i am reading them now. ill decide if i want to download and burn an image and upgrade the distro for my dad.

---

### Post by vasa1 on 2016-12-31
Is this the same machine as the one in your other [Super slow]("https://ubuntuforums.org/showthread.php?t=2335535") thread?

---

### Post by matt18 on 2016-12-31
> **vasa1 said:**
> Is this the same machine as the one in your other [Super slow]("https://ubuntuforums.org/showthread.php?t=2335535") thread?

i think its a different one, but i will double check. i have like 4 machines that are simular in specs but this one i actually added more ram and a new hdd

yeah its a simular system as this one. thanks for bringing that post up. do you think a better nvida gpu will help it? is there a way to upgrade the distro with out having to re-install and download anything? i just want to get it fixed for my dad haha

looks like im using a way old ati driver...

*-display               
       description: VGA compatible controller
       product: RC410 [Radeon Xpress 200/1100]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: **driver=radeon latency=64 mingnt=8**
       resources: irq:17 memory:d0000000-d7ffffff ioport:ec00(size=256) memory:dfdf0000-dfdfffff memory:dfe00000-dfe1ffff

---

### Post by poorguy on 2016-12-31
I'm using a computer with the same integrated ati radeon graphics adapter RC410 [Radeon Xpress 200/1100] which can be a bottleneck when streaming youtube videos in HD resolution so try lowering your resolution and see if that helps.
I believe that your other cause may be due to your Pentium 4 Processor which just doesn't have enough power to run youtube videos using firefox as firefox requires massive resources.

I would also recommend Lubuntu 16.04 32bit for that computer as mentioned in my earlier post.

---

### Post by matt18 on 2017-01-01
ok cool. i will think of upgrading then. i have tried to use lower res on youtube but still no go. thanks for all the help. What is going to be the best way to upgrade the OS without losing any apps or data?

thanks

---

### Post by Yellow Pasque on 2017-01-01
> do you think a better nvida gpu will help it?

No, not for watching streaming video, nor do I think upgrading from 14.04 to 16.04 is going to give you a big boost.

Probably the best way to deal with the issue is using an add-on to watch the video locally: [https://addons.mozilla.org/en-US/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-US/firefox/addon/watch-with-mpv/)
In that case, a newer video card may help if your system is still too slow. (Or it may help keep power consumption down since I imagine a 3.3GHz P4 also doubles as a space heater when decoding video without GPU help.)

---

