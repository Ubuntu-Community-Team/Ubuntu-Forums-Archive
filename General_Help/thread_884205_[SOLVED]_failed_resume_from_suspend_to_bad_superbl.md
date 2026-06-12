---
title: "[SOLVED] failed resume from suspend to bad superblock"
date: 2008-08-08
forum: General Help
---

### Post by SeanBlader on 2008-08-08
So tried to suspend my HP tx2000 tablet, and when it didn't come back up I had no recourse but to hard power down and restart. But upon restarting Grub reported an Error 17. Turns out that just means it can't get to the partition it needed. Well the partition it needed was the one with the menu.lst file on it, which meant that I had a very expensive paperweight at the moment.

So super grub disk didn't have anything it could do for my MBR, guess it looked fine. I can boot to Vista with SGD, but can't get anything off the Linux ext3 partition with SGD or Vista. So in goes the live CD. Turns out I can't mount the partition. So I check into trying to fix it because it's reporting a bad superblock. Then when I try to run e3fsck to copy an alternate superblock it says I can't because the partition is in use. And that's where I'm stuck. This is the second time I lost access to Ubuntu for the same suspend crash, the first time I just reinstalled from the live CD.

The laptop is running the bios based hard disk self test right now, but in a few minutes I should be able to get back and report on what it's results say and then get into a live CD to check what else anyone can recommend.

Help!

---

### Post by SeanBlader on 2008-08-08
Bios Hard Drive Test reports no problems, any help?

---

### Post by SeanBlader on 2008-08-16
Well I did a reinstall that time.

Then it happened again. I was thinking maybe something with the dual booting and partitioning and so I got a second drive for the laptop. Reinstalled a new setup to all new partitions.

Then after being unable to come out of hibernate again, I had to hard shutdown. Same results "grub error 17". This time I was able to save it by going to the live CD and running "sudo fsck /dev/sda1" and hitting "y" like 50 times.

So I figured I'd be safe going forward, anything that went wrong on the system I could get fixed from the live CD. Of course it happened again today. So I put in the live CD and did fsck again. Upon rebooting I ended up with what was apparently a kernel panic with the capslock key flashing.

Doesn't look like Ubuntu wants to run on my HP tx2000 tablet. I'll try it again when Ibex is released.

---

### Post by SeanBlader on 2008-10-20
Solved by this thread:
[http://ubuntuforums.org/showthread.php?t=927831](http://ubuntuforums.org/showthread.php?t=927831)

Once I get the touch screen working for the tablet, I'll be all set to go with like 100% running hardware on my system, fun.

---

### Post by gali98 on 2008-10-21
Here is my tutorial for wacom on this laptop :)
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)
Kory

---

### Post by SeanBlader on 2008-10-21
Yeah Kori, I'd read it a couple times and I have it bookmarked too. :-) I'm not really up for setting up the drivers now and then having to repeat it after I upgrade to Intrepid in a few weeks, so I'm just hanging out, trying to make sure everything here is running solid. Then I'll be more prepared to get the tablet running and notice any weird side effects, like if it stops working after resuming from standby or hibernate.

And on top of that, I'm kind of hoping that since Intrepid was supposed to be a "mobile" release, that maybe it has support for the tablet natively. That would be impressive.

---

### Post by gali98 on 2008-10-22
It may....
The default packages right now for wacom on Intrepid are 0.8.1-4 which support usb tablets. The problem is you will still have to configure your xorg.conf. I am not sure if they will work either. I am on Intrepid beta and it is great. The tablet works perfect (I did it manually) and suspend and hibernate work perfectly also!
The only problem is that it updates so much (fixing bugs and whatnot) that the wacom module always gets replaced, and I have to copy the module again. So I finally just gave up, and will wait until the release comes out to fix it permantly.
Kory

---

