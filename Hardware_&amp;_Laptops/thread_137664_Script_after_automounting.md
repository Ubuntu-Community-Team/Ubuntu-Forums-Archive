---
title: "Script after automounting?"
date: 2006-02-28
forum: Hardware &amp; Laptops
---

### Post by MightyFlea on 2006-02-28
Hi folks,

I was wondering if there was a way to automatically run a script whenever a USB drive is automounted, after the actual mount?

(What I want this for:
I do my backups to an USB drive, so it would be nice to be able to run the backup script automatically when the USB drive is switched on. One-button backup, so to say..
The other reason: I keep my photo library also on a USB drive. The (otherwise very nice) KDE application digikam can only deal with one, fixed-configured photo library. So I am helping myself with a symbolic link to the actual library on the USB drive. I wrote a script that detects the library and sets the link accordingly, but having to run int manually is not so nice.)

Any ideas how to do this? I looked around in the hal and pmount documentation, but did not find anything. Maybe I am blind..

Cheers,

MightyFlea

---

### Post by Hansers on 2006-07-08
Just wanted to know if you had figured this out. I would also like to see your script.

Cheers

---

### Post by MightyFlea on 2006-09-26
Not so far; but I did not try lately.

I am in the process of upgrading to 6.06, and will probably try again then.

---

### Post by TrinitronX on 2006-09-30
I've been trying to do the same type of thing in Dapper, and have gotten close, but can't figure out why my script won't run.

I think the answer lies somewhere in the mess of udev, hotplug, and hal.
I've tried using some udev rules to run my script, but it doesn't work.

You can find my udev rules and more info here: [http://www.ubuntuforums.org/showthread.php?t=268291](http://www.ubuntuforums.org/showthread.php?t=268291)

If anyone figures this out, I'm interested in the fix :D

---

