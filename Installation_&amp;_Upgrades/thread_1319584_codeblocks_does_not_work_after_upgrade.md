---
title: "code::blocks does not work after upgrade"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by froff on 2009-11-08
hello
code::blocks fails to start after system upgrade;
Anybody can help?

```

codeblocks: relocation error: /usr/lib/libcodeblocks.so.0: symbol _Z18wxSafeConvertWX2MBPKw, version WXU_2.8.2 not defined in file libwx_baseu-2.8.so.0 with link time reference

```

and after c::b removal and instalation:

```

codeblocks: symbol lookup error: codeblocks: undefined symbol: _Z12cbLoadBitmapRK8wxStringi

```

---

### Post by froff on 2009-11-08
sovled
Complete C::B reintallation helped!

---

### Post by spil on 2009-11-11
I have this fails too
```
codeblocks: relocation error: /usr/lib/libcodeblocks.so.0: symbol _Z18wxSafeConvertWX2MBPKw, version WXU_2.8 not defined in file libwx_baseu-2.8.so.0 with link time reference

```
This fails to start after upgrade 9.04->9.10
Installed package:
```
codeblocks-contrib_8.02svn5857-0ubuntu1~karmic_i386.deb
```

Reinstall not help :(

---

### Post by chimiasanchi on 2009-11-30
try this:

"go to Synaptic, chose libwxbase2.8-0 and click Package->Force Version to 2.8.10.1-1(jaunty-wx)"

[http://www.openframeworks.cc/forum/viewtopic.php?f=5&t=2945](http://www.openframeworks.cc/forum/viewtopic.php?f=5&t=2945)

I couldn't get that to work for me, even after completely removing the package and reinstalling with the openFrameworks install_codeblocks.sh script.

---

### Post by chimiasanchi on 2009-11-30
Also the same error when installing from PPA:

[http://launchpad.net/~simger/+archive/codeblocks](http://launchpad.net/~simger/+archive/codeblocks)

I'll try with all three versions of libwxbase2.8

---

