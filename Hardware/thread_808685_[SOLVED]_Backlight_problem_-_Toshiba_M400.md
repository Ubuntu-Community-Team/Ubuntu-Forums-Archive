---
title: "[SOLVED] Backlight problem - Toshiba M400"
date: 2008-05-26
forum: Hardware
---

### Post by martin5349 on 2008-05-26
Hello

I have very strange problem with backlight intensity setting on my Toshiba Portege M400. Buttons set the backlight correctly, but in a while backlight goes to value "3"(no matter what value it was set to). Same thing when setting backlight manually in toshset.

Thanks for support

Martin

---

### Post by martin5349 on 2008-05-27
I'll answer myself :-) this solves the problem :

Add this "blacklist video" in /etc/modprobe.d/blacklist then restart.

---

