---
title: "HP6715b and Ubuntu"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by wizbit on 2007-07-27
I've got Ubuntu Feisty installed on my HP6715b and most things seem to work with the exception of the following things. I haven't seen/heard of many people running Ubuntu on this laptop so if anyone can help with the issues below I'll try and get some sort of HOWTO together for this laptop.

1. Sometimes when I boot up I get a black screen before GDM starts up. There's no way of dropping into a terminal window as the laptop freezes. Anyone come across this before?

2. The HP6715b comes with a fingerprint reader. I'd like to get this working if possible but at the moment I've no idea how. I've heard of "thinkfinger" and wondered if this might work on HP laptops. Any ideas?

3. Compiz Fusion kind of worked with the fglrx drivers for the ATI Xpress 1250 (I think thats the chipset) card but then went a bit funny (I kept losing titlebars and everything slowed down to a crawl), so I removed it all. Anyone managed to get compiz fusion working with this chipset? I've seen a few threads about this but nothing that says how to definitely get it to work correctly.

Just in case someone else has this laptop and is struggling with the wireless card, I sorted the problem out by doing the following:-

Download ndiswrapper from sourceforge - version 1.47 at the time.
Download the Windows XP Broadcom driver from HP's website for this laptop.
Compile ndiswrapper and use the driver from HP.
This got it working straight away.

If anyone else has this laptop and wants to share tips, let me know.

---

### Post by pinio on 2007-09-15
Hello

I have HP6715b.I install Ubuntustudio 7.04, upgrade to Gusty. Wireless working ok. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty) little howto.

---

