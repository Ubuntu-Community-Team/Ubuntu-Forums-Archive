---
title: "Installing ndiswrapper when not on the internet"
date: 2005-11-30
forum: Hardware &amp; Laptops
---

### Post by harisund on 2005-11-30
Hello 
 
I installed Ubuntu 5.10 on my Dell Laptop, and everything works fine !

I want to get my wireless to work. I have a Linksys WPC 11 ver 3 card, which is listed as compatible and working in the ndiswrapper wiki. 
( [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L) and scroll a little down) 

However, I need ndiswrapper. Is it already installed in Ubuntu?. Since I don't have a wired internet, apt-get is out of the question. I am not sure I can get the source and compile, since Ubuntu doesn't come with development tools before an apt-get install build-essentials, right? 

Any suggestions? Should I download the .deb package of ndiswrapper and do a dpkg -i ? 

Thanks !

---

### Post by az on 2005-11-30
ndiswrapper-utils is on the cd.  You do not need to be on the net to install it.  You are good to go.

Build-essential is also on the cd, but the kernel was build with a different compiler than the on eon the cd. If you need to build kernel modules, you need to install gcc-3.4 from the internet.

Everything you need to get onto the net is already there, though.

---

### Post by harisund on 2005-11-30
really? Wow.. don't know why I didn't think of that.. 

so what do I do

*apt-get install ndiswrapper-utils* ??

Will try that as soon as I get back home.. thanks !

---

