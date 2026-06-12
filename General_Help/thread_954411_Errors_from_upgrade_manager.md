---
title: "Errors from upgrade manager"
date: 2008-10-21
forum: General Help
---

### Post by jonboy99 on 2008-10-21
Hi folks, am running hardy heron ubuntu with kde desktop installed as well.

Hadn't run the update manager for a while, and when I did it yesterday I got a load of errors, and same today,  Seems to be a lot of the kde ones.  Any ideas?

BYW my net connection is fine and hasn't changed recently.


```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008e-1ubuntu0.8.04_all.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hal-info/hal-info_20080508+git20080601-0ubuntu0.8.04_all.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kate_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-data_3.5.9-0ubuntu7.3_all.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdm_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-bin-kde3_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/konqueror_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdesktop_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-bin_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/libkonq4_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-kio-plugins_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kfind_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/konqueror-nsplugins_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kicker_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kcontrol_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kdenetwork-filesharing_3.5.9-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kdenetwork-kfile-plugins_3.5.9-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdepasswd_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdeprint_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kdnssd_3.5.9-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/khelpcenter_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/klipper_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kmenuedit_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/konsole_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kopete_3.5.9-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kpf_3.5.9-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kppp_3.5.9-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/krdc_3.5.9-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/krfb_3.5.9-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/ksmserver_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kwin_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/ksysguard_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/ksysguardd_3.5.9-0ubuntu7.3_i386.deb
  404 Not Found



```

---

### Post by Nepherte on 2008-10-21
Refresh your repository list:
```
sudo apt-get update
```
and try it again. The mirror appears to be on line but you can always try another one if it still doesn't work.

---

### Post by jonboy99 on 2008-10-21
Cheers mate, sorted.  I should've known to do that, I just pressumed the update manager would have done it by itself.
All updated now.

---

