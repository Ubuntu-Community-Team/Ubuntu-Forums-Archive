---
title: "What packages must be in place before trying to install rtorrent/libtorrent from svn?"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by rusma on 2009-07-12
Hi! 

I tried installing rtorrent and liibtorrent from svn, using the instructions listed at [http://libtorrent.rakshasa.no/wiki/Install](http://libtorrent.rakshasa.no/wiki/Install). I got these errors: 

```
root@ubuntu:/home/rtorrent# ./update.sh 

[...]

checking pkg-config is at least version 0.9.0... yes
checking for OPENSSL... configure: error: Package requirements (openssl) were not met:

No package 'openssl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables OPENSSL_CFLAGS
and OPENSSL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
aclocal...

[...]

checking for libcurl... configure: error: Package requirements (libcurl >= 7.15.4) were not met:

No package 'libcurl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libcurl_CFLAGS
and libcurl_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
root@ubuntu:/home/rtorrent# 
```What packages are needed to make a successful installation? 

/Rasmus

---

### Post by terryeden on 2009-08-08
There's an excellent tutorial on HOWTOFORGE [http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron](http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron)

If you want to do it the hard way, though....

To install OpenSSL you need to download the latest OpenSSL source and install it.
```
wget http://www.openssl.org/source/openssl-0.9.8g.tar.gz
tar -zxvf openssl-0.9.8k.tar.gz
cd openssl-0.9.8g
./Configure gcc
make
make install
```

At the moment, 0.9.8k is the latest - but check [http://www.openssl.org/source/](http://www.openssl.org/source/) to see if a newer one has been released

You can download the latest version of CURL from [http://curl.haxx.se/download/](http://curl.haxx.se/download/)

HTH

---

### Post by rusma on 2009-08-21
> **terryeden said:**
> There's an excellent tutorial on HOWTOFORGE [http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron](http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron)

If you want to do it the hard way, though....

To install OpenSSL you need to download the latest OpenSSL source and install it.
```
wget http://www.openssl.org/source/openssl-0.9.8g.tar.gz
tar -zxvf openssl-0.9.8k.tar.gz
cd openssl-0.9.8g
./Configure gcc
make
make install
```At the moment, 0.9.8k is the latest - but check [http://www.openssl.org/source/](http://www.openssl.org/source/) to see if a newer one has been released

You can download the latest version of CURL from [http://curl.haxx.se/download/](http://curl.haxx.se/download/)

HTH

Thanks, really nice answer - I think I did found that howto some time ago, but did forgot to report back.

---

