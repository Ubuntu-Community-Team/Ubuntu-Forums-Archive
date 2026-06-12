---
title: "trying to ./configure &quot;monodevelop-0.16&quot;"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by animeh on 2009-09-04
I have done so far:

(step 1) sudo apt-get install mono-devel build-essential mono-gmcs libmono-dev libpango1.0-dev libgtk2.0-dev libgtksourceview2.0-cil libgecko2.0-cil monodoc libmono-system-runtime2.0-cil libmono-cairo2.0-cil gettext

(step 2) wget [http://go-mono.com/sources/monodevelop/monodevelop-0.16.tar.bz2](http://go-mono.com/sources/monodevelop/monodevelop-0.16.tar.bz2)

(step 3) bunzip2 monodevelop-0.16.tar.bz2

(step 4) tar xvf monodevelop-0.16.tar

(step 5) cd monodevelop-0.16

(step 6) ./configure –prefix=`pkg-config –variable=prefix mono`
     (error message) configure: error: invalid variable name: –prefix

Can anyone help me with this error?, I would like to download the software to learn.

---

### Post by animeh on 2009-09-05
I have found monodevelop 2.0 and installed it.

---

