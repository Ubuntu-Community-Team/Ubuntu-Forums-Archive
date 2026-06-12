---
title: "Update manager fails to connect"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by itsols on 2009-05-30
Hi everyone. I wonder if anyone faced this problem recently. My update manager fails with this error:

[http://apt.wxwidgets.org/dists/gutsy-wx/main/binary-i386/Packages.bz2:](http://apt.wxwidgets.org/dists/gutsy-wx/main/binary-i386/Packages.bz2:) Hash Sum mismatch
[http://apt.wxwidgets.org/dists/gutsy-wx/main/source/Sources.bz2:](http://apt.wxwidgets.org/dists/gutsy-wx/main/source/Sources.bz2:) Hash Sum mismatch
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]

But I am online right now so it can't be a network error on my side. Your thoughts are appreciated. My version is 7.10 Gusty.

---

### Post by pastalavista on 2009-05-30
Gutsy is no [longer supported]("http://www.ubuntu.com/news/ubuntu-7.10-eol") for updates as of April. The server you were using is 404. Time to upgrade  to Hardy... ```
sudo do-release-upgrade
```

---

### Post by itsols on 2009-05-30
Thank you pastalavista for your feedback. I've installed about 10 boxes with Gutsy in one location. Updating 10 on ADSL is kind of difficult. Is there a way I can burn the upgrade onto CD and run it on each machine?

Many thanks.
Khalid

---

### Post by pastalavista on 2009-05-30
If you download the Hardy 'alternate' install CD (text based), I believe you can just insert the disk into a running Gutsy machine and a dialog will ask if you want to upgrade. At least, that's what it says on [this page.]("http://releases.ubuntu.com/hardy/")> The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * setting up automated deployments;
    * [COLOR="Red"]upgrading from older installations without network access[/COLOR];
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 384MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 

---

### Post by itsols on 2009-05-30
Perhaps that's true about the CD but I don't have it. I only have one CD and that's the normal installation.

I think there's a way to download the upgrade and save it on the HDD. Then burn it on CD. Do you know this command? Perhaps I should see if the package manager has it.

Thanks anyway.

---

### Post by pastalavista on 2009-05-30
[This page]("https://help.ubuntu.com/community/HardyUpgrades") explains it. The alternate CD is the only way to upgrade in place without doing a net upgrade. You can download the iso with a torrent. You can burn it to a CD or a USB flash which is the best way (fastest) IMO. You might be thinking of [something like this]("http://packages.ubuntu.com/hardy/upgrade-system"), but I have no experience with that.

---

### Post by itsols on 2009-05-30
Thanks for all your inputs. I'll try the torrent download first.

Happy computing!

---

