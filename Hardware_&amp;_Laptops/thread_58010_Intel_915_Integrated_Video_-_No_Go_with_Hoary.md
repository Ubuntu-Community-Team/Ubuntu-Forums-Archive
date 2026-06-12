---
title: "Intel 915 Integrated Video - No Go with Hoary?"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by Player0 on 2005-08-18
Hi folks, I've spent several days looking for answers to this problem with no luck, so please forgive me if this has been answered elsewhere already.

I have an Intel D915GLVG motherboard with i915 video.  It took some doing to get the ALSA sound driver to work, but that does.  But I still have no luck in the video department.

I am fairly new to linux so please bare with me.  I actually run Kubuntu but I don't suspect there is a huge difference in that.  I use the 2.6.10-5-686 kernel.  I have gotten all updates for Hoary through apt-get.

Hoary autodetects the i915 video at install (or dpkg-reconfigure xserver-xorg), and tries to set up vesa for it.  The vesa drivers do not work on my system.  I do get video but it's all garbled.  Using the i810 driver in xorg.conf causes the machine to reboot on 'startx'.  Using vga does work fine, but at an unusable resolution.  Im sure the monitor settings are fine, with the right refresh rates defined.  I tried setting the VideoRam size in xorg.conf to 8192, the size of system ram allocated to the video card in BIOS.  No settings here seem to work.

Right now, I have a PCI TNT2 video card in the system and it works fine.  However, I would much rather get the onboard video working.

Newer versions of Xorg have better i915 support I gather, and this is built in to Breezy.  However, this is a work machine and I'm concerned about the ugprade from Hoary to the unstable Breezy.  I tried downloading the newer i915 drivers from Intel (using the RPM and Alien).  However, setting xorg.conf to i915 after doing this gives me a "failed to load module i915" error so something isn't right there, although I have /usr/X11R6/lib/modules/drivers/i915_dri.so, but I guess this isn't enough.

I looked in to installing Breezy's version of Xorg 6.8.2-50 from source on my Hoary install, but the dependancy list is nightmarishly huge, and I dont think its ideal to compile all that from source manually (unless I am missing an easier way to do it).

I tried 855resolution without success.  I see theres a 915resolution out but I havent tried it, since I beleive it requires an i810 setting in xorg.conf, and as I said, that just puts me in a reboot loop.

Any other things I should try?  Would the upgrade from Hoary to Breezy be that worrisome?  Thanks!

---

### Post by Player0 on 2005-08-18
Just a quick update.  I tried installing the common and i915 drivers from:

[http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)

they installed okay, and i confirmed that the new i915_dri.so and the new i810_drv.o from this package copied over to the correct locations.

It looks like I needed to leave i810 set in xorg.conf, which I did.

Again, the machine will just restart itself if I try running X.

Also, doing a modprobe on i915 (since it's not entereed in to /etc/modules) also causes an automatic restart.  I am using the 0718 version and dont have high hopes that the 0714 version would work better for me.

Almost ready to give it up!

---

### Post by tseliot on 2005-08-18
Try this HOWTO:

[http://www.ubuntuforums.org/showthread.php?t=27029](http://www.ubuntuforums.org/showthread.php?t=27029)

---

### Post by Player0 on 2005-08-18
Already have read through that.

None of it works.  855resolution is kind of moot cause setting the driver to i810 causes the machine to restart.

But i have used 855resolution as I had mentioned, but it doesnt have an effect for me.

---

### Post by tseliot on 2005-08-18
Sorry pal, I haven't got a graphic card like yours, I can't help you.  :| 

I hope someone else has the right answer.

---

### Post by Player0 on 2005-08-19
[QUOTE=tseliot]Sorry pal, I haven't got a graphic card like yours, I can't help you.  :| 

I hope someone else has the right answer.[/QUOTE]
 Me too :)  Bump for more help?

---

### Post by Player0 on 2005-08-26
Update:

It's no go with Breezy either.  Im now running 2.6.12 kernel with Breezy installed, and the i810 driver reboots instantly.  I again, updated to the latest DRIPKG src for the 915, reboot.

Im beginning to think the i810 driver is very silly lol.  Maybe in a future BIOS update for this board, something will get more fixed.

Vesa mode is still a no go either.  I have integrated memory and this somehow breaks things.

Im not sure if I need to do anything special with the i810 driver since it's on a PCI-e interface and not an AGP.

As usual, any suggestions would be appreciated.  PS - Breezy actually runs very well.  Im on Gnome now too which I seem to prefer in some ways.  The panels are nicer I think, but it seems to basic in terms of what you can configure.  KDE was freezing up on me in Hoary tho so Gnome it is.  Gnome was also a fair bit slower, but I got a huge improvement by moving to an SMP kernel (since this is a P4).  

The ALSA-ESD driver works good too, so everything runs very well with the exception of a few bugs (Kate will NOT run right on this machine, so Im using Bluefish which has sftp support and it's nearly as good as FISH.)  Just the darn video driver...  Im lucky to get text mode through the onboard, i really am.

---

