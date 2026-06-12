---
title: "problems with configuring sound"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by chopeen on 2005-05-02
Motherboard: Gigabyte GA7N400S-L
Soundcard: integrated
Ubuntu: 5.04

After I installed Ubuntu I couldn't play MP3 files. I tried XMMS and Amarok. 

I configured my system accoording to the tips posted here <[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)>.

XMMS works fine. Amarok still does not.

---

### Post by gunnyman on 2005-05-02
try sudo apt-get install amarok-engines
this downloads and installs both the xine and gstreamer engines for amarok,
After that, start amarok and go to settings/configure amarok/engines.
You should see engines in a drop down box. Pick either gstreamer or xine.
They both should work.

---

### Post by chopeen on 2005-05-03
Thanks for your reply.

I've already had amarok-engines installed. My problem was caused by the lack of gstreamer0.8-mad package.

More about this can be found here:
[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

---

