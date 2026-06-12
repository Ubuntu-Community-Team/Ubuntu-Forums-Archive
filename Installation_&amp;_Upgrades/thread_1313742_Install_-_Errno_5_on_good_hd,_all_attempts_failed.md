---
title: "Install - Errno 5 on good hd, all attempts failed"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by jumping_snake on 2009-11-04
I'm trying to start from scratch so that I can have the ext4 installed...and I've already deleted the partition with 9.04 on it. After the 9.04 partition is deleted, the only remaining partition is the WinXP partition.

Ok, so after setting up a USB flash drive with the image, I am able to bring up the live CD very fast and effectively. Awesome. Yet, no matter how I try, I can only get the installation to ~30% (sometimes it's around 27%, sometimes 30% depending on the day). I continue to get the "Errno 5 - IO Error". I read the little message and have used the "Drive Utility" on the live CD to run some tests on the HD to ensure that it's in working condition even though it was working fine with 9.04 a couple of days ago..

So, I ran the extensive, longest test there was and everything reported back just about perfectly. No bad sectors, 7 CRC errors for 788 Power Ons for my 36GB WD Raptor. Before the tests, the HD's temp was at 70F, so temp shouldn't be a factor either.

I've also read that trying "ubiquity --no-migration-assistant" from the terminal inside of the live cd should work, but that doesn't either.

Any ideas what would cause the error and/or how to get this install to work?! I could install 9.04 again, but I want to move forward to 9.10 if I can!

---

### Post by jumping_snake on 2009-11-09
Alright, no new ideas....so I guess I'll just do what I didn't want to do: use one of my under 10k rpm drives to see if that works. Keep you all posted!

Update: And I don't have that much space left on my file server for me to transfer what I have over to it to use another of the HDs in the same computer...so after I get my RAID setup, I'll do this. Hopefully within a week or two.

---

### Post by jumping_snake on 2009-11-10
As I'm writing this, I'm installed on the same HD with 9.04....gah.

So, I'm going to start over at the beginning: Re-downloading the image and re-creating the USB stick to have the boot ready. I'll post again once I'm done.

---

### Post by a_z1_9scores on 2009-11-20
I'm having this same error, but I read that if you remove one of the memory chips you can get it installed. I'm going to try that and see what happens. It's unverified but it was on the launchpad and several people have reported success.

---

### Post by a_z1_9scores on 2009-11-21
It was a no-go. Turns out netbooks only have 1 memory chip, so you're on your own.

---

### Post by jumping_snake on 2009-12-08
It's been awhile since I've had some time to try getting this going again, so I'm going to try using a new USB key and downloaded image to see if I can get this to work.

I should mention that I'm not trying to do this on a netbook, but on a desktop system.

---

### Post by jumping_snake on 2009-12-08
I'm in! After swapping for a new USB stick and a new image, I'm currently running 9.10!

---

### Post by atomicben on 2009-12-22
I just had the same problem.  Wanted to kill somone for the last 5 hours.  I re-downloaded the ISO and BAM, away it goed.  No problems.  Completely unexpected and utterly ridiculous.

---

### Post by aamonster on 2010-02-21
> **atomicben said:**
> I just had the same problem.  Wanted to kill somone for the last 5 hours.  I re-downloaded the ISO and BAM, away it goed.  No problems.  Completely unexpected and utterly ridiculous.

The same problem (downloaded Ubuntu with MultiBootISOs-v0.6.exe, started from usb stick - errno 5, zsync'ed iso from another mirror - errno 5, removed one DIMM - errno 5, burned cd - errno 5, another PC - errno 5), the same solution (downloaded from third mirror - all ok)

Looks like some mirrors are broken and you need always check md5.

---

