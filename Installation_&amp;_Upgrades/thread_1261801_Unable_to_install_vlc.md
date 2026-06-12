---
title: "Unable to install vlc"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by levis lover on 2009-09-09
i had alpha version of vlc i.e. 0.9.9a and when i saw that version 1 had been launced i tried to update it but couldnot..
then i uninstalled vlc and again tried re-installing but it said this..
```
vlc: Depends: libqtcore4 (>= 4.5.1) but 4.5.0-0ubuntu4.1 is to be installed
       Depends: libqtgui4 (>= 4.5.1) but 4.5.0-0ubuntu4.1 is to be installed
E: Broken packages

```

how can i solve this problem?

---

### Post by rob-ward on 2009-09-09
I don't know what the cause of your problem is but the way I have installed the new version of VLC is documented here:[http://rob-ward.co.uk/thisarticle.php?id=18](http://rob-ward.co.uk/thisarticle.php?id=18) not sure if installing it that way will help or not.

---

### Post by jerrrys on 2009-09-09
in my synaptic they are listed as libqt4-core and libqt4-gui

---

### Post by levis lover on 2009-09-23
what does this error means..?
i can see these files in the synaptic.. shall i delete these files?

---

### Post by tommcd on 2009-09-23
The error you are getting:
```
vlc: Depends: libqtcore4 (>= 4.5.1) but 4.5.0-0ubuntu4.1 is to be installed
       Depends: libqtgui4 (>= 4.5.1) but 4.5.0-0ubuntu4.1 is to be installed
E: Broken packages
```
means that vlc 1.x depends on a newer version of libqtcore4 (>=4.5.1) than is present in the Jaunty repos (4.5.0). How exactly did you install the new version of vlc?
Try uninstalling vlc and then install vlc using the ppa repos as per the link Rob-Ward posted.

---

### Post by wilee-nilee on 2009-09-23
I don't know if this is helpful, but the PPA is the latest version. 

[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

---

