---
title: "Inspiron CPU Fan"
date: 2012-02-26
forum: Hardware
---

### Post by waveOSBeta on 2012-02-26
I have a Dell Inspiron 15R (N5010), and the CPU fan does not work in Ubuntu. It works in Windows 7. I have Ubuntu 10.10, and I love it, but it overheats my CPU, and I don't want to break my laptop. Can someone please tell me a fix for this?

---

### Post by alegomaster on 2012-02-26
By that, do you mean that all of the fans don't work, or does one certain fan not work.

---

### Post by waveOSBeta on 2012-02-26
I think the CPU fan is the only one, and it doesn't work.

---

### Post by ahallubuntu on 2012-02-26
If you still have Windows 7 installed somewhere, go to Dell's website at support.dell.com and look for an updated BIOS; you will probably need to install it within Windows.  Sometimes a BIOS update might fix something that wasn't broken in Windows but might work better in Linux.

Also, if you really mean 10.10, time to upgrade.  10.10 is only supported for another few months.  11.04 gets you another six months of support and it may handle your fan better; you can revert to Gnome 2 (instead of the Unity desktop that some of us dislike) easily in 11.04 so it looks much like 10.10 does.  I've had great luck with Ubuntu 11.04 actually.

11.10 is the latest version and may work a lot better with your laptop - it has the 3.0 kernel.  Might at least be worth a try.  I'm personally holding off on 11.10 (except for one test install) because it's a pretty radical change from past versions.  I'm going to wait for 12.04 and until it is ironed out a bit before moving to it.

---

### Post by waveOSBeta on 2012-02-26
I never knew you could revert to gnome! I completely modded the UI, with compiz and themes, and a bunch of other cool stuff. I'll try the BIOS update, and I'll upgrade to 11.04. Thanks!

---

### Post by ahallubuntu on 2012-02-26
Gnome 2 is still included with 11.04 but not in 11.10 - you have to use Gnome 3 (I think) which is a bit different.

Try this to revert to Gnome 2 in 11.04:

[http://ubuntuguide.net/ubuntu-11-04-natty-login-to-classic-gnome-2-desktop](http://ubuntuguide.net/ubuntu-11-04-natty-login-to-classic-gnome-2-desktop)

I can't guarantee you 11.04 will fix your CPU fan.  You might try booting up the Live CD first and see if it works any better.  Same for 11.10 .

---

### Post by waveOSBeta on 2012-02-26
Also, I read that enabling enhanced real time clock support may help. The issue? I have absolutely no idea how. Can anyone please help me out?

---

### Post by Mark Phelps on 2012-02-28
> **waveOSBeta said:**
> ... but it overheats my CPU, and I don't want to break my laptop. Can someone please tell me a fix for this?

The source of the overheating is a known bug in recent Linux kernels.  I've read that this is in the process of being fixed, so if you want to experiment, you could download and burn a CD of 12.04 Beta, boot from that, and see if that kernel fixes the problem.

Also, I would strongly advise AGAINST just arbitrarily upgrading your BIOS in the hopes that if fixes something.

I used to do the same thing myself, and then a few months ago, I got a new Gigabyte motherboard.  When I noticed the BIOS was "old", I immediately downloaded and updated it with the lates BIOS -- and my memory speed dropped from 1600 to 1200!  

Fortunately, I had saved off the original BIOS, reflashed using it, and my memory speed was back to 1600.

So now, I advise folks against doing BIOS upgrades.  These are not the "miracle cure" for Linux-related problems that everyone seems to think they are.

---

### Post by ahallubuntu on 2012-02-28
Mark, you found one case out of many where the manufacturer either defeatured your motherboard with an upgraded BIOS or fixed a problem. (Maybe their motherboards aren't stable with 1600MHZ RAM on all types of RAM?).  One anecdote doesn't change the general case that BIOS upgrades often fix problems or add features (like supporting newer CPUs).  In another thread, someone was having the same CPU fan issue with an Acer laptop, and it is a known solution to upgrade the BIOS to fix this specific laptop's issue.

I do try to caution people that upgrading a BIOS is much more dangerous than simply installing a driver, because a bad BIOS update can "brick" your computer whereas simply messing up a driver install can't break anything.  BIOS updates usually don't take long and are painless, but I always remind people to leave their computers on AC power and don't interrupt a BIOS update or turn the power off in the middle.  FOLLOW the manufacturer's instructions.  It is possible to install a BIOS update in a different way than was intended, say using Linux instead of Windows, but that is very dangerous if you don't know exactly what you are doing.

I have upgraded many BIOSes and only bricked a motherboard once, but that's because I was careless and not following the manufacturer's instructions (It was an ancient motherboard and I knew I was taking a chance, trying to fix a weird issue).  Worst case, as you have found, it's usually possible to revert if need be to the old one.  Manufacturers often have all the old versions available for download even if you didn't back up the old one.

---

### Post by Mark Phelps on 2012-02-28
ahallubuntu:  I'm not looking to start an argument, but I also stick to my position that folks should not be upgrading BIOS's in the hopes of fixing Linux problems.

And, although I've never "bricked" a PC with any of the numerous BIOS updates I've done over the years, I can't say the same for the other folks that post here.

Also, since this is nearly always a kernel-related issue, trying the newer kernel with 12.04 (which I read separately is supposed to fix this regression) poses much less risk than flashing the BIOS.

---

