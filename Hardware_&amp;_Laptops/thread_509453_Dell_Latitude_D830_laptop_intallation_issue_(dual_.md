---
title: "Dell Latitude D830 laptop intallation issue (dual boot w/ Vista)"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by abadfish on 2007-07-25
I got my brand new Dell Latitude D830 laptop pre-installed with Vista. So before I started loading all my junk on it, I attempted to make a dual-boot system with Ubuntu.

here's what I've done so far:
1. used SystemRescueCD (with GParted) to shrink the windows partition and create partitions for linux. So now I have a 30 gb partition for Vista, 30 gb partition for Ubuntu, 4 gb partition for swap, and the rest as shared partition for both Vista and linux.

2. installed Ubuntu with the alternative cd. (to my knowledge this went fine. I didn't see any error messages or anything like that).

3. Used BcdEdit in Vista to make a boot sector for linux in the Vista boot record (procedure listed [here]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx")).

When the system boots, I select Linux and then nothing happens. I just get a blank screen with the cursor blinking in the top left corner. My windows boot is fine.

Any suggestions? I'm willing to try installing Ubuntu again but I was hoping to see if this can be salvaged.

Thanks.

---

