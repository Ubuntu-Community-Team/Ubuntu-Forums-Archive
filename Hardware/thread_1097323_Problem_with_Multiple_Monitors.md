---
title: "Problem with Multiple Monitors"
date: 2009-03-15
forum: Hardware
---

### Post by RonnieV on 2009-03-15
I recently purchased 15 identical Dell GX110 PCs in a government auction and installed Windows 98SE and Ubuntu 8.11 on the single hard drive in each. My intent was to build PCs for young children. I installed Windows and linux apps on the first machine, imaged the entire hard drive, and quickly cloned my setup on the next five PCs.  What I did not realize is that Ubuntu was expecting an identical monitor for each PC.  I tried several monitors and found only the monitor that I used for the initial installation performed properly when I booted into Ubuntu.

After doing a little research, it's my impression that changing monitors after an installtion can be a problem for Ubuntu. Several articles pointed to the xorg.conf file. I looked at that file on one of machines and it contained the following:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

The video devices on these PCs are the same but each will likely be matched with a different monitor.  Can I edit this file in such a way that Ubuntu can live with a different monitor for each box or will it be necessary to install Ubuntu on each PC with the monitor that it will be permanently paired with?

It may be helpful to know that I usually set the resolution at 800 X 600.  The monitors that I purchase are older CRT monitors that were used 5-10 years ago.  Finally, I'm reasonably geeky but have little experience with linux so please assume I may need a bit of detail if you're kind enough to respond to my inquiry.

Thanks very much.

---

