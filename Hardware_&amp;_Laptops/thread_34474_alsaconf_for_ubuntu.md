---
title: "alsaconf for ubuntu"
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by toto23 on 2005-05-15
is there any way to install "alsaconf" in hoary? did anybody try this?alsaconf is necessary for my sound card

---

### Post by edm00se on 2005-05-15
I'm in the same boat. alsaconf is not recognized as a known command when I try to run it, in Hoary. When I try to install alsaconf through apt-get, it selects alsa-utils and says it is already the newest version.

---

### Post by wvslkr on 2005-05-16
What cards do you have?

---

### Post by toto23 on 2005-05-16
[QUOTE=wvslkr]What cards do you have?[/QUOTE]
my sound card is "ess 1869".it works in mandrake 10.1 with alsaconf.

---

### Post by nad on 2005-05-16
Try the alsamixer command and unmute and increase the channels you wish. Then use 'alsactl store' to retain these settings.

---

### Post by wvslkr on 2005-05-16
That is the card I have.  Add this line to /etc/modules/

snd-es18xx isapnp=0

Reboot or restart sound should work.  It is most likely an isa card  and most
of the newer kernels aren't compiled to check for them.
Works fine for me. :)

---

### Post by andlinux21 on 2005-05-25
[FONT=Comic Sans MS]I have a similar driver for my Micron Laptop I will try what you suggested by adding the line and see if it works after restart.  I sure hope so I just got the display settings fixed and to add sound would make everything complete.[/FONT]

---

