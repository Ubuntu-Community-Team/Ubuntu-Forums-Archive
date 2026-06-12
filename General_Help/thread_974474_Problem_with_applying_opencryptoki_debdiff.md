---
title: "Problem with applying opencryptoki debdiff"
date: 2008-11-07
forum: General Help
---

### Post by dustice on 2008-11-07
Hi, I'm trying to install the tpm-tools package to get access to the TPM features of my laptop. However, opencryptoki, one of tpm-tools's dependencies, has this bug:
```
dpkg: error processing /var/cache/apt/archives/opencryptoki_2.2.6+dfsg-1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/opencryptoki/stdll/libpkcs11_sw.so', which is also in package libopencryptoki0
```

Which I traced to this bug report: [https://bugs.launchpad.net/ubuntu/+source/opencryptoki/+bug/262708](https://bugs.launchpad.net/ubuntu/+source/opencryptoki/+bug/262708)

In the bug report someone nicely provided a debdiff that fixes the bug, which I try to apply:
```
apt-get source opencryptoki
apt-get build-dep opencryptoki
cd opencryptoki-2.2.6+dfsg/
patch -p1 < ../opencryptoki*.debdiff
debuild -uc -cs
```

But then I get this error:
```
Makefile.am:2: required directory ./testcases does not exist
make[1]: *** [Makefile.in] Error 1
```

I haven't been able to find a record of this bug - am I applying the debdiff wrong? :( Or is this just yet another problem with the opencryptoki package?

---

