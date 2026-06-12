---
title: "[SOLVED] Touchpad Preferences Missing in xorg.conf 8.10"
date: 2008-11-02
forum: Hardware
---

### Post by Dahaka14 on 2008-11-02
I'm sorry if this was already posted.  I did search the forums for a good 10 minutes for a resolution to my problem, but I didn't find anything in particular, so please don't attack me for not trying.

I just became aware of the missing device management in xorg.conf for the Synaptic touchpad for laptops.  I read somewhere that if you want to deal with it, it has something to do with HAL (idk what that is).  After the preceding text in my xorg.conf file, it is as follows:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

There is nothing there having to do with my touchpad.  How can I adjust the settings of my touchpad now?  All I want to do is make the vertical scrolling a little bit more sensitive.  I previously had this set to my preference in 8.04, but now it's gone.  How can I make the vertical scrolling a little bit more continuous/less jumpy in 8.10?

If there is something that has already come up on the forums for this issue, please link it for me; thanks!

---

### Post by wgrant on 2008-11-02
See [the Synaptics documentation wiki page](https://help.ubuntu.com/community/SynapticsTouchpad).

---

### Post by monkeys on 2008-11-18
How did this issue actually get resolved? I've read the documentation page, and have tried to enter a new .fdi into policy for touchpad modifications and still have no result. s: My post is [here]("http://ubuntuforums.org/showthread.php?t=984618").

---

