---
title: "Automounting problems SOLVED"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by WorLord on 2005-05-27
If anyone suddenly has automounting issues (USB drives / CD-Roms no longer automagically mount), but everything was working fine until just recently... I now know why.  

The Kernel in the last security update - linux-image-2.6.10-5-686-smp version 2.6.10-34**.1**, in my case - *totally breaks the automounting stuff*.  I downgraded to the stock kernel from the Hoary repository (version 2.6.10-34, without the .1) and everything is working magically again.  

Just an FYI for anyone out there beating their heads over restarting DBUS-1 or HAL and still not getting results.

---

### Post by denisliber on 2005-05-30
Very good, but I have  3 questions:

1. If I downgrade it will leave me with unsafe kernel ?
2. Can you please explane how to downgrade (i am a UBUNTU newbie :( )
3. I saw that this bug existing from late April at least, does some one knows when it will be fixed?

Thanks

---

