---
title: "Installing Ubuntu onto External Hard Drive"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by daspyx07 on 2009-06-02
Hi guys! i just recently bought a WD 250GB Passport, an external usb harddrive , and was hoping to install/boot ubuntu from it.

Now i do not want to partition either the c disk, or the e-disk (the passport/external usb harddrive). I also want to be able to access all of my files already stored on my harddrive when/wherever I want. And Finally, i want to be able to delete ubuntu whenever i want to (hopefully that won't happen =D ).

What options do i have in order for me to be able to go to any computer and just plug in the hard drive and boot ubuntu? (if possible, persistent, but don't care if this is not possible)

I have seen wubi, and I tried to use it to install ubuntu 9.04 it onto my usb drive, but for some reason, it works fine until it gets to "Creating virutual disks..." and i waited an hour or so, but the progress bar didnt budge. Is there any possible solution?

I have also heard of unetbootin, but i haven't tried it yet. If I use this to install ubuntu 9.04 onto my hard drive, will it delete all of my current files?

I am very open to other solutions. (especially if it is quick and/or easy

Thanks in advance!

ps. please nothing extremely complicated plz....or else i might get to scared to try it...

---

### Post by utnubuuser on 2009-06-03
Make a USB start-up disk from the live cd maybe?

Use gparted from the liveCD to shrink and existing partition on the USB drive, then use the Make USB boot disk from System>>Administration>>Make USB startup disk.

Don't use gparted if the partitions on the disk are Vista.  You have to use a Vista disk to change Vista partitions.

- I've never tried this, and it's only a suggestion about a possible solution!!!

Also, I've used the USB keys available at UbuntuStore.com to do what you're asking about, - one disk to rule them all - Plug the key into any USB-bootable device to use the OS. Even when it was set to persistent.  Not bad for $20.00.

---

