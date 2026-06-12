---
title: "GRUB Error 18"
date: 2011-06-18
forum: Hardware
---

### Post by guppygould on 2011-06-18
Hey all, 

I've just got my laptop back from a shop after having a new charger port resoldered to the motherboard, when I turn my lappy on it hangs for ages whilst loading the grub menu (which I use to select which kernel I boot from.) Eventually it kicks out a GRUB error 18. I've googled the nature of this problem and I was wondering if this could have been caused by something the shop could have done? ie not reconnecting the hard drive properly. 

If it can't, could you walk me through how to fix this? The data on the laptop isn't particularly important and I was thinking of doing a fresh install sometime soon anyway.

I'm running the latest version of Ubuntu on ext3 if that makes a difference. 

Cheers,

-Leo

---

### Post by coffeecat on 2011-06-18
Hi. Legacy grub error message 18 means:

> 18 : Selected cylinder exceeds maximum supported by BIOS

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).Since you were able to get the grub menu and boot into Ubuntu before the repair, it must be that the BIOS can support higher addresses. These grub errors tend to be a bit cryptic and can be slightly off the mark. However, when repairing the motherboard, the technician may have reset the BIOS back to defaults. So, first thing is to go into the BIOS and see if there is any relevant setting you can change.

Second - do you have a live Ubuntu CD? If so, boot up with the CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there and post the contents of the RESULTS.txt file. I think the BIOS issue is more likely to be relevant, but if changing BIOS settings doesn't help, then the boot script may reveal something important. 

Third thing - When you say latest version of Ubuntu with ext3, do you mean version 11.04/Natty. And if so, was this originally Jaunty/9.04 and upgraded? Your personal details say Jaunty.

---

### Post by guppygould on 2011-06-18
Thanks for the quick reply.

I'm downloading a new live CD as I type this. I've had a quick look through my bios and can't see anything relevant, although to be honest I'm not exactly sure what I'm looking for. The only things I can see are the SATA modes, HDD passwords and a boot priority menu.

Yeah, I'm using a Natty install that I've upgraded since Jaunty or earlier, I can't remember which release it was to be honest. I haven't been here in a while and so, haven't updated my user info!

---

