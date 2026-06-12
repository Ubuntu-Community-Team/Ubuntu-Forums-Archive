---
title: "make: *** No rule to make target `install'.  Stop."
date: 2008-11-27
forum: General Help
---

### Post by lavadisco on 2008-11-27
Today I downloaded tar.gz files for both LiVES 0.9.9.3 and Kdenlive 0.7 video editing packages. I extracted both to my desktop, opened terminal and went into the extracted directory and tried to do a "make install" of both programs per the installation instructions. But I get this error:

```
lavadisco@lavadisco:~/Desktop/lives-0.9.9.3$ make install
make: *** No rule to make target `install'.  Stop.

```

Anybody know how I can fix this?

---

### Post by cariboo on 2008-11-27
Make sure you have all the dependencies listed on the download page installed, and make sure you have build-essential installed. then in a terminal type:

```
./configure
```

If you don't have any errors type:

```
make
```

once the program has been compiled type:

```
sudo make install
```

Alternatively, if you want to create a deb subustitute checkinstall for make.

Jim

---

### Post by lavadisco on 2008-11-27
I get an error when I run ./configure:

```
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.4.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I went into Synaptics and searched for GTK - I can't tell which one I need to install because there are so many options.

---

### Post by mc4man on 2008-11-27
You'll want libgtk2.0-dev, that should get your configure going.
If your missing other packages the configure errors should point the way.
Many times you'll need to put lib in front of what it says it's missing and the -dev if available.


Did a quick configure, should be no problem if you've got every needed.

By default it will install to /usr/local

You may consider installing to /usr, if so 

```
./configure --prefix=/usr
```

---

