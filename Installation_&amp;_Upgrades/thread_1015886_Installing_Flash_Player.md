---
title: "Installing Flash Player?"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by nielscase on 2008-12-19
So I started installing it on my own so I could try to learn a little more about linux.  I got about halfway through and got stuck and was going to finish the next day then when I was using firefox it poped up something saying it would install the flash player for me so I tried it and here is my problem.

When I try and install with the update manager it says: You have 1 broken package on your system!

Use the "Broken" filter to locate it.

and then says:  E: /var/cache/apt/archives/nspluginwrapper_1.1.2-0ubuntu1_amd64.deb: trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386

also when I try to fix the broken package with the synaptic package manager it says the same thing.

I have tried to force overwrite but I'm not sure if I am doing it properly.

---

### Post by lovelyvik293 on 2008-12-19
you can use the command 
```

sudo apt-get install -f

```
To fix the broken packages.

---

### Post by nielscase on 2008-12-19
Did that and got the same thing:
Unpacking replacement nspluginwrapper ...
dpkg: error processing /var/cache/apt/archives/nspluginwrapper_1.1.2-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/nspluginwrapper_1.1.2-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by nielscase on 2008-12-19
I posted this in the wrong place can a mod move it to General help or the proper place Ty.

---

