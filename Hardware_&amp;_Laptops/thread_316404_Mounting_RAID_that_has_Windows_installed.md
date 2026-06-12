---
title: "Mounting RAID that has Windows installed"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by Capslock118 on 2006-12-10
Hey Guys,
  I am new to this forum, I also recently installed Ubuntu.
I have searched through these forums and a few others and came to a few conclusions. 
First, my RAID is a software raid, since Ubuntu doesn't see it. I don't recall what type of Raid I have but, currently its a 160gb raid with 20gb of that formatted as a Windows installation, It is not a mirrored raid, and it is 2 80gb SATA disks; I hope that is sufficient for you all to understand what type of raid it is, 0 maybe?

What I want is the ability for Linux to see my raid, so I can access my Windows partition, i DO NOT want to accidentally, or purposefully delete the windows partition, since I have a lot installed, games and what not on another drive.

I want to do this so a) I can dual boot, and b) use the extra space to start transferring my data to a Linux file system (I am trying to migrate myself to exclusively use Linux; do you think thats a good idea to begin with?).

I have read that mdadm can help configure a RAID, but I am worried about losing my current windows partition with the creation of a RAID...is this something I should be worried about?

Any help is greatly appreciated.

---

### Post by psusi on 2006-12-12
You probably have a fake raid controller.  See [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for info.  

If you are running edgy, there is a bug report linked to in the howto that has an updated package attached.  Install that and you should be able to access the raid array.

---

