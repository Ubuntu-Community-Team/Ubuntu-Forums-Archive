---
title: "Video Output on Sony VAIO SR"
date: 2009-01-08
forum: Hardware
---

### Post by mlyons on 2009-01-08
Hello,

I have a Sony VAIO SR-210D notebook that I am trying to run the live CD off of. It seems that I can get to the point of selecting to start the live CD (the still text based screen before you make a menu selection: check cd for defects, check memory, etc.), however, no output seems to be being delivered to my laptop screen.

I've observed the same problem with Fedora 10 from a Live CD environment. No video output.

How do I get my laptop screen to display something? I haven't tried the discs in another computer, but I'm sure the problem is that my laptop's video controller isn't supported. Any help?

---

### Post by igknighted on 2009-01-08
> **mlyons said:**
> Hello,

I have a Sony VAIO SR-210D notebook that I am trying to run the live CD off of. It seems that I can get to the point of selecting to start the live CD (the still text based screen before you make a menu selection: check cd for defects, check memory, etc.), however, no output seems to be being delivered to my laptop screen.

I've observed the same problem with Fedora 10 from a Live CD environment. No video output.

How do I get my laptop screen to display something? I haven't tried the discs in another computer, but I'm sure the problem is that my laptop's video controller isn't supported. Any help?

Choose safe graphics mode at the boot.  Once booted you can install the proper proprietary driver, or apply a fix for the intel gm45 if thats what your laptop uses (some sony's have an odd quirk with it)

---

### Post by mlyons on 2009-01-08
Hi there, Yes!, Using safe graphics mode does work. I'm actually typing this while in the live CD environment. So once I install (thinking about doing a dual boot, then I will be able to install all the proprietary drivers. At least the wireless internet works! And its very fast. 

The only thing I notice is that the screen resolution is a lot less than the optimal resolution of my laptop screen. Will this problem be able to be rectified once I install the actual operating system?

To do a dual boot, do you have any resources you can direct me to?

---

### Post by chex_m8 on 2009-01-10
I just recently set up a dual boot with vista and ubuntu on my vaio sr290 and everything is working great. I used the ndiswrapper to get the wireless working and there was an issue with the intel video driver for this model so here is a link to help with that.
  
[Link]("http://ubuntuforums.org/showthread.php?t=1023801") to post with info about intel video driver on vaio. 

I had the same problem you had with the live cd at first so i'm thinking  you will need to do this to get your video driver working.

Here is a LINK to the resource i used to set up my dual-boot. I did not use the vista partitioner though, I always use Gparted. [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

---

### Post by niceguy123 on 2009-01-10
> **mlyons said:**
> Hi there, Yes!, Using safe graphics mode does work. I'm actually typing this while in the live CD environment. So once I install (thinking about doing a dual boot, then I will be able to install all the proprietary drivers. At least the wireless internet works! And its very fast. 

The only thing I notice is that the screen resolution is a lot less than the optimal resolution of my laptop screen. Will this problem be able to be rectified once I install the actual operating system?

To do a dual boot, do you have any resources you can direct me to?

I was think of dual boot to [http://ubuntuforums.org/showthread.php?t=1032547](http://ubuntuforums.org/showthread.php?t=1032547)

But as you'll see ended up with no windows and am not sorry.

---

