---
title: "Tell Me About 13.04/13.10 on a ThinkPad W530"
date: 2013-08-11
forum: Hardware
---

### Post by buzzingrobot on 2013-08-11
I have a ThinkPad W530 on order.  I'll need to use Windows with it for a few months but then will likely move it to 13.04 or, perhaps by then, 13.10.

The machine will have two 500GB drives in a hardware RAID 1 setup, discrete Nvidia K1000M GPU plus the onboard Intel, 1920x1080, and an Intel Centrino Ultimate-N 6300 for the wifi.

So, some questions about Ubuntu on my new toy:

1. Are there any obvious "you can't do that!" gotchas? Any component Ubuntu won't support?

2. How should I configure video in the BIOS for the install?  I am assuming it will find the onboard Intel and install with Nouveau.

3. I hope to disable the Intel GPU in the BIOS, install an Nvidia driver for the K1000M and use it exclusively. Doable? Can I get that driver via "Additional Drivers" or will I need to go to the Nvidia download? 

(3A.  I assume the sequence for installing that Nvidia K1000M driver is this: Running on Nouveau on the Intel, install the Nvidia driver, reboot, enter the BIOS and enable only the K1000M, then reboot and watch the Nvidia driver in action.)
  
4. Any issues or quirks with that video setup?  I've seen one post complaining about small video artifacts.  

5. Will the fans behave if I'm running the K1000M? (The machine will almost always be plugged in, not on battery power.) If the fans don't behave, is software available to control them?

5. I'll be on ethernet most of the time, but will need to use wifi sometimes.  Will I need to jump through any hoops to get that Centrino working?

6.  Fingerprint ID seems like it will be handy.  Can Ubuntu handle it?

7.  How's the TouchPad on Ubuntu?

Thanks.

---

### Post by RichardET on 2013-08-13
I have a W530 bought last December, like the laptop, but still running native Windows 8 pro and using VMWare, with Ubuntu 13.04 as a guest.  It works flawlessly;  I would prefer the reverse setup, because i already have an existing licensed copy of windows 7 64 bit also configured as a VM and it also has all my main windows applications on it,if my hardware worked nearly 100% with Ubuntu as the host OS, but I am simply not interested in experimenting right now, I don't have time for it.  Also I have attended many free events here in NYC sponsored by VMWare, and their concepts really make sense to me and I am wondering why we should ever waste time making a system fit a particular hardware configuration, if a VM solution for that OS exists now, and works flawlessly.

---

