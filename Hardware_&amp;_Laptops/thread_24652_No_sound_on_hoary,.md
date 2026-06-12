---
title: "No sound on hoary,"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by Nekrataal on 2005-04-07
i have this sound card:

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC '97 Audio Controller (rev 02)

and i cant hear anything on hoary, is there anything i can do to make it work??

---

### Post by dataw0lf on 2005-04-07
Ok, here's the deal.  Hoary uses the esd (Enlightened Sound Daemon) for sound now.  Although ALSA still works, you have to 'killall esd' in the terminal to actually use it on the system.  Alternatively, you can configure your apps to use esd.  For example, in XMMS, go to Options->Preferences->Audio I/O Plugins->Output Plugins and choose the 'eSound' plugin.

---

