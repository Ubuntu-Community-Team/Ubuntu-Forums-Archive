---
title: "HoTTProxy Error, Help needed!"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by firehawk_1989 on 2009-10-12
I went through the community documentation on how to install HoTTProxy. Installed all of the perl modules etc... When I get to the point where I go to start the admin script I get this.

greg@greg-server:~/HoTTProxy-Source-0.24.0.0$ sudo perl HoTTProxy_Admin.pl

HoTTProxy Admin Daemon 0.24.0.0 - (c) 2005 Brian A. Blakley

Use of uninitialized value $path in pattern match (m//) at HoTTProxy_Admin.pl line 20, <DATA> line 16.
Cannot open config file HoTTProxy_Admin.conf.
Error: No such file or directory
Ending.


But when I do an ls, it shows that the file is there, and the file is not empty.

greg@greg-server:~/HoTTProxy-Source-0.24.0.0$ ls
cookies                      HoTTProxy_Admin.pl     ReleaseNotes_0.24.0.0.txt    HoTTProxy_Admin.pl~    UpgradeGuide_0.24.0.0.txt    HoTTProxy.conf         User.Attributes
HoTTProxy                    HoTTProxy.pl           www
HoTTProxy_Add-In_Filters.pl  InstallationGuide.pdf
HoTTProxy_Admin.conf         License.txt


I don't know anything about perl, so I don't know if it is something wrong with that, or what I have done wrong. But I have tried redoing the entire installation multiple times with the same result. I'm sure its something simple. I get the same type of error when trying to start the proxy too even though it's config file is there also. any help would be greatly appreciated! Thanks in advance!

---

