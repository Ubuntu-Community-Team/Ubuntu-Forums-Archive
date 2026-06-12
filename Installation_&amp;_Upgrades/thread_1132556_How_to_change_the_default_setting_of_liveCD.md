---
title: "How to change the default setting of liveCD"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by Mr.Dust on 2009-04-22
Hello.

I made a my own LIVE iso file for USB memory stick using UCK. It works very good. 
However I faced some problems.

**1. Can't change the default keyboard layout. us => kr**
```
/tmp/remaster-root/usr/share/initramfs-tools/scripts/casper-bottom/19keyboard
kbd=us => kbd=kr
```It doesn't work.

**2. Can't change contents of /etc/apt/sources.list**
I changed the default repository from kr.archive.ubuntu.com to ftp.daum.net
In live environment it applied, But after installation the default repository came back to kr.archive.ubuntu.com
And I added some third party repositories, but they also applied only in live environment.

**3. Where can I change the default setting of LIVE CD? I can't find.**
which file should I edit?


Please help me.

---

### Post by lisati on 2009-04-22
If you've installed Ubuntu, you can use the System->Administration->Software sources menu item to choose the server. If you click on "other", you even get an option to automatically choose the best server.

---

### Post by Geochelone on 2009-04-22
I'm looking forward to learn something from this thread.

My current interest is to netinst Ubuntu from my trusted local repositories instead of Internet.

---

### Post by Mr.Dust on 2009-04-22
> **lisati said:**
> If you've installed Ubuntu, you can use the System->Administration->Software sources menu item to choose the server. If you click on "other", you even get an option to automatically choose the best server.
I already knew about that.
But I want to make a perfect iso for korean users. :)

---

### Post by Mr.Dust on 2009-04-22
For changing the default keyboard layout, from us, pc105 => kr, kr106

* Failed
/remaster-root/etc/default/console-setup &#50640;&#49436;
XKBMODEL="kr106"
XKBLAYOUT="kr"
XKBVARIANT="kr104"

* Failed
dpkg-reconfigure console-setup

* Failed
/usr/share/initramfs-tools/scripts/casper-bottom/19keyboard
kbd=us => kbd=kr


Humm.. which file shall I edit for the keyboard layout and sources.list?

---

### Post by Mr.Dust on 2009-05-15
About sources.list

I modified the sources.list.
and I check there is the modified one in my live cd.
However when I install using my own live, there's the default one, not the modified.

I think the installation system backups my sources.list to sources.list.save and makes the default sources.list.

How can I apply my modified sources.list?

---

