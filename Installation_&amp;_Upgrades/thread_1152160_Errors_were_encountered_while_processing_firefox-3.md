---
title: "Errors were encountered while processing: firefox-3.0"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by BetterSense on 2009-05-07
I currently can't use firefox ever since the last upgrade I ran froze my system. Details on that in this

thread.[http://ubuntuforums.org/showthread.php?t=1150315](http://ubuntuforums.org/showthread.php?t=1150315)

Now the only thing I know to do was run apt-get upgrade, but it fails with a bunch of errors, and firefox will not run.  I'm using konqueror now.  I do not know what to do to fix my packages. Can anybody help me recover my system?

```

chaz@brutus:~$ sudo apt-get upgrade
[sudo] password for chaz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
10 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up xulrunner-1.9 (1.9.0.10+nobinonly-0ubuntu0.9.04.1) ...
Bus error
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9.0.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-branding:
 firefox-3.0-branding depends on firefox-3.0 (= 3.0.10+nobinonly-0ubuntu0.9.04.1); however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox-3.0-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
 firefox depends on firefox-3.0-branding; however:
  Package firefox-3.0-branding is not configured yet.
dpkg: error processing firefox (--configure):
 dependenNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                   No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                    No apport report written because MaxReports is reached already
                                         No apport report written because MaxReports is reached already
                                                                                                       No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                                                                                                          cy problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9.0.10+nobinonly-0ubuntu0.9.04.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-3.0 (= 3.0.10+nobinonly-0ubuntu0.9.04.1); however:
  Package firefox-3.0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Setting up libamrnb3 (7.0.0.2-0.1medibuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libamrnb3 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libamrwb3 (7.0.0.3-0.0medibuntu1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libamrwb3 (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mplayer:
 mplayer depends on libamrnb3; however:
  Package libamrnb3 is not configured yet.
 mplayer depends on libamrwb3; however:
  Package libamrwb3 is not configured yet.
dpkg: error processing mplayer (--configure):
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
 libamrnb3
 libamrwb3
 mplayer
E: Sub-process /usr/bin/dpkg returned an error code (1)
[1]+  Bus error               firefox
chaz@brutus:~$ 
chaz@brutus:~$ 

```

---

### Post by BetterSense on 2009-05-07
If I try to use the graphical update manager, it makes me enter my password and then it fails with a dialog saying something about a line in iscan-interpreter, and now it says my system is up-to-date, even though it didn't do anything.

---

### Post by BetterSense on 2009-05-07
I cannot run apt-get upgrade, apt-get remove firefox, or apt-get dist-upgrade, without similar errors showing. I guess I could reinstall the whole system, but shouldn't dist-upgrade do the same thing? I don't understand what's broken.

---

### Post by alikbalik on 2009-06-16
i have the same problem.
Errors were encountered while processing:
 xulrunner-1.9
 xulrunner-1.9-gnome-support
 firefox-3.0
 firefox-3.0-gnome-support
 firefox-gnome-support
 firefox-3.0-branding
 firefox

---

### Post by Noob Programmer on 2009-06-16
I had the same issue. I removed xulrunner then installed firefox since xulrunner also removed the current firefox with it.

I was able to use the Synaptic Package Manager but I think the commands are:
```
apt-get uninstall xulrunner-1.9
apt-get install firefox firefox-3.0-gnome-support
```

You might want to also install any other files that were also removed with xulrunner well you are at it.

---

