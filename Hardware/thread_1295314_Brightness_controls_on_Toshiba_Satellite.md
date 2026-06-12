---
title: "Brightness controls on Toshiba Satellite"
date: 2009-10-19
forum: Hardware
---

### Post by Nalroff on 2009-10-19
I know this is a very weathered subject, but I'm revisiting it simply because my particular problem is nothing like anything I've seen on forums or HOWTO's so far.

Before you start jumping on me to do searches before I post, believe me when I say that I have. I've Googled the snot out of the interwebs to find very little help at all.

Anywho, on to the actual task at hand. I have a Toshiba Satellite A105-S4094 (I know it's old, deal with it), and I'm running Jaunty (Ubuntu 9.04) on it. Everything has been working flawlessly on it as far as my needs go, but I recently got a battery for it. I had had a gaping hole in the back of my laptop and needed an outlet for everything, but now I have a battery, so I'm happy. The problem is, the brightness controls will not work at all. And I don't just mean the stupid Fn keys. I mean at all. I installed the way to use acpi_fakekeys, and when I fire the event to lower (or raise) brightness manually, the icon comes up to say that it's doing the job, but nothing happens.

So I figured it was a driver issue and I read about the Omnibook Kernel Module and decided to give that a shot. Found out that the module's main download is not compatible at all with the newest kernel build, so the only way I got that working was by getting it from SVN. "make" ran just fine, "make install" was good, and "make load" gave me a few fits with modprobe being picky with config files, but was fixed in about 30 mins or so. I got everything installed and to the point that I can edit the /proc/omnibook/lcd file and change the brightness number, but guess what? Nothing happens when I change the number. I'm pulling my hair out over a stupid dimmer switch, but I'd rather extend the life of my battery than have it die in 1.5 hours.

Please, please, PLEASE -- any help/advice/"Ah, why not?" will be GREATLY appreciated. Thanks, community.

---

### Post by Nalroff on 2009-10-19
anyone?

---

### Post by rygar on 2009-10-21
did you try adding "omnibook" to /etc/modules?

For me, omnibook didn't work if I started it manually, but worked fine after it started on startup.  Adding it to the modules file should do that...

---

### Post by rygar on 2009-10-21
also, you could try updating your BIOS.
worked for this guy...

[http://ubuntuforums.org/showthread.php?t=383062](http://ubuntuforums.org/showthread.php?t=383062) (post #6)

---

