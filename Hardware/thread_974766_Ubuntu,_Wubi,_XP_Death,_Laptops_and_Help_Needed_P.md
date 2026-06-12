---
title: "Ubuntu, Wubi, XP Death, Laptops and Help Needed :P"
date: 2008-11-07
forum: Hardware
---

### Post by UnderTheOath on 2008-11-07
Okay, so I had Ubuntu installed on my ASUS M6000 via Wubi. Thing was, once I was using XP for a lot of stuff, and the laptop overheated making the processor shut itself down. When I logged back into XP, it wouldn't let me. My XP install had been kinda screwed up, and my only option was a complete reinstall.

Now my dad, who's very knowledgeable about computers - he works with them for a living - mentioned something about Ubuntu not being configured to properly deal with the laptop's power management or something, and that was why XP died. Is this right? If so, what can I do? I want to reinstall Ubuntu, but I don't want XP to die again.

I would have thought that XP dying was totally unrelated to Ubuntu... And while my dad DOES know so much about computers, he's very anti-anything-that-isn't-windows...

So, what are my options here?

---

### Post by UnderTheOath on 2008-11-08
I'm actually considering going the Kubuntu route instead, but it's the same issue.

---

### Post by rpavic on 2008-11-08
If you were running Windows and not Ubuntu than the problem was not caused by Ubuntu. Ubuntu and it's power management problems (if they exist, I don't know of them TBH) had nothing to do with your problem. I have 8.04 on my Acer laptop and it works without any problems regarding overheating and power management.

If you want Ubuntu and XP, but without Wubi (to make your father less likely to suspect Ubuntu) try installing XP on a part of your disk and leave a fraction of unallocated space for Ubuntu. Then install it as dual boot on the unallocated space. That way Ubuntu is completely unattached to Windows.

Kubuntu or Ubutnu - same thing.

Hope I was of some help.

---

### Post by UnderTheOath on 2008-11-08
> **rpavic said:**
> If you were running Windows and not Ubuntu than the problem was not caused by Ubuntu. Ubuntu and it's power management problems (if they exist, I don't know of them TBH) had nothing to do with your problem. I have 8.04 on my Acer laptop and it works without any problems regarding overheating and power management.

If you want Ubuntu and XP, but without Wubi (to make your father less likely to suspect Ubuntu) try installing XP on a part of your disk and leave a fraction of unallocated space for Ubuntu. Then install it as dual boot on the unallocated space. That way Ubuntu is completely unattached to Windows.

Kubuntu or Ubutnu - same thing.

Hope I was of some help.

Cheers mate. I'll have a go, and if weird things start happening I'll ditch Ubuntu :P

---

### Post by UnderTheOath on 2008-11-09
Okay so now I have a totally different problem. I installed Kubuntu with Wubi, but I don't get an operating system choice menu thing. It just complains about my invalid boot.ini or something and goes straight into XP...

---

### Post by razy60 on 2008-11-10
personally i would download and burn to disc, or get a cd of the live disc and install from that. i tried installing using wubi and unetbootin but with no luck, cd worked first time. just remember to clear/uninstall wubi and reinstall the windows mbr, you may want to format/defrag the partition of the drive your going to load ubuntu onto so as to give yourself a nice clean install area. 
if you look in wubi on this forum it will give you details on how to do this.

Raz

---

### Post by UnderTheOath on 2008-11-10
Yeah, there's no way I wanna partition my drive though... That's a little too perminent in my mind.

---

