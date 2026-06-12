---
title: "firefox will not config"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by xaegis on 2009-05-17
This is the error I'm getting. I am currently unable to surf the net using firefox! Seems like i'm caught in a loop where xulrunner needs firefox and firefox needs xulrunner.

Any suggestions?
 





```

user@home:~$ sudo apt-get -f install
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up xulrunner-1.9 (1.9.0.10+nobinonly-0ubuntu0.9.04.1) ...
/var/lib/dpkg/info/xulrunner-1.9.postinst: 5: /usr/bin/xulrunner-1.9: not found
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9.0.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of firefox-3.0-branding:
 firefox-3.0-branding depends on firefox-3.0 (= 3.0.10+nobinonly-0ubuntu0.9.04.1); however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox-3.0-branding (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
 firefox depends on firefox-3.0-branding; however:
  Package firefox-3.0-branding is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9.0.10+nobinonly-0ubuntu0.9.04.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-3.0 (= 3.0.10+nobinonly-0ubuntu0.9.04.1); however:
  Package firefox-3.0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 xulrunner-1.9
 firefox-3.0
 firefox-3.0-branding
 firefox
 xulrunner-1.9-gnome-support
 firefox-3.0-gnome-support
 firefox-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@home:~$
 
```

---

### Post by xaegis on 2009-05-17
ok I used the terminal command:

```

sudo dpkg --remove --force-remove-reinstreq --force-depends xulrunner-1.9

```

to uninstall xulrunner. Then I removed "xulrunner-1.9-gnome-support" using synaptic.

Removed Firefox using synaptic and then reinstalled everything starting with the xulrunner files using synaptic. 

Everything works perfectly now.

---

