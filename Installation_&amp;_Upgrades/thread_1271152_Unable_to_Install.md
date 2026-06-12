---
title: "Unable to Install"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by Hremsfeld on 2009-09-20
Hello, all.

Interesting problem: A few days ago, I tried to install Ubuntu to a 16gb flash drive (You know, the type that says you have 14.9gb of storage, but that's a different story). I used Wubi, selected 14gb as the installation size, set up user name, password, etc. and let it go.

It stayed at "Creating virtual discs" for about a day and a half. Eventually, I hit "cancel" and tried to install it to my hard drive; I'm getting an error that "A previous installation was detected in L:\ubuntu. Please uninstall that before continuing." Where L:\ is the flash drive. If I restart my computer with the CD I burned in it, it gives me the boot menu, but if I select Ubuntu, I get an error. I'll post that in a second, once I restart again. Something like part of the CD is missing.

I know that a typical answer is, did I burn the CD correctly? Well, I took a screenshot of the CD and the "correct" view, and uploaded a comparison here: [http://img84.imageshack.us/img84/3073/linuxquestion.png](http://img84.imageshack.us/img84/3073/linuxquestion.png)

I've also re-formatted the flash drive roughly three times since then to try to get it to realize that, hey, ubuntu is *not* installed there. I've tried removing the flash drive and installing, same thing.

Next, I figured, hey; I'll reassign the drive letter and see if that clears it up. Unfortunately, whenever I select a letter besides "L," it tells me that "parameter is incorrect."

Now, I think it *is* possible to install it inside windows, but I don't want to leave Vista-64bit on my ASUS laptop at all, I want to leave it behind for Linux. Now that the wall of text is done, can anyone help me?

---

### Post by Hremsfeld on 2009-09-20
Update: Restarted with the disc in, and wrote down the error:

"Windows Failed to start. [Umm...Ubuntu failed to start?] A recent hardware or software change might be the cause. To fix the problem:

[LIST=1]
[*]Insert your windows installation disc and restart your computer.
[*]Choose your language settings, and then click "next."
[*]Click "Repair your computer."
[/LIST]
If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

File: \ubuntu\winboot\wubildr.mbr

status: 0xc000000e

Info: The selected entry could not be loaded because the application is missing or corrupt."


Figured out what my problem was; that file, was previously written to the flash drive. I erased _everything_ on the flash drive. Anyone have an idea what registry keys I'd have to change, or at least where I could get those files again? I still have the .iso if that helps.

---

### Post by ajgreeny on 2009-09-20
Are you saying that you can't even boot to windows now, or did I misunderstand?

I'm sorry to say, but your screenshot gives no idea of whether or not the iso file you burned, or if the burn itself was successful, but it looks as if there are some folders missing.   OK, you burned it as an image, not just as an iso file, but that was certain from the fact that the CD booted.  What you need to be sure of is that the iso file you downloaded was not corrupt, which can happen; it has to me once.  This is usually done with a check of the md5 checksum, which I could do in ubuntu but have no idea how you do it in windows.  You can find the correct md5sums of the iso files at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes), so find the md5 checksum of the iso file using windows and then compare the two figures; they must be exactly the same.

When you boot the CD you can also check that the burn was OK by using the Check CD option in the boot menu.

---

### Post by Hremsfeld on 2009-09-20
> **ajgreeny said:**
> Are you saying that you can't even boot to windows now, or did I misunderstand?

You misunderstood, yeah. Windows boots fine, but when I try to boot Ubuntu, it says it can't, and I guess the default message starts by telling you Windows can't boot. Even though it can. :/

> **ajgreeny said:**
> I'm sorry to say, but your screenshot gives no idea of whether or not the iso file you burned, or if the burn itself was successful, but it looks as if there are some folders missing.   OK, you burned it as an image, not just as an iso file, but that was certain from the fact that the CD booted.  What you need to be sure of is that the iso file you downloaded was not corrupt, which can happen; it has to me once.  This is usually done with a check of the md5 checksum, which I could do in ubuntu but have no idea how you do it in windows.  You can find the correct md5sums of the iso files at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes), so find the md5 checksum of the iso file using windows and then compare the two figures; they must be exactly the same.

When you boot the CD you can also check that the burn was OK by using the Check CD option in the boot menu.

I was afraid it would, yeah. Okay, so: I downloaded the md5 checksum, and the .iso lines up. It's possible that image was for Intrepid, though. Which got me thinking: What if I tried to install Intrepid instead of Jaunty? It's working, so far; 590.2 / 699.0 MiB downloaded .iso so far, 30 GB version. I'll let you know how it works out.

---

### Post by Hremsfeld on 2009-09-21
Ended up solving my problem; I installed Intrepid instead, and installed it to my hard drive instead of my flash drive. That ended up working beautifully, and I am now a new Ubuntu user :guitar:

When I boot up my computer, though, I still get the broken Ubuntu choice, but there's a working Ubuntu below it, so it's just slightly annoying. I'm going to try installing Jaunty to my flash drive again and seeing if that fixes it. There were briefly two Ubuntu programs, 696 mb each, in the Vista equivalent of Add/Remove programs. I removed the broken one, Vista said it couldn't find the uninstaller, so it just removed it from the list. I hope this helps anyone in the future with this problem.

---

