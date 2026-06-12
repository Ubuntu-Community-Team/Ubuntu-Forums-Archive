---
title: "Error message when doing updates"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2009-05-06
When I do my updates I get the following message:
> Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

aptitude-doc-en
gcc-4.4-base
gcj-4.4-base
gdb
ggzcore-bin
info
install-info
lib32gcc1
lib32stdc++6
libgcc1
libgcj-bc
libgcj10
libggz2
libggzcore9
libggzmod4
libgomp1
libgssapi-krb5-2
libiw30
libk5crypto3
libkrb5-3
libkrb5support0
libpq5
libstdc++6
openoffice.org-common
openoffice.org-java-common
openoffice.org-style-crystal
openoffice.org-style-galaxy
openoffice.org-style-tango
totem-gstreamer
totem-mozilla
wireless-tools


Any Ideas what is causing this and/or how to fix it

---

### Post by Stolea on 2009-05-06
Anyone with any ideas, Please.

---

### Post by Stolea on 2009-05-06
I tried the following
> sudo apt-get dist-upgrade
Terminal reported
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Does that make any sense to anyone?

---

### Post by taurus on 2009-05-06
It means you have another process like update-manager or something like that running.  You cannot start update-manager, synaptic, or apt-get at the same time.  Only one at a time.

---

### Post by Stolea on 2009-05-06
OOps.
Closed the update and tried again. This time the process worked OK. Ran the update manager again and after 2 goes it seems to be happy now.
Thanks

---

