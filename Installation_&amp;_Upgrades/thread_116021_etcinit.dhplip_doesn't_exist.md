---
title: "/etc/init.d/hplip doesn't exist"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by MichaëlVD on 2006-01-11
Hello!

Since my printer didn't work anymore, I reinstalled everything that has cups or hplip or hpijs in its name.

I have a hp deskjet 5470.

Now, I'm supposed to restart hplip en cupsys, but there's no /etc/init.d/hplip file. How do I get it back.

(I have to admit that this is all my fault, I even deleted this file one, but that was before the reinstall.)

Thanks!

---

### Post by srt4play on 2006-01-11
A quick search in synaptic revealed /etc/init.d/hplip comes from the package hplip-base.

---

### Post by MichaëlVD on 2006-01-12
A new reinstall of those packages did the trick. Thanks.

---

