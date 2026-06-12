---
title: "syncing Sony Walkman NWZ-S616F with Ubuntu Jaunty"
date: 2009-06-08
forum: Hardware
---

### Post by pythonscript on 2009-06-08
When I plug in my Walkman, Ubuntu picks it up and displays it as a device, but I can't see any of the files on it, and none of my media players recognize it. What software can I use to sync music (preferably from within a music player) to the player? I've heard that you need special Sony software to even use the device in Windows, but I've always used Windows Media Player and never had any trouble. Is there a way to do this in Ubuntu 9.04? Thanks for the help!

---

### Post by meeples on 2009-06-08
you should have a look at [Jsymphonic]("http://sourceforge.net/projects/symphonic") :)

---

### Post by pythonscript on 2009-06-09
That sounds promising; thank you. I've never had to use SonicStage on Windows, though. With Jsymphonic, if I copy it to my player then decide that I'd rather not use it (or it causes unforeseen problems) will it do any permanent damage to my device, or will the format options *on the player* be able to fully reset the device? Thanks for the help!

---

### Post by pythonscript on 2009-09-06
I posted a similar question elsewhere and later posted my solution to it. Here's what I worked out:

> All right, so... I've found that a lot of people have had nothing but problems with sony's devices, and I'm apparently in the same boat. I ended up creating a virtualbox xp image that I connect my walkman to. I set up ~/Music as a network share between xp and ubuntu, installed a windows driver for the ext2/ext3 file system so Windows Media Player can read my music from the aforementioned network share. I then just use the basic WMP functionality to sync music to my walkman. Not exactly the solution I was hoping for, but it was easy to set up and works flawlessly. Main point: it works.

Thanks for the tip about jysmphonic, too. That ended up not working for this model, but hopefully in the future it'll be easier to use these devices with *nix.

---

