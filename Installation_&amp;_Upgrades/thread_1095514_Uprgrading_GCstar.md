---
title: "Uprgrading GCstar"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by jfalco on 2009-03-13
Hey all! I'm running Ubuntu Intrepid and GCStar v1.3.2 and I'm trying to upgrade to 1.4.3 I download the .deb and try to install it and get this...

Error: Cannot install 'libarchive-tar-perl'

So I head over to Synaptic and try to install libarchive-tar-perl and it gives me this:


to be removed>
   firefox
   and just about every other program on my system!!!

I'm not going to press OK to this!!!!

Any ideas

--Joe

---

### Post by ad_267 on 2009-03-13
Where did you get the .deb file from? Is it the .deb for Intrepid from getdeb?

I get this when I try to install libarchive-tar-perl on Intrepid:
```
Package libarchive-tar-perl is a virtual package provided by:
  perl-modules 5.10.0-11.1ubuntu2.2
You should explicitly select one to install.
E: Package libarchive-tar-perl has no installation candidate

```
So perhaps you could try installing perl-modules.

---

### Post by jfalco on 2009-03-13
> Where did you get the .deb file from? Is it the .deb for Intrepid from getdeb?

Yeah it's the .deb for Intrepid 64 from get deb

I have perl-modules installed but libarchive-tar-perl is not installed

---

