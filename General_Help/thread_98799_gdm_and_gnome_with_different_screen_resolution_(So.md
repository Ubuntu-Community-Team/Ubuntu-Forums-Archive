---
title: "gdm and gnome with different screen resolution (Solved)"
date: 2005-12-04
forum: General Help
---

### Post by daucourt on 2005-12-04
My problem is that gdm and gnome do not have the same screen resolution.
gdm is in 1280x1024, and logging into gnome, it goes down to 1024x768
(but if I logg into xfce from gdm, i stay at 1280x1024 !)

From the default installation, and after a 
[FONT="Courier New"]$ sudo dpkg-reconfigure xserver-xorg[/FONT]
(that was so long and so useless)

I updated my xorg.conf by adding one modeline generated using gtf

[FONT="Courier New"]$ gtf 1280 1024 60 -x
  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync[/FONT]

I pasted the modeline in my xorg.conf and added the mode 

[FONT="Courier New"]Modes           "1280x1024@60" "1024x768@60" "1024x768" [/FONT]

Video were not playing in totem with error message (from command line)
[FONT="Courier New"]BadAlloc (insufficient resources for operation)[/FONT]

I found the trick to go down to default depth to 16
[http://www.dtek.chalmers.se/groups/dvd/faq.shtml]("http://www.dtek.chalmers.se/groups/dvd/faq.shtml")

So updated my xorg.conf with 
[FONT="Courier New"]DefaultDepth    16[/FONT]

But now gdm display has a 1280x1024 resolution, but just after logging into gnome the resolution of gnome go down to 1024x768

Any help greatly appreciated.

---

### Post by aysiu on 2005-12-04
Are you able to get the proper screen resolution in Gnome at all and it won't save once you exit, or you can't even get it as an option in System > Preferences > Screen Resolution?

I highly doubt it has anything to do with you /etc/X11/xorg.conf if you're able to get the right resolution in XFCE...

---

### Post by daucourt on 2005-12-04
Thanks. I fill stupid after having done the hardest job, and not able to finish with this quick hint... Maybe I was disturbed with stupid hints from #ubuntu...

---

