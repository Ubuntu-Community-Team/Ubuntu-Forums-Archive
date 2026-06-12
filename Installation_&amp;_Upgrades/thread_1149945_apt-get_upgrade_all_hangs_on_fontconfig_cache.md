---
title: "apt-get upgrade all hangs on fontconfig cache"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by dirtside on 2009-05-05
When I run 'apt-get upgrade all', everything else works fine, except this one package, "xfonts-scalable".  I started running this about 23 hours ago, and it's still sitting there "Updating fontconfig cache".  I've had this problem before and I simply uninstalled the package (some font package that I didn't need).  However when I went to try to uninstall this one (xfonts-scalable), it told me it would also uninstall just about everything, so I don't feel safe trying that.

/etc/issue contains "Ubuntu 8.04.2" (Hardy Heron).  Here's a paste of what happens.

```
@@ 14:43:47 [mattw@argo - ~]$ sudo apt-get upgrade all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils indi kalzium kalzium-data kanagram kbruch kdeedu-data keduca khangman kig klatin klettres klettres-data kmplot kpercentage kstars kstars-data ktouch kturtle kverbos kvoctrain kwordquiz libbind9-30 libdns35
  libisccc30 libisccfg30 linux-386 linux-headers-386 linux-headers-generic linux-image-386 linux-image-generic linux-restricted-modules-386 vim vim-common vim-gui-common vim-runtime vim-tiny
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up xfonts-scalable (1:1.0.0-6ubuntu0.8.04.1) ...
Updating font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating category type1..
Updating category truetype..
Updating category cid..
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core /usr/share/fonts/truetype/ttf-sil-gentium /usr/share/fonts/truetype/thai /usr/share/fonts/truetype/ttf-lao /usr/share/fonts/truetype/ttf-arabeyes /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/truetype/ttf-devanagari-fonts /usr/share/fonts/truetype/ttf-gujarati-fonts /usr/share/fonts/truetype/ttf-bengali-fonts /usr/share/fonts/type1/gsfonts /usr/share/fonts/truetype/dustin /usr/share/fonts/truetype/ttf-tamil-fonts /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/truetype/ttf-punjabi-fonts /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/baekmuk /usr/share/fonts/truetype/ttf-kannada-fonts /usr/share/fonts/truetype/sjfonts /usr/share/fonts/truetype/ttf-telugu-fonts /usr/share/fonts/truetype/freefont /usr/share/fonts/truetype/ttf-oriya-fonts /usr/share/fonts/truetype/arphic /usr/share/fonts/truetype/ttf-malayalam-fonts /usr/share/fonts/truetype/kochi /usr/share/fonts/truetype/ttf-mgopen /usr/share/fonts/truetype/ttf-gentium /usr/share/fonts/truetype/msttcorefonts

```

If I CTRL-C out of it, then when I run apt-get again, it tells me it's confused and I have to clean it up, dpkg-reconfigure -a or something.  Eventually I end up seeing the above again.  Any idea what I can do to fix this permanently?

---

### Post by dirtside on 2009-05-12
Just an update, I left apt-get running for four days hanging on that "Updating fontconfig cache" line, and nothing changed.  I've had this happen with other font packages before, and just removed those packages; but trying to remove this package tells me it's going to uninstall Ubuntu entirely, which seems like a bad solution :)  If anyone knows the general cause of these "Updating fontconfig cache" errors, the information would be most appreciated.

...And now I have a worse problem, which is that I can't run apt-get because it tells me "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."  So I do that, and it tries to finish configuring "xfonts-scalable" again!  Which then, of course, hangs on "Updating fontconfig cache".  So now there's no way I can update anything, short of figuring out how to manually fix this error.  Help!

---

