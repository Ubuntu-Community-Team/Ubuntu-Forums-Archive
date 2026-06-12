---
title: "activate component out"
date: 2010-07-31
forum: Hardware
---

### Post by jjh76 on 2010-07-31
Is there some way to activate the component out on my radeon x1300? I'm trying to set my old pc up as an htpc but I just get a blank screen when i connect it to my tv.

---

### Post by IcarusR on 2010-07-31
This may help, despite being for archlinux...

[http://wiki.archlinux.org/index.php/ATI]("http://wiki.archlinux.org/index.php/ATI")

---

### Post by jjh76 on 2010-07-31
Thx, but no help there.

xrander tells me i have vga, dvi, and s-video output. Even though the card actually has component  out, not s-video,  I tried this command from that page:

xrandr --output S-video --set load_detection 1[FONT=monospace]

[/FONT]but it just gives me this error:
[FONT=Verdana]X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  27
  Current serial number in output stream:  27

[/FONT]

---

