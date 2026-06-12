---
title: "Error rebuilding squid3 package"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by keefe007 on 2009-01-24
I need to rebuild the squid3 package because I need to have the build time option of --enable-ssl.

With prior version of squid I would just do the following:

apt-get source squid
apt-get build-dep squid
apt-get install devscripts build-essential fakeroot
cd squid-2.6.1
vim debian/rules
Add --enable-ssl \ to “# Configure the package” section
./configure
debuild -us -uc -b
cd ..
dpkg -i squid

Now when I tried this with squid3 i'm getting the following error:

make[1]: Leaving directory `/root/squid3-3.0.STABLE7'
touch debian/stamp-patched
touch debian/stamp-autotools-files
/usr/bin/make -C . 
make[1]: Entering directory `/root/squid3-3.0.STABLE7'
Making all in lib
make[2]: Entering directory `/root/squid3-3.0.STABLE7/lib'
make[2]: *** No rule to make target `all'.  Stop.
make[2]: Leaving directory `/root/squid3-3.0.STABLE7/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/squid3-3.0.STABLE7'
make: *** [debian/stamp-makefile-build] Error 2
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
debuild: fatal error at line 1329:
dpkg-buildpackage -rfakeroot -D -us -uc -b failed

I'm in intrepid.

Any ideas?

Thanks,

Keefe

---

### Post by geostrydar on 2009-03-09
I was also running into the same error ```
debuild: fatal error at line 1329:
``` I did some googling and found the following link, 2nd post. [https://www.linuxquestions.org/questions/debian-26/-enable-icap-client-at-squid3-640035/]("https://www.linuxquestions.org/questions/debian-26/-enable-icap-client-at-squid3-640035/"). Of course, replace the --enable-icap-client with --enable-ssl. 

Notice the lack of "**./config**" and "debuild -us -uc **-b**" appear to be the only discrepancies compared to the original method. Additionally, the only difference in error I had compared to yours, I was lacking in some dev libs. Once I installed them and followed the given link's steps, I was able to build the deb files and install. 

I hope this helps out and good luck!

---

