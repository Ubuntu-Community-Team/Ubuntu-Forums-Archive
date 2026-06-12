---
title: "Xmms-scrobbler"
date: 2004-12-25
forum: General Help
---

### Post by LordSummerisle on 2004-12-25
Has anyone packaged the xmms-scrobbler plugin? I'm currently using Warty. I've tried installing the plugin .deb from Debian unstable, but it fails on some dependencies. Just looking to see if someone else had already installed this before I try to compile it myself.

---

### Post by inz on 2005-03-04
[QUOTE=LordSummerisle]Has anyone packaged the xmms-scrobbler plugin? I'm currently using Warty. I've tried installing the plugin .deb from Debian unstable, but it fails on some dependencies. Just looking to see if someone else had already installed this before I try to compile it myself.[/QUOTE]

getting these packages:
[http://ftp.se.debian.org/debian/pool/main/libi/libidn/libidn11_0.5.2-3_i386.deb](http://ftp.se.debian.org/debian/pool/main/libi/libidn/libidn11_0.5.2-3_i386.deb)
[http://ftp.se.debian.org/debian/pool/main/c/curl/libcurl3_7.13.0-2_i386.deb](http://ftp.se.debian.org/debian/pool/main/c/curl/libcurl3_7.13.0-2_i386.deb)
[http://ftp.se.debian.org/debian/pool/main/libm/libmusicbrainz-2.1/libmusicbrainz4_2.1.1-3_i386.deb](http://ftp.se.debian.org/debian/pool/main/libm/libmusicbrainz-2.1/libmusicbrainz4_2.1.1-3_i386.deb)
[http://ftp.se.debian.org/debian/pool/contrib/x/xmms-scrobbler/xmms-scrobbler_0.3.6-1_i386.deb](http://ftp.se.debian.org/debian/pool/contrib/x/xmms-scrobbler/xmms-scrobbler_0.3.6-1_i386.deb)

and installing them in that sequence by using dpkg -i %package.deb worked fine for me, well with xmms anyway. beep media player doesn't find the plugin which is rather annoying, but I might poke into that later.


UM. No, xmms doesn't load at all, gives me some pissy error message (libmikmod.so.2: cannot open shared object file: No such file or directory. Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed!), so I poked around unstable and found these two packages that I installed:

[http://ftp.se.debian.org/debian/pool/main/b/beep-media-player/beep-media-player_0.9.7-1_i386.deb](http://ftp.se.debian.org/debian/pool/main/b/beep-media-player/beep-media-player_0.9.7-1_i386.deb)
[http://ftp.se.debian.org/debian/pool/main/x/xmms-scrobbler/beep-media-player-scrobbler_0.3.7-1_i386.deb](http://ftp.se.debian.org/debian/pool/main/x/xmms-scrobbler/beep-media-player-scrobbler_0.3.7-1_i386.deb)

now beep-media-player works fine with audioscrobbler and all is right with the world, I don't want xmms anyway. :)

---

### Post by Ste on 2005-03-04
Compiling from source works fine.
The readme has all the required deps, so grab them from synaptic then compile.

[http://www.audioscrobbler.com/user/Ste-/](http://www.audioscrobbler.com/user/Ste-/)  :lol:

---

### Post by inz on 2005-03-04
I tried that, but it gave me tons of error, so I didn't have the stamina to try figuring that mess out. I prefer the .deb solution. ;)

---

### Post by tonderai on 2005-09-10
You can find the xmms-scrobbler in the following repository (add to /etc/apt/sources.list, then sudo apt-get update, then sudo apt-get install xmms-scrobbler)

## XMMS-Scrobbler
deb [http://www.sommitrealweird.co.uk/ubuntu/](http://www.sommitrealweird.co.uk/ubuntu/) hoary scrobbler
deb-src [http://www.sommitrealweird.co.uk/ubuntu/](http://www.sommitrealweird.co.uk/ubuntu/) hoary scrobbler

---

### Post by fearmd2916 on 2007-05-15
> **LordSummerisle said:**
> Has anyone packaged the xmms-scrobbler plugin? I'm currently using Warty. I've tried installing the plugin .deb from Debian unstable, but it fails on some dependencies. Just looking to see if someone else had already installed this before I try to compile it myself.


[music biology memory Bankruptcy insects](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/latin-porn.html)

---

