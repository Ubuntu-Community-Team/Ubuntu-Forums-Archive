---
title: "help using preseed to choose mirror"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by ScottTFrazer on 2009-03-02
I'm attempting to set up a preseed disc for server installations, and I'd like to point the mirror to something other than us.archive.ubuntu.com.

Here's what I've got now:
```

# Mirror Settings
d-i mirror/http/hostname string astromirror.uchicago.edu
d-i mirror/http/directory string /ubuntu
choose-mirror-bin mirror/http/directory string /ubuntu/
choose-mirror-bin mirror/http/hostname string astromirror.uchicago.edu
choose-mirror-bin mirror/http/mirror select astromirror.uchicago.edu
d-i apt-setup/use_mirror boolean true
d-i mirror/suite string intrepid
d-i apt-setup/restricted boolean true   
d-i apt-setup/universe boolean true
d-i apt-setup/services-select multiselect security
d-i apt-setup/security_host string security.ubuntu.com
d-i apt-setup/security_path string /ubuntu
choose-mirror-bin       mirror/http/proxy       string

```

It's mostly working, but the path string doesn't seem to be taking, I keep getting this:

```

deb http://astromirror.uchicago.edu/(null) intrepid multiverse
deb-src http://astromirror.uchicago.edu/(null) intrepid multiverse
deb http://astromirror.uchicago.edu/(null) intrepid-updates multiverse
deb-src http://astromirror.uchicago.edu/(null) intrepid-updates multiverse

```

Anyone know what I'm doing wrong?

---

### Post by bazzer on 2009-03-13
Wouldn't be this would it?
```
base-config apt-setup/hostname string www.emdebian.org
base-config apt-setup/directory string /grip
```
from [http://www.emdebian.org/d-i/lenny/preseed.cfg]("http://www.emdebian.org/d-i/lenny/preseed.cfg")

---

### Post by ScottTFrazer on 2009-03-16
> **bazzer said:**
> Wouldn't be this would it?


Nope, still getting "/(null)" at the end of my repository paths.

Thanks for the try, though.

---

### Post by bazzer on 2009-03-18
[http://awtrey.com/files/autodebian/autodebian.seed]("http://awtrey.com/files/autodebian/autodebian.seed") seems to think that 
```
d-i  mirror/http/directory		string  /debian/
d-i  mirror/http/hostname		string  http.us.debian.org
d-i  mirror/http/mirror			select  http.us.debian.org
```
is the way?

---

