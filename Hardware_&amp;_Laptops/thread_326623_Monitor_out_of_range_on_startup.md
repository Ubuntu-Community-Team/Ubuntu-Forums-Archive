---
title: "Monitor out of range on startup"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by Mateo on 2006-12-27
I've always had the problem of not being able to see the splash screen during boot up.  This is true for windows and ubuntu (as long as i've owned the computer).  The monitor always has a floating box that says "out of range"  and says to change the resolution to at least 1024x786.

It's not really a problem, just an annoyance.  I'd like to fix it if possible.

---

### Post by Tux Aubrey on 2006-12-27
I had the same problem when I got a new monitor.  You can tell GRUB what resolution to use during the boot process.

To try it out, interrupt GRUB at boot up and edit the kernel line to add vga=791

It should look something like this:

> /boot/vmlinuz-2.6.15-27-686 root=/dev/hda2 ro quiet splash vga=791


If that works, edit menu.lst to add the same thing so that it works each time.

If 791 doesn't work, try another number from the attached table.

Good luck.

---

### Post by Mateo on 2007-01-02
are there any other general solutions, that work outside of grub?  I can't see the bios startup screen unless I have my tv hooked up through tv-out.

---

### Post by Mateo on 2007-01-06
bump

---

### Post by Mateo on 2007-01-09
bump

---

### Post by kellingt on 2007-02-11
You probably have something configured incorrectly in your system bios.  I'd hook up through your TV and look through the system bios screens for anything video related.

---

### Post by Mateo on 2007-02-11
People say that.  I'll give it a shot.  I've never owned a computer with a BIOS that you can change video settings.  I've never seen that. I've never specifically looked for that in this BIOS, so I'll give it a shot.  I just doubt it.

---

### Post by chocolateboy on 2007-11-30
[Computer Monitor Loses Sync When TV OUT Feature Is Enabled ]("http://tinyurl.com/yvb5qb")


Install [StartUp Manager]("http://web.telia.com/~u88005282/sum/index.html"), and try changing System -> Administration -> StartUp-Manager -> Boot options -> Display -> Resolution to 1024 x 768.

---

