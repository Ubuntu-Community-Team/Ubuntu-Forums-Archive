---
title: "Canon printer driver for imageClass MF4890 and MF4800"
date: 2014-01-04
forum: Hardware
---

### Post by martin.danjou14 on 2014-01-04
Here is how I installed the Canon printer driver for the imageClass MF4890 (MF4800 series).

Install some prerequisites that may or may not be on your system. I had to install these:
```

sudo apt-get intltool
sudo apt-get libglade2-dev
sudo apt-get libxml2-dev
sudo apt-get libgtk2.0-dev

```

Get the Canon driver for the imageClass printer MF4890dw from the Canon website. Open the tar.gz and cd into the "Sources" directory. There should be two tar.gz files in the Sources directory.

First, we copy the tar file and keep an original as required by the build tools:
```

cp cndrvcups-common-2.70-1.tar.gz cndrvcups-common_2.70.orig.tar.gz

```

Then we open it:
```

tar xf cndrvcups-common-2.70-1.tar.gz
cd cndrvcups-common-2.70

```

Create the .deb package:
```

dpkg-buildpackage -us -uc
cd ..

```

Install the .deb package (you must install it as you need it to build the next package). I prefer to do this by double clicking on the ".deb" file in the file manager.

We repeat the same steps for the "lb" package:
```

cp cndrvcups-lb-2.70-1.tar.gz cndrvcups-lb_2.70.orig.tar.gz
tar xf cndrvcups-lb-2.70-1.tar.gz
cd cndrvcups-lb-2.70

```

The Canon package is a bit out of date, there are thus two changes to make. First, edit [FONT=courier new]allgen.sh[/FONT] and remove all instances of [FONT=courier new]--enable-static --disable-shared[/FONT].

Second, the previous package (cndrvcups-common) has created a symbolic link on which the debian build script "dh_shlibdeps" chockes. We have to tell it to ignore that error. Edit debian/rules and add --dpkg-shlibdeps-params=--ignore-missing-info to dh_shlibdeps like this:

```

dh_shlibdeps --dpkg-shlibdeps-params=--ignore-missing-info

```

Now we can build:
```

dpkg-buildpackage -us -uc
cd ..

```

Install the .deb package.

You should be able to setup the printer the usual way. Hope this helps.

---

### Post by mörgæs on 2014-01-05
Thanks. 
When the thread is marked 'solved' there's a better chance that people find it. Have done it for you.

---

