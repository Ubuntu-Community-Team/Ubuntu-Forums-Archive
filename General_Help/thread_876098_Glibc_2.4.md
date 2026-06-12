---
title: "Glibc_2.4"
date: 2008-07-31
forum: General Help
---

### Post by KenSpeedie on 2008-07-31
I am attempring to install blockout game on Dapper.

I get the following error:

libc.so.6: version `GLIBC_2.4' not found (required by ./blockout)

1st question - how do I tell which version of GLIBC I have installed?

"locate libc.so.6" yields

/lib/tls/i686/cmov/libc.so.6
/lib/tls/libc.so.6
/lib/libc.so.6

"locate glibc" yields:

/etc/init.d/glibc.sh
/home/ken/cxoffice/bin/cxglibc-check
/usr/lib/glib-2.0/include/glibconfig.h
/usr/share/aclocal/glibc2.m4
/usr/share/aclocal/glibc21.m4

I can't tell if GLIBC_2.4 is newer or older than the one I have installed - will it make a difference if I install 2.4?

2nd question - How do I install the required GLIBC and am I going to run into trouble runing existing applications if I change to GLIBC_2.4?

I found an old post (2006) that said in part:


"Just get it (GLIBC_2.4) from the edgy repos (easiest is to temporarily                replace dapper -with edgy in /etc/apt/sources.list, and then revert back)."

"I have installed glibc 2.4 and gcc 4.1.1 this way 1 week ago, it works fine, so it seems to be binary compatible."


I am getting into un-charted territory here.  I am assuming (always a bad thing to do) that you would use apt-get to download and install GLIBC_2.4.

I am not sure of syntax to accomplish what I need to do (install GLIBC_2.4).

Blockout is my favorite game, but so far I have not been able to get it to run in linux.

Thanks for you help.


Ken

---

