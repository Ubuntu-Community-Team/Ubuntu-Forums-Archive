---
title: "[SOLVED] CD Drive has mind of its own."
date: 2008-11-03
forum: General Help
---

### Post by rwap on 2008-11-03
Hi, I am running a new install of 8.10 on a self built pc with a lite on DVD-RW light scribe drive, I love 8.10, I finally got my ATI GFX card to work *Gasp* it all works beautifully, with exception of a very annoying and possibly damaging issue.

My cd drive constantly retracts when I press the eject button, sometimes it doesn't come out at all unless I reboot, also it does the same thing if I unmount and eject it from the gui...

I found this guide to fixing this issue with Udev- Whatever that is.

[https://bugzilla.redhat.com/show_bug.cgi?id=453095#c26](https://bugzilla.redhat.com/show_bug.cgi?id=453095#c26)

However, this "guide" is to me, more like a very sick maze of technical garbage. :p lol...

Could some higher being please interpret this and post a fool-proof resolution? or better yet, post a patched version of the file?

I don't want to screw up my system and I have no idea what the above "guide" is telling me to do.

If this is a bug in udev, shouldn't a patch be pushed out on the update system?

Thanks in advance- I'm tired of racing to change my cd's

---

### Post by Interpreter on 2008-11-03
There is a bug report for this issue.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283316]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283316")

The importance has been marked 'High', so a fix should make it's way into the repos soon. Proposed allrewady has one methinks. There presently is a patch mentioned in the report and people are reporting no ill effects from it.

---

### Post by bscbrit on 2008-11-03
rwap - thank you, and you are correct.  This is a known bug.  The 'trick' is to press the eject button a second time before the drive closes.  Apparently, the drive will then open again and stay open.

Yeah, I know, it's a crappy solution but it is the **only** solution at present.

---

### Post by rwap on 2008-11-03
Ok thanks both of you, 

Interpreter- Thanks for the link, but I think I'll just wait for the official fix.- sounds like it won't be very long.

bscbrit - Thanks- I haven't read about that one yet, I'll try it.

Cant wait for the fix.

---

