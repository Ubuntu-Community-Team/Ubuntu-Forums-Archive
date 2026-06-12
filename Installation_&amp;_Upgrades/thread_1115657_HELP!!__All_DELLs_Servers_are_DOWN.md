---
title: "HELP!!  All DELLs Servers are DOWN"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by jackal242 on 2009-04-04
I have a brand new Dell Mini 12.

It came with Ubuntu preinstalled and the sources.list points to Dells servers.   
```

$ cat sources.list
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
```

Dells servers are non-responsive.

So I can't do a apt-get update.

How do I work around this?

I tried changing all the servers names to us.archive.ubuntu.com and re-ran the sudo apt-get update and I got the following errors:

```
Err http://us.archive.ubuntu.com hardy/main Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/universe Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/multiverse Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/restricted Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/main Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/universe Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/multiverse Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/restricted Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-netbook-base/main Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-netbook-base/universe Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-netbook-base/multiverse Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-netbook-base/restricted Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-netbook-base/main Sources
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-netbook-base/universe Sources
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-netbook-base/multiverse Sources
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-netbook-base/restricted Sources
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-dell-mini/main Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-dell-mini/universe Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-dell-mini/multiverse Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-dell-mini/restricted Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-dell-mini/main Sources
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-dell-mini/universe Sources
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-dell-mini/multiverse Sources
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-dell-mini/restricted Sources
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-security/main Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-security/universe Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-security/multiverse Packages
404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-security/restricted Packages
404 Not Found [IP: 91.189.88.40 80]
```

---

### Post by jackal242 on 2009-04-04
Best part was when I called Dell and told them their servers are down and they instead asked me if I had a problem with my "bluetooth".


hahahahaha


FAIL!

---

