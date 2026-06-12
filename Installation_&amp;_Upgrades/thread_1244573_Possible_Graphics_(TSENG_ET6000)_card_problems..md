---
title: "Possible Graphics (TSENG ET6000) card problems."
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by iains on 2009-08-19
I have an old Pentium 256Mb

vendor_id	: GenuineIntel
cpu family	: 6
model		: 7
model name	: Pentium III (Katmai)
stepping	: 3
cpu MHz		: 551.242
cache size	: 512 KB

which has been running W2K with a 15" LCD monitor (1024x768 V60 H49) for 8-9 years as as an underused server.
I wanted to try out Xubuntu as a test bed for apache2.

It loaded 9.04 quite happily but has problems with X-windows - refusing to run better than 800x600 (and then not properly).

"(EE) TSENG(0) : No valid Framebuffer address in PCI config space
(EE) Screen found but none have a usable configuration"

I suspect the graphics card

VGA compatible controller: Tseng Labs Inc ET6000 (rev 30)
	Flags: slow devsel, IRQ 11
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	I/O ports at b400 [size=256]
	Expansion ROM at e2000000 [disabled] [size=16M]

Details in attached file(xubuntu_problems.txt) - including /Xorg.0.log.

Can anyone confirm this diagnosis ?

---

### Post by dlmarti on 2009-08-19
I know a lot of guys in my area that worked for Tseng labs, thats practically antique video card  :)

You CAN get the card working, but its going to take a bunch of massaging the config files.  If you really want to do this your going to have to limit the color depth, to get the resolution up.  Personally I would skip it.

Either use the thing non-graphically, after all you said you wanted an apache server, not a desktop.

Or purchase a new card with more memory, you can pick one up on geeks.com for only a few bucks.

---

### Post by dlmarti on 2009-08-19
for example: [http://www.geeks.com/details.asp?invtid=CL-MX400-64M-PCI&cat=VCD](http://www.geeks.com/details.asp?invtid=CL-MX400-64M-PCI&cat=VCD)

---

### Post by Aguamiga on 2009-08-26
This might work for you: Had the same sort of problem, and solved it by having Xubuntu 7 generate a correct Xorg.conf file! (You don't need to install version 7, just boot from the cd)

For more info, read this post: [[COLOR=#444444]http://ubuntuforums.org/showthread.p...03#post7850803[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7850803#post7850803")

---

