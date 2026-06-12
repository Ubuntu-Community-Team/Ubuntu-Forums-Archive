---
title: "Can Ubuntu 15 run on a BayTrail processor?"
date: 2015-08-26
forum: Hardware
---

### Post by bomyne on 2015-08-26
I've tried googling the processor in relation to linux and only seem to get information about tablets...

I have a laptop that is running an Intel Bay Trail M processor (Asus F553M). I had bought it with the intent of replacing Windows with Linux, but I had never heard of the Bay Trail M before... I get the laptop home and try to install Linux Mint 17.2. It freezes permanently during the boot process. Annoyed, but determined, I load up the other iso stored on my PC's hard drive, Ubuntu 14, and try to boot it... It also freezes. Considering Mint 17.2 is based on Ubuntu 14, I am not surprised.

I have been continually googling to no luck... Either I am not trying the right search phrase, or there is no information out there.

My question is, does anyone know if Ubuntu 15 can run on a Bay Trail M Laptop? And if not, can any distro?

Thank you.

---

### Post by TheFu on 2015-08-26
The CPU is fine.  x86 is x86.  x64/amd64 are fine.

The motherboard might be the issue or any of the other components.
Google found this: [https://askubuntu.com/questions/558476/computer-only-starts-recovery-mode-ubuntu-14-04-lts](https://askubuntu.com/questions/558476/computer-only-starts-recovery-mode-ubuntu-14-04-lts)
and lots of others seem to be having a similar issue. My Spanish and Portugese aren't good enough to tell if they found solutions or not.

[http://ubuntuforums.org/showthread.php?t=2253168](http://ubuntuforums.org/showthread.php?t=2253168) far down the replies says:

> I found that solution for this was to change "OS Selection" in BIOS Advanced settings from "Windows 8" to "Windows 7". 
That is in addition to disabling SecureBoot and Widnows Fastboot.

---

### Post by bomyne on 2015-08-26
> **TheFu said:**
> 
[http://ubuntuforums.org/showthread.php?t=2253168](http://ubuntuforums.org/showthread.php?t=2253168) far down the replies says:


That is in addition to disabling SecureBoot and Widnows Fastboot.

Changing that setting to Windows 7 worked. The computer booted Linux. Then the touchpad didn't work but I'm sure that'll be easy compared to this.

Thanks.

---

