---
title: "DVI-0 and DVI-1 have been swapped"
date: 2010-08-27
forum: Hardware
---

### Post by subi211 on 2010-08-27
I have a PC-based board in a homebrew arcade cab in my sitting room, and I'm currently moving from Gentoo to Ubuntu.  The board has three graphical outputs, VGA, DVI-0 and DVI-1.

The cab has two screens in it, and I usually run my game in a single window spanning both monitors (I would use two seperate windows, but Ubuntu does not seem to like more than one window using OpenGL at any one time even on the same monitor - one of the windows always flickers - curiously this does not happen on Gentoo).

The install is quite minimal, a command line install with vanilla X installed on it, configured through xorg.conf.

My problem is that performance is markedly slower on Ubuntu than on Gentoo, even through both are using the same Radeon driver and Mesa DRI R300.

I *think* this is caused by the fact that when I installed Ubuntu, the DVI-0 and DVI-1 sockets swapped.  On Gentoo I can use VGA and DVI-0, but on Ubuntu I have to use VGA and DVI-1.  These are the same physical sockets, but are identified differently by the OS.  Why, I don't know, but what I'm thinking is that this means Ubuntu treats them as two difference devices, and Gentoo as one (as anyone who's tried to use OpenGL in a Windows multi-monitor system will know is a problem :) )

The other DVI socket does not output anything above 640x480 despite claiming to be able to do so (this is not a monitor limitation, I have tried all monitors in all sockets).

So, I'm looking for a way to make Ubuntu swap the two DVI sockets back around again.  Or any other speedup solution anyone has to offer, I'm not proud.  :)

Thanks in advance.

---

### Post by subi211 on 2010-08-27
Curious.  I just checked with xrandr, and according to that DVI-0 is connected, at a resolution of 1024x768, which it is capable of.  Certainly the mouse pointer behaves as if it is connected (leaving the VGA display when I move it down).  It's just not sending an image down the cable!  :)

---

### Post by subi211 on 2010-08-27
Found the problem.  A lot of googling turned up some problems with the Radeon driver on laptop chipsets like the one on my board (X1200).  Sometimes disabling KMS fixes them.  I remembered that I have KMS disabled in Gentoo (as the initramfs stuff doesn't like it), so I tried turning it off in Ubuntu.  It worked!  The DVI outputs are back in the configuration they were in Gentoo, and it's going at a better speed.

You can turn KMS off by editing "/etc/modprobe.d/radeon-kms.conf" and adding the line "options radeon modeset=0" and rebooting.

I also learnt that the proprietary Radeon driver was replaced after Ubuntu 8.04.  It's being continued as open source however, so I may try that as well.

---

