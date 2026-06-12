---
title: "A compatible pci-e RAID controller card?"
date: 2014-02-24
forum: Hardware
---

### Post by morningstar.fallen on 2014-02-24
Hey people,

I'd like to install my OS (ubuntu gnome) on a separate drive and then have another two large capacity drives in RAID 1 serving as a safe storage. Is there any RAID controller card I could use with the latest Ubuntu's, without either spending sleepless nights trying to set it up or paying loads of cash for some corporate level gear?

Something proven 100% compatible, simple to set up and under £40GBP or $80?

Cheers

---

### Post by CharlesA on 2014-02-24
I used to use a [RocketRAID card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816115053"), but had a nasty time getting it to cooperate with DKMS to get the kernel modules built after kernel upgrades. Now I am running an LSI MegaRAID 9280-8i and haven't looked back.

I would go with software RAID in your case, especially if you don't want to deal with incompatible gear and you have a budget that wouldn't work for a enterprise class card.

Have a read here:
[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)

---

### Post by morningstar.fallen on 2014-02-24
Thanks, I thought this wasn't going to be straightforward. As a last chance before I turn to software RAID. I do have a Silicon Image SIL5723 controller chip on my mainboard and the manufacturer (ASUS) claims that it can create a driverless BIOS (fake?) RAID? Is there any chance this might actually work under ubuntu? 

The only reason I am asking is that I don't quite like the fact that otherwise I have to setup the software raid with an alternate disc of standard (unity type) ubuntu, then abort the installation and start again with the ubuntu gnome disc which I wish to use as my OS of choice.

---

### Post by CharlesA on 2014-02-24
I guess you could set it up for RAID in the BIOS, but then your options to manage it will probably be limited if Asus only makes RAID management software for Windows.

In any case, it would still be fakeraid and I would rather use mdadm instead of that, especially with how robust mdadm is.

What do you mean you need to do an alternative disc installation? If you are going to have one main OS drive and two "data" drives, you don't need to reinstall anything. Check out the tutorial I posted earlier. it is for RAID5, but you can use it as a base for what creating a RAID1 mdadm array would be like.

---

### Post by morningstar.fallen on 2014-02-25
No, it will be a fresh install with the two storage drives set up as RAID 1 and a separate (ssd) drive for the OS. I will have to replace a corrupted (beyond repair) installation of Fedora. So If I want to use software raid, I will either have to use an alternate CD of a differen flavor to set it up and then continue installing with ubuntu gnome, or just try to set it up after install using mdadm.

---

### Post by CharlesA on 2014-02-25
Ah ok, I thought you were doing the clean install just to get the raid set up.

I would do a normal install and get Ubuntu installed on the SSD and then deal with mdadm afterwords. :)

---

### Post by morningstar.fallen on 2014-02-26
Okay, I've done that. Tried the asus driverles thingie but it didn't work as you predicted. Thanks for helping me mate!

This was a fairly good step-by-step guide to for newbies:
[http://www.youtube.com/watch?v=mee9l1aNZdc](http://www.youtube.com/watch?v=mee9l1aNZdc)
[http://www.youtube.com/watch?v=HryJvlOtEVU](http://www.youtube.com/watch?v=HryJvlOtEVU)

---

### Post by morningstar.fallen on 2014-02-26
As a conclusion to the whole thread topic, I can only say: Unless you're ready to spend $400 plus on an enterprise level controller card, you're better off sticking with the software RAID like the Man with the hat says... :)

---

### Post by CharlesA on 2014-02-26
> **morningstar.fallen said:**
> As a conclusion to the whole thread topic, I can only say: Unless you're ready to spend $400 plus on an enterprise level controller card, you're better off sticking with the software RAID like the Man with the hat says... :)

That's coming from the goofball who spent a ton of money on enterprise class drives and a raid card. I like the performance though. ;)

So, totally worth it.

---

### Post by morningstar.fallen on 2014-02-26
I know, I use them at work... :)

---

