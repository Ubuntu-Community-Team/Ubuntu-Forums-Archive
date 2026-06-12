---
title: "No sound in toshiba satellite U200 SP7011"
date: 2009-03-09
forum: Hardware
---

### Post by ap99999 on 2009-03-09
Hi All,

I can not get sound working in a laptop toshiba satellite U200 SP7011 running Ubuntu 8.10. The sound card model appears to be this:

$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I would like to explain how I got to this point. I originally had a dual
boot in this machine XP and Ubuntu (it was Ubuntu 7.04). The sound worked fine at the beginning, but then I noticed something odd. This laptop has a hardware volume control, and if I reduced the volume to zero in Windows, then when I booted into Ubuntu there was no sound. I can always boot back in Windows move the volume up reboot into Ubuntu and the sound worked fine.

I was working like this for a while, but I eventually decided to get rid of Windows, so I formated the windows partition to be used by Ubuntu 7. However I forgot about this sound issue and the volume was set in zero when i did this. I haven't been able to move it up back since then.

I tried upgrading to Ubuntu 8.10 but it did not help. I have looked around in the forums, I found some threads of people with issues getting sound working in toshiba laptops, but not the same issue. I would appreciate any hints or pointers. Thanks in advance for your time.

andres

---

### Post by LLudovic on 2010-09-26
Hi There,
I've got the same issue, did you find a fix?

---

