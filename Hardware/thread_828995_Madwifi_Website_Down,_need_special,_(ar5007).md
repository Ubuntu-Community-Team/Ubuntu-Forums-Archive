---
title: "Madwifi Website Down, need special, (ar5007)"
date: 2008-06-14
forum: Hardware
---

### Post by Jellman on 2008-06-14
Hey every one, it appears that the madwifi site is down, i was wondering if any one has

[http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)
"madwifi-nr-r3366+ar5007.tar.gz"

I cant seem to find any mirrors, and i need the file to get my wirless working. :)

thanks in advance!
Scott

---

### Post by yuretsz on 2008-11-02
Have anyone found it?

---

### Post by ardvark71 on 2008-11-02
> **Jellman said:**
> Hey every one, it appears that the madwifi site is down

Hi...

Not sure what happened but their site was up a couple three days ago when I went there, now it's down again. :confused:

Would the commands listed on post #11 at this thread help?

[http://ubuntuforums.org/showthread.php?t=732945&page=2](http://ubuntuforums.org/showthread.php?t=732945&page=2)

```
sudo apt-get install build-essential
wget 'http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz'
tar zxvf madwifi-ng-r3366+ar5007.tar.gz
cd madwifi-ng-r3366+ar5007
make clean
make
sudo make install
reboot
```

Of course, if and when the site's down, this probably won't help much. :( Just keep trying.

EDIT: Just found this thread too...

[http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)

Best Regards...

---

### Post by osuna on 2008-11-04
[HTML]http://www.megaupload.com/es/?d=YZZ04LZY[/HTML]

):PSee Ya):P

---

