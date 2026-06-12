---
title: "Video Corruption after Suspend/Resume"
date: 2005-03-09
forum: Hardware &amp; Laptops
---

### Post by oaaltone on 2005-03-09
I have Hoary running fairly well on my IBM ThinkPad T42. Here's the deal (and I know this problem plagues more users than just myself):
[list]
[*]Both suspend/resume to RAM and disk work perfectly with the "ati" drivers for Xorg.
[*]After installing the "fglrx" drivers for Xorg, 3D acceleration now works, but display corruption occurs on resume, and there is no way around this besides a hard reset.
[/list]
Now I've seen many people complain about this, but have been unable to find a solution thus far in my perusings of the forums/mailing list. Has anyone been able to find a suitable workaround or complete solution?

---

### Post by alastair on 2005-03-09
This rings a bell as a known issue with the fglrx drivers. Perhaps have a look through ATI's release notes or website. They have some sort of "knowledgebase/bug system" note about something like this. In other words, you might be at their mercy.

You might try changing to a VT before the suspend.

---

### Post by oaaltone on 2005-03-09
[QUOTE=alastair]This rings a bell as a known issue with the fglrx drivers. Perhaps have a look through ATI's release notes or website. They have some sort of "knowledgebase/bug system" note about something like this. In other words, you might be at their mercy.[/QUOTE]
Yeah, I came across [this link](http://www2.ati.com/drivers/linux/linux_8.10.19.html#174111), but the URL given for information doesn't seem to work anymore. 

> You might try changing to a VT before the suspend.
First thing I tried :) I had a notebook a few years ago that required this sort of workaround, but no luck with this trick on the ThinkPad.

Edit: I should clarify: suspend/resume works when switched to a virtual terminal, but immediately upon switching back to the X session, the screen becomes corrupt and the system hangs.

---

### Post by alastair on 2005-03-10
I've got a thinkpad as well - but use the "radeon" driver. Suspend seems to work OK.

---

