---
title: "Install from harddrive?"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by Iteria on 2009-07-13
I'm a big believer in partitions. Currently, I have one for windows, one for linux, one for the data they share, and one for emergency backup (you never know when you won't have a backup drive handy and your OS is dying). 

My cd burner died the other day and I started thinking about that 10 gig partition I have for emergency back ups. I was wondering if if was possible to install linux straight from the harddrive (Or really any OS, I'm planning on upgrading to Windows 7 in October and I've never met a Windows OS I didn't have to reinstall at least once)?

It should be just a matter of placing the contents of the iso or the iso itself on the partition. The problem is how do I make the partition bootable?

---

### Post by csabo2 on 2009-07-13
PCs cannot boot off of an image on a drive, as there needs to be an OS loaded to access the filesystem.  The closest thing is Windows is capable of booting off of a .VHD natively, which is very cool, but doesnt really help you :(  

You can put the ISO on an external HDD or a Thumb drive.

---

### Post by Iteria on 2009-07-13
I would think that there would be a way. The install iso (for linux anyway) is a freaking mini-OS. Couldn't you just unzip the contents, alert grub to the partition, boot into the live-cd part then ask it to install the OS?

Not that I have the slightest idea how to do any of that, though I know that grub partition part is possible.

---

