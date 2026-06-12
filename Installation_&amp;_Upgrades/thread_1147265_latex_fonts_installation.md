---
title: "latex fonts installation"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by chatterd on 2009-05-03
Hi!

Just wondering whether fonts such as kpfonts, iwona, etc, are part of the usual texlive distribution that comes with Jaunty. I think I've installed all of the texlive and also whatever is obtainable with "getnonfreefonts-sys" on my laptop, but still no kpfonts or iwona. I know kpfonts comes with MikTeX (complete) installations, but not with [k]ubuntu texlive distribution. Could anyone point me to a link that explains the steps for installation of these (nonstandard but very useful, and certainly quite beautiful) fonts, or an apt-get command that I've missed out which does the job smoothly?

Best regards.
    - D.

---

### Post by hugmenot on 2009-05-04
iwona seems to [be in texlive-fonts-extra]("http://packages.ubuntu.com/search?mode=filename&suite=jaunty&section=all&arch=i386&searchon=contents&keywords=iwona"). Don&#8217;t know about kpfonts.

---

### Post by chatterd on 2009-05-04
Thanks a lot. I see it is, but no kpfonts :(  It's funny, because ctan has them for sure, and they're public.

Any methods to install fonts missing from texlive2007?

Also, is there any indication that karmic will be packaged with the texlive2008 distribution? It'll be nice to work with the latest texlive version...

---

### Post by hugmenot on 2009-05-04
I installed Texlive 2008 manually. I&#8217;ve read that Texlive 2008 won&#8217;t be packaged with the new tlmgr package manager included, because that would collide with the packaging approach used in Debian/Ubuntu.

So I set out and used the net-based install script and installed a minimal set of packages into /opt. It works well. And I can use tlmgr to install and update the TeX packages directly from CTA N.

---

### Post by hugmenot on 2009-05-04
To manually install font packages from CTAN you basically have to follow the instructions from the README that comes with all of CTAN packages. Mostly you need to setup a personal TEXMF tree and the fonts go into specially designated subfolders therein. In the end you run mktexlsr on the tree and TeX will find the fonts. This would be the general way to do it.

---

### Post by chatterd on 2009-05-04
Thanks a lot!

---

