---
title: "Linux Doesn't Recognize USB Hard Disk [Solved]"
date: 2013-04-06
forum: Hardware
---

### Post by Iggy64 on 2013-04-06
I have a Dell Optiplex 360 desktop PC that I have been running on WinXP.  I have converted it over to a Bodhi Linux machine.  (Bodhi is based on Ubuntu, but uses E17.)

I have two USB hard drives that I use for backups and playing music:

Western Digital MyBook WD2500i032
Western Digital Dual-Option Combo WD2500B011.

When plugged in, the first one is immediately recognized and automounted.  However, I have not been able to get the second one recognized by Linux.  When I plug it in (using the very same port), nothing happens.  

If I do an fdisk, it does not show the USB drive.  

If I do a dmesg, there is no new system message.  Essentially, nothing has happened.  The system has not noticed that the drive is plugged in.  

If I remove the drive and plug it into a Win7 machine, it automounts immediately.  So the drive is OK.  BTW, it is formatted NTFS.

I do not know enough about Linux to guess whether this is a driver issue, or what other causes there might be.  Can anyone suggest things I could try in order to diagnose/fix??

Thanks, in advance.

---

### Post by Iggy64 on 2013-04-06
I wrote my question to this forum after several hours of frustration trying to mount the reluctant USB HD.  As noted earlier, I tried various sequences of powering the drive and plugging it in, with absolutely no success.  The procedures yielded no new drive under fdisk, and even dmesg showed no system activity as a result of pluggin in the drive.

Then I plugged in a different USB drive and it automounted just fine.

Then I plugged the problem USB drive into a Win 7 machine, and it automounted OK.

So I wrote my question to this forum: What is going on?

Shortly thereafter I thought: What the heck, let's try it one more time before calling it a day.  And sure enough, the doggone thing automounted right away in Linux.  There was a popup error message, saying "Error: A job is pending on /dev/sdb1."  However, the drive is mounted and I can read the files.

I don't know whether mounting the alternative USB drive did something to change Linux, or if mounting the problem USB drive on Windows 7 did something to change the drive itself.  Something evidently changed, though.

I guess this is one of those things I'll never figure out.  I suppose we can consider this issue "Solved," even though I don't quite know how it was solved.

---

### Post by cortman on 2013-04-06
Lol. Glad it worked out for you, although those kinds of "solutions" are almost as maddening as the problem itself...
You can mark the thread [SOLVED] by editing the first post, and changing the title.
Good luck!

---

### Post by Iggy64 on 2013-04-06
Thanks for sharing the humor in the situation.  Yes, it is rather maddening.  I always would rather know WHY the problem occurred.  At least, I know some things to try and to look for if it happens again.

Thanks for the tip on how to mark it "solved."  I was wondering how to do that.

I appreciate the help!!

---

### Post by ajgreeny on 2013-04-06
Have you always removed the disk properly from your windows machine, or have you just pulled the USB from the socket like a lot of windows users do?  If you did that the NTFS disk/partition would be flagged as still in use and thus unmountable in Linux, though I would have thought dmesg would still have shown something being attached.

---

### Post by Iggy64 on 2013-04-06
Good question, ajgreeny.  

I can say that I am have always been very religious about using "Safely Remove" whenever removing a USB device under Windows.  I also typically look to make sure the drive letter is gone from Windows Explorer, and that the drive has stopped spinning.  When Windows tells me "The Device May Now Be Safely Removed," I pull it.

That being said, there are still a few of possiblities that validate your question:

1) Maybe I was having a bad day the last time I used the drive, and I screwed up.  Unlikely I would make a mistake like pulling a powered up drive; but I am definitely not perfect.

2) Maybe the system locked up or crashed last time I used that drive under Windows, and I just don't remember that.

3) This particular USB drive has always seemed a bit odd.  Even under Windows, there were times when it just didn't want to power off.  I would do the Safely Remove Device business, and Windows would say it's OK to remove.  The drive would spin down, but the power light would stay on.  I would have to press the power button on the drive, and hold it for several seconds until the drive "clicked" off.  Sometimes, I'd even get a message saying it couldn't be turned off right now.  I could find no rhyme or reason why it would sometimes do this.  A few times, I'd end up powering down the entire system in order to remove the drive, just to be safe.  Very annoying.  It was like this from the day I bought it (new).  The other WD drives I've bought over the years have not had this strange behavior.  Maybe the best thing at this point is to simply copy the contents onto a new USB HD and dump this goofy thing.

It's working OK with Bodhi Linux right now, but it is not consistently mounting/dismounting/ejecting from the desktop icon dialog.  I have to use the udisks commands in Terminal to remove it. Too bad WD doesn't have much in the way of product support.  I'd love to learn how this particular model is SUPPOSED to work (button pushes, etc.).  Maybe there's a secret to how it should be connected/disconnected (although I think I've tried every possible combo).

Thanks a lot for taking time to comment.  I appreciated it.

---

