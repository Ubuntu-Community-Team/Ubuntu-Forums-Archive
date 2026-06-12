---
title: "No resolution above 800x600 with unichrome on laptop"
date: 2010-01-09
forum: Hardware
---

### Post by lateral on 2010-01-09
Hi all. I'm (obviously) new to Ubuntu, and Linux in general. A friend hooked me up with 9.10 Karmic back in November, and everything's been going fine apart from this problem with resolution. 

I can't set the res higher than 800x600. I know my laptop - an old Iqon LM7W - is capable of higher resolutions because I could use them under Windows XP. Apparently I've got an S3 Unichrome Pro P4M800 card, which I believe should use the Openchrome driver. 

However, when I go into xorg.conf and switch the 'vesa' driver for 'openchrome', Ubuntu opens the login screen in 1024x768 fine, then switches to a dodgy-looking 800x600 when it gets to desktop, with the desktop area much larger than the screen itself (so I can't see the right-hand and lower portions of the desktop). If I try and use Display Manager to change the res from 800x600 to any other setting while it's like this, all I get is a fuzzed-up mess of colours and I have to ctrl-alt-f5 out and reset xorg.conf's driver back to vesa. 

This is really irritating me, cos in all other respects Ubuntu seems much better than XP was, and I really respect the whole philosophy behind it, but I can't play any games - they just try and set a different resolution resulting in fuzzed-up mess as above - and 800x600 just looks really primitive. 

I should post some log info and such here, I know, but I'm not sure which ones, so if anyone's willing and able to help let me know what to put up and I'll do so pronto. 

Thanks in advance.

---

