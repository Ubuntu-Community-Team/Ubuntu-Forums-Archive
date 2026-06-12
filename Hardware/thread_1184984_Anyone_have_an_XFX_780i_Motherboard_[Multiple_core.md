---
title: "Anyone have an XFX 780i Motherboard? [Multiple cores issue]"
date: 2009-06-11
forum: Hardware
---

### Post by jseabold on 2009-06-11
I also posted to [www.kubuntuforums.net](www.kubuntuforums.net).  I don't know about crosstraffic, so I apologize if this is a crosspost.

I am following up on a discussion started [here](http://kubuntuforums.net/forums/index.php?topic=3104360) on the Kubuntu forums.  

My installation of Kubuntu does not detect my multiple cores.

```

~$ grep -i core /proc/cpuinfo
model name      : Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz
core id         : 0
cpu cores       : 1

```

Which clearly isn't right.  I have a 64-bit OS (Kubuntu 9.04 with KDE 4.2) and an SMP kernel.  I have also discussed this with XFX and they say that it is an OS specific issue and not a hardware one because BIOS shows the option to disable each of my cores (which apparently means that they are detected by the hardware, therefore working...).  I have tried booting with a Live CD of both Ubuntu 9.04 32 and 64-bit and Sidux KDE-lite.  All had the same results (/proc/cpuinfo should change for a live cd right?)

Anyway, I was just wondering if anyone had any ideas what was going on.

Also if anyone is using an XFX 780i could you please post the output of 

```

cat /proc/cpuinfo

```

Cheers

---

### Post by jseabold on 2009-06-18
In case anyone ever stumbles across this post.  I figured out my problem.  I needed to enable APIC in BIOS.

---

