---
title: "How to install outside apllication or software using command line interface?"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by nayaksuraj on 2009-06-18
Hi All, 

I want to install VLC player in my pc. I am using fedora. Can anyone tell me how to install it using command line interface? Please explain in brief.

Thanks.
Suraj Nayak

---

### Post by PureLoneWolf on 2009-06-18
This is for help with Ubuntu...

That said, a quick visit to the VLC homepage gave me this..

[http://www.videolan.org/vlc/download-fedora.html](http://www.videolan.org/vlc/download-fedora.html)

---

### Post by dstew on 2009-06-18
Fedora uses a different software packaging system than Ubuntu, so I don't think you will get much help here on an Ubuntu forum. However, here is the site for [VLC player for Fedora]("http://www.videolan.org/vlc/download-fedora.html"). For Fedora 9, 10 or 11, this is the code:```
$> su -
    #> rpm -ivh http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm
    #> yum install vlc
    #> yum install mozilla-vlc
```But, if you are having trouble, maybe you should seek help on a [Fedora forum]("http://forums.fedoraforum.org/").

---

