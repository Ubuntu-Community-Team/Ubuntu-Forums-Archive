---
title: "Kernel Sources RPM???"
date: 2005-01-21
forum: Installation &amp; Upgrades
---

### Post by knowtown on 2005-01-21
I just made the jump from Suse 9.1 to Ubuntu and I love it. I could never get my wireless working right in Suse and in Ubuntu it was automatic. The problem I am having in Ubuntu is getting my sound working. In Suse I could install the 4front technologies oss soundcard driver and feel the love. Unfortunately when I try the same thing with Ubuntu the driver will not compile. A quick check with the 4Front tech support and they tell me I need to install the Kernel source RPM in order for the driver to compile correctly.  

I did a search in synaptic and could not find it.  Does anyone know how I can get the Kernel Source RPM installed?

Thanks,

James

"blessed are the poor, for they shall use Linux"

---

### Post by az on 2005-01-21
Forget rpms, think debian packages - deb

the package name is linux-source

apt-get install linux-source-2.6

or just use synaptic.

You probably will have a better time just using the linux-headers instead.  Use 
/usr/src/linux-headers-2.6.8-1(whatever your kernel is) as your kernel source tree when asked...

---

### Post by knowtown on 2005-01-21
Thanks so much azz!!

I have installed the headers so I will point the oss install to that location later and see if it works.

---

