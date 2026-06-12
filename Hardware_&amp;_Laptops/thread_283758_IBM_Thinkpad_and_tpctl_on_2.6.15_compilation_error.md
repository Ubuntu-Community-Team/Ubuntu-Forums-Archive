---
title: "IBM Thinkpad and tpctl on 2.6.15 compilation error"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by omri on 2006-10-24
Hello,
I've installed Ubuntu 6.06 couple of days ago on my IBM Thinkpad R50e
Works great out of the box - which is quite impressive for a laptop except one or two things.
I've fixed the sleep\suspend resume with some help on previous posts around here, works great now, but I have another problem:
I'm trying to install tpctl to control some more settings I found are editable via tpctl on google (changing charging precentage for start charging the battery) - a feature that is available on the windows I'm dual booting here with.

There has been a problem compiling the module, since there is no binary (none that I'm aware of)
I've compiled it with make-kpkg and I'm getting the while issuing "make-kpkg  modules":
```

/usr/src/modules/thinkpad/2.6/drivers/thinkpadpm.c:475: error: ‘pm_active’ undeclared (first use in this function)
/usr/src/modules/thinkpad/2.6/drivers/thinkpadpm.c:475: error: (Each undeclared identifier is reported only once
/usr/src/modules/thinkpad/2.6/drivers/thinkpadpm.c:475: error: for each function it appears in.)
/usr/src/modules/thinkpad/2.6/drivers/thinkpadpm.c:513: warning: ‘inter_module_register’ is deprecated (declared at include/linux/module.h:571)
/usr/src/modules/thinkpad/2.6/drivers/thinkpadpm.c: In function ‘thinkpadpm_exit’:
/usr/src/modules/thinkpad/2.6/drivers/thinkpadpm.c:522: warning: ‘inter_module_unregister’ is deprecated (declared at include/linux/module.h:572)
make[5]: *** [/usr/src/modules/thinkpad/2.6/drivers/thinkpadpm.o] Error 1
make[4]: *** [_module_/usr/src/modules/thinkpad/2.6/drivers] Error 2
make[4]: Leaving directory `/usr/src/linux-source-2.6.15'
make[3]: *** [default] Error 2
make[3]: Leaving directory `/usr/src/modules/thinkpad/2.6/drivers'
make[2]: *** [build-modules] Error 2
make[2]: Leaving directory `/usr/src/modules/thinkpad'
make[1]: *** [kdist_image] Error 2
make[1]: Leaving directory `/usr/src/modules/thinkpad'
Module /usr/src/modules/thinkpad failed.
Hit return to Continue?

```

Thanks alot,
Omri.

---

### Post by John.Michael.Kane on 2006-10-24
If your running dapper tpctl should be in the repo. search synaptic.
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=tpctl&version=dapper&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=tpctl&version=dapper&arch=i386)
[https://launchpad.net/distros/ubuntu/dapper/+source/tpctl](https://launchpad.net/distros/ubuntu/dapper/+source/tpctl)

---

