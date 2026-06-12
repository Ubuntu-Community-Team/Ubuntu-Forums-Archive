---
title: "Why are updates announced, but not available?"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by Peter Bell on 2009-03-02
I seem to be experiencing this more and more often ... updates are reported by the Update Manager, but when I try to fetch them I get a 404.

For instance, today I have 19 failures.  I think that the 'Urgent' update to sudo was offered more than three weeks ago, but still I can't fetch it.

This is the list of failures from this morning:

> W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.22.87ubuntu1~intrepid1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.22.87ubuntu1~intrepid1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-runtime/kde-icons-oxygen_4.1.4-0ubuntu1~intrepid1.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-runtime/kde-icons-oxygen_4.1.4-0ubuntu1~intrepid1.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kde4libs/kdelibs-bin_4.1.4-0ubuntu1~intrepid1.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kde4libs/kdelibs-bin_4.1.4-0ubuntu1~intrepid1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kde4libs/kdelibs5-data_4.1.4-0ubuntu1~intrepid1.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kde4libs/kdelibs5-data_4.1.4-0ubuntu1~intrepid1.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kde4libs/kdelibs5_4.1.4-0ubuntu1~intrepid1.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kde4libs/kdelibs5_4.1.4-0ubuntu1~intrepid1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-runtime/kdebase-runtime_4.1.4-0ubuntu1~intrepid1.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-runtime/kdebase-runtime_4.1.4-0ubuntu1~intrepid1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-runtime/kdebase-runtime-bin-kde4_4.1.4-0ubuntu1~intrepid1.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-runtime/kdebase-runtime-bin-kde4_4.1.4-0ubuntu1~intrepid1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-runtime/kdebase-runtime-data-common_4.1.4-0ubuntu1~intrepid1.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-runtime/kdebase-runtime-data-common_4.1.4-0ubuntu1~intrepid1.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-runtime/kdebase-runtime-data_4.1.4-0ubuntu1~intrepid1.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-runtime/kdebase-runtime-data_4.1.4-0ubuntu1~intrepid1.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-workspace/kdebase-workspace-libs4+5_4.1.4-0ubuntu1~intrepid3.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-workspace/kdebase-workspace-libs4+5_4.1.4-0ubuntu1~intrepid3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-workspace/libplasma2_4.1.4-0ubuntu1~intrepid3.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-workspace/libplasma2_4.1.4-0ubuntu1~intrepid3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-workspace/kdebase-workspace-data_4.1.4-0ubuntu1~intrepid3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-workspace/kdebase-workspace-data_4.1.4-0ubuntu1~intrepid3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdepimlibs/kdepimlibs-data_4.1.4-0ubuntu1~intrepid1.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdepimlibs/kdepimlibs-data_4.1.4-0ubuntu1~intrepid1.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdepimlibs/kdepimlibs5_4.1.4-0ubuntu1~intrepid1.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdepimlibs/kdepimlibs5_4.1.4-0ubuntu1~intrepid1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-runtime/khelpcenter4_4.1.4-0ubuntu1~intrepid1.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/k/kdebase-runtime/khelpcenter4_4.1.4-0ubuntu1~intrepid1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/p/postgresql-8.3/libpq5_8.3.6-0ubuntu8.10_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/p/postgresql-8.3/libpq5_8.3.6-0ubuntu8.10_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/s/sudo/sudo_1.6.9p17-1ubuntu2.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/s/sudo/sudo_1.6.9p17-1ubuntu2.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.6+nobinonly-0ubuntu0.8.10.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.6+nobinonly-0ubuntu0.8.10.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.6+nobinonly-0ubuntu0.8.10.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.6+nobinonly-0ubuntu0.8.10.1_i386.deb)
  404 Not Found


---

### Post by Yashiro on 2009-03-02
Change which main Ubuntu repository you connect to and disable any 'extra' ones you have added manually.

---

### Post by Peter Bell on 2009-03-02
Hmmm .. not something that I've ever knowingly changed, but I've done a 'Select Best Server'.  It chose public.planetmirror.com - which failed to supply all the repository indexes.  This seems to be a minefield!

---

### Post by Peter Bell on 2009-03-02
Okay, I've now tried 'Main Server' and there are only a few repositories which it doesn't supply.  I'm now downloading some updates.

---

### Post by Peter Bell on 2009-03-02
> **Peter Bell said:**
> Okay, I've now tried 'Main Server'

That appears to select gb.archive.ubuntu.com which seems to be fairly slow here in Philippines!

---

### Post by Yashiro on 2009-03-02
Select Other and pick one closer.

---

### Post by Peter Bell on 2009-03-02
Ah, the nearest, topologically, would be Hong Kong (all international traffic from here seems to go via Hong Kong) and the HK server is ftp.hostrino.com ... which is where I started!

---

