---
title: "Audacity Install Issues"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by Mrtrick8586 on 2009-04-06
I'm a newbie when it comes to ubuntu since I recently started using it. Since I'm just playing around with it (never going back to Windoze), I installed ubuntu 9.04 beta. I'm starting to get the hang of it, but I've been having trouble installing Audacity. I wasn't sure it was a bug or just something I did. Anyone mind helping resolve these issues?

Here is the output for add/remove.

E: libwxbase2.8-0: subprocess post-installation script returned error exit status 2
E: libwxgtk2.8-0: dependency problems - leaving unconfigured
E: audacity: dependency problems - leaving unconfigured
E: python-wxgtk2.8: dependency problems - leaving unconfigured

I tried re-installing it again in the terminal and here is what popped up. Apparently audacity has been installed, but the other things failed.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
audacity is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libwxbase2.8-0 (2.8.9.1-0ubuntu6) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libwxbase2.8-0 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libwxgtk2.8-0:
 libwxgtk2.8-0 depends on libwxbase2.8-0 (>= 2.8.9.1); however:
  Package libwxbase2.8-0 is not configured yet.
dpkg: error processing libwxgtk2.8-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of audacity:
 audacity depends on libwxbase2.8-0 (>= 2.8.9.1); however:
  Package libwxbase2.8-0 is not configured yet.
 audacity depends on libwxgtk2.8-0 (>= 2.8.9.1); however:
  Package libwxgtk2.8-0 is not configured yet.
dpkg: error processing audacity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-wxgtk2.8:
 python-wxgtk2.8 depends on libwxbase2.8-0 (>= 2.8.9.1); however:
  Package libwxbase2.8-0 is not configured yet.
 python-wxgtk2.8 depends on libwxgtk2.8-0 (>= 2.8.9.1); however:
  Package libwxgtk2.8-0 is not configured yet.
dpkg: error processing python-wxgtk2.8 (--configure):
 dependency problemsNo apport report written because the error message indicates its a followup error from a previous failure.
                                              No apport report written because the error message indicates its a followup error from a previous failure.
                                                                        No apport report written because MaxReports is reached already
                                                       - leaving unconfigured
Errors were encountered while processing:
 libwxbase2.8-0
 libwxgtk2.8-0
 audacity
 python-wxgtk2.8
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

