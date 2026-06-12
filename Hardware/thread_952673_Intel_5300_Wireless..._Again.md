---
title: "Intel 5300 Wireless... Again"
date: 2008-10-19
forum: Hardware
---

### Post by zdoesitlikethis on 2008-10-19
Hey everyone!

This is my first post here.  

I just installed ubuntu (hardy... with the kernel on the latest livecd) for the first time ever on my new thinkpad w500...  I scoured and scoured the internet for the how-to's and after reinstalling using the non-64bit version this morning, my intel 5300 wireless started working (of course after i used the instructions using the compat/iwlwifi stuff)  The wireless light came on and is still on and I downloaded some updates, surfed some websites, etc... Wirelessly.  

PROBLEM:

I turned my computer on at work and it's not working anymore!  The wireless light is still on, but I'm not detecting any signals, but there SHOULD be signals.  I don't know if this affected anything, but I was messing with the taskbar(?) on the top and rearranging icons, and i accidently deleted my network icon (and i put a new one on... I THINK it's the right one.)  

Other than that, I don't know why my wireless stopped detecting anything!


Any words of wisdom?  PS I'm completely virgin to linux and the terminal, but i could surely type some commands to find some specs if needed.  

Thanks!

Zac

---

### Post by sreyan on 2009-01-16
Hi,
I think I might be having the same issue. I filed a bug report with some information.

[https://bugs.edge.launchpad.net/ubuntu/+bug/318078](https://bugs.edge.launchpad.net/ubuntu/+bug/318078)


Try seeing if the kernel is detecting your hardware. Open up a terminal and type lspci this will list pci devices on your machine visible to the kernel.

you might also want to check to see if the intel wireless kernel driver is loaded. lsmod lists kernel modules. I think iwlagn is for wifi link 5xxx and 4xxx cards.

Lastly for me at least it seems that the wireless driver was itself loaded and the hardware was detected, but the issue was with the network manager applet. Launchpad wouldn't let me select that package even though i could search for it within launchpad... maybe this is a transitional bug and nm-applet is being phased out? See this bug report: [https://bugs.edge.launchpad.net/launchpad/+bug/318079](https://bugs.edge.launchpad.net/launchpad/+bug/318079) and the attached image :(

---

