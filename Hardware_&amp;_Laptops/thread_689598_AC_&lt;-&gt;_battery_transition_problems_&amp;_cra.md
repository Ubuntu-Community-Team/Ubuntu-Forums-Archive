---
title: "A/C &lt;-&gt; battery transition problems &amp; crashes"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by subwayfox on 2008-02-06
Hello all, I'm new here, so I hope I'm posting in the right place, etc., etc.

Anyways, I'm running the semi-customized eeeXubuntu (based on 7.10) distribution on my fairly new Asus EEE PC, however with the ubuntu-desktop package installed to make it the usual distribution.  I asked this question on the eee forums and got no help, so I thought I'd try here:

	I have two problems that may be connected:

	1.)  Whenever I disconnect from A/C, Firefox automatically opens to file:///home/(username).  Conversely, the same thing happens when I plug in, plus I get a message that evolution isn't found (I removed evolution to save disk space as I have no need for it).  I've poked around a bunch in  /etc/acpi/, the scripts linked to from there, and the anacrontab/crontab files and haven't found a damn things.  It's a minor nuisance, sure, but it shouldn't happen, and I think it is related to my second problem-

	2.)  I can suspend and resume the machine fine when it is plugged in, or when it is on battery power.  However, I can't change state in between without the system freezing hard.  That is, say I suspend the machine while plugged in, unplug it to take it somewhere, then try to resume: the machine will freeze hard.  The same is true vice-versa; it needs to be in the same state as when it was suspended to resume.  It seems to be about 50/50 freezing before the screen turns on again, or coming to the desktop, flashing a gnome-power warning about a policy error, then freezing hard.  This is more of a major problem- it's tough to have a laptop that you can't plug/unplug at will.

	I've searched a ton and tried everything I can think of, to no avail.  Anyone out there have any ideas?

	Thanks a lot,
	Blair

---

### Post by jawbreaker on 2008-03-07
I can confirm #1.

I did the same thing. Installed eeeXubuntu and then installed ubuntu-desktop. I haven't found a fix either.

I did, however, discover that the problem is tied in with Preferred Applications. AC off launches the preferred browser, and AC on launches the preferred email.

---

### Post by subwayfox on 2008-03-08
Interesting.  I have no idea why the Preffered Application should launch then.

As a quasi-fix, I installed the standard version of Ubuntu and then the Ubuntu Eee patches.  This has a number of problems of its own, but it fixes the most egregious ones such as described above.  It still freezes on occasion from return to suspend but I may have stumbled upon the larger problem-

If I disable the wireless driver (the Ubuntu Eee modules  give you a keyboard shortcut to do so quickly), I seem to have no problems suspending and/or resuming.  That said, I haven't tested it exhaustively as I've reluctantly gotten into the habit of turning the machine off instead of suspending.  

I will say that I think installing vanilla Ubuntu Desktop then using the Ubuntu Eee packages is a better solution than eeeXubuntu; I've had far fewer problems with the machine ever since.  That said, I hope someone with more knowledge of the Ubuntu internals is reading this (or others); I'd love to see some better Eee support in future versions.

---

