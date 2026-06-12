---
title: "Removing all unused packages"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by rabidityfactor on 2009-08-15
I have installed Ubuntu Jaunty on my pendrive, so that I can take all my stuff whereever I go.
My problem is that, I have an 8gb pendrive, and ubuntu takes up 2+gb of space. I wanted to remove all the unwanted packages and keep only the VERY BASE stuff + openoffice, firefox, pidgin etc.... :D

Is there any way I can reduce the size to around 500mb or atleast 1gb??

Thanks in advance.

UBUNTU ROCKS!

---

### Post by rabidityfactor on 2009-08-15
Somebody help!

---

### Post by sblunix on 2009-08-15
well, I suppose you could open Synaptic Package manager or something of the sort and start uninstalling files, but I'd recommend downloading and installing Xubuntu on your flash drive instead, it's smaller and a bit easier for flashdrives.

---

### Post by stlsaint on 2009-08-15
yes you def. should install a different version of ubuntu because jaunty is rather large for what your trying to do!!
check this out...should be what you are looking for.....
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by harry2006 on 2009-08-15
Xubuntu would be a better option [that can run even on 256 mb ram without any issues]

---

### Post by stlsaint on 2009-08-15
> **harry2006 said:**
> Xubuntu would be a better option [that can run even on 256 mb ram without any issues]


i wasnt saying xubuntu wouldnt be a great option...just doing what ubuntu is all about...freedom/options!!

---

### Post by raymondh on 2009-08-15
> **rabidityfactor said:**
> I have installed Ubuntu Jaunty on my pendrive, so that I can take all my stuff whereever I go.
My problem is that, I have an 8gb pendrive, and ubuntu takes up 2+gb of space. I wanted to remove all the unwanted packages and keep only the VERY BASE stuff + openoffice, firefox, pidgin etc.... :D

Is there any way I can reduce the size to around 500mb or atleast 1gb??

Thanks in advance.

UBUNTU ROCKS!

8GB is ok for root.  Just remember that you'll have to save your files/data elsewhere or you'll soon run out of space.

Go to synaptic and see what you don't need.  Remember that some apps require dependencies.

---

### Post by kayvortex on 2009-08-15
You can check to see if /var/cache/apt/archives is empty or not. If not, then you can remove them safely with

```
sudo aptitude clean
```

---

