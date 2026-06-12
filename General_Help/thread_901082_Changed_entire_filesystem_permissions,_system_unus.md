---
title: "Changed entire filesystem permissions, system unusable"
date: 2008-08-26
forum: General Help
---

### Post by Agares Media on 2008-08-26
Well, I made a big mistake today.  I had several windows up doing a lot of copying to different hard drives.  In one window I had the entire filesystem selected, running nautilus with gksudo, and I changed the permissions on the entire filesystem and all enclosed files to 777.  This crashed just about everything all at once, fonts couldn't even be used on most of the error messages that popped up, icons all disappeared.

When I reboot it dumps me to the command line.

Any way I can restore the previous permissions or any other advice in this situation.  

Real stupid move on my part, but I guess I had it coming as its been several years since I managed to totally crash a Linux install.

Thanks.

---

### Post by iaculallad on 2008-08-26
> **Agares Media said:**
> Well, I made a big mistake today.  I had several windows up doing a lot of copying to different hard drives.  In one window I had the entire filesystem selected, running nautilus with gksudo, and I changed the permissions on the entire filesystem and all enclosed files to 777.  This crashed just about everything all at once, fonts couldn't even be used on most of the error messages that popped up, icons all disappeared.

When I reboot it dumps me to the command line.

Any way I can restore the previous permissions or any other advice in this situation.  

Real stupid move on my part, but I guess I had it coming as its been several years since I managed to totally crash a Linux install.

Thanks.

Best thing that you can do: Do a clean reinstallation of your Ubuntu as it would be difficult changing permissions from root/users.

---

### Post by Agares Media on 2008-08-26
> **iaculallad said:**
> Best thing that you can do: Do a clean reinstallation of your Ubuntu as it would be difficult changing permissions from root/users.

That was my first line of thought as well.  I popped in my disc but apparently its scratched too bad as I can't even boot the live distro without a kernel panic.

Looks like I'll be using a friend's CD burner to get myself out of this one.

---

### Post by iaculallad on 2008-08-26
> **Agares Media said:**
> That was my first line of thought as well.  I popped in my disc but apparently its scratched too bad as I can't even boot the live distro without a kernel panic.

Looks like I'll be using a friend's CD burner to get myself out of this one.

That would be the best solution so as to deviate from further permission problems in the future.

---

