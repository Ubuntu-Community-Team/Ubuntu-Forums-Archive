---
title: "Squid 3.0 STABLE19 for Ubuntu"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by pcirne on 2009-10-01
Hi,

I'm looking for the binaries packages of Squid 3.0 STABLE19, does any one know where I can find them for Ubuntu 9.04?

Thank you very much!

Pedro

---

### Post by realzippy on 2009-10-01
Here you go:

[http://www.squid-cache.org/Versions/v3/3.0/squid-3.0.STABLE19.tar.bz2](http://www.squid-cache.org/Versions/v3/3.0/squid-3.0.STABLE19.tar.bz2)

Assuming the file is on your desktop,rightclick the file,choose "unpack here"
Open a terminal,type:

sudo apt-get install build-essential

cd Desktop
cd squid-3.0.STABLE19/
./configure
make
sudo make install

---

### Post by pcirne on 2009-10-01
Hi,

I'm looking for the binaries not the sources packages :)

Pedro

---

### Post by realzippy on 2009-10-01
> **pcirne said:**
> Hi,

I'm looking for the binaries not the sources packages :)

Pedro

..after compiling in /sbin ?

[http://packages.debian.org/search?searchon=sourcenames&keywords=squid](http://packages.debian.org/search?searchon=sourcenames&keywords=squid) :
Source Package squid3

    * etch (web): 3.0.PRE5-5+etch1
      Binary packages: squid3, squid3-cgi, squid3-client, squid3-common
    * etch-m68k (web): 3.0.PRE5-5
      Binary packages: squid3, squid3-cgi, squid3-client, squid3-common
    * lenny (web): 3.0.STABLE8-3+lenny2
      Binary packages: squid3, squid3-cgi, squid3-common, squidclient
    * squeeze (web): 3.0.STABLE19-1
      Binary packages: squid3, squid3-cgi, squid3-common, squid3-dbg, squidclient
    * sid (web): 3.0.STABLE19-1
      Binary packages: squid3, squid3-cgi, squid3-common, squid3-dbg, squidclient
    * experimental (web): 3.1.0.14-2
      Binary packages: squid3, squid3-cgi, squid3-common, squid3-dbg, squidclient

---

### Post by eugenevdm on 2010-09-05
I also had this question for ages.

Check packages.ubuntu.com search for "squid**3**".

If you want to be brave check out [http://packages.ubuntu.com/source/maverick/squid3](http://packages.ubuntu.com/source/maverick/squid3) contains Squid 3.1 binaries.

---

