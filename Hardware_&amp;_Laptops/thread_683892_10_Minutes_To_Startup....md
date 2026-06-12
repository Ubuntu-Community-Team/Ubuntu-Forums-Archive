---
title: "10 Minutes To Startup..."
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by nbitting on 2008-01-31
I am seeing something right after the text "Starting up..." pops up on the screen during bootup...it says something like BIOS 8254 Timer not connected....something like that.  What does that mean?  It just hangs and doesn't display a splash page....then it finally gets to the login window...

Any help would be greatly appreciated!

Thanks!

---

### Post by KyleAnderson on 2008-02-05
Sometimes in these I like to get more verbose messages from the kernel to see what is going on. Try pressing "ESC" when to get to the grub menu. Press "E" to edit the default booting kernel, then goto the end of the kernel line and delete "quiet" and anything that references the "framebuffer" or "bootsplash"

If you can boot like that, it should hang at something for a long time, whatever it is hanging at, that is probably the problem.

The bios 8254 may or may not be it. (Could be bogus)

---

