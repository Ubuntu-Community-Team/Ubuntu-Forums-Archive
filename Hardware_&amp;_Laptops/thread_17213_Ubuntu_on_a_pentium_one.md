---
title: "Ubuntu on a pentium one"
date: 2005-02-26
forum: Hardware &amp; Laptops
---

### Post by az on 2005-02-26
Typically, dissabling font antialiasing makes rendering faster.  It is a tradeoff that I like to make on older hardware.  It used to be easy, running debian Sarge/Sid.  
dpkg-reconfigure fontconfig
and enable bitmapped fonts.  i would then diable any other fonts.

This never worked for me in Ubuntu.

However, I read this:
[http://www.inittab.de/blog/2005/02/27#20050227_antialiased-fonts-suck](http://www.inittab.de/blog/2005/02/27#20050227_antialiased-fonts-suck)

Norbert Tretkowski rocks!

An ubuntuforum thread with five replies still takes a few seconds to load in firefox,but I can scroll down the page five times faster.

Quote:
Luckily, disabling antialiasing for fonts is quite easy. Add these lines to your /etc/fonts/local.conf file:

<match target="font">
  <edit mode="assign" name="antialias">
    <bool>false</bool>
  </edit>
</match>

You don't need to restart X, it's enough to restart your applications using antialiased fonts.

I reccommend this on older hardware, which is why I am posting this here in the hardware support forum.

---

