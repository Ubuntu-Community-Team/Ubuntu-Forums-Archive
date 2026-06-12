---
title: "Grub error: out of disk"
date: 2010-10-12
forum: Hardware
---

### Post by shakyj on 2010-10-12
I have a compaq nx7400 which I replaced the hard drive on with a 250GB 7200 RPM drive. I installed 10.04 on it. Then I updated to 10.10. When I installed 10.04 I started getting the following error before boting "error: out of disk" but the OS would still boot.

Since I updated to 10.10 I have also been getting the error "error: no suitable mode found" although it still boots.

Whilst I am not currently having any problems I would still like to find out why it is doing this.

I have tried the script found at [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) but it means nothing to me. :lol:

Not sure if this is the right place to post it. But it's both a laptop and a disk error so I guessed.

---

### Post by Werm on 2010-10-12
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

As for the suitable media error it's a graphics setting.

The file you posted shows:

if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480

Change gfxmode to whatever you're running normal (something your monitor can support, too).

/boot/grub/grub.cfg

Do this off a live CD/USB and as root.

If you upgrade grub though, in the future, this will change back.

---

### Post by shakyj on 2010-10-13
Thanks loads for the help. I will try that when I get home and add a solved if I'm successful :)

---

