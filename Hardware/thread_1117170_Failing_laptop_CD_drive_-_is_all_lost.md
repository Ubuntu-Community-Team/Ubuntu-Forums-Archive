---
title: "Failing laptop CD drive - is all lost?"
date: 2009-04-05
forum: Hardware
---

### Post by scradock on 2009-04-05
I have a happy little laptop, triple-booting Windows XP (its original OS) and a couple of Ubuntu flavors, even another linux from time to time. But its CD drive started to get unreliable, and now doesn't read, let alone write. I suddenly feel very much as if I'm walking tightrope without a net - can't boot from a live CD, or a system rescue CD, try another distro, or even blow away my Jaunty install and re-install from CD.

Obviously, I can try replacing the drive; but the machine is four years old, and I've never opened the case in earnest, so I don't know how much hassle it would be to actually do. 

Alternatively, I could spend a few hundred dollars and get a replacement laptop, or even a netbook - I don't do much with image files that would need huge memory (1.25GB ram at the moment).

Any other ideas? AFAIK the BIOS is too old to allow booting from USB stick.

---

### Post by Cybie257 on 2009-04-05
what is the brand and model of the laptop?

Check out ebay for replacement drives. I killed my DVD/RW drive on my laptop and got one for $35 from eBay. Most laptops, the CD/DVD drive is very simple to replace, especially if its only 4 years old. just remove a screw, pull the drive out, replace it, and wholla. 

You say that it won't boot from USB? Curious to know the make and model of the laptop. most BIOS in the past 4-6 years have had the option. 

-Cybie

EDIT: Is the HP listed in your footer the actual system in question?

---

### Post by PatrickVogeli on 2009-04-05
I work in a computer repair shop and changing a laptops cd drive is usually quite easy. The most common thing is to take out a screw or two an then slide out the drive. After that mount the new drive in and that's it.

However, it could be a little trickier, but it's not the rule.

---

### Post by axelroo on 2009-04-05
All hope is not lost. You can still install Ubuntu and use live disks using UNetBootin

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

It works for both Windows and Linux and can automatically download and install the most current distributions and install them to a usb stick. Reboot and change your BIOS settings to run from usb.  You're good to go. If you already have some .iso images better, it can even use those.  Give it a shot.

---

### Post by Cybie257 on 2009-04-05
> **axelroo said:**
> Reboot and change your BIOS settings to run from usb.  You're good to go. 

He stated the his system can't be booted from USB. So, this probably won't work if you are referring him to boot from USB. 

I've looked around and it seems that it isn't able to do so, but maybe a BIOS upgrade will fix that..

OP--> Have you updated to the latest BIOS flahs update? 

[http://h10025.www1.hp.com/ewfrf/wc/previousVersions?softwareitem=ob-43144-1&lc=en&cc=uk&lang=en&os=228&dlc=en&product=453185](http://h10025.www1.hp.com/ewfrf/wc/previousVersions?softwareitem=ob-43144-1&lc=en&cc=uk&lang=en&os=228&dlc=en&product=453185)

-Cybie

---

### Post by scradock on 2009-04-05
Yup, I'm on the F.1C (current) BIOS version.

And yes, it is the zv6000 I'm talking about. I did look into setting up a bootable USB stick a few months ago, but gave up when I found that the BIOS couldn't be set to boot from USB.

I'm encouraged by the two posts suggesting that replacing the drive should be simple - I'll see what I can do myself.

Meanwhile, I'll look into UNetBootin.......

Thanks a lot - very helpful responses!

---

### Post by scradock on 2009-04-13
But to continue - the plot thickens!

After finding that yes, the removal of the CD drive involves removing one small screw, and that replacement drives (of the same model) cost around $200, unless I take a chance on one ripped from a dead laptop....

I also found that the drive reads audio CDs just fine, in Intrepid, jaunty and even Windows XP. Put in an audio CD, it's detected, and Rhythmbox starts up and plays the tracks.

What I can't do is mount a CD - so it begins to seem as if it's another file-system problem. Did Ubuntu change the way CD drives mount and forget to tell us?

Does anyone know anything that I might have missed - like a fundamental change in mounting optical media? My CD drive is connected as a slave to the SATA hard drive (pci-0000:00:14.1-scsi-1:0:0:0, where the hard drive is -scsi-0:0:0:0). The standard "/dev/scd0" is linked to "/dev/sr0", but when I try to mount either of those to /media/cdrom0 or /media/cdrom I get no joy - an error message saying that device sr0 is read-only. The permissions on the drive say that root and members of the group cdrom have read and write access; I've tried adding myself to the new group cdrom, to no avail.

Any ideas?

---

