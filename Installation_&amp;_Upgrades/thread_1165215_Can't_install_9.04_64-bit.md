---
title: "Can't install 9.04 64-bit"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by disk11 on 2009-05-20
System:
Intel Core2Duo E6320
Gigabyte P35-DS3R mobo (P35 northbridge, ICH8R southbridge)
2GB RAM
Nvidia 7800GS
Audigy 2
NEC 3550A DVD-RW
Maxtor 200GB (holds XP, XP apps, and Win 7 partitions)
Western Digital 640GB (Ubuntu, swap, and an Storage partiton using NTFS)

I tried the Desktop edition, but all I get is a blank screen.  I can Ctrl+Alt to command lines but I dunno where to go from there.

So I snagged the Alt edition, and it gets stalled at 74% asking for the CD.  It seems to get unmounted as I cannot get the tray to come out without the paper clip trick.  I tried putting the Desktop CD in, but it doesn't try to read it.

I tried acpi=off option and it couldn't find the CD drivers.  Also tried noapic with no change in the result.

---

### Post by coffeecat on 2009-05-20
Have you tried the 32-bit desktop CD? I know you want to install the 64-bit version, and your setup should be fine with that, but it might be interesting to see whether it's Jaunty itself or the 64-bit version stalling on some aspect of your hardware.

The only other thing I can suggest is to try a net install. You get the 64-bit mini.iso from here:

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/)

.. burn in to CD and boot up from it. You need an ethernet connection to broadband for this. The mini CD first of all downloads a few megabytes of stuff into memory and then presents you with an installer very much like the alternate CD. Once you've made all your selections (and you can mix and match things like ubuntu-desktop, kubuntu-desktop, server, and a whole load of other things I can't remember now), it downloads and installs at the same time by downloading every single deb package needed to make a complete install. You get one hell of a bulging /var/cache/apt/archives/ folder at the end. :wink: This took me about an hour with a good BB connection for just vanilla Ubuntu.

The advantage is that you get yourself Ubuntu installed. The disadvantage is that it might not boot up if there's something really problematic between Jaunty and your hardware. If, by chance, you decide to go for the 32-bit version, just navigate yourself up about four levels of directory in that link and then down again in the i386 branch.

---

### Post by disk11 on 2009-05-20
I got it to work with the mini, and posting from it now.

One thing I keep forgetting to do is unplug my 2nd monitor.  Default Gnome setup doesn't seem to like it at all, and probably why the Desktop setup didn't work.  Don't think it would have an effect on the Alt though.

---

