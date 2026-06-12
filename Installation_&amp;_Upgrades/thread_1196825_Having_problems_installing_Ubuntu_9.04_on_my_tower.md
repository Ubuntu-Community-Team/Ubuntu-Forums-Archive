---
title: "Having problems installing Ubuntu 9.04 on my tower"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by DMBoricua on 2009-06-25
Hello, I'm having problems installing Ubuntu. This is a very rare case because in the past years I have installed Ubuntu on my computer, and on many machines, regardless of their configuration, and has been absolutely flawless. Loved Ubuntu for that. 

Now I wanted to have Ubuntu on my tower again. This is how it is, I have 3 hard drives on my tower, one with Windows XP and the other one with Vista, the last one being the free spaced 250GB hard drive for me to install Ubuntu. When I do the process of installation, it goes great, I do the restart and goes without problems. Normally I would see the GRUB Bootloader of Ubuntu which would take me to choose either Ubuntu first, or choose other operating systems and from there I choose either Windows XP or Vista but this time it didnt do it :confused:. I did not get that bootloader this time.

When I boot, I get the same Windows bootloader of either Vista or "Earlier version of Windows" which is XP. I change the hard drive boot sequence on the BIOS to see if I can get to load Ubuntu up and I get a different message, pretty much regarding to Ubuntu, which goes like this: 

GRUB Loading stage1.5.

GRUB loading, please wait....
Error 17
_


I have tried installing Ubuntu 2 times, performing a full format of the 250GB hard drive once (which took a very long time) and yet again tried to install Ubuntu to see if that was the problem, but came with the same results. Anyone know the problem?

---

### Post by DMBoricua on 2009-06-25
Ok, I have been downloading the Ubuntu 9.04 **i386** ISO which to my understanding is incorrect, I should be getting the AMD64 version since I got an AMD Athlon 64 X2 Dual Core Processor 6000+. When the download is done, I will atempt to install Ubuntu again.

I got another question for this, is this Ubuntu version (AMD64) the Ubuntu 9.04 **64-bit** Operating System? I've been doing a lot of research just now and I still dont get a clear message if this version is fully 64-bit architecture.

---

### Post by oldos2er on 2009-06-25
"I got another question for this, is this Ubuntu version (AMD64) the Ubuntu 9.04 **64-bit** Operating System?"

 Yes, and it works on 64-bit Intel processors as well.

---

### Post by mk1w86 on 2009-06-25
Although you have a 64bit processor the 32bit version of Ubuntu should still work fine.

---

### Post by DMBoricua on 2009-06-25
Ok, I got Ubuntu to work now. I have used this program called Wubi under Windows XP, have done a restart and was finally able to see the selection of Ubuntu on the bootloader and log on :)

I have done a fresh install of the **AMD64** version of Ubuntu because I wanted to see if I could take advantage of the 64-bit architecture, but in my opinion is not very good. You get less driver/plugin selections and are not fully reliable. Even loading up Firefox I could not get a good flash plugin to view videos right, videos were pixely or otherwise would not play. So I just installed the **i386** version of Ubuntu and everything works perfect, videos are fine and such. You get a lot more wide selection of drivers and plugins on the more common i386 version of Ubuntu :)

I guess I'm not ready for 64-bit architecture :)

---

### Post by lisati on 2009-06-25
To get the best from your 64-bit machine, you'll need the 64-bit version of the OS, but occasionally you might run into a situation where there's only 32-bit software available. I've seen workarounds mentioned in the forums that sometimes help use 32-bit software on a 64-bit OS.

The 32-bit OS should work fine on a 64-bit machine if you find things a little daunting. For most of the time I've had my main desktop, I've been running 32-bit software quite happily, unaware until recently that it was a 64-bit machine.

---

### Post by oldos2er on 2009-06-27
> **DMBoricua said:**
> I have done a fresh install of the **AMD64** version of Ubuntu because I wanted to see if I could take advantage of the 64-bit architecture, but in my opinion is not very good. You get less driver/plugin selections and are not fully reliable. Even loading up Firefox I could not get a good flash plugin to view videos right, videos were pixely or otherwise would not play. So I just installed the **i386** version of Ubuntu and everything works perfect, videos are fine and such. You get a lot more wide selection of drivers and plugins on the more common i386 version of Ubuntu :)
  :)

 Not sure which drivers or plugins you're referring to; but there is a 64-bit version of Flash which, though it is alpha, has worked well for me. I've been using 64-bit Ubuntu for not quite two years, and haven't found a lack of 64-bit apps.

---

### Post by monkeyking on 2009-06-27
We've been running a mix of 32bit and 64bit for the last couple of years.

And the driver issues has improved alot, but its not really the state of the art yet.
Installing an alpha driver on a production machine with the database backbone for 100clients is not really sane.

It is true though, that the problems are normally in the more exortic area,
like rev. engined winxp drives and win32 media drivers.

Its very likely possible to work things out on a 64bit,
but the 32bits are, atleast for our setup,
less hazzlefree

---

