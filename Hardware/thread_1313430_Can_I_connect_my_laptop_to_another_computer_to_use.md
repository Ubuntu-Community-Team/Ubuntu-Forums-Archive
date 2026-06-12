---
title: "Can I connect my laptop to another computer to use it's DVD-drive?"
date: 2009-11-03
forum: Hardware
---

### Post by Blue Dolphins on 2009-11-03
I can't burn DVD's on my computer, but I know someone that has one that can.  Could I connect them with a usb cable, and then use their Disc Drive to burn DVD's?  If so, how would I do it? 

My computer has Xubuntu 8.10 installed, the one with a DVD burner has Windows XP.

---

### Post by issih on 2009-11-03
At the risk of being proved wrong by someone more knowledgeable, I'm going to say that you can't do that.

you can theoretically share a dvd drive much as you'd share a folder of anything else under windows..and samba in ubuntu should pick that up, and providing you have everything configured correctly in terms of user permissions you would then be able to read data off that remote drive...but I'm pretty sure its a read only thing.

If I was you I'd just punt the files over to the other machine over a network and then burn them locally.

Hope that helps

---

### Post by diesch on 2009-11-03
Maybe it's possible using rscsci.[Here's a doc for Gentoo](http://en.gentoo-wiki.com/wiki/Burning_disks_over_a_network_with_rscsi).
I never tried it and I don't klnow if it can be made working with Windows.

---

### Post by Blue Dolphins on 2009-11-03
> **diesch said:**
> Maybe it's possible using rscsci.[Here's a doc for Gentoo]("http://en.gentoo-wiki.com/wiki/Burning_disks_over_a_network_with_rscsi").
I never tried it and I don't klnow if it can be made working with Windows.
I forgot to say that I ain't too computer-savvy, everything in that link just flew over my head.

---

