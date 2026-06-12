---
title: "computer always selects tv instead of monitor at bootup"
date: 2016-11-02
forum: Hardware
---

### Post by marsdenf on 2016-11-02
Using a fairly new desktop computer with three ssd's, one with xubuntu 14.04, one with xubuntu 16.04 and the third with ubuntu mate 16.04.  This may be a pure hardware problem, nothing to do with linux.  I have an LG 23MP55 monitor, about a year and half old and a Toshiba 26C100U1 tv, which is several years old.  Graphics card is   Nvidia GM107 [GeForce GTX 750 Ti], though the card itself may be irrelevant to the problem.  Motherboard is Gigabyte Z170X Gaming-3, which is probably the key.  The monitor is connected by hdmi port in the back of the monitor to hdmi port (graphics card) on the back of the desktop.  The tv is connected to the desktop by one of two hdmi ports on the back of the tv to a dvi port on back of the desktop (graphics card) with a dvi to hdmi adapter at the desktop.
       
     If both are connected, and the computer is restarted, or shutdown and then booted up,  then the bios and grub menu always appear on the tv, and the monitor is blank (black). After choosing the drive with Ubuntu Mate 16.04 in grub, then both displays have the login screen and then the full desktop with icons, menus panels etc show on both. (But something is wrong with the graphics, the font is far too small and poor quality.)  After choosing Xubuntu 14.04 drive, then the tv has login screen and monitor has just the wallpaper.  After logging in, both displays have full desktop.  After choosing Xubuntu 16.04 drive, the monitor has the login screen and the tv has just the wallpaper, and after logging in, both display the full desktop.   Whether the tv is powered on or off makes no difference, the bios and grub don't appear on the monitor.  I want either the bios and grub to show up only on the monitor, or on both the monitor and tv.  That way, I could keep the tv connected to the desktop and powered off, and only watch the tv when I want to see a movie with Kodi. ( I don't have a tv cable connection with my provider, just internet).  But the only way I can guarantee to see the bios and grub on the monitor is to unplug the hdmi connection on the back of the tv, and then only plug it in when I want to watch tv.  It is a pain to have keep plugging and unplugging the tv.  I have tried using the other hdmi port on the back of the tv, it makes no difference.  I have also tried plugging the monitor using the dvi to hdmi, and the tv using hdmi to hdmi, no difference.
     
                      It seems that in the first stages of boot up, the computer recognizes the tv as the 'primary' device and chooses it to display bios and grub.  I have tried fiddling with display settings and nvidia xserver settings, with no luck.  In nividia xserver settings/xserver display configuration/selection, the two devices are listed but after the tv it says " (DFP-0) " and after the monitor: " (DFP-2) ".  Maybe that indicates the priority settings.  Is there some way to change this, perhaps in bios settings?

---

### Post by marsdenf on 2016-11-02
UPDATE:  I tried again connecting the monitor to dvi port on desktop and tv to hdmi on desktop and this time it worked. I don't know why. Now the bios and grub always show up on monitor.  I read somewhere that the computer checks the oldest technology port first, ie vga, then dvi, then hdmi last.  I would have preferred to use hdmi for the monitor, because I think it is higher quality signal then dvi (Am I wrong?).  Anyway the problem is now solved.

---

### Post by QIII on 2016-11-02
It really depends on how the manufacturer has the graphics card enumerate the ports - but that may play in the enumeration.

---

### Post by kpatz on 2016-11-02
From a video perspective, DVI-D and HDMI are more-or-less identical.  (There's also DVI-A which is analog like VGA and DVI-I which has both analog and digital for compatibility purposes... most of us use DVI-D nowadays).  For higher resolutions (2K, 4K) you'll need dual-link DVI while HDMI will still work.  HDMI passes audio as well as video, so if you want your TV to play sound from the computer, connect that with HDMI and your monitor with DVI.

As for your bootup issue and primary vs. secondary monitor, the card probably polls the ports in a certain sequence and the first one that responds with a monitor connected becomes the primary display.

---

