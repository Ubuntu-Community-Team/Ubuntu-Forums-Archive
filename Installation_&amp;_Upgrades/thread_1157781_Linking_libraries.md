---
title: "Linking libraries?"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-05-13
Since it appears that there's on one on planet earth (or in the forum atleast) who has installed the ATI drivers directly from source, I'll be the first one to do so, i.e do all the hard work.



The drivers that I compiled using standard technique (you know ./configure, make, make install) really appear to be negligible since after unintalling the old ATI drivers of version 6.12.1 and them making and installing these new 6.12.2 drives, I boot into command line. 

The precompiled binaries for 6.12.2 doesn't seem to have been made till date for ubuntu 8.10 and installing the jaunty drivers will give an error that xserver-xorg-core is missing, which's of course not (actually it needs an upgrade, when I tried to upgrade (i.e downloaded the new package which were again only made for jaunty only) they give a number of conflicts mainly involving other xorg packages which my 15.4 inch laptop screen were not able to show off completely at 1280*800 resolution).

So I gave up resolving the conflict (or upgrading the like...........100 packages manually cause ubuntu doesn't do it automatically for 8.10) and thought about searching (from the dungeons of like......200 packages) and downloading the source codes from [this]("https://launchpad.net/~tormodvolden/+archive/ppa") place and compiling, who's efforts and results I have previously expressed.

However there seems to be a small amount of light which comes by the fact that while doing 'make install', it produces certain illegible scripts among which are found certain legible words arranged in sentences which I've filtered as follows - 

```

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for more information, such as the ld(1) and ld.so(8) manual pages.
more information, such as the ld(1) and ld.so(8) manual pages.





Libraries have been installed in:
   /usr/local/lib/xorg/modules/drivers

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.


Libraries have been installed in:
   /usr/local/lib/xorg/modules/multimedia

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.






Libraries have been installed in:
   /usr/local/lib/xorg/modules/multimedia

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.




Libraries have been installed in:
   /usr/local/lib/xorg/modules/multimedia

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.

```

i.e its asking me to use a program called 'libtools' which I searched for and figured out that it's meant solely for programers/developers after realising that I did not understood a thing after reading the whole article on how to link the libraries using this tool which makes the job 'easier'.



So what I'm exactly expecting here are a few responses to help me sort this mess out, or actually 'invoke' the fact to the develops that if they have launched a new version of ubuntu doesn't mean you'll boycott the older versions and - 
1)Stop giving the users updates unless they upgrade.
2)Stop making precompiled binaries exclusively for older versions.
3)Stop diving upgrades to newer libraries for older version of ubuntu

---

