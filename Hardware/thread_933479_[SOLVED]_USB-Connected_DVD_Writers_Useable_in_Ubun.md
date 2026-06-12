---
title: "[SOLVED] USB-Connected DVD Writers Useable in Ubuntu?"
date: 2008-09-29
forum: Hardware
---

### Post by SamNSane on 2008-09-29
I've got a laptop with two hard drives running Ubuntu 8.04.1. one of the drives is a modular bay drive. I would like to keep that modular hard drive in its bay and use an external USB-connected DVD writer for my data backups.

That external DVD writer is not failing hardware. I used it for installing Ubuntu on the laptop, as a matter of fact. And the external writer worked perfectly in XP and Vista, too, doing multiple burns per week.

But I don't seem to be able to get writing to that drive from within Ubuntu to work more than a small percentage of the time. And I don't get any error messages from the applications I'm using.

So far:
1. Tried both Brasero and K3B.
2. Tried different brands and types of optical discs (DVD-R, DVD+R, DVD-RW, CD-R, CD-RW). The drive writes fine to all of these in other operating systems on this system -- and on other systems.
3. I have made minor changes in the OS configuration. Outside a single unsupported application (Beyond Compare) I have installed nothing from outside the standard repository. The problem with writing to this drive has persisted since day one of the installation.

I can just eject the modular hard drive and use the modular optical drive. Writing to that drive works perfectly. But my workflow would go better if I could be using OS/apps/data on my primary drive while burning data from the modular drive to the external USB-connected writer.

Searching for information on this turns up a fair number of threads here and there, none of them (that I found, anyway) purporting to have arrived at a solution.

Is this likely to be an Ubuntu issue, or a system/luser issue?

---

### Post by markbuntu on 2008-09-29
If you are having a problem with a piece of hardware, it would be good if you told us who made it and what model it is.

---

### Post by TheIdiotThatIsMe on 2008-09-29
SamNSane:

Hi, when you are able to will you list the manufacturer and model of the external you trying to use? I myself use an external HP dvd 840, and found that sometimes I must unplug the power in the back and plug it back in for it to work properly.

---

### Post by SamNSane on 2008-09-30
> **markbuntu said:**
> If you are having a problem with a piece of hardware, it would be good if you told us who made it and what model it is.

Uh, doh! *administers smack to own forehead*

Sony DRX-830U

It reads all brands and types of discs perfectly. Under Brasero it typically finishes writing and then the software just quits doing anything about half-way through the verification. Under K3B the application's popup writing window just disappears as though it forgot it had a job to do. But there's variability in the behavior of both applications, and I have been able to burn a couple of discs (but only a couple) using Brasero. After either application fails, the drive won't read a disc until after a reboot.

I guess I could have been more informative if I wanted information.

---

### Post by SamNSane on 2008-09-30
> **TheIdiotThatIsMe said:**
> SamNSane:

Hi, when you are able to will you list the manufacturer and model of the external you trying to use? I myself use an external HP dvd 840, and found that sometimes I must unplug the power in the back and plug it back in for it to work properly.

Hello. Sorry I forgot to list the make and model when I first posted.

So, if you have to cycle power on your HP DVD 840, does that mean that your system generally comes up with the external drive being unable to read discs, or does it read fine but just fail to burn? That's what mine does. And after it fails to burn it won't read any more until after a reboot. (I hadn't thought of simply cycling the power on the drive.)

---

### Post by SamNSane on 2008-10-01
Well, I guess I've figured out the problem. Luser error. Though I'm a little annoyed that the actual source of the problem was certainly not made clear by either the mode of failure or by the error logs from brasero. (Brasero just whined about not being able to mount the drive, when it was clearly mounting the drive.)

My method for doing backups is to place a copy of everything that I want to back up on a second physical hard drive (formatted as a single ext3 partition), then to use brasero to burn the entire contents of that partition to DVD-R. That way, I can go on using the primary hard drive with my live data without interfering with the backup, and without the backup interfering with me.

The data I copy to this second hard drive is documents, pictures, videos, etc. But I also back up the .mozilla and .mozilla-thunderbird folders to that drive.

Now I might have taken a hint from brasero that it doesn't like "hidden" folders by the fact that its own interface doesn't allow for viewing hidden folders/files. But it does allow you to drag what you want to burn from nautilus to the target disc, and then burn. So I was making the hidden stuff on the second hard drive visible in nautilus, and then dragging the whole lot from the nautilus window to the target pane in the brasero window, then burning. Brasero would go through the motions, and ruin a perfectly good disc, and then fail without giving me a useful (well, to me, anyway) error message. If the danged thing had just said, "Stop trying to burn hidden files, stupid.", then stupid (That's me.) would have removed the dumb little dot from the beginning of those folder names.

In the end, that's what I did. I removed the dumb little dot, and everything burned to disc properly.

Dang.

Thank you two for trying to help me out. I'll just leave the account of my humiliation here for all to see in case it might help another dummy like me.

---

