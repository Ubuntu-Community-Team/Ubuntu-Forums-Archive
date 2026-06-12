---
title: "Dell Latitudde D600 - Strange Cursor Problem"
date: 2009-11-23
forum: Hardware
---

### Post by uberamd on 2009-11-23
I have Ubuntu 9.10 running on a Dell Latitude D600 and everything works fine **except** a slight bug in clicks. A click doesn't register until the cursor is moved. For example I will click a link and it will not register the click unless I move the trackpad ever so slightly. Its like the click doesn't register the depress until I move the cursor, otherwise it thicks I'm holding the button down or something. Its strange.

This happens with tapping the trackpad to click, as well as both left trackpad buttons. Has anyone experienced this before? Its bugging the heck out of me.

---

### Post by sremick on 2010-05-20
This exact problem is happening to me too, even with 10.04. Are there any solutions to this?

---

### Post by PRC09 on 2010-05-21
I have the same machine and the only thing I did,I didnt research it alot, was to go into bios and turn off the touchpad and use a usb mouse which works for my purposes.Not really a solution but is usable....

---

### Post by sremick on 2010-05-21
> **PRC09 said:**
> I have the same machine and the only thing I did,I didnt research it alot, was to go into bios and turn off the touchpad and use a usb mouse which works for my purposes.Not really a solution but is usable....

Unfortunately not really a solution. This needs to be used as a laptop.

I don't get it, as from reading the forums here there are tons of people using the D600 with Ubuntu. Since it's obviously not a 1-off hardware fluke on my laptop but instead is a known problem affecting other people, there ought to be a known solution.

---

### Post by uberamd on 2010-05-26
Still no solution to this. I have tried Ubuntu 10.04 on 4 different Dell D600's and they all exhibit the exact same issue. Very annoying.

---

### Post by sremick on 2010-06-25
Oh well, multiple confirmations but no developer acknowledgments or possible solutions. Unfortunately that leaves me no choice but to put XP back on this laptop for my mom. Saddens me, as I was hoping to give her a safer experience by bypassing Windows, and Ubuntu/Mint would run faster on the old hardware than Windows bogged down with AV software, but these touchpad issues are a dealbreaker.

---

### Post by biofuelfarmer on 2010-06-25
FYI, under 10.04 I had strange cursor/trackpoint/left click problems on the Dell D600 that I am writing this note on.  Became so troublesome that I thought the palmrest assembly had gone bad.  Reinstall with 9.04 fixed the issue.   Only bummer is that some website video seemed to work slightly better under 10.04.

---

### Post by sseelbinder on 2010-07-20
I also have encountered this issue with 9.04, 9.10, and 10.04.  I installed CentOS linux and did not encounter this issue.  I couldn't get my wireless on the D600 to work with CentOS and reloaded Ubuntu 10.04 - and I am back with the annoying mouse click problem with the internal mouse.  Drives me batty too!

---

### Post by P4man on 2010-07-28
This seems to work for me:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/444674](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/444674)

Post 24

---

