---
title: "Installing Ubuntu on Compaq Presario 2505"
date: 2012-12-17
forum: Hardware
---

### Post by franrc on 2012-12-17
Hi all,

  I have installed XBMCbuntu 11 on my Compaq Presario 2505EA: Pentium4 2,4GHz and ATI RADEON video card but the system works ver very very slow and CPU usage is always at 99%.

  I thinks there's something misconfigured about the video card and X system, what can I do? Any help?

 Thanks in advance.

---

### Post by mastablasta on 2012-12-17
what radeon card?
 
you can check the system usage by using top command and see which process is runnig too much.

---

### Post by Bucky Ball on 2012-12-17
> **franrc said:**
> I thinks there's something misconfigured about the video card and X system, what can I do? Any help?

What makes you think that, exactly? Could you give a bit more detail? And yes, as suggested my MastaBlasta, open a terminal and type in 'top' then see what's gobbling up your resources ...

---

### Post by franrc on 2012-12-17
Well, the proceess that consumes 99% CPU is XBMC, when I kill it the CPU charge is reduced to 10-15%
The video card is ATI Radeon IGP 345

---

### Post by franrc on 2012-12-17
> **lillyruiz80 said:**
> I worked around this issue removing global menu's (and HUD) altogether.
[IMG]http://www.smallbusinessdevel.com/xiaowang1.jpg[/IMG]
[IMG]http://www.smallbusinessdevel.com/xiaowang13.jpg[/IMG]
[IMG]http://www.smallbusinessdevel.com/xiaowang14.jpg[/IMG]
[IMG]http://www.smallbusinessdevel.com/xiaowang15.jpg[/IMG]

Sorry, Could you explain a little more detailed?
Thanks in advance

---

### Post by Bucky Ball on 2012-12-17
> ****lillyruiz80]** 				
 				I worked around this issue removing global menu's (and HUD) altogether.[/QUOTE]

[QUOTE=franrc said:**
> Sorry, Could you explain a little more detailed?
Thanks in advance

??? lillyruiz80 has not posted on this thread ...

---

### Post by franrc on 2012-12-17
Wow lillyruiz80... I'm going crazy...
Well, the proceess that consumes 99% CPU is XBMC, when I kill it the CPU charge is reduced to 10-15%
The video card is ATI Radeon IGP 345
Can anybody help me?

---

### Post by mastablasta on 2012-12-17
it seems it is an xbmc issue then. if everything else works normally. 
it seems that this version is compiled separatelly and working on LXDE. i don't know how their kernel is. 

otherwise the GPU has opensource driver support and should support 3D according to this page: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

have a read and see if oyu can tweak it. Otherwise the chip is not so powerfull think.

---

### Post by franrc on 2012-12-18
Well, it is possible that fglrx driver doesn't support my ati igp 345 video card but is there a supported video card list for this driver? Where can I find it? Just to be 100% sure.
In the link you posted me I can read that there's an alternative opensource driver called "radeon". Can I install this driver using package manager?
Where can I find this driver for download? Is this the url [http://www.x.org/wiki/radeon?](http://www.x.org/wiki/radeon?)
Thanks a lot.

---

### Post by M3m3nt0 on 2012-12-18
I think you're already using *radeon* open source drivers ;)

I have a Presario nx9005 with an ATI IGP 320m and my problem is that simply using glxgears 3D performance are too bad (=too slow)...
disabling acpi bring things back to normal but i cannot use suspend [SIZE=1](and maybe I lose other useful feature...)[/SIZE]

:(

---

### Post by franrc on 2012-12-18
Disabling acpi... what's that?
How can I do it?
Thanks

---

### Post by franrc on 2012-12-19
> **M3m3nt0 said:**
> I think you're already using *radeon* open source drivers ;)

I have a Presario nx9005 with an ATI IGP 320m and my problem is that simply using glxgears 3D performance are too bad (=too slow)...
disabling acpi bring things back to normal but i cannot use suspend [SIZE=1](and maybe I lose other useful feature...)[/SIZE]

:(

Well, I'm not really sure about if I'm already using radeon open source driver, in fact 'aptitude' says that fglrx-updates is installed on my computer

How can I check which video driver is really installed?

How do I disable acpi?

Thanks in advance

---

