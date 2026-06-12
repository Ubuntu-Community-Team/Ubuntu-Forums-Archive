---
title: "make install-webconf"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by sunnywavez on 2009-03-06
Hi,
  I am trying to install, webinterface, but below is the error.
Please help to solve this problem, my apache2 is installed in default location "/usr/loca/apache2", and the httpd.conf is in directory  "/usr/local/apache2/conf"

make install-webconf
/usr/bin/install -c -m 644 sample-config/httpd.conf /etc/httpd/conf.d/nagios.conf
/usr/bin/install: cannot create regular file `/etc/httpd/conf.d/nagios.conf': No such file or directory
make: *** [install-webconf] Error 1

Please do help, i am a newbie using this to configure Nagios.:)

---

### Post by sunnywavez on 2009-03-06
> **sunnywavez said:**
> Hi,
  I am trying to install, webinterface, but below is the error.
Please help to solve this problem, my apache2 is installed in default location "/usr/loca/apache2", and the httpd.conf is in directory  "/usr/local/apache2/conf"

make install-webconf
/usr/bin/install -c -m 644 sample-config/httpd.conf /etc/httpd/conf.d/nagios.conf
/usr/bin/install: cannot create regular file `/etc/httpd/conf.d/nagios.conf': No such file or directory
make: *** [install-webconf] Error 1

Please do help, i am a newbie using this to configure Nagios.:)

Please do reply Friends... i am still confused....somebody suggest solution!!!

---

### Post by byb3 on 2010-08-25
I know this is an old post, but this is the first thing I found when I had the same issue.

Although I am no Linux expert, I believe the problem is with Nagios using an older installation directory for apache.  In this case it is using /etc/httpd/conf.d/ instead of /etc/apache2/conf.d/ where the apt-get installs it.

To fix this, you will need to cd into the nagios-3.2.1 directory and type this command (it worked for me anyhow):

```
cat Makefile | sed -e 's/httpd/apache2/' > Makefile
```You will then have to recompile by using ./configure, make all, make install, make fullinstall.

---

### Post by tonyyarusso on 2010-11-18
You would be much better off just installing the nagios3 package from the repositories and letting the package maintainers do the work for you.

---

### Post by willyika on 2011-01-04
hi byb3,
 
after i try on    cat Makefile | sed -e 's/httpd/apache2/' > Makefile
and recompile again,i only manage to run ./configure   , when run on make command (make all, make install,etc) i will get error No rule to make target 'all'. stop
 
kindly assist plz..
wille

---

