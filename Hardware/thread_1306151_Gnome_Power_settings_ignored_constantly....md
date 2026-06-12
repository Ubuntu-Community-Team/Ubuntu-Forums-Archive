---
title: "Gnome Power settings ignored constantly..."
date: 2009-10-30
forum: Hardware
---

### Post by PaulW21781 on 2009-10-30
[B]Please refer to this post, I've added a link to a bug I filed with a possible solution (albeit a dirty fix) but the cause I feel has been found.

[http://ubuntuforums.org/showpost.php?p=8456748&postcount=13](http://ubuntuforums.org/showpost.php?p=8456748&postcount=13)[/B]

*---Old Post Follows---*

I've done a fresh install of Karmic on my laptop (was running since Alpha 2), but decided to clear everything out...

Now, no matter how I configure the power options, they just never work.  I've turned off "Everything" (screensaver is off too, blank screen timeouts, etc) yet the laptop it still going to a blank screen after 5 minutes REGARDLESS if its plugged into the mains or not.  I've also tried clicking "Make Default" and rebooting, nothing...

This is happening on both my laptops since fresh installs of Karmic.  before Karmic (Jaunty) the settings were fine, and no issues at all!

This is getting a bit annoying, especially as I watch films on the laptop and with the blank screen coming on regardless of power plugged in... I can't watch a damn thing without having to move the cursor all the time...

---

### Post by Figaro123 on 2009-10-30
Yep, this is happening to me too. Just upgraded today, the screen decides to fade after 5 minutes without input no matter what the power settings are, even if a video's running. Very annoying.

---

### Post by inigopete on 2009-10-30
interesting - I thought it was just something I'd done wrong or a setting I'd missed...

Fresh install of 9.10 on my Dell 10v yesterday and while the screen blanks after 5 mins (I set it to do that anyway), it won't suspend after any time after that when on battery power. And having tinkered with the power settings, it turns the screen off after 5 minutes on every other setting.

What can this be?

---

### Post by jeremy on 2009-10-31
My desktop running 9.10 won't blank the screen, regardless of my power management settings!

---

### Post by iamnotthemessiah on 2009-10-31
i sort of have the opposite problem, screen turned off after x mins even if im playing a movie, regardless of which player

---

### Post by umr3b3l on 2009-11-02
Same here, Clean install of Karmic and monitor goes blank every 10 minutes regardless of the settings.  Im on a dell inspiron 1525

---

### Post by ./mario on 2009-11-03
I have the same problem as Jeremy and it won't standby on battery power.

Regards,

./mario

EDIT: Karmic Koala 9.10 Final

---

### Post by isoToxin on 2009-11-03
I'm seeing slightly different problems on a Fujitsu/Siemens lifebook p7010, but still power management related.  Screen tends to randomly dim, even when I'm working on the machine.  I've also noticed that brightness adjustments performed using the brightness applet seem to stick better than if I just use the function key + brightness+ key combo (which just gets ignored after a few minutes).  Seems power management still needs a little work on some machines.  I've now disabled the "fade on backlight" and "dim when idle" options, and it seems to behave a little better.

---

### Post by ./mario on 2009-11-03
I think we are facing some kind of bug, because this was some bug in 2.26 when I was using Archlinux:

[http://bugs.archlinux.org/task/14221](http://bugs.archlinux.org/task/14221)

---

### Post by ./mario on 2009-11-03
New findings:

If I kill gnome-power-manager and gnome-screensaver, all works well.

Saw this in bugs.launchpad post #23:

[https://bugs.launchpad.net/ubuntu/+bug/273484/comments/23](https://bugs.launchpad.net/ubuntu/+bug/273484/comments/23)


Try it and worked.

Apparently the two processes went to sleep...

Any ideas?

./mario

---

### Post by ./mario on 2009-11-20
Bump...

---

### Post by iris-n on 2009-12-06
I've nailed it.

What we have here is the combination of a bug and sadism.

The bug is that playing a video does not count against a computer being idle. This is a regression and should be investigated.

The sadistic part is that someone, somewhere, decided that it would be good to override everyone's screensaver settings. Yep, that's right. The blanking has nothing to do with gnome-power-manager. Some sick ******* turned the screensaver on, with 5 minutes timeout. And with which screensaver? Blank screen. Yep, that's right, the one that is indistinguishable from gnome-power-manager's monitor sleep.

If this is not a prank, gnome has reached a whole new level of incompetence. Disgusting.

And good news: the bug is only with gnome-screensaver. With it disabled, gnome-power-manager never dims the screen while playing a video. Which reminds me of [this]("http://xkcd.com/196/"). A bit old, but maybe this is a reincarnation of that bug.

---

### Post by PaulW21781 on 2009-12-07
I've since filed a bug today about this, there is a dirty fix which can be used by editing the xorg.conf file (which I have included in the bug report)

Alas, without adding the entry into the xorg.conf file, the power settings are still ignored (well, the blank screen at 10 minutes of idle still happens), but with the config added, I can happily leave my laptop running now playing videos, completely idle and it will not die after 10 minutes, and will instead rely totally on gpm.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/493645](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/493645)

So from what I can make out, the issue is with xorg, although could also be linked to gpm not successfully altering the value...  I've not had a play with kde see if the problem is the same there though...

---

