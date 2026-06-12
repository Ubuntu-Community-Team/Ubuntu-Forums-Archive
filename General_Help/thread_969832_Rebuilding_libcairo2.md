---
title: "Rebuilding libcairo2"
date: 2008-11-03
forum: General Help
---

### Post by MaskedMuchacho on 2008-11-03
Hi all,

i try to recompile libcairo2 with glitz support on Intrepid 64bit.
When i perform these steps:
```

mkdir cairo
cd cairo
apt-get source libcairo2
sudo apt-get build-dep libcairo2
sudo apt-get install fakeroot
cd cairo-1.8.0
gedit debian/rules

```

Change --disable-glitz to --enable-glitz , save and close gedit.

```
dpkg-buildpackage -rfakeroot
``` 

Then dpkg-gensymbols gives a warning that debian/libcairo2/DEBIAN/symbols don't fits to debian/libcairo2.symbols and prints this diff output:
```

--- dpkg-gensymbolsTXpHc1	2008-11-04 00:27:03.000000000 +0100
+++ dpkg-gensymbolsrRN4St	2008-11-04 00:27:03.000000000 +0100
@@ -70,6 +70,7 @@
  cairo_get_target@Base 1.2.4
  cairo_get_tolerance@Base 1.2.4
  cairo_get_user_data@Base 1.4.10
+ cairo_glitz_surface_create@Base 1.8.0-0ubuntu1
  cairo_glyph_allocate@Base 1.7.4
  cairo_glyph_extents@Base 1.2.4
  cairo_glyph_free@Base 1.7.4

```

And finally dh_makeshlibs returns error code 512


Would be great if someone could tell me what is going wrong here.

---

### Post by MaskedMuchacho on 2008-11-04
Ok i solved the problem.

Just added the missing symbol to debian/libcairo2.symbols

---

