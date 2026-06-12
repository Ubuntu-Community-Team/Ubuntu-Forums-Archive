---
title: "Monitor Going Black on Bootup; Hardy on hp pavilion dv5000"
date: 2008-11-04
forum: Hardware
---

### Post by MST3Kakalina on 2008-11-04
While I was working a couple nights ago, my laptop monitor suddenly dimmed so drastically I thought it had blacked out. I had been working in OOo and just hit "ctrl-S" to save, so theoretically I could have hit some weird key combination, but I doubt it.  Trying to adjust the brightness with my fn keys (fn + f7 and fn + f8 ) is completely ineffective, so.

I rebooted and (while on battery) my laptop worked just fine, to my relief.  I sent what I was working on to myself, tooled around some more on Ye Olde Tubes, and shut down.

The next morning, however, the monitor stayed uselessly dim, even on battery, and continued to do so through an upgrade to Ibex and a fresh (re)install of Hardy.  I used an image I downloaded today; my last install I used an image I downloaded back in October.  I don't understand why the reinstall didn't fix it.

If I close the laptop lid, I get a few seconds of usability again when I open it before it dims back to uselessness. So the monitor itself isn't broken.

What I've tried:

The proposed fix in [this](http://ubuntuforums.org/showthread.php?t=609722&page=15) thread (adding "acpi=noirq" to /boot/grub/menu.lst).

Installing xbacklight.

Upgrading and reinstalling (as I mentioned).

Playing with the brightness applet in GNOME.

What I haven't tried:

Mucking about with the BIOS settings.



Now, as you can imagine, getting any kind of useful information from my machine is very difficult, so it's tough going trying to figure this out.

Does anyone know if there were any updates from November 3 or so that would have affected this?

---

### Post by MST3Kakalina on 2008-11-05
Turned out to be a busted inverter board.  Apparently the timeline for the one in my particular model of HP laptop is 1.5 - 2 years.

---

