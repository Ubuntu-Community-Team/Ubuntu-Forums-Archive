---
title: "HELP! nVidia nForce 750a SLI"
date: 2008-09-08
forum: Hardware
---

### Post by gforcing on 2008-09-08
I just finished an unusually difficult install of Ubuntu 8.04 on a system with an nVidia nForce 750a SLI chipset. (Gigabyte GA-M750SLI-DS4, specifically). 

When the system booted up, imagine my surprise when I didn't have internet connectivity! forcedeth is running, which is also surprising. Hardware address is reported correctly, but it's not retrieving any information (IP address, DNS, etc) from DHCP.

I've seen a couple of threads on here already, but it doesn't seem like anyone has figured this out yet. Is there a solution I'm missing? Please help!

---

### Post by Throwback on 2008-10-30
FYI I now have the same mobo and will be installing 8.10 as soon as it is available (I have prepped a fakeraid setup that I dont mind hosing so I can test that too)

---

### Post by athlonx2 on 2009-03-12
lucky you two.. my install won't even begin the install i have some problems with an usb device in port 2 and i can't find the problem..


xfx nforce 750a sli
athlon x2 6000+
crucial pc6400 8 gb
xfx geforce 8800 GT
2x36gb raptor system disk
2x640gb storage

even do i undo the raid config i still have the same problem..

---

### Post by merganzer on 2009-05-18
i must have beginners luck.

i also have the XFX nForce 750a SLI motherboard with XFX nVidia 8800 GT video card.

i managed to install ubuntu 9.04 (jaunty) without a hitch.

i have yet to try any 3d acceleration etc. but the basics are just fine.

does anyone know about installing the proper drivers for these devices?

---

### Post by kodiyan on 2009-06-11
I called 750a SLI support for ubuntu drivers. They are not supporting Linux now for this MB. How did u get drivers for ethernet card and audio in Ubuntu? Nothing in the xfxforce.com.
I have Linux ver9.0

---

### Post by Throwback on 2009-06-24
I have a gigabyte version of this board. I use a creative labs sound card instead of the on board audio so I don't know about the audio chip (although its ac97 so i cant imagine it not working) but everything else works. Networking etc is fine- the only problem I have had is that the thermal sensors are not yet supported in the repository version of lm-sensors: you need to get hold of a patch from the lm-sensors developers, I have not got round to doing this yet.

Other gotcha was installing the nvidia video card drivers- I have 2 cards in there for sli, and installing the drivers initially hosed it so I couldnt get into X and was "trapped" (this used to scare me, now i prefer the prompt just because it doesnt go wrong!) on the prompt. If you get that problem, make sure you specify the exact busid (do a lspci at the prompt) in /etc/X11/xorg.conf under the nvidia card identifier section.

---

### Post by Aquinus on 2009-06-24
Does anyone know if 9.04 supports hardware raid on the 750a without dmraid?

---

### Post by gforcing on 2009-06-24
Tried to mark this several times, but the option doesn't show up in thread tools - this thread is SOLVED. 

I discovered the problem was with my motherboard's BIOS settings. The onboard graphics were screwing with the video card. All I had to do was disable onboard graphics, problem solved.

Thanks much for all the replies. If someone could help me figure out how to mark this thread as closed I'd appreciate it (again, the option isn't in the Thread Tools menu).

---

