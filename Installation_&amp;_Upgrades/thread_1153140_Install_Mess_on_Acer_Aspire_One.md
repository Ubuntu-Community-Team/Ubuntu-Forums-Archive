---
title: "Install Mess on Acer Aspire One"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by Holden99ca on 2009-05-08
Hi,

I'll try to make this short. A quick scan of other posts seems to have revealed other similar problems.

After a successful experience with Ubuntu on my home desktop I decided to make my Acer Aspire One a dual-boot machine. I'm kind of regretting it. I installed as per instructions, i.e., download the file, confirm the hash, make a bootable USB drive, boot from the drive, install.

During the install process I'm quite sure it never asked me anything about how to partition the drive. It's now acting *very *buggy including things like: evolution just spins but consistently fails to load, firefox's back button is always grayed out and the google search engine does nothing after you enter data into it. Last, and perhaps most importantly, it reports no space available in the "/" drive when it runs update. Indeed when I load up the Home directory it reports 0 bytes available.

How did this happen and what can I do about it? All suggestions are welcome and appreciated.

Holden

---

### Post by wpshooter on 2009-05-08
1) Did you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

2) Did you install from the Desktop CD version or the ALTERNATE (text based) CD version ?  My suggestion would be that you use the ALTERNATE for the best possibility of a good outcome.

---

### Post by Holden99ca on 2009-05-08
> **wpshooter said:**
> 1) Did you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

2) Did you install from the Desktop CD version or the ALTERNATE (text based) CD version ?  My suggestion would be that you use the ALTERNATE for the best possibility of a good outcome.

Hi Wpshooter,

1. I don't think I did check the integrity. Remember I didn't do it from a CD but rather from a USB drive.

2. The installer I used was the usual graphical. The install *seemed *to go just fine.

Now that it's FUBAR, what can I do? I've noticed I can boot from the Vista Installer (why the GRUB menu calls it that, I have no idea--the Acer Aspire One runs XP), which has an option to restore to factory default state. I suppose that would work but it's a lot of effort to start my computer from square one again.

Holden

---

### Post by Holden99ca on 2009-05-09
bump

---

### Post by Holden99ca on 2009-05-12
bump

---

### Post by MrCab on 2009-11-29
Bump

Firefox's back button doesn't seem to work (9.04 Netbook Remix from a USB stick), and other inconsistancies with it.

---

### Post by darkod on 2009-11-29
Holden,

if you open terminal and run
sudo fdisk -l (small L)

what does it say? Copy the results here. That will show you all partitions.

---

