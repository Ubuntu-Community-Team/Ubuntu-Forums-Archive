---
title: "[SOLVED] Lenovo R61i issues (fan &amp;amp; diode)"
date: 2008-10-21
forum: Hardware
---

### Post by robgr85 on 2008-10-21
Hi!

I've just installed kubuntu 8.04 on my brand new laptop, most of the things seems to work fine, but there are still two issues about interraction between my Lenovo R61i (NG1F7PB) laptop and the OS. 

1. My cpu fan is working instantly all the time (even if there is no cpu load [according to the 'top' program]). That is the reason why I started that thread, and I would really appreciate Your help.

2. My wireless network is working ok, but the led network indicator is all time off (is there any way to make it working as it should?)... (that is minor problem) any sugestions about that are also welcome.

Cheers,
Robert

---

### Post by Dougie187 on 2008-10-21
I don't know about your fan, but for your wireless led, you can probably install the linux-backports package, I actually think its called linux-restricted-backports. You can also check out [www.thinkwiki.org](www.thinkwiki.org) for any help on your laptop type.

---

### Post by robgr85 on 2008-10-21
> **Dougie187 said:**
> I don't know about your fan, but for your wireless led, you can probably install the linux-backports package, I actually think its called linux-restricted-backports. You can also check out [www.thinkwiki.org](www.thinkwiki.org) for any help on your laptop type.

thanks for Your answer. Upgrading to the newest kernel (by dist-upgrade) solved the fan issue. I will try suggested linux-backports.

---

