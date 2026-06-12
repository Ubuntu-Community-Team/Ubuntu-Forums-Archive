---
title: "php-gd is missing features"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by bwooster47 on 2009-08-24
Well, it looks like the Debian package php-gd does not fully support all the PHP features, such as the function imageantialias.

[http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu](http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu)
and
[http://www.hostingforum.ca/804602-php-problem-gd-library.html#post1898625](http://www.hostingforum.ca/804602-php-problem-gd-library.html#post1898625)
describe the situation, and looks like the only solution is somewhat tedious - have to download PHP source, and then compile it by hand.

Is there some other easier method? Possibly some non-Debian blessed source that compiles PHP correctly so that all the GD functions in the embedded gd work correctly?

Installing from source means cannot use apt-get for any php related install anymore, which means cannot get updates that way, etc, so it is a somewhat painful approach.

---

### Post by Smartin on 2010-02-12
> **bwooster47 said:**
> Well, it looks like the Debian package php-gd does not fully support all the PHP features, such as the function imageantialias.

[http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu](http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu)
and
[http://www.hostingforum.ca/804602-php-problem-gd-library.html#post1898625](http://www.hostingforum.ca/804602-php-problem-gd-library.html#post1898625)
describe the situation, and looks like the only solution is somewhat tedious - have to download PHP source, and then compile it by hand.

Is there some other easier method? Possibly some non-Debian blessed source that compiles PHP correctly so that all the GD functions in the embedded gd work correctly?

Installing from source means cannot use apt-get for any php related install anymore, which means cannot get updates that way, etc, so it is a somewhat painful approach.

bwooster47,

I'm in the same spot.

What did you decide to do?

:-)

S

---

