---
title: "ubuntu on T43"
date: 2013-07-01
forum: Hardware
---

### Post by ikki_72 on 2013-07-01
hi,

any recent success with T43 laptop especially 13.04 in terms of wireless, video (ati), and sound?

---

### Post by tgalati4 on 2013-07-01
I have Jaunty running on my T43p.  I plan to upgrade soon.  I will probably set up triple boot:  WinXP (for legacy connection to audio equipment), Jaunty (because it works), and Linux Mint Mate 14 (based on 12.10).

Let us know what works and what doesn't.

---

### Post by ikki_72 on 2013-07-01
apparently radeon mobility caused radeon driver to restarts randomly which causes the hang on debian 6, debian 7, ubuntu 13.04. 

on ubuntu 13.04, removing x11 driver for radeon (couldn't remember package name, just find it with 'dpkg --get-selections | grep radeon') settles that issue but still quite slow compared on debian 6 & 7.

still do not figure out about wireless connection disconnecting, reconnecting and sound issue

same ati radeon issue on win 7 but can be solved by deleting ati mobility driver from windows update, no issues with wireless and sound though

---

### Post by ikki_72 on 2013-07-01
> **tgalati4 said:**
> I have Jaunty running on my T43p.  I plan to upgrade soon.  I will probably set up triple boot:  WinXP (for legacy connection to audio equipment), Jaunty (because it works), and Linux Mint Mate 14 (based on 12.10).

Let us know what works and what doesn't.

yours with ati or intel gpu?

would i still be able to download jaunty?

---

### Post by tgalati4 on 2013-07-02
The T43p has an ATI radeon FireGL.  It's an upgraded video card from the standard T43.  I had no problems with it under Jaunty with the open radeon driver, but I have not yet tried a Live CD of Linux Mint 14 Mate.  If it boots and works OK, then I will install it on its own partition.  You can find Jaunty under the older Ubuntu archives, but it's old and not supported.  It's been a solid distro on this old machine.  I even recompiled the kernel to get undervolting to work, which increased battery life to nearly the same as WinXP.  I used a custom *thinkfan* profile to reduce the noisy fan--a common complaint with these older thinkpads.

Wireless was an intel abg card and it worked fine out of the box.  Sound was an Intel ICH chipset which also worked fine out of the box.

I find this link helpful for installing linux on thinkpads:  [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

---

