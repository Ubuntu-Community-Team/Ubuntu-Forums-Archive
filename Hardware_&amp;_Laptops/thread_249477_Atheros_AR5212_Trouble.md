---
title: "Atheros AR5212 Trouble"
date: 2006-09-02
forum: Hardware &amp; Laptops
---

### Post by AndyCR on 2006-09-02
I am having trouble with an Atheros AR5212 Wireless card built into my Toshiba Satellite M35X using Ubuntu Dapper.

Sometimes it works. It just works. When it does, it's amazing - it's much faster than it is in Windows, and installing software is a breeze.

I'm emphasizing when it does. At random times, it will choose not to work. Actually, it's more like at random times, it will choose to work. The rest of the time, it will in firefox say "Looking up soandso.com..." for several seconds, then go to "Connecting to soandso.com..." and hang on a timeout after several minutes. In apt-get, sometimes it works, most of the time it gives an error of "404 not found." for packages I try to install.

Thanks in advance.

(My apolagies for double posting, I accidentally posted it in the wrong forum before)

---

### Post by mariner09 on 2006-09-03
Instead of relying on browsers or ather apps to determine your wireless status, do you have any visual or functional aids installed, like networkmanager?

What happens when you ping your gateway when the browser is erroring out?

What does ifconfig show when your browser is unresponsive?

Lots of things to look at in getting to the root of the matter...

---

