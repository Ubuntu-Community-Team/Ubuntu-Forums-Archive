---
title: "HP PSC750 scanner invisible to XSane"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by OriTheEep on 2009-11-02
The update manager announced a new version 9.10 so muggins asked for it. I certainly did "ask for it"! Lots of things don't appear to be working but we'll start, please, with the scanner which I need to use "Now!", as it were.

It's one of those awful multifunction jobbies but the printer part is (sort of - A printed test page could only tell me that I was using the wrong driver.) working so XSane's inability to find the scanner is doubly curious. "sudo sane-find-scanner" didn't see it either.

Previously, with Ubuntu 9.04,  XSane could use the scanner.

I've been trying to make sense of the various troubleshooting options in the "sane-usb" manual. Given time, I might eventually puzzle them out. Time is not currently a plentiful resource.

I tried installing HPLIP from HP. It hasn't made a difference.

Any suggestions?

---

### Post by OriTheEep on 2009-11-02
Problem solved!

As per emptymind's post (No. 26) in the thread, [kubuntu] No sound after upgrading to 9.10, I ran "sudo apt-get install grub2" and the scanner re-appeared.

I think I'll have a lie down before tackling the rest of it.

:)

---

