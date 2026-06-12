---
title: "really old box"
date: 2008-06-27
forum: Hardware
---

### Post by vikramaditya on 2008-06-27
I have an old AT clone box (1996) with an AMD K62 400mhz CPU and 512mb RAM.  All the other hardware was decent in its day.  I've tried installing damn small linux, but it hangs when no ACPI support is detected.  It's been running win98 SE for years without any complaints.  Can anyone suggest a way to get linux aboard this thing?

---

### Post by luisito on 2008-06-27
Have you tried XUbuntu? I don't see why it wouldn't work. I'm running it in a Celeron 800Mhz with 384Mb of ram.

If your kernel does not load when it does not detect acpi support, you can try booting with the noacpi option (I'm guessing here)

---

### Post by dominiquec on 2008-06-27
The memory is actually quite decent, and that's the usual stumbling block that I've seen.  I'd agree with Luisito and try Xubuntu.  If that doesn't work out for you, you can go for a minimal Ubuntu install (basic command line) and just add the things you need.  I wrote down my own experiences here -> [http://ubuntuliving.blogspot.com/2008/06/minimalist-ubuntu.html](http://ubuntuliving.blogspot.com/2008/06/minimalist-ubuntu.html)

---

### Post by lswb on 2008-06-28
I've successfully installed dapper on an old P2-366 thinkpad 600E with just 288MB ram. Performance is adequte for most tasks, this is using the standard ubuntu gnome desktop. Your 1996 system won't have ACPI, can DSL be configured to use APM instead?

---

### Post by starcannon on 2008-06-28
[http://fluxbuntu.org/js.html](http://fluxbuntu.org/js.html)

---

