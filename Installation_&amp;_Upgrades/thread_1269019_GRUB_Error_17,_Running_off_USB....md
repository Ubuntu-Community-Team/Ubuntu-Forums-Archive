---
title: "GRUB Error 17, Running off USB..."
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by flamefury on 2009-09-17
Major help, please.

When I installed Ubuntu 9.0.4, I made a specific partition to put it in. I booted up, and the GRUB menu DID load. But then when I selected Vista, the computer printed out a huge red "ERROR". I reset, and now I get GRUB error 17. The only way I can even use my computer now is running off the Ubuntu on my only USB.

I saw possible fixes using bootable media, but I have no CDs I can use. I'm also an Linux n00b, so I have no idea how to access simple things using this OS.

What do I do?

Also, I (accidentally) used a partition that had stuff in it for the swap space. I can't find anything free that has a chance in recovering that data. Suggestions for that would be great.

EDIT: I fixed GRUB error 17 by reinstalling GRUB loader with the Terminal. However, now I find that I cannot access the majority of my system space. If I log on to Vista, the only hard drive I see is the Vista64 drive and not the 180 GB OS-less partition that (used to) have all of my data.
How do I make it accessible to both operating systems?

---

### Post by quixote on 2009-09-18
You're not doing too badly if you went from zero to fixing grub! :D

The bad news is that the partition you used for swap space is probably toast.  If there's something you absolutely have to try to recover, it's possible to do a low level scan for a specific string, find the clusters that file occupies, and then read those clusters directly.  But you have to really, really, really need it for that because it's a huge bother, and even then you'll only recover it if it hasn't been overwritten already.

Regarding the 180GB data partition, it's still there, it's just not being accessed.  I don't know enough about Vista to know why it's not seeing it.  Ubuntu is probably not seeing it because it's not being mounted.  Since you're booting Ubuntu off a USB drive, I think the default is not to mount any internal hard drive partitions.  If you open nautilus (ie the file manager, for instance if you go to Places > Home), there should be a list of "places" potentially accessible in the side pane.  (if there's no side pane, go to View > SidePane.)  The drives / partitions listed should mount when you click on them.

I realize this doesn't really solve most of the trouble, but at least it may be a start.

---

### Post by flamefury on 2009-09-20
Yeah, I figured as much about my drive. Thankfully, it was only assigned homework that I can re-download at any time from my course webpages, Warcraft III which I still have the CD for, and my valedictorian speech, which I had sent to somebody for review a couple weeks prior (phew, dodged a high-calibur bullet there).

Ah, well, no sweat! I can now read the data drive on both Ubuntu and Vista, which is totally awesome. Vista's unable to read the Linux drive though, which is odd, but I suppose not completely necessary.

I think I had to mount the drives to get it working, but I'm not exactly sure...In Ubuntu, I was able to see both Vista and data drives, and when I double-clicked it, I had to enter my password before I could get in. Not sure if that was mounting, but I can access my files there now.

I suppose that's everything for my partition and installation issues, so I thank you for taking the time to respond!

---

### Post by quixote on 2009-09-21
Great to hear that it's kinda, sorta working, and that you can recover the essential data.  Vista, and Windows, read a much more restricted set of filesystems than linux or unix, and Microsoft tries quite hard not to touch any of that icky open source stuff. :biggrin:

---

### Post by raymondh on 2009-09-21
> **flamefury said:**
> 

Ah, well, no sweat! I can now read the data drive on both Ubuntu and Vista, which is totally awesome. Vista's unable to read the Linux drive though, which is odd, but I suppose not completely necessary.


See this which allows windows to read linux ext formats.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Happy ubuntu-ing :)

---

