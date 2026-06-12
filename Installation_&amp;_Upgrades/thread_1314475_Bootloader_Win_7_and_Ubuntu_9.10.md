---
title: "Bootloader: Win 7 and Ubuntu 9.10"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by IamHydrogen on 2009-11-04
So it went like this...

  I already had installed Windows 7 RC, build 7100.  Things run well, but I want to use Ubuntu too, cause, well...its windows.  

So I put in another drive, named it K:  Windows is on C:  I put in the Ubuntu live cd, use wubi (i didn't use Vista compatibility, more on that in a minute) and installed on K: with a 30 GB partition.  Seems to go fine.  REboot, bootloader shows, select Ubuntu, goes through a few lines of code and doesn't boot.  Not sure what the prompt is at the moment cause I'm at work, but I'll update tonight. 

I boot back into windows, reformat drive K: in NTFS cause nothings working.  Reboot, bootloader still shows Win 7 and Ubuntu selections.  So I restart with the Ubuntu CD in and perform a boot cd install on Drive K:, split in half, so half Ubuntu partitions, other half remains NTFS (approx 157 GB for each)  Ubuntu install runs through fine.  Reboot, still two selections, Ubuntu selection still points to ubuntu install that isn't there and lands at the prompt again, even though there is a good clean install on drive K.  

I download EasyBCD, boot into windows.  Erase the ubuntu selection from the 1st wubi install and attempt to add and direct it to the new install on K.  Reboot, get two selections, Ubuntu selections does the same as before, booting into a prompt and going nowhere.  

So...where do I go from here?  Try to reinstall GRUB or is there a way I can use wubi or EasyBCD to get the result I'm looking for?  i.e.  I want to have a bootloader to choose between Ubuntu and Windows (which are on K: (ubuntu) and C: (win 7)both 64 bit versions)  I believe both are set as master disks, which I'll rearrange to master and slave however it would work best.  Please advise.

---

### Post by Mark Phelps on 2009-11-04
Wish I had more encouraging news for you ... but I don't.

You're mixing several different kinds of installs -- it's not a wonder nothing is working.

Wubi installs to a special file -- that Ubuntu treats LIKE a partition.  But it is not a partition. It is installed INSIDE an existing NTFS partition. It works inside MS Windows because the right software is installed to boot into Ubuntu.

Traditional dual-boot versions install to separate partitions, formatted for Linux, and require GRUB (or some other Linux boot loader) to work.

Since you have such a mixture at present, your best bet would be to remove all the Ubuntu installs, clean up the BCD entries, and start over.

However ... and here's where the bad news comes in ... I've been trying a similar situation with Windows 7 and an older Ubuntu, using easyBCD, and NOTHING works.  Choosing the menu selection only boots me into GRUB.  The only thing that worked was installing GRUB to the MBR and using GRUB to boot all the OSs -- but I recently had to repair the MBR and want to avoid messing with it again.

And, yes, I've posted on the NeoSmart forums, and tried all their suggestions (as have others), and still -- nothing works.

Hopefully, someone will come along that HAS made this work and can tell us how to fix it.

---

### Post by IamHydrogen on 2009-11-04
Ya, I figured I had a mess on my hands.  I'm gonna wipe the Ubuntu slate clean and see what it gets me.  I figured I would have to use GRUB for all of the OSs but I don't really have a problem with that.  However, I'm not that familiar with GRUB, but something tells me I will be.  I'll let you know how it goes.  If anyone has any other suggestions, be sure to chime in.  Thanks.

---

### Post by Mark Phelps on 2009-11-05
> **IamHydrogen said:**
> Ya, ...However, I'm not that familiar with GRUB, but something tells me I will be.  I'll let you know how it goes...

You do know that 9.10 uses GRUB2, right? That's a whole LOT more complicated than legacy GRUB.

I've seen lots of posts from folks struggling to get GRUB2 and Windows 7 to work together -- and not seen any solutions yet.

So, if anyone HAS made this combination work, it would be great to hear the details.

---

