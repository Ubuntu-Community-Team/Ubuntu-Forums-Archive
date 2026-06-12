---
title: "IBM thinkpad 600x no screen after booting and logging in"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by thurid on 2005-04-17
hi,
I have installed hoary 5.04 on my machine and everything is fine until I try to log in. I enter username and password, hit the login button, then watch as the screen goes a nice brownish grey and then - nothing. I have tried re-installing with variations like a different language (German instead of English), various "special machine" features but the result is the same.
Any ideas?

thurid

---

### Post by steinarne on 2005-04-20
I have the same problem, after a new install
the same computer worked with warty

steinarne

---

### Post by fduplex on 2005-05-01
I am also having this exact same problem on my Thinkpad 600x. As far as I can tell everything is working fine except logging into gdm.

The system boots up as usual, the GDM login screen comes up, I enter my username and password, then the background is brown and all I see is a cursor. Gnome does not load.

**Update:** I found a bug report on this, see here: [https://bugzilla.ubuntu.com/show_bug.cgi?id=8477](https://bugzilla.ubuntu.com/show_bug.cgi?id=8477) , It appears to be audio related.

---

### Post by ernestoongaro on 2005-05-01
The bug suggests an IRQ problem. I also have a Thinkpad 600x, had similar problems, try adding ```
acpi=off
``` at the grub menu.

---

### Post by Delph on 2005-09-01
[QUOTE=fduplex]I am also having this exact same problem on my Thinkpad 600x. As far as I can tell everything is working fine except logging into gdm.

The system boots up as usual, the GDM login screen comes up, I enter my username and password, then the background is brown and all I see is a cursor. Gnome does not load.

**Update:** I found a bug report on this, see here: [https://bugzilla.ubuntu.com/show_bug.cgi?id=8477](https://bugzilla.ubuntu.com/show_bug.cgi?id=8477) , It appears to be audio related.[/QUOTE]

Adding "irqpoll" to the kernel boot options in grub fixed this issue for my Thinkpad 600x.

---

### Post by NeilS on 2005-09-01
Hi all.

I was having the same problem with my Samsung VM8000 series laptop - when I logged in to Gnome, the drum sample repeated indefinitely whilst Gnome refused to log-in.

I'm pleased to say that adding irqpoll to the Grub config, as suggested, now means I can log into Gnome, but my SiS integrated sound now refuses to work at all. (It does show up in the Device Manager as a "Sis PCI Audio Accelerator".)

Does anyone have any ideas on how to fix my sound?

Many thanks,
Neil.

[EDIT A COUPLE OF MINUTES LATER: Ah! I now realise my sound was muted by default. D'OH! Please ignore me. :-(]

---

