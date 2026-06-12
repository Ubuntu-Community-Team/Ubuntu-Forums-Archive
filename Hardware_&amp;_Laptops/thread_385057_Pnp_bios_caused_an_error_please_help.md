---
title: "Pnp bios caused an error please help"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by jputman01 on 2007-03-15
Everyone, i am having an issue with 6.10 and vista dual boot system. My laptop is hp dv6000, AMD X2, nvidia. I was having major issues running the live cd also but finally got thru it and now everything is partitioned and have ubuntu on my second partition. 

The problem is I only get about 5 minutes out if before it freezes up. 

Sometimes my touchpad works and sometimes it doesnt.

Sometimes when I type something, for example, the letter "A" it will show up as "AAAAAAA" even though I only tapped the key once.

The only think I see is a quick flash while the system is loading that says "pnp bios have caused an error..." but cant read the rest because it goes too fast. 

can anyone help me, any ideas would be greatly appreciated. I was using ubuntu 6.10 on my desktop and it worked great but now on my laptop I am having issues.

---

### Post by teaker1s on 2007-03-15
welcome, you are in fact not alone with your DV6000, we have quite a few threads regarding them and I both have one and started this wiki page, I'd have a read as it covers usual issues
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")


these may help
```
gksudo synaptic
``` 
search

ksynaptics  (kde)
gsynaptics (gnome)

or

qsynaptics (general for config of synaptic)

panel
system>administration>preferences>keyboard
you can alter repeat rate etc

---

### Post by jputman01 on 2007-03-15
thank you, i did not check the wiki but will do so now

---

### Post by teaker1s on 2007-03-15
see my previous post I've updated it:popcorn:

---

### Post by jputman01 on 2007-03-15
is any of this because of the vista operating system, what if i ditched vista and put XP on? I had xp and ubuntu on my desktop without and issue and for the 4 days I have been using vista I have come to completely hate it. Would that fix anything?

---

### Post by jputman01 on 2007-03-15
what if i download a prior bios, a friend of mine has a dv5000, turion 64, ati chip and his works just fine without all the glitches i seem to be having. could i find out what bios he is using and get it from hp.com?

---

### Post by teaker1s on 2007-03-15
stick with later bios, also you need to use a vista boot loader and not grub, search forums for vista and vista duel boot

---

### Post by jputman01 on 2007-03-15
using vista bootloader will fix my plug and play error issue?

---

### Post by teaker1s on 2007-03-16
sorry my mix up-if you use vista duel boot then you want to use vista boot loader from what I read.
xp duel boot use grub.

do you have a fault code with this error?
[http://bioscentral.com/postcodes/phoenixbios.htm]("http://bioscentral.com/postcodes/phoenixbios.htm")

have you tried the various boot options like NOAPIC NOAPCI

---

