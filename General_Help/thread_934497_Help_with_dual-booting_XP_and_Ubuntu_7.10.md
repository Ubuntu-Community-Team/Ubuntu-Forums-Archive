---
title: "Help with dual-booting XP and Ubuntu 7.10"
date: 2008-09-30
forum: General Help
---

### Post by SonicRacer1412 on 2008-09-30
I need a bit of help. My dad is buying a new hard drive for our computer (because the other one got corrupt and made an odd noise inside the computer). I am considering dual booting with Ubuntu 7.10.

I need some help with Windows back-up. What do I do if my XP doesn't come with a recovery disk? What if my CD drive doesn't come with a CD burner? How can I get a DSL modem to work with both OS systems on the dual boot?

Any help will be greatly appreciated ASAP.

---

### Post by kk0sse54 on 2008-09-30
If your CD drive doesn't come with a burner you can either 1) burn a Ubuntu CD off another computer or 2) order a free Ubuntu CD

As for your XP not coming with a recovery disk it should have a recovery partition which usually is available on boot up

If you use dhcp instead of a static ip address you shouldn't worry about being able to connect to the internet. During the install Ubuntu should auto detect and configure your network for you while you won't need to change any Windows settings at all.

Just wondering why do you plan on installing Ubuntu 7.10 instead of 8.04 or perhaps waiting a few weeks until 8.10?

---

### Post by lisati on 2008-09-30
If your machine didn't come with a recovery CD/DVD, then have a look for a recovery partition as cloud suggested. If it's on the drive you're looking at replacing, I'm sure there are people on the forums who can give you suggestions for copying it (or your current Windows partition) to the replacement drive. Otherwise you might want to talk nicely to the people you purchased the computer from. 

(Be cautious of Windows CDs of the "don't ask too many questions where it came from" variety - they sometimes come with with nasty surprises in the form of viruses etc. And telling you where to get them from is frowned upon here in the forums)

As for a fresh installation, sort out Windows first.

---

### Post by kk0sse54 on 2008-09-30
If the recovery partition is indeed on the old Hard Drive plug it in and if you have a Ubuntu CD boot your computer up from the LiveCD. From there see if you might be able to access the recovery partition and copy to another median. Otherwise if you request it from your manufacturer and/or microsoft they might send one to you if you can prove that you bought it(ex. registration number for your computer).

---

### Post by SonicRacer1412 on 2008-09-30
How can I access the hidden partition? The partition might not be on this hard drive, as it will most likely be blank and not have any partitions on it.

---

### Post by SonicRacer1412 on 2008-10-02
Well, it turns out our dual-boot plan was a flop. We got Ubuntu installed, but when we tried to boot into windows, the boot screen appears briefly before that blue screen with the "STOP 000..." message at the bottom. Is this because I chose the easy way out to put both OS' on the same partition?

---

### Post by JDorfler on 2008-10-02
> **C!oud said:**
> If your CD drive doesn't come with a burner you can either 1) burn a Ubuntu CD off another computer or 2) order a free Ubuntu CD

As for your XP not coming with a recovery disk it should have a recovery partition which usually is available on boot up

If you use dhcp instead of a static ip address you shouldn't worry about being able to connect to the internet. During the install Ubuntu should auto detect and configure your network for you while you won't need to change any Windows settings at all.

Just wondering why do you plan on installing Ubuntu 7.10 instead of 8.04 or perhaps waiting a few weeks until 8.10?

Or you can boot from a USB drive.  You can use unetbootin.  There's a version for linux and windows.

---

### Post by JDorfler on 2008-10-02
> **SonicRacer1412 said:**
> Well, it turns out our dual-boot plan was a flop. We got Ubuntu installed, but when we tried to boot into windows, the boot screen appears briefly before that blue screen with the "STOP 000..." message at the bottom. Is this because I chose the easy way out to put both OS' on the same partition?

More than likely.  Go to my blog and look up how to dual boot.  It's just one of many ways of doing so.  The link is in my signature.

---

