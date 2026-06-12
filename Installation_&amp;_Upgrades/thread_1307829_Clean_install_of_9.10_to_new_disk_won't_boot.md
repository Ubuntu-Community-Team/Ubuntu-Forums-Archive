---
title: "Clean install of 9.10 to new disk won't boot"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by myxiplx on 2009-10-31
Hey folks, can anybody point me in the right direction to troubleshoot this.  I'm pretty good with computers, but my Linux knowledge is still quite basic.

I've been running Ubuntu 9.04 on a 30GB disk for ages, but that disk sounds like it has bad sectors, so I fitted a new 1TB disk for 9.10.

I left the 30GB drive connected, so I could copy my files later, and just set the boot order in the BIOS to boot from the 1TB drive.  9.10 was then installed from the CD, selecting the 1TB disk, and telling Ubuntu to use the whole disk.

The install appeared to work fine, but when I reboot, nothing happens, the system just hangs.

However, if I boot from the 9.10 CD, and then choose 'boot from first hard drive', I get my original 9.04 grub menu, but the first option boots 9.10 on the new hard drive.

It looks to me like Ubuntu has installed grub on the wrong disk.  I don't want this since that disk is failing, but I don't know enough to fix it.

Can anybody help?

thanks :)

---

### Post by D-Dan on 2009-10-31
I had exactly the same problem, and if yours is the same, you've hit the nail on the head with bad sectors.

I tried to install on 29th which failed, and again last night. When I booted the live CD my Data drive reported bad sectors. I didn't expect this to be a problem. I have three drives, one with Windows Vista, one for data, and the third for Ubuntu.

After installation, I was either hanging completely, or getting errors suggesting the root file system failed to mount.

As a result of the liveCD warnings, I've bought a new HD today (and increased storage by 250 Gb :) and copied everything across from the reported bad drive. After setting up Windows so that it thought the new drive was the old drive, I rebooted to Linux and voila - it worked.

Seems to me 9.10 is a hell of a lot more sensitive to failing drives than previous versions.

Try a new drive (or if it's a different one that has bad sectors, disconnecting it).

Steve

---

### Post by myxiplx on 2009-10-31
No, you mis-understood.  My old drive sounds like it's starting to go.  9.10 is installed onto a brand new drive.

The problem is that the installation looks to me like it's installed grub onto the old bad drive.

The old drive probably boots fine, but that doesn't help me.  I need to get this booting from the new 1TB drive.

---

### Post by D-Dan on 2009-10-31
No - I understood. My point was, the failing drive in my system was nothing to do with the Ubuntu install. It was an NTFS formatted, non-bootable drive. Nothing more than storage, and on a clean install, not even mounted at boot. However, replacing it fixed the problems.

This is why I suggest disconnecting for the testing, and see if the install and boot works then.

Steve

---

### Post by myxiplx on 2009-10-31
Ok, I'll give it a try, thanks for the tip.

I've found another problem now though - I can't boot back to Ubuntu 9.04 any more.

I specifically told Ubuntu to install on the 1TB disk so that it wouldn't affect my existing installation, but whatever it's changed in Grub has broken things.  If I try to select Ubuntu 9.04 now I get:

"error:  you need to load the kernel first"

---

### Post by D-Dan on 2009-10-31
Try disconnecting the new drive, boot from the live CD and repair grub on the old drive.

Edit: Alternatively, if you installed the new Grub on the new drive, leaving the old drive untouched, change the boot order of the drives to boot from the old drive first. Personally, I keep the Vista MBR on the Vista drive, and install Grub on the Ubuntu drive. That way, if Grub fails, I can still boot Vista by switching the boot order.

Steve

---

### Post by myxiplx on 2009-11-05
Ok, I've no idea what the original problem was, but disconnecting the original drives and re-installing has got the new drive working ok.

The old install is still messed up though and I suspect this might be a bug, I'm going to look into it a little more and then I'll submit a bug report.

thanks anyway

---

### Post by wkulecz on 2009-11-05
Sounds like the problem I had.  Bios had drive boot order set as IDE drive first, SATA drive second. But grub2 assumed SATA was first disk and thus my freshly installed (to the IDE drive) system wouldn't boot. 

I changed the bios boot order, booted the system, made changes to the grub2 config to make it boot the "second" drive and put my BIOS boot order back the way it was and all is fine now.  The installer correctly setup boot options for my 6.06 and 8.04 systems on the SATA drive.

--wally.

---

