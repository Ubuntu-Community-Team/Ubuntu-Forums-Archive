---
title: "4gb kernel patch for 32 bit"
date: 2008-07-25
forum: General Help
---

### Post by sonicb00m on 2008-07-25
Does anyone know of a guide or can give me some help in recompiling the hardy kernel to allow for 4gb. Only 3gb of my system is being shown.

Is it even possible to actually run 4gb of physical ram with a swap file set?

---

### Post by RAOF on 2008-07-25
The [custom kernel build guide](https://help.ubuntu.com/community/Kernel/Compile) is a good howto.  You'll need to enable the PAE stuff (highmem or somesuch).

Alternatively, installing the x86-64 variant will give you full access to the full RAM space.

---

### Post by sdennie on 2008-07-25
It's possible to use 4GB+ of memory with Ubuntu: [http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

---

### Post by Krupski on 2008-07-25
> **sonicb00m said:**
> Does anyone know of a guide or can give me some help in recompiling the hardy kernel to allow for 4gb. Only 3gb of my system is being shown.

Is it even possible to actually run 4gb of physical ram with a swap file set?

If you have a 4+ gb capable computer (i.e. an Intel EMT64 or AMD64 CPU)... why not just Ubuntu 64 bit?

-- Roger

---

### Post by sonicb00m on 2008-07-25
Ubuntu 64 is too much trouble. I never get a stable system with Firefox and flash for a start and I can't get games to work because I can't get opengl to work despite installing the 32 bit stuff. That plus it doesn't seem any faster so the only real pro to it is ram above 4gb.

32bit should run with 4gb so why bother with ubuntu 64 ?

I will try the server kernel first and failing that building my own.

thanks.

---

### Post by Krupski on 2008-07-26
> **sonicb00m said:**
> Ubuntu 64 is too much trouble. I never get a stable system with Firefox and flash for a start and I can't get games to work because I can't get opengl to work despite installing the 32 bit stuff. That plus it doesn't seem any faster so the only real pro to it is ram above 4gb.

32bit should run with 4gb so why bother with ubuntu 64 ?

I will try the server kernel first and failing that building my own.

thanks.

That really seems strange to me. I've got a 64 bit capable machine (Intel DQ965GF motherboard and a Q6700 CPU with 8 GB DDR-2 memory) and Ubuntu Desktop 8.04.1 64 bit runs just beautifully for me. It's stable and everything works.

Maybe there's something dodgy with your computer? Are you overclocking it? Or, maybe you have a ram problem? Did you try running MEMTEST 86+ and see if your ram is up to snuff?

-- Roger

---

### Post by hyper_ch on 2008-07-26
simplest way would be to switch from the generic to the server kernel...

or just recompile the generic one with PAE

---

### Post by sonicb00m on 2008-07-28
> **Krupski said:**
> That really seems strange to me. I've got a 64 bit capable machine (Intel DQ965GF motherboard and a Q6700 CPU with 8 GB DDR-2 memory) and Ubuntu Desktop 8.04.1 64 bit runs just beautifully for me. It's stable and everything works.

Maybe there's something dodgy with your computer? Are you overclocking it? Or, maybe you have a ram problem? Did you try running MEMTEST 86+ and see if your ram is up to snuff?

-- Roger

I've run 64bit on 2 completely different systems and firefox and flash is just not as stable as running the 32 bit version. The other issue was running games in Wine, it just doesn't work properly in 64 bit. Otherwise the system was very good but the flash problem was very annoying, and those free versions of flash are just useless. Then you have other problems like having to install 32bit libraries for Skype and other hacks and tricks to get a few other proprietary software running. I just can't be bothered anymore.

I've installed the server version of the kernel and have 4gb enabled now so i feel i've lost nothing.

---

