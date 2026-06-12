---
title: "Installing ubuntu with no cd/bootable usb/network"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by wleejolly on 2009-03-04
I've found this forum very helpful in the past, but this is my first post.  I just got an old laptop for my daughter (Dell inspiron 2500) and I'm trying to install ubuntu on it (I actually wanted Qimo on it, but I'll take what I can get for now).

The problem is the cd rom doesnt work, and the USB is not listed in the BIOS as a bootable device, due to age I'm sure.  Also, the network card will eventually be a wireless card, but I don't have much hope of getting it working in the setup program (I have 2 cards to choose from, one uses madwifi drivers and was kind of strange to setup on my main system, the other is a t-mobile branded sony ericsson card that I have no drivers for yet).

On the plus side, there is a working version of windows 2000 that I can boot into and from there access the data on the usb thumbdrive.  So I followed the instructions from here:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) 
Using the CD Image method (the only exception being I used grub4ntfs, not dos), and I was able to boot into the debian installer and start an installation.  The problem is it seems to be a network install, which I can't do.  I copied the entire 600+ MB alternate install iso to the root of C:, so why can't I just do a standalone install?  Is it because it would have to format the partition to ext2 (thus deleting the iso) and the whole iso won't fit in the ramdrive I created?

To clarify my goals here, I would prefer not having windows on the system at all.  No dual booting.  I'm just not sure exactly how to get there without network connectivity.  Any help you all can provide I would be much appreciated!  Thanks in advance.

---

### Post by avtolle on 2009-03-04
I've looked at the instructions in the linked piece, and under using the CD Image part, I see no indication that this should be a network install. Wondering out loud (that's what I'm good at, and sometimes the only thing I'm good at) about the following: Is it necessary, before beginning the installation, to shrink the Windows partition to create unallocated space on the HDD for the partitioner to work on? Additionally, again wondering whether it would be advisable to defrag the HDD a few times (if that's not already been done) to clean it up before shrinking the partition? 

What is occurring that causes you to think it (the installer) is wanting to do a network installation?

---

### Post by avtolle on 2009-03-04
BTW, while you don't want a dual boot (eventually), at this point keeping Windows 2000 on the computer is likely a requirement to complete the installation (perhaps stating the very obvious here).

---

### Post by avtolle on 2009-03-04
I'm sure you have looked at the unetbootin page, too; it appears it is able to do a "frugal install" (not sure what that is) on the HDD using an already existing iso image. It seems from reading the page that **if**the iso image is already present, no network connectivity is needed to do the installation.

---

### Post by wleejolly on 2009-03-04
Thanks for the response!  The debian installer starts up, I choose the language and keyboard language, the next step is detecting network hardware which it fails to do.  I pretty much say ok and it continues, but the next step is configure network hardware, which again it fails to do, but I can continue on.  The next step it says 'Choose a mirror of the debian archive', and at this point it wants you to select an ftp site from a list, and there is no other option.  Once I select one it says I can't reach it and then wants me to select another one.  I see no way to get beyond this at all and choose the iso on the disk itself.

About keeping windows for now, yeah....I'm afraid its going to crap out and then I'll really be stuck, so I'm not touching a thing on it until I see a working linux install :)

About unetbootin, I actually haven't seen that page yet so I'm going to go check it out now and see if anything there can help me out.  Thanks!

---

### Post by wleejolly on 2009-03-04
Man, unetbootin seemed like it was going to work, but it ends up in the same spot.  I thought this might be an issue with the alternate install iso of ubuntu that I had, so I copied the qimo iso there and tried with that, but it is the same thing.  It wants me to 'choose a mirror of the debian archive'.  Any ideas?

---

### Post by wleejolly on 2009-03-05
Well I heard back from the previous owner of the laptop and apparently the cdrom drive only works if you keep constant heavy pressure on it while it's accessing it.  So many sore fingers later I have installed linux :).  Thanks again for your responses!

---

