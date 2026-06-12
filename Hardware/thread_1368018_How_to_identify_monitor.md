---
title: "How to identify monitor"
date: 2009-12-30
forum: Hardware
---

### Post by bkline on 2009-12-30
I'm running Ubuntu 9.10 on a box with a GeForce G210.  I installed the proprietary driver (185.18.36) and brought up the display configuration utility, but there's no option for identifying the monitor.  There's a dropdown with a single item on it saying "CRT-0 (CRT-0 on GPU-0)."  I've got a Hanns-G 28-inch monitor, capable of resolutions up to 1920x1200, but (presumably because I'm not able to tell the configuration utility which monitor is attached) the best I can get is 1152x864.  How do I identify the monitor to the driver?

Thanks!

---

### Post by bkline on 2009-12-30
I got it working by manually editing the xorg.conf file.  It seems that Ubuntu has dropped the displayconfig tools, so we're back to hacking the conf file. :-)

---

### Post by JSeymour on 2009-12-30
> **bkline said:**
> I got it working by manually editing the xorg.conf file.  It seems that Ubuntu has dropped the displayconfig tools, so we're back to hacking the conf file. :-)
You have no System -> Preferences -> Display?

---

### Post by bkline on 2010-01-13
> **JSeymour said:**
> You have no System -> Preferences -> Display?

I do, but it didn't give me any way to tell the system what kind of monitor I have (as it used to).

---

### Post by barnex on 2010-01-13
I don't know a solution but please tell me when you've fixed it, I had a similar problem with an external monitor and I'm curious for an answer.

---

### Post by bkline on 2010-01-13
> **barnex said:**
> I don't know a solution but please tell me when you've fixed it, I had a similar problem with an external monitor and I'm curious for an answer.

As noted above, I solved the problem (my own problem, that is, not the problem that Ubuntu is becoming harder to use), by hacking the xorg.conf file.  I had to boot into Windows to get PowerStrip to give me the numbers that work for my monitor, which I then fed to X (via the xorg.conf file).  See [this thread]("http://ubuntuforums.org/showthread.php?t=1366542") for more details.

---

### Post by howefield on 2010-01-13
> **bkline said:**
> I installed the proprietary driver (185.18.36)

Do you have System > Administration > Nvidia X Server Settings > X Server Display Configuration ?

---

### Post by bkline on 2010-01-13
Looks like there's a bug in the forum software, because I received an email notification of another post to this thread, but the interface to the thread itself isn't displaying that post.  It provides what appears to be a useful tip, so I'm reproducing it here (apologies if it turns up later, resulting in two copies of the post in the thread):

> Dear bkline,

barnex has just replied to a thread you have subscribed to entitled - [ubuntu] How to identify monitor - in the Hardware & Laptops forum of Ubuntu Forums.

This thread is located at:
[http://ubuntuforums.org/showthread.php?t=1368018&goto=newpost](http://ubuntuforums.org/showthread.php?t=1368018&goto=newpost)

Here is the message that has just been posted:
***************
[COLOR="Blue"]***If you happen to have a kubuntu installation or liveCD handy: the KDE display settings provide a "identify outputs" feature that show s the name of the outputs on the respective displays. Sorry for giving a KDE answer to a gnome question, but it's the only way that I know of.***[/COLOR]
***************


There may also be other replies, but you will not receive any more notifications until you visit the forum again.

All the best,
Ubuntu Forums

Excellent tip, thanks!

---

### Post by bkline on 2010-01-13
> **howefield said:**
> Do you have System > Administration > Nvidia X Server Settings > X Server Display Configuration ?

Yes, but (as noted in the original post for this thread), it doesn't provide any way to identify the monitor.  It's got a "picklist" with one item on it ("CRT-0 (CRT-0 on GPU-0)") -- if you can call a list with one item a picklist.  In earlier versions of Ubuntu, with this same hardware, I got a list with hundreds of choices to identify the monitor, some very specific manufacturer/model number combinations, and others more generic identifications of classes of monitor.  Worked just fine.  No idea why they thought users would be happier having to hack down into refresh rates for the hardware, the way we used to have to do back in the early days of Linux.  Seems like a step backward to me.

---

### Post by howefield on 2010-01-13
> **bkline said:**
> Yes, but (as noted in the original post for this thread),..

The only reason I ask is because it wasn't clear on the post which utility you were using. It does identify monitors on my setup but obviously not on yours.

---

### Post by bkline on 2010-01-13
> **howefield said:**
> The only reason I ask is because it wasn't clear on the post which utility you were using. It does identify monitors on my setup but obviously not on yours.

Thanks for checking.  I tried both, actually, with effectively the same result: the generic "Display Preferences" tool doesn't have a picklist at all, just static text in pink saying "Monitor: Unknown"; the proprietary utility had the one-item "picklist" described above.

---

### Post by bkline on 2010-01-13
[QUOTE=barnex]"If you happen to have a kubuntu installation or liveCD handy: the KDE display settings provide a "identify outputs" feature that show s the name of the outputs on the respective displays. Sorry for giving a KDE answer to a gnome question, but it's the only way that I know of."[/QUOTE]

Hmm, well that sounded promising when I first read it, but if I had thought about it more carefully it would have occurred to me that the changes that have broken the system's ability to detect and/or specify the type of monitor attached to the system (or even the specify manufacturer and model) are at a lower level than the display manager/desktop layer.  At any rate, I tried it: downloaded the latest Kubuntu LiveCD (I even pulled down the 32-bit version in case this might have been a 64-bit-specific issue), booted into it, pulled up the display configuration tool, and clicked on the "identify outputs" button at the bottom.  Didn't do anything other than flash "CRT0' on the panel.

At any rate, I appreciate the suggestion, even though it didn't bear fruit.  And as I said, I've solved the problem for my own system (falling back on lower-level hacking).  I was only pursuing this further in hopes that I'd have a tool to recommend for others encountering this regression in Ubuntu usability.

Thanks!

---

