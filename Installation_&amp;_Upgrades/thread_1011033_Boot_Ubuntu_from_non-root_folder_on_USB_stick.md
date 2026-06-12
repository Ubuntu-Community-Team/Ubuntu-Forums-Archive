---
title: "Boot Ubuntu from non-root folder on USB stick"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by mn_lay on 2008-12-14
I want to create multi-boot USB drive with several live distros. So I moved Ubuntu (Interpid, x86) Live CD/USB contents to /boot/ubuntu/ folder on my USB stick.

It fails to finish boot, and BusyBox shell prompt appears.

Maybe the reason is same as this:
[http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=printview&t=8498&start=0](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=printview&t=8498&start=0)

So, anybody knows how to boot it without hacking kernel/initrd? Because it's not convenient to re-edit it each time new kernel arrives.

P.S. Slax Linux has nice option which allows to specify distro location: **kernel /boot/slax/vmlinuz from=/boot** (**slax** folder is searched automatically)

---

