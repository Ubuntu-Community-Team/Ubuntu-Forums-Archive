---
title: "T43p and Fingerprint"
date: 2005-12-14
forum: Hardware &amp; Laptops
---

### Post by viz_e on 2005-12-14
Hello,
I am trying to enable the fingerprint reader on my Thinkpad T43p. I followed carefully some guides, like 

[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader")

Everything worked without problem (I had to install some extra packages, though), the Sample files works, but I cannot use it for authenticating sudo or kdm, for example. This is the output of my /var/log/auth0.log:

Dec 14 14:36:14 localhost sudo: PAM [dlerror: /lib/security/pam_bioapi.so: undefined symbol: rpl_malloc]
Dec 14 14:36:14 localhost sudo: PAM adding faulty module: /lib/security/pam_bioapi.so
Dec 14 14:38:16 localhost sudo:      viz : TTY=pts/1 ; PWD=/home/viz/Desktop/pro ; USER=root ; COMMAND=/usr/bin/gedit DEBIAN/control
Dec 14 14:38:16 localhost sudo: PAM unable to dlopen(/lib/security/pam_bioapi.so)
Dec 14 14:38:16 localhost sudo: PAM [dlerror: /lib/security/pam_bioapi.so: undefined symbol: rpl_malloc]
Dec 14 14:38:16 localhost sudo: PAM adding faulty module: /lib/security/pam_bioapi.so
Dec 14 14:39:36 localhost sudo:      viz : TTY=pts/1 ; PWD=/home/viz/Desktop ; USER=root ; COMMAND=/usr/bin/dpkg -i pro.deb
Dec 14 14:39:36 localhost sudo: PAM unable to dlopen(/lib/security/pam_bioapi.so)
Dec 14 14:39:36 localhost sudo: PAM [dlerror: /lib/security/pam_bioapi.so: undefined symbol: rpl_malloc]
Dec 14 14:39:36 localhost sudo: PAM adding faulty module: /lib/security/pam_bioapi.so
Dec 14 14:39:59 localhost sudo: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=pts/1 ruser= rhost=  user=viz

Any idea? Thx a lot!!

P.S. I am running Kubuntu Breezy

---

### Post by viz_e on 2005-12-15
Nobody has an idea? My guess is that it should have something to do with modules link and so on (ldd, ldconfig), but I am not really expert in this kind of stuff. ;)

---

### Post by hady on 2006-11-04
that same HOWTO has a notice regarding the 'rpl_malloc' error...don't know if it's the same error u're getting though....

---

