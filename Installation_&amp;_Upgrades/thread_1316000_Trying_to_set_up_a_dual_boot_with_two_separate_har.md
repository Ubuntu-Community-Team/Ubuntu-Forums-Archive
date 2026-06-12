---
title: "Trying to set up a dual boot with two separate hard drives, without RAID"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by Veteropinguis on 2009-11-05
In the past I have had horrible luck trying to dual-boot. My XP CD is scratched so while I have no problems in XP, it decides that ntoskrnl.exe is missing and won't accept when I put it back.

However, I have just gotten my hands on a spare 160 GB SATA hard drive out of an old Dell and would like to try a different dual-booting scenario.

I'm keeping Windows around for a few games...and in case I decide to get an iPod Touch and need iTunes. However for all my other computing needs I'd rather use Ubuntu, as it's faster and more fun. I already use a lot of open-source products and have used Ubuntu a bit in the past.

However I have never tried to set up a dual-boot with two hard drives. I'm planning on just wiping the 160 GB disk and doing a fresh install of Karmic, while leaving my 250 GB MS disk untouched. I'm something of a noob so my questions might be retarded.

So:

1. I was planning on taking out my Windows drive, popping in the Ubuntu drive, installing Karmic, and then putting the Windows drive back in. Will that work?

2. Once I have the two drives with their respective OSes how do I set up the dual-boot with GRUB and all that?

3. Will I be able to transfer my music from the Windows drive to the Ubuntu drive without having to set up some sort of RAID thing? I know what RAID basically is but I have no idea how to set it up.

4. What should I definitely not do to the hard drives?

Both HDDs are SATA. I did a little research but most of what I found involved setting IDE drives as master/slave.


Thanks guys.

---

### Post by Virtualburn on 2009-11-05
I'm no expert but I've just set up a Dual boot with Win XP.

> **Veteropinguis said:**
> 1. I was planning on taking out my Windows drive, popping in the Ubuntu drive, installing Karmic, and then putting the Windows drive back in. Will that work?

This would work but then the machine wouldn't be 'Dual boot' you would have single booting drives that you are replacing manually.. why would you wnat to do that?

> **Veteropinguis said:**
> 2. Once I have the two drives with their respective OSes how do I set up the dual-boot with GRUB and all that?

Best way for you is to run the iso from within your windows environment choosing 'Install inside windows'.  This will extract the files reboot the machine and then install Ubuntu, you can choose your secondary drive as the partition for this.  when the computer restarts you will have a choice of XP or Ubuntu.. Simples.

> **Veteropinguis said:**
> 3. Will I be able to transfer my music from the Windows drive to the Ubuntu drive without having to set up some sort of RAID thing? I know what RAID basically is but I have no idea how to set it up.

I was quite surprised at the fact that from 'Root' I can access all the files in my Windows and Files folders.. all videos, music, etc are readable from within Ubuntu.. Great!

> **Veteropinguis said:**
> 4. What should I definitely not do to the hard drives?

Swap them manually.. 

> **Veteropinguis said:**
> Both HDDs are SATA. I did a little research but most of what I found involved setting IDE drives as master/slave.

You don't use Jumpers on SATA drives, you set Drive 0 in the Bios and that's it.

I'm just running through this for the first time myself, so please anybody add anything or correct me. Ubuntu Rox!

:D

---

### Post by Veteropinguis on 2009-11-05
I figure what I'm trying to do is probably impossible.

The problem is, as soon as Ubuntu touches my Windows installation, I can't boot back in to Windows and I've wasted too many weekends trying to make it work. What you're describing, Virtualburn, basically sounds like Wubi- which made my XP get cranky the last time I tried it.

I guess what I should be asking is: can I set up GRUB so that it will let me pick between hard drives?

Just to make things clear, I was never planning on going and changing between OSes by plugging and unplugging the drives.

---

