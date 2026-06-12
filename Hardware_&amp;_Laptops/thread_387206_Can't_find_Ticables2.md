---
title: "Can't find Ticables2"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by cactaur on 2007-03-18
I have a TI-89 Titanium calculator which I am trying to connect to my computer. I heard that the TiLP I has a lot of trouble with Titaniums, so I'm compiling the TiLP II program from source. However, the dependency I cannot satisfy is the ticables2 package. It's not in the repositories. I noticed that there was a libticables3, however it was already installed and did not help. I was wondering if anyone knew where I could get the ticables2 program. I searched all over the internet, but I was not able to find it. If anyone knows I'll be extremely thankful.

---

### Post by cactaur on 2007-03-19
Halloo? Anyone know?

---

### Post by cfackler on 2007-03-22
I'm having the same problem installing TiLP2 from source in Gentoo.  If you look at the [Linux page]("http://lpg.ticalc.org/prj_tilp/linux.html") for TiLP, there is another bundle for cables/calcs/files/conv.  I'm working on building that from source, to see if it works.

---

### Post by podfish on 2007-04-15
[http://repo.calcforge.org/fedora/6/i386/repodata/](http://repo.calcforge.org/fedora/6/i386/repodata/)

you can download all 5 i386 rpms, and they convert perfectly with alien.

however, like all the other tilp versions, you have to run as root.  If you have trouble, it's probably the config file.  Just ask, and I'll post my .tilp file.  I finally got it working last night.  And, of course, it's underwhelming, for all the work I put into it...  oh well.

Cheers,

The Podfish

---

### Post by Edward Hou on 2007-06-15
> **podfish said:**
> [http://repo.calcforge.org/fedora/6/i386/repodata/](http://repo.calcforge.org/fedora/6/i386/repodata/)

you can download all 5 i386 rpms, and they convert perfectly with alien.

however, like all the other tilp versions, you have to run as root.  If you have trouble, it's probably the config file.  Just ask, and I'll post my .tilp file.  I finally got it working last night.  And, of course, it's underwhelming, for all the work I put into it...  oh well.

Cheers,

The Podfish

I installed all five of those rpms, as well as the -devel packages. And even when I run tilp from root it still says
```
tilp: error while loading shared libraries: libkio.so.4: cannot open shared object file: No such file or directory
```

What do I need to do?

---

### Post by eternalsword on 2007-06-30
the necessary libs for tilp2 are available at [http://www.ticalc.org/archives/files/fileinfo/374/37479.html](http://www.ticalc.org/archives/files/fileinfo/374/37479.html)
first, compile and install libticables (you probably want libusb dev files installed)
then compile and install  libticonv
then compile and install libtifiles
lastly, compile and install libticalcs

then you should be able to compile and install tilp2

---

