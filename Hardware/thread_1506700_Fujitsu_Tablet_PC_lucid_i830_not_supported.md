---
title: "Fujitsu Tablet PC lucid i830 not supported?"
date: 2010-06-10
forum: Hardware
---

### Post by Enter t'Ibex on 2010-06-10
I USB booted LUCID on my Fujitsu ST4120.
Honestly I wasn't expecting anything, but lo and behold, it ran the screen found the pen, sound, even backlight intensity control: I was floored. Looks pretty good too.

So I went off and loaded it over opensuse.

Now the error comes up: Lucid does see the i830 video chipset or have a compatible driver for it.  I tried editing xorg.conf to add the i830 i810 listing as worked in opensuse as well.

Im guessing that the driver is not in the new package.

It does run "in low resolution mode" whatever that means, just seems to flip alot during startup.

Is there anything I can do to make this better? Hints or clues welcome.

Thanks

---

### Post by Favux on 2010-06-10
Hi Enter t'Ibex,

You could check to see if it is a KMS (kernel mode set) issue by adding nomodeset to the kernel boot line by following these instructions:  [http://ubuntuforums.org/showpost.php?p=9442063&postcount=4](http://ubuntuforums.org/showpost.php?p=9442063&postcount=4)

But looking at the bug reports I can't tell if a newer Intel driver supports the 830.  They do seem to be working on it though.  You may need to try a legacy driver.  See:
[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/362582](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/362582)
Linked by the launchpad bug:
[https://bugs.freedesktop.org/show_bug.cgi?id=17902](https://bugs.freedesktop.org/show_bug.cgi?id=17902)
There's patch that seems to kind of work near the bottom.

---

### Post by Enter t'Ibex on 2010-06-14
Thanks for the link.  I dont know how you found this, but the bugs.freedesktop is exactly the error I have.
Thanks for this...

---

### Post by Enter t'Ibex on 2010-09-10
I have checked back, it seems like there is no current fix for this.  Is there a way to tell from the links above whether work is being done or not?

My tablet is usable under 10.04, but I need to restart x several times to get it the display right...

Any information would be good...
Thanks

---

### Post by Favux on 2010-09-10
Hi Enter t'Ibex,

The freedesktop bug report shows activity up to mid July and then the "fix" was assigned to the "community".  I gather that means the "official" maintainers  won't work on it and they're hoping a developer from the community will take it on and submitt a patch that fixes it.  Which is probably why the Ubuntu launchpad bug's status was changed in mid August to "confirmed-unknown".  In other words no one has heard of anyone tackling the bug.

Sorry, but not looking good.  I'm glad to hear you can get the display up even if it requires multiple restarts of X.

---

### Post by Enter t'Ibex on 2010-10-31
Okay. One more try. Intel is showing a linux driver back in March.
Has anyone tried this or is this more wishful thinking.

---

### Post by Enter t'Ibex on 2010-11-23
Well, unless anyone has a parting idea I think I'm going to drop the 200 Bucks and put window 7 on this thing. I'm tired of the random hangs from the missing intell driver. I will miss Xournal sniff!

---

### Post by Enter t'Ibex on 2010-11-24
yes I will.  IMHO Xournal has been extremely useful being able to annotate PDF's and puke them back out as PDF's.

---

