---
title: "Toshiba Satellite and Wine Unrecoverable Freeze"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by Caedis on 2008-01-28
I have been looking everywhere for a fix on this but nothing is specific to my issue.

I have a Toshiba Satellite A105-S4001 with a Intel 945GM Chipset/GPU. I'm running Ubuntu 7.10 Gutsy.

I can run with all features enabled in Emerald, no slowdowns at all.  In fact my system runs flawlessly in Ubuntu.  One problem.  When attempting to run any Direct X game in Wine  OR Cedega, the whole computer freezes.

With wine, I run the programs and the screen freezes with the exception of the mouse cursor. I cannot use keyboard shortcuts like Ctrl+Alt+Backspace, I cannot click ANY buttons, no visible keyboard response.  I've let it stay in this state for 30 minutes just to make sure its not just loading the game. 

At this point the only way to recover is to do a hard restart by holding down the power button for 10 seconds.

Heres my system info according to Cedega:

cpu: Genuine Intel(R) CPU           T1300  @ 1.66GHz
cpu_ghz: 1.0
memory: 3033
videocard_manufacturer: Tungsten Graphics, Inc
videocard_type: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
videocard_ram: 4096
agp_aperture_size: N/A
videocard_driver_version: 1.3 Mesa 7.0.1
soundcard: HDA Intel at 0xdc240000 irq 2
soundcard_driver: ALSA Version 1.0.14
machine_bitness: 32
kernel: 2.6.22-14-generic
x_version: Xorg Version 1.3.0
distro: Debian lenny/sid
GUI version: 6.0.2


Also, the whole point of this is to delete my Windoze partition, dual-booting is a pain, and I'm sick of Windows all together, yes, all my games run perfectly in Windows.  Bleh.


Any help will be IMMENSELY appreciated.

---

### Post by ubuntu-freak on 2008-02-11
I'm sorry you didn't get a reply before now. It sounds like Wine doesn't like your sound card/chip very much. Not sure what you can do except report it as a bug, give them full details of your hardware and then hope they correct the problem soon.
 
Nathan

---

