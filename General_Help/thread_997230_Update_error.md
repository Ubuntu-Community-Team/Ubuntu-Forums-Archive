---
title: "Update error"
date: 2008-11-29
forum: General Help
---

### Post by Oliver.BS on 2008-11-29
I keep getting this error when trying to update my system 

Run a partial upgrade, To install as many updates as possible 

This can be caused by:

A previous upgrade didnt complete
Problems with some of the installed software
Unofficial software packages not proved by ubuntu 
normal changes or a pre-release version of ubuntu 

Any ideas ?

---

### Post by falcon61102 on 2008-11-29
Have you previously tried updating your system and had it fail for any reason?

Also, does it give you the option to do a full update or to start again?

---

### Post by Oliver.BS on 2008-11-29
I can partial Upgrade,Close once I close I can check for updates it finds around 57 updates and once that is complete I get the error I said at the start 

My last update was 1 day ago.

---

### Post by falcon61102 on 2008-11-29
I'm sorry but can you clarify things a little bit.

If I am understanding you correctly, you ran the Upgrade and then closed it before it completed and now you are trying to run it again.  When you attempt to run it again, you get the error listed in your first post.  You can also check for updates and it shows that you have about 57 updates that can be installed.  Is that all correct?

By the sounds of it, the updates that you are seeing are for 8.04 and not for 8.10.  You should be able to continue the Upgrade from where it left off when you closed it or you should have the option to restart the Upgrade.  If neither of those work, you are probably going to have to do a fresh install from the CD.

---

### Post by markharding557 on 2008-11-29
Have you tried running the updates in synaptic?if that does not work then check your sorces list are pointing to intrepid 
> sudo gedit /etc/apt/sources.list
if not change them to intrepid and then in a terminal
> sudo apt-get dist-upgrade
good luck

---

### Post by Oliver.BS on 2008-11-30
> **markharding557 said:**
> Have you tried running the updates in synaptic?if that does not work then check your sorces list are pointing to intrepid 

if not change them to intrepid and then in a terminal

good luck

I did what you said I get this error now

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by markharding557 on 2008-11-30
this means it is unable to connect.
In synaptic there is an option to change the servers in the software sources tab.
click on download tab and you shouls see a list of servers you will want one as close as possible maybe greek

---

### Post by Oliver.BS on 2008-12-01
> **markharding557 said:**
> this means it is unable to connect.
In synaptic there is an option to change the servers in the software sources tab.
click on download tab and you shouls see a list of servers you will want one as close as possible maybe greek

I keep failing still after changing to a server closer to me its giving me this error 

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

