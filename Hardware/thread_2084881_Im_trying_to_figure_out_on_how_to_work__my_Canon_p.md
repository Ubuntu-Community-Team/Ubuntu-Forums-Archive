---
title: "Im trying to figure out on how to work  my Canon pix max430 printer?"
date: 2012-11-16
forum: Hardware
---

### Post by chrissy.millichamp on 2012-11-16
How do we install or use canon pix max430  in Ubuntu 12.10?

---

### Post by ahallubuntu on 2012-11-16
I have a Pixma 420 that is supported directly by Canon (Europe site) in Ubuntu 10.04.  I have not fully installed 12.04 LTS yet, but it was automatically detected in 12.04.

I found a Debian driver for the 430 on Canon's Europe site.  This may not work automatically but you may be able to build it from the source in there:

[http://www.canon-europe.com/Support/System/Search.aspx?TcmUri=tcm:13-913553&SearchType=3](http://www.canon-europe.com/Support/System/Search.aspx?TcmUri=tcm:13-913553&SearchType=3)

---

### Post by BicyclerBoy on 2012-11-16
Far easier to use a maintained source ppa:

[https://launchpad.net/~michael-gruz/+archive/canon-trunk?field.series_filter=quantal](https://launchpad.net/~michael-gruz/+archive/canon-trunk?field.series_filter=quantal)

Likely but not guaranteed your printer is in there..
Is this the same model "mx-430" ??

If your printer has a scanner then install
scangearmp-mx420 & scangearmp-common (the mx420 seems the closest model).

---

