---
title: "problem with video hardware acelleration (ubuntu14.04 - Intel Atom)"
date: 2014-06-22
forum: Hardware
---

### Post by Danieladelvalle on 2014-06-22
Hi folks! Things go like this...

**1 - experience level:**

I have no experience with coding, already used ubuntu but I didn't nothign special, just the same simple tasks I used windows before. Even though I try to do stuff and had at the past installed one or two apps readding detailed "how to's", I have no idea of howit is really done, I just go and try form what I read.


**2 - installation:**

I installed ubuntu 14.04 in my netbook days ago, using pen drive, erasing all the contet of the disk, windows 7 included, and I chose the option where linux does the disc partition itself


**3 - problem:**

The problem I noticed is that the colors are being processed the way windows did when booting in safe mode and the screen is flickering/trembling the same way. Also, it boots really slowly and takes it time for any tiny task, like searching or oppening the web browser, slower than when I had windows running.

As I felt powerless to solve this, tried to install Mint, and when it boots from pen drive, a error message appears saying that mint was "running without video hardware acelleration" therefore it was using the CPU  which explained why it was so slow. At the end I didn't installed mint, but I believe the same is going on here, as the videos problems I note are the same.

Sorry if it too stupid but it seems that when firts installing ubuntu, the video controler went away along with windows.


**4 - information:**

I searched for help and found a way to know what my video card was, and this is what I got:

```
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 0b)
```

and the description of the system that I got from "System Settings" is this one:

Memory: 1,9 GiB
Processor: Intel® Atom™ CPU N2600 @ 1.60GHz × 4 
Graphics: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OS type: 32-bit
Disk: 490,0 GB

________________

So... what should I do? There are any information I can get to help you help me out? It is really posible that ubuntu installation got the videocard controler away? I have to just download and install it? Beeing that the case how do I do it?


thanks in advance

---

### Post by Mark Phelps on 2014-06-22
Ubuntu uses the Unity desktop by default -- which demands considerable graphics power and expects hardware acceleration.

You would have done better, with a netbook, to try using Lubuntu. It uses a lot less graphics power and would probably perform a lot better.

---

### Post by Yellow Pasque on 2014-06-22
[http://askubuntu.com/questions/290515/how-to-install-intel-cedarview-drivers-on-ubuntu-12-10-or-higher#290680](http://askubuntu.com/questions/290515/how-to-install-intel-cedarview-drivers-on-ubuntu-12-10-or-higher#290680)

---

