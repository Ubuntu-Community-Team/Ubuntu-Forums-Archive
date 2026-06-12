---
title: "Window manager hangs in Edgy"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by bonzini on 2007-01-09
Good people;

This problem comes and goes for me.  Yesterday and today, it is hanging around the office like a bad smell.

I'll be working away happily on my Toshiba A70 laptop running Edgy and suddenly the mouse continues to move but that's it.  Keystrokes don't produce input, windows don't scroll, etc etc.

If I'm quick, I can hit ctrl-alt-backspace and partway kill the window manager, but not all the way; window outlines and a few miscellaneous colours are still showing.  I can't get other console windows either.

So it looks like either the video driver (ATI RADEON driver, not fglrx though fglrx fails like this too) or Xorg are having their way with me.

No messages in the logs; things are quiet, then I push the big red button.

I see similar problems on the forums.  The closest I've seen to solutions relates to seeing someone suggest putting PCI=nommconf on the kernel boot flags.  I'm desperate, I'll try it, but I'd really like to know why that might work.  Any ideas?

Help!  Please?

---

### Post by bonzini on 2007-01-10
I rebooted last night with the PCI=nommconf option and had no subsequent hangs.

Same with today so far.  Maybe that's it.  I'll post my experiences again today, since I see people are reading the post.

---

### Post by bonzini on 2007-05-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/98999](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/98999) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This problem is solved in Feisty (don't know about Edgy) by setting noapic as a boot option.

My machine has been running fine, with no hangups, since April.

---

