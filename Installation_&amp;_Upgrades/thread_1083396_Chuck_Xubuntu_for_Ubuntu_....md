---
title: "Chuck Xubuntu for Ubuntu ..."
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by pmooney78 on 2009-02-28
Hello,

I'd like to migrate from Xubuntu 8.10 to Ubuntu 8.10, largely because of problems with Thunar. Is there an easier way to do this than a complete reinstall?

Thanks in advance for any help.

---

### Post by taurus on 2009-02-28
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by pmooney78 on 2009-02-28
Thanks! Should I also remove the xubuntu-desktop package? Uninstall Thunar and/or other applications? Hard drive space isn't particularly short, but waste not, want not ...

---

### Post by taurus on 2009-02-28
Xubuntu-package is just a metapackage.  Removing it won't remove XFce4 from your machine.  Have a look at this link.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by pmooney78 on 2009-03-01
Work through that now. Thank you very much!

---

### Post by AnonCat on 2009-03-01
If Thunar is the only reason you want to quit Xubuntu, you could just install Ubuntu's file manager which is Nautilus and use that.  Just make sure you run it as  Nautilus --no-desktop to keep it from screwing with Xubuntu's desktop.

---

### Post by pmooney78 on 2009-03-03
I LIKE desktop integration ... and other stuff that's new to me in Ubuntu. Overall, I'm happy, although there have been a few "Where is my [insert name of feature]" moments.

I initially decided to go with Xubuntu because I was running it on a very old computer. With a faster processor, I'm happy to spend a little extra processor speed on eye candy and other, more useful features. :)

---

