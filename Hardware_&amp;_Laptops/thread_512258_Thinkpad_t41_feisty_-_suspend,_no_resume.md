---
title: "Thinkpad t41 feisty - suspend, no resume"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by veebis on 2007-07-29
Suspend seems to work fine, but it's not resuming/waking up (black screen)...

I've found some mention of this being a "known bug," but with the addendum that it was fixed with a subsequent kernel update... Not so for me. 

All latest updates intsalled, no custom drivers, all stock Ubuntu.

Please help!
Thanks,
-Vb

---

### Post by veebis on 2007-07-30
Me again...

Been trying _everything_ (fglrx, uswsusp, etc., etc.), no luck.
The computer seems to wake up (lights come on, disk activity, but the screen remains black.

ATI FireGL 9000 R250

Is this just a known bug? Anybody?

Thanks!
-Vb

---

### Post by mucho_maze on 2007-08-13
Hey... I have the exact same problem with my thinkpad t41... suspend works fine, but I can't wake up the computerscreen again...

Anyone got a clue???

---

### Post by Dirk Lately on 2007-08-13
Same problem here on an HP Omnibook 6000 laptop.

---

### Post by Dirk Lately on 2007-08-15
Bump. 

Any thoughts?

---

### Post by inzpektor on 2007-10-13
Same thing here.  ...and it has been so through Hoary, Dapper, Edgy, and now Feisty.  Another guy at work also has a T41 and he **can** suspend/resume with Ubuntu.  I don't get it.

Also, some time ago, I Hibernated (Suspend to disk) the machine (I think it was Dapper), and it corrupted the disk totally.  After a pretty serious fsck-scene (excuse my French), it had placed all my files in /lost+found and all files/directories formerly in / were renamed with a # (I beleive - can't remember) followed by part of the original name.  If anybody's interested, I've always used ext3 filesystem.

Nowadays, I just shutdown normally everytime.  Luckily, Ubuntu seems to boot faster and faster with each new release. :-)

My advice to everyone else is to do the same - the risk is just too high, IMHO.

---

### Post by mperry on 2007-10-30
I wanted to provide a update on using Ubuntu 7.10 on my thinkpad T40.  I spent time with the last two releases not being able to resume cleanly after a suspend event.  Same problems as you all report.  I just did a fresh 7.10 install here on my t40 and initially had the same issues. 

At this point, I am able to suspend and resume the laptop and have wifi networking active across suspends. Things I have tried recently:

1) tried using uswsusp deb package - no real difference in quality of suspends with that package.  Had to fix the swap file location thing in its config file but even then no real successes.

2) tried installing fglrx and I could not get the driver to work for some reason.  Gave up finally and went back to ati driver.  Still no suspend happiness.

3) tried a few hacks to /etc/defaults/acpi-support with no real luck

4) changed the video driver to "radeon" from "ati" using the X config tool and added in some AGP speedups found on the web.  Changed a few values back in /etc/defaults/acpi-support.

At this point, suspend and resume works on the laptop so far everytime.  wifi networking works after a resume which seemed broken before and sound works.  I did not remove or change the gnome networkmanager program either.  I should also qualify that if I left my laptop suspended for over about 5 hours on any previous release of Ubuntu, it would never wake up at all.  The crescent moon would stay lit and force a reboot.  This does not happen any more either.

Its doubly frustrating for me because on regular old Debian Etch with its 2.6.18 kernel or so, it all works flawlessly but I have to remove the gnome-power-manager deb package or it borks.  I just ordered sidux which is a Debian Sid based build on CD to try out on a spare disk drive I have.

I'm at work now; so when I get home, I'll post a few relevant sections of changes.  Maybe it will help folks.  I have also applied the latest bios update using the non-diskette method on thinkwiki.

---

### Post by Vadi on 2007-10-30
I'm on a T40, and both suspend and hibernate, along with Compiz, work just fine, out of the box :)

What does the bios upgrade to, by the way? Anything useful?

---

