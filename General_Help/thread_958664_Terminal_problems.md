---
title: "Terminal problems"
date: 2008-10-25
forum: General Help
---

### Post by Tictoon on 2008-10-25
when trying to install my favorite game, Ltris, I found that when I enter the command ./configure it ends with this error:

```
checking for sdl-config... no
checking for SDL - version >= 1.0.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: lib SDL is needed

```

also when trying to update GIMP and isntall the new version I get this:

```
checking for xgettext... (cached) /usr/bin/xgettext
checking for iso-codes... yes
checking for BABL... configure: error: Package requirements (babl >= 0.0.22) were not met:

No package 'babl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BABL_CFLAGS
and BABL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

what do i do now?

---

### Post by geirha on 2008-10-25
Both ltris and gimp are in the repositories, and if you need a newer gimp than the one in the repository, I recommend you try to find a .deb file instead of compiling yourself, which is hard. getdeb.net has a newer version of gimp. Download all the deb-files for it, put them in the same directory and run ```
sudo dpkg -i *.deb
```

If you still want to compile yourself, run ```
apt-get build-dep ltris
``` to get the needed packages for building ltris yourself. The same applies for gimp.

---

### Post by Tictoon on 2008-10-25
will ubuntu 8.10 have the newer version of GIMP??

---

### Post by geirha on 2008-10-25
Intrepid has version 2.6.1: [http://packages.ubuntu.com/search?keywords=gimp&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=gimp&searchon=names&suite=intrepid&section=all)

---

### Post by Tictoon on 2008-10-25
that is a lot of packages to download, isn't there a simpler one?

---

### Post by geirha on 2008-10-25
Can't say I know of any easier ones. It's only about 15MiB to download. The sources are at least 25MiB. 

This should download and install the packages:
```

mkdir /tmp/gimp
cd /tmp/gimp
wget http://www.getdeb.net/download/3257/{0,1,2,7,8}
sudo dpkg -i *.deb

```

If you want to keep the .deb files afterwards, move them to your homedir or something. Everything under /tmp is wiped during boot.

---

### Post by stoneage on 2008-10-25
Most of those packages would be already included in Intrepid(and in Hardy, though maybe not the same versions). 

Get Gimp here instead - [http://www.getdeb.net/category.php?id=4](http://www.getdeb.net/category.php?id=4)

There is also a version for 64 bit - select 'other version' at the top of the page.




EDIT - Whoops, too slow. geirha is right though, it is fairly straightforward.

---

