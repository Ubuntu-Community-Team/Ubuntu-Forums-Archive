---
title: "Gentoo has an undeserved reputation"
date: 2007-09-20
forum: Gentoo and derivatives
---

### Post by g2g591 on 2007-09-20
Gentoo has an undeserved reputation as an extremely hard to learn distro. I have found this completely untrue. Everything is very well documented, and the only *slightly *negative thing is you must install x and your desktop environment of choice. If you are up for a little bit of learning, give Gentoo a try, its only a 150Mb download if you install from a working Linux setup (Ubuntu, Kubuntu, Suse, etc.)

---

### Post by Sayers on 2007-09-20
It's not hard to use, but for me it doesnt have bennifits, I do run source mage in a Virtual Box however for the fun of it :P

---

### Post by Kingsley on 2007-09-20
I agree with you. I occasionally use the Gentoo Wiki tutorials for help with Ubuntu problems.

---

### Post by jrusso2 on 2007-09-20
I prefer to use my computer rather then working on it all the time.  My job is to fix servers and when I get home I just want my stuff to work.

I like things easy, Ubuntu, Linux Mint, PCLinuxOS or Sam Linux all work fine.  Debian is good too.

I don't want to spend all day compiling

---

### Post by rsambuca on 2007-09-20
> **jrusso2 said:**
> I prefer to use my computer rather then working on it all the time.  My job is to fix servers and when I get home I just want my stuff to work.

I like things easy, Ubuntu, Linux Mint, PCLinuxOS or Sam Linux all work fine.  Debian is good too.

I don't want to spend all day compiling

I agree with the OP here.  I have never understood the "I don't want to spend all day compiling" comment.  It's not like you have to sit there watching it do it's work.  You can still use your rig for whatever you want in the meantime.  

Also, compiling only really takes a long time with very few builds, like the DE, or Open Office.  Almost everything else is done in a couple of minutes or less.

---

### Post by SunnyRabbiera on 2007-09-21
well gentoo is definately not for the beginner though, especially before it got its new installer...

---

### Post by Bachstelze on 2007-09-21
Agreed 100%

But moved to Gentoo Talk nevertheless ;)

---

### Post by MrHippocampus on 2007-09-21
> well gentoo is definately not for the beginner though, especially before it got its new installer...
Not forgetting of course the fun of emerging an update which causes an ABI breakage, that can be very nasty if you don't know its coming, and even if you do it can involve a good few hours of recompilation.

---

### Post by Foxmike on 2007-09-21
> **MrHippocampus said:**
> Not forgetting of course the fun of emerging an update which causes an ABI breakage, that can be very nasty if you don't know its coming, and even if you do it can involve a good few hours of recompilation.
How often such things happens?  It never  happened to me, may be i'm just lucky.;)

I must admit, tho that I'm not too hot on the graphical installer... it's quite buggy and at the end, I think that the whole experience is more interesting from the command line, just my 2 cents...

---

### Post by g2g591 on 2007-09-21
it hasn't happened to me yet either

---

### Post by Bachstelze on 2007-09-22
It happened recently when Xorg was updated from 7.2 to 7.3, you had to recompile your Xorg drivers. But it hasn't heppened for you guys yet, if you're running stable ;)

---

### Post by MrHippocampus on 2007-09-22
I got hit by libexpat.so the other day, I emerged a few things as normal, then noticed firefox wouldn't start, thunderbird wouldn't start, thunar wouldn't start..... Thankfully I had gone through the same thing with dbus a while back so I knew what to do.

Anyway, the lesson is, learn what the command "revdep-rebuild" does and how to use it. That will get you out of any ABI breakage problem :)

---

### Post by happysmileman on 2007-09-22
I use it now as my main OS, I think for me the best thing to do is simple, install everything I need, and only upgrade when it's needed (as in depended on by new upgrade) or when you want to (new release of KDE or Opera means so much more to me than some library I'm not even sure if is in use regularly)

Whereas on Ubuntu I updated every time the icon tells me to, if there's a bugfix release of something you've never noticed a bug in, why spend the time recompiling?

Though of course I use Gentoo for the speed, Compiz-Fusion runs fine without any stutters at all on KDE, though I usually leave it off on Kubuntu becase of slowness

---

### Post by Foxmike on 2007-09-22
Concerning updates, I heared that if you want to keep a sane system an sane upgrades in the future, you better not wait so much, for an update after several weeks might break things (there is too much to upgrade).  That is what I heared, but I'm not sure what to think about it.  I guess that if Gentoo is about choices, then it would be about choice to update or not for any reason you would have to, no?

---

### Post by Bachstelze on 2007-09-23
I usually do my upgrades as soon as they're available, just because I see no reason not to, but I don't think not doing them breaks thigs, as long as you do them properly when you decide to.

> **Foxmike said:**
> I guess that if Gentoo is about choices, then it would be about choice to update or not for any reason you would have to, no?

I guess you didn't understand it all. For example, when Xorg 7.3 was released and I upgraded it from 7.2, I also had to upgrade my nvidia drivers. Not because Gentoo said "thou shalt upgrade yer nvidia drivers", but simply because the old ones were not compatible with it. It's like you're saying that if not upgrading things break, it's because Gentoo does not want to give you the choice of uprgading or not. No. It's because sometimes, an older version of something is not compatible with a newer version of something else, so if you want to ugrade, you must upgrade them both, but you can also not upgrade at all if you wish. Just don't be surprised when you will want to upgrade one little thing and it will ask you to upgrade a lot more.

---

### Post by Foxmike on 2007-09-23
As I said previously, I don't see any reason not to upgrade any package.  But I'm new to Gentoo and still learning (I guess I'll be still learning for a while...) so there are still a lot of things I may not understand.  Tho, I think that the nvidia example would be true no mather which distro you use, no?

As of the upgrade or not discussion, I was referring to a comment I saw on gentoo forums (I'll have to search it back) in wich the author complained that he made an upgrade after several months of not-upgrade and it took 2 weeks to sort things out.

---

### Post by Bachstelze on 2007-09-23
> **Foxmike said:**
> 
As of the upgrade or not discussion, I was referring to a comment I saw on gentoo forums (I'll have to search it back) in wich the author complained that he made an upgrade after several months of not-upgrade and it took 2 weeks to sort things out.

It's true that it can take a while to sort thigs out, especially after several months. ABI changes, configuration files changes, etc. But two weeks ? No way. Either the person who posted that was a Gentoo newbie and definitely should have asked for advice instead of trying to do it all on his own, or he's trying to despise Gentoo and is talking FUD about it.

---

### Post by cotcot on 2007-09-28
Running gentoo for 2 years now without reinstalling. Updates done any 3 months : no problem.

---

### Post by yabbadabbadont on 2007-09-28
Say it with me, "revdep-rebuild is your friend."  :D

I was going to put a Gentoo install on my machine again, but I'm going to wait until the stage files for the next release are ready.  As it stands with the current stage files, there are glibc, gcc, and libexpat updates waiting immediately upon install.  One of which definitely requires an "emerge -e world".

---

### Post by Bachstelze on 2007-09-30
> **yabbadabbadont said:**
> Say it with me, "revdep-rebuild is your friend."  :D

I was going to put a Gentoo install on my machine again, but I'm going to wait until the stage files for the next release are ready.  As it stands with the current stage files, there are glibc, gcc, and libexpat updates waiting immediately upon install.  One of which definitely requires an "emerge -e world".

If you update those three and do an *emerge -e world* right after you've extracted the stage, it doesn't actually take that long...

---

### Post by yabbadabbadont on 2007-09-30
> **HymnToLife said:**
> If you update those three and do an *emerge -e world* right after you've extracted the stage, it doesn't actually take that long...

Not on your machine perhaps...  ;)

---

### Post by MrHippocampus on 2007-09-30
Well, after being away from my desktop for 2 months I have this many updates:

```
[ebuild     U ] dev-util/pkgconfig-0.21-r1 [0.20] USE="-hardened" 976 kB 
[ebuild     U ] dev-libs/expat-2.0.1 [1.95.8] USE="(-test%)" 436 kB 
[ebuild     U ] media-libs/audiofile-0.2.6-r3 [0.2.6-r2] 0 kB 
[ebuild     U ] app-arch/zip-2.32 [2.31-r1] USE="crypt" 789 kB 
[ebuild     U ] dev-libs/nspr-4.6.7 [4.6.5-r1] USE="-debug -ipv6" 1,274 kB 
[ebuild     U ] sys-devel/gcc-config-1.4.0-r2 [1.3.16] 0 kB 
[ebuild     U ] net-wireless/bluez-libs-3.19 [3.12] USE="-debug" 302 kB 
[ebuild     U ] sys-fs/device-mapper-1.02.19-r1 [1.02.10-r1] USE="(-selinux)" 179 kB 
[ebuild     U ] app-arch/cpio-2.9 [2.7-r1] USE="nls" 741 kB 
[ebuild  N    ] dev-util/unifdef-1.20  65 kB 
[ebuild     U ] sys-libs/timezone-data-2007g [2007e] USE="nls" 344 kB 
[ebuild     U ] app-text/libpaper-1.1.21 [1.1.20] 343 kB 
[ebuild     U ] sys-apps/dmidecode-2.9 [2.8] 48 kB 
[ebuild     U ] dev-libs/libdaemon-0.12 [0.11] USE="-doc" 347 kB 
[ebuild     U ] media-sound/alsa-headers-1.0.14 [1.0.14_rc2] 2,540 kB 
[ebuild     U ] sys-process/cronbase-0.3.2-r1 [0.3.2] 0 kB 
[ebuild     U ] app-portage/portage-utils-0.1.28 [0.1.23] 78 kB 
[ebuild  N    ] net-misc/mDNSResponder-107.6-r5  USE="-debug -doc -java" 1,408 kB 
[ebuild     U ] sys-apps/busybox-1.6.1 [1.4.1-r2] USE="-debug -make-symlinks -savedconfig (-selinux) -static" 1,653 kB 
[ebuild     U ] sys-apps/hdparm-7.7 [6.9] 62 kB 
[ebuild     U ] app-text/dos2unix-3.1-r2 [3.1-r1] 0 kB 
[ebuild     U ] sys-apps/smartmontools-5.37 [5.36-r1] USE="-static" 577 kB 
[ebuild     U ] sys-apps/sdparm-1.01 [1.00] 315 kB 
[ebuild     U ] net-misc/dhcpcd-3.1.5 [3.0.17] USE="-vram%" 40 kB 
[ebuild     U ] sys-apps/ethtool-5 [4] 121 kB 
[ebuild     U ] net-dns/bind-tools-9.4.1_p1 [9.3.4] USE="-idn -ipv6" 6,193 kB 
[ebuild     U ] sys-devel/gettext-0.16.1-r1 [0.16.1] USE="nls -doc -emacs -nocxx" 0 kB 
[ebuild     U ] media-libs/libpng-1.2.18-r1 [1.2.18] USE="-doc" 0 kB 
[ebuild     U ] sys-libs/ncurses-5.6-r1 [5.6] USE="gpm unicode -bootstrap -build -debug -doc -minimal -nocxx -trace" 7 kB 
[ebuild     U ] media-libs/libvorbis-1.2.0 [1.1.2] USE="-doc% (-aotuv%)" 1,186 kB 
[ebuild     U ] sys-kernel/linux-headers-2.6.21 [2.6.17-r2] USE="(-gcc64%)" 4,287 kB 
[ebuild     U ] dev-libs/nss-3.11.7 [3.11.5] USE="-utils%" 3,644 kB 
[ebuild     U ] sys-apps/pciutils-2.2.4-r3 [2.2.3-r2] USE="zlib%* -hal% -network-cron%" 206 kB 
[ebuild     U ] dev-java/java-config-wrapper-0.14 [0.13] 8 kB 
[ebuild     U ] net-nds/portmap-6.0 [5b-r9] USE="tcpd (-selinux)" 22 kB 
[ebuild     U ] sys-devel/m4-1.4.9-r1 [1.4.8] USE="nls -examples%" 596 kB 
[ebuild     U ] app-shells/bash-3.2_p17 [3.2_p15-r1] USE="nls -afs -bashlogger -vanilla" 5 kB 
[ebuild     U ] sys-apps/gawk-3.1.5-r3 [3.1.5-r2] USE="nls" 0 kB 
[ebuild     U ] media-libs/libexif-0.6.16 [0.6.15] USE="nls -doc" 676 kB 
[ebuild     U ] dev-lang/yasm-0.6.2 [0.6.0] USE="nls" 1,230 kB 
[ebuild     U ] dev-libs/libcdio-0.78.2 [0.77] USE="nls -cddb -minimal -nocxx" 1,977 kB 
[ebuild     U ] sys-apps/findutils-4.3.8-r1 [4.3.4] USE="nls (-selinux) -static" 1,766 kB 
[ebuild     U ] net-misc/rsync-2.6.9-r3 [2.6.9-r1] USE="-acl -ipv6 -static -xinetd" 0 kB 
[ebuild     U ] app-editors/nano-2.0.6 [2.0.4] USE="ncurses nls spell -debug -justify -minimal -slang -unicode" 1,285 kB 
[ebuild     U ] app-arch/gzip-1.3.12 [1.3.11] USE="nls -pic -static" 452 kB 
[ebuild     U ] app-arch/tar-1.18-r2 [1.16.1] USE="nls -static" 1,834 kB 
[ebuild     U ] sys-apps/less-406 [394] USE="-unicode" 480 kB 
[ebuild     U ] sys-process/htop-0.6.6 [0.6.5] USE="-debug" 138 kB 
[ebuild     U ] sys-power/powertop-1.8 [1.5] USE="-unicode%" 66 kB 
[ebuild     U ] sys-process/lsof-4.78 [4.77] USE="-static" 739 kB 
[ebuild     U ] sys-libs/readline-5.2_p7 [5.1_p4] 2,008 kB 
[ebuild     U ] sys-devel/bison-2.3 [2.2] USE="nls -static" 1,055 kB 
[ebuild     U ] media-libs/x264-svn-20070924 [20070325] USE="threads -debug" 317 kB 
[ebuild     U ] sys-apps/ed-0.8 [0.4] 67 kB 
[ebuild     U ] dev-util/dialog-1.1.20070704 [1.1.20070227] USE="-examples -unicode" 359 kB 
[ebuild     U ] x11-libs/motif-config-0.9-r1 [0.9] 0 kB 
[ebuild     U ] media-tv/linuxtv-dvb-apps-1.1.1.20070924 [1.1.1.20070114] USE="-usb" 300 kB 
[ebuild     U ] sys-devel/binutils-2.17-r1 [2.16.1-r3] USE="nls -multislot (-multitarget) -test -vanilla" 28 kB 
[ebuild     U ] sys-apps/parted-1.8.8 [1.7.1-r1] USE="nls readline -debug -device-mapper% (-selinux)" 1,518 kB 
[ebuild  NS   ] sys-libs/db-4.5.20_p2  USE="-bootstrap -doc -java -nocxx -tcl -test" 9,068 kB 
[ebuild     U ] sys-apps/man-pages-2.64 [2.44] USE="nls" 1,799 kB 
[ebuild     U ] sys-apps/diffutils-2.8.7-r2 [2.8.7-r1] USE="nls -static" 1,038 kB 
[ebuild  NS   ] dev-libs/apr-util-1.2.8  USE="berkdb -gdbm -ldap -postgres -sqlite -sqlite3" 632 kB 
[ebuild     U ] sys-apps/debianutils-2.17.5 [2.17.4] USE="-static" 132 kB 
[ebuild     U ] sys-devel/autoconf-2.61-r1 [2.61] USE="-emacs" 0 kB 
[ebuild     U ] dev-perl/XML-Parser-2.34-r1 [2.34] USE="(-minimal%)" 0 kB 
[ebuild     U ] sys-devel/libtool-1.5.24 [1.5.22] USE="-vanilla%" 2,852 kB 
[ebuild     U ] gnome-base/gnome-mime-data-2.18.0 [2.4.3] USE="-debug" 593 kB 
[ebuild     U ] dev-perl/DBI-1.55 [1.54] 467 kB 
[ebuild     U ] dev-perl/Event-ExecFlow-0.63 [0.62] 15 kB 
[ebuild     U ] media-libs/alsa-lib-1.0.14a-r1 [1.0.14_rc2] USE="midi%* -alisp% -debug -doc" ALSA_PCM_PLUGINS="adpcm%* alaw%* copy%* dshare%* dsnoop%* extplug%* file%* hooks%* ladspa%* lfloat%* linear%* meter%* mulaw%* multi%* null%* rate%* route%* share%* shm%*" 768 kB 
[ebuild     U ] x11-proto/inputproto-1.4.2.1 [1.4.1] USE="-debug" 47 kB 
[ebuild     U ] media-sound/lame-3.97-r1 [3.97] USE="-debug -mp3rtp (-gtk%)" 0 kB 
[ebuild     U ] x11-libs/xtrans-1.0.4 [1.0.3] USE="-debug" 102 kB 
[ebuild     U ] media-libs/flac-1.2.1-r1 [1.2.1] USE="ogg sse -3dnow (-altivec) -debug -doc (-pic%)" 0 kB 
[ebuild     U ] x11-proto/renderproto-0.9.3 [0.9.2] USE="-debug" 53 kB 
[ebuild     U ] media-libs/libdvdcss-1.2.9-r1 [1.2.9] USE="-doc (-static%)" 0 kB 
[ebuild     U ] sys-apps/coreutils-6.9-r1 [6.7-r1] USE="nls -acl (-selinux) -static -xattr" 5,307 kB 
[ebuild     U ] x11-proto/xf86dgaproto-2.0.3 [2.0.2] USE="-debug" 43 kB 
[ebuild     U ] x11-proto/compositeproto-0.4 [0.3.1] USE="-debug" 45 kB 
[ebuild     U ] media-libs/xvid-1.1.3 [1.1.0-r3] USE="(-altivec) -examples% (-doc%)" 614 kB 
[ebuild     U ] net-dns/libidn-0.6.9-r1 [0.6.5-r1] USE="nls -doc -emacs -java -mono" 2,143 kB 
[ebuild     U ] net-libs/libpcap-0.9.7 [0.9.4] USE="-ipv6" 506 kB 
[ebuild     U ] dev-lang/tcl-8.4.15 [8.4.14] USE="-debug -threads" 3,550 kB 
[ebuild     U ] x11-misc/makedepend-1.0.1 [1.0.0] USE="-debug" 106 kB 
[ebuild  N    ] x11-libs/pixman-0.9.5  USE="-debug" 284 kB 
[ebuild     U ] sys-libs/libieee1284-0.2.8 [0.2.1] USE="-doc" 206 kB 
[ebuild  N    ] dev-libs/libpthread-stubs-0.1  USE="-debug" 190 kB 
[ebuild     U ] media-libs/libdvb-0.5.5.1-r3 [0.5.5.1-r2] USE="-doc" 305 kB 
[ebuild     U ] net-libs/libnfsidmap-0.19 [0.17] USE="-ldap" 319 kB 
[ebuild     U ] app-doc/xorg-docs-1.4-r1 [1.4] USE="-debug -doc" 0 kB 
[ebuild     U ] sci-libs/fftw-3.1.2 [3.0.1-r2] USE="sse* sse2* (-altivec) -test% (-3dnow%) (-mpi%)" 2,673 kB 
[ebuild     U ] sys-process/psmisc-22.5-r2 [22.3] USE="X nls -ipv6 (-selinux)" 271 kB 
[ebuild     U ] sys-apps/lomoco-1.0-r2 [1.0-r1] 24 kB 
[ebuild     U ] dev-util/strace-4.5.15 [4.5.14] USE="-aio -static" 445 kB 
[ebuild     U ] x11-libs/libX11-1.1.3 [1.1.1-r1] USE="-debug -ipv6 -xcb" 1,492 kB 
[ebuild     U ] x11-libs/libICE-1.0.4 [1.0.3] USE="-debug -ipv6" 247 kB 
[ebuild     U ] media-libs/libdvdread-0.9.7 [0.9.6] USE="(-static%)" 380 kB 
[ebuild     U ] media-libs/libsndfile-1.0.17-r1 [1.0.17] USE="alsa flac -sqlite" 0 kB 
[ebuild     U ] net-fs/nfs-utils-1.0.12-r1 [1.0.12] USE="tcpd -kerberos -nonfsv4" 761 kB 
[ebuild     U ] net-misc/whois-4.7.22 [4.7.21] USE="nls" 60 kB 
[ebuild     U ] x11-libs/libXrender-0.9.4 [0.9.2] USE="-debug" 222 kB 
[ebuild     U ] x11-libs/libSM-1.0.3 [1.0.2] USE="-debug -ipv6" 219 kB 
[ebuild     U ] x11-apps/iceauth-1.0.2 [1.0.1] USE="-debug" 95 kB 
[ebuild     U ] x11-apps/xmodmap-1.0.3 [1.0.2] USE="-debug" 101 kB 
[ebuild     U ] x11-apps/sessreg-1.0.3 [1.0.2] USE="-debug" 93 kB 
[ebuild     U ] x11-libs/libXi-1.1.3 [1.1.0] USE="-debug" 243 kB 
[ebuild     U ] x11-libs/libXrandr-1.2.2 [1.2.1] USE="-debug" 220 kB 
[ebuild     U ] x11-libs/libXtst-1.0.3 [1.0.1] USE="-debug" 220 kB 
[ebuild     U ] x11-libs/libXcursor-1.1.9 [1.1.8] USE="-debug" 230 kB 
[ebuild     U ] x11-libs/libXcomposite-0.4.0 [0.3.2] USE="-debug" 213 kB 
[ebuild     U ] x11-libs/libXfont-1.3.1 [1.2.8] USE="-debug -ipv6" 552 kB 
[ebuild     U ] x11-libs/libXxf86dga-1.0.2 [1.0.1] USE="-debug" 213 kB 
[ebuild     U ] x11-apps/setxkbmap-1.0.4 [1.0.2] USE="-debug" 91 kB 
[ebuild     U ] x11-libs/libXpm-3.5.7 [3.5.6] USE="-debug" 350 kB 
[ebuild     U ] x11-libs/startup-notification-0.9 [0.8] 221 kB 
[ebuild     U ] x11-misc/xkeyboard-config-1.1 [0.9] 529 kB 
[ebuild     U ] app-text/poppler-0.5.4-r2 [0.5.4-r1] USE="jpeg zlib -cjk" 0 kB 
[ebuild     U ] media-gfx/imagemagick-6.3.5.10 [6.3.4-r1] USE="X jpeg mpeg perl png tiff zlib -bzip2 -doc -fpx -graphviz -gs -hdri -jbig -jpeg2k -lcms -nocxx -openexr -q32 -q8 -truetype -wmf -xml" 7,394 kB 
[ebuild     U ] dev-lang/tk-8.4.15-r1 [8.4.14] USE="-debug -threads" 3,263 kB 
[ebuild     U ] x11-apps/xrandr-1.2.2 [1.2.0] USE="-debug" 95 kB 
[ebuild     U ] x11-misc/xcompmgr-1.1.3-r1 [1.1.3] USE="-debug%" 78 kB 
[ebuild     U ] x11-libs/libXaw-1.0.4 [1.0.3] USE="-debug -xprint" 506 kB 
[ebuild     U ] x11-apps/xrdb-1.0.4 [1.0.3] USE="-debug" 99 kB 
[ebuild     U ] x11-apps/xprop-1.0.3 [1.0.2] USE="-debug" 105 kB 
[ebuild     U ] x11-apps/xwininfo-1.0.3 [1.0.2] USE="-debug" 97 kB 
[ebuild     U ] x11-apps/xsetroot-1.0.2 [1.0.1] USE="-debug" 87 kB 
[ebuild     U ] media-libs/gd-2.0.35 [2.0.34] USE="jpeg png xpm -fontconfig -truetype" 1,185 kB 
[ebuild     U ] net-misc/nx-3.0.0 [2.1.0-r1] USE="-rdesktop -vnc" 22,000 kB 
[ebuild     U ] x11-apps/xhost-1.0.2 [1.0.1] USE="-debug -ipv6" 96 kB 
[ebuild     U ] x11-apps/xmessage-1.0.2 [1.0.1] USE="-debug -xprint" 93 kB 
[ebuild     U ] x11-terms/xterm-228 [222] USE="-Xaw3d -paste64 -toolbar -truetype -unicode" 822 kB 
[ebuild     U ] x11-apps/xclock-1.0.3 [1.0.2] USE="-debug -xprint" 112 kB 
[ebuild     U ] x11-misc/xdg-utils-1.0.2 [1.0] USE="-doc%" 276 kB 
[ebuild     U ] sci-visualization/gnuplot-4.2.0-r2 [4.0-r1] USE="X readline -doc -emacs -gd -ggi -pdf -plotutils (-svga) -tetex% -wxwindows% -xemacs (-png%*)" 2,771 kB 
[ebuild     U ] x11-wm/fluxbox-1.0_rc3_p5059 [1.0_rc3_p4949] USE="disableslit gnome imlib nls xinerama -disabletoolbar -kde -truetype" 509 kB 
[ebuild     U ] dev-libs/openssl-0.9.8e-r2 [0.9.8d] USE="(sse2*) zlib -bindist -emacs -test" 3,264 kB 
[ebuild     U ] net-misc/rdesktop-1.5.0-r3 [1.5.0-r2] USE="-ao -debug -ipv6 -oss" 240 kB 
[ebuild     U ] dev-lang/swi-prolog-5.6.40 [5.6.32] USE="X berkdb doc readline ssl threads zlib -debug -gmp -java -minimal -odbc -static -tetex" 11,695 kB 
[ebuild     U ] net-misc/curl-7.16.4 [7.15.1-r1] USE="ssl -ares -gnutls -idn -ipv6 -kerberos -ldap -nss% -test (-krb4%)" 1,630 kB 
[ebuild     U ] dev-lang/python-2.4.4-r5 [2.4.4-r4] USE="berkdb gdbm ncurses readline ssl -bootstrap -build -doc -examples -ipv6 -nocxx -nothreads -tk -ucs2" 0 kB 
[ebuild     U ] sys-apps/file-4.21-r1 [4.21] USE="python" 0 kB 
[ebuild     U ] dev-python/sip-4.7 [4.5.2-r1] USE="-debug" 429 kB 
[ebuild     U ] dev-util/scons-0.97 [0.96.1] 430 kB 
[ebuild     U ] media-gfx/fontforge-20070831 [20060703-r1] USE="X gif jpeg nls%* png python%* tiff -svg -truetype -unicode" 4,133 kB 
[ebuild     U ] dev-libs/libxslt-1.1.20-r1 [1.1.20] USE="crypt python -debug" 0 kB 
[ebuild     U ] app-admin/eselect-1.0.10 [1.0.7] USE="-bash-completion -doc -vim-syntax%" 150 kB 
[ebuild     U ] net-misc/neon-0.26.3 [0.26.1-r1] USE="nls ssl zlib -expat -socks5 (-static%)" 771 kB 
[ebuild     U ] media-libs/libsvg-0.1.4 [0.1.2] 359 kB 
[ebuild     U ] sys-devel/autogen-5.8.8 [5.7.1] 1,269 kB 
[ebuild  N    ] x11-proto/xcb-proto-1.0  USE="-debug" 70 kB 
[ebuild  NS   ] app-emulation/emul-linux-x86-java-1.6.0.02  USE="X alsa nsplugin" 57,040 kB 
[ebuild     U ] app-emulation/emul-linux-x86-java-1.5.0.12 [1.5.0.11] USE="X alsa nsplugin" 48,483 kB 
[ebuild     U ] app-text/gnome-doc-utils-0.10.3 [0.8.0] USE="-debug" 442 kB 
[ebuild     U ] dev-util/subversion-1.3.2-r4 [1.3.2-r3] USE="berkdb nls perl python zlib -apache2 -bash-completion -emacs -java -nowebdav -ruby" 0 kB 
[ebuild     U ] sys-apps/shadow-4.0.18.1-r1 [4.0.18.1] USE="cracklib nls pam -nousuid (-selinux) -skey" 0 kB 
[ebuild     U ] net-misc/netkit-rsh-0.17-r8 [0.17-r7] USE="pam" 14 kB 
[ebuild     U ] app-admin/eselect-oodict-20061117 [20060706] 4 kB 
[ebuild  N    ] x11-libs/libxcb-1.0  USE="-debug" 410 kB 
[ebuild     U ] net-misc/openssh-4.7_p1-r1 [4.5_p1-r1] USE="X pam tcpd -X509 -chroot -hpn -kerberos -ldap -libedit (-selinux) -skey -smartcard -static" 968 kB 
[ebuild     U ] media-sound/esound-0.2.38 [0.2.36-r2] USE="alsa tcpd -debug -ipv6" 385 kB 
[ebuild     U ] media-libs/mesa-7.0.1 [6.5.2-r1] USE="nptl -debug -doc -hardened -motif -xcb" VIDEO_CARDS="-i810 -mach64 -mga -none -r128 -radeon -s3virge -savage -sis (-sunffb) -tdfx -trident -via" 3,266 kB 
[ebuild     U ] x11-apps/xinit-1.0.5-r1 [1.0.3-r4] USE="-debug -hal% -minimal" 105 kB 
[ebuild     U ] x11-misc/icon-naming-utils-0.8.2-r1 [0.8.1] 65 kB 
[ebuild     U ] media-libs/libsdl-1.2.12 [1.2.11-r2] USE="X alsa opengl xinerama xv -aalib -arts -dga -directfb -esd -fbcon -ggi -libcaca -nas -noaudio -noflagstrip -nojoystick -novideo -oss (-svga)" 2,764 kB 
[ebuild     U ] x11-themes/gnome-icon-theme-2.18.0 [2.16.1] USE="-debug" 2,671 kB 
[ebuild  N    ] x11-libs/fltk-1.1.7-r2  USE="opengl -debug -noxft" 2,013 kB 
[ebuild     U ] media-libs/smpeg-0.4.4-r9 [0.4.4-r8] USE="X opengl -debug (-mmx) (-gtk%*)" 312 kB 
[ebuild     U ] media-libs/openal-0.0.8-r2 [0.0.8-r1] USE="alsa mp3 sdl vorbis -arts -debug -esd" 0 kB 
[ebuild     U ] media-libs/sdl-net-1.2.6 [1.2.5] 364 kB 
[ebuild     U ] media-libs/devil-1.6.7-r2 [1.6.7-r1] USE="X gif jpeg opengl png sdl tiff xpm -allegro -mng" 0 kB 
[ebuild     U ] x11-apps/mesa-progs-7.0.1 [6.5.2] 1,310 kB 
[ebuild     U ] dev-python/pycairo-1.4.0 [1.2.2] USE="-examples% (-numeric%)" 469 kB 
[ebuild     U ] dev-games/cegui-0.5.0b-r3 [0.5.0b-r2] USE="opengl -devil -doc -examples -expat -lua -xerces-c -xml (-freeimage%)" 0 kB 
[ebuild     U ] dev-perl/Cairo-1.04.0 [1.02.1] 46 kB 
[ebuild     U ] media-libs/openexr-1.4.0a [1.2.2-r2] USE="opengl%* -doc -examples" VIDEO_CARDS="nvidia%*" 9,447 kB 
[ebuild     U ] media-gfx/blender-2.45 [2.44] USE="jpeg nls png sdl -blender-game -ffmpeg -openal -openexr -verse%" 13,894 kB 
[ebuild     U ] sys-fs/udev-114 [104-r12] USE="(-selinux)" 195 kB 
[ebuild  NS   ] sys-kernel/gentoo-sources-2.6.22-r8  USE="-build -symlink" 44,198 kB 
[ebuild     U ] media-sound/alsa-utils-1.0.14 [1.0.14_rc2-r3] USE="midi nls" 991 kB 
[ebuild     U ] media-gfx/sane-backends-1.0.18-r4 [1.0.18-r2] USE="gphoto2 usb -ipv6 -v4l" 3,709 kB 
[ebuild     U ] sys-fs/fuse-2.7.0 [2.6.4-r1] 491 kB 
[ebuild     U ] sys-fs/cryptsetup-luks-1.0.4-r3 [1.0.3-r2] USE="nls -build% -dynamic (-selinux)" 300 kB 
[ebuild     U ] net-libs/libnfnetlink-0.0.30 [0.0.25] 219 kB 
[ebuild     U ] net-firewall/iptables-1.3.8-r1 [1.3.5-r4] USE="-extensions -imq -ipv6 -l7filter -static" 169 kB 
[ebuild     U ] net-libs/libnetfilter_queue-0.0.15 [0.0.13] 216 kB 
[ebuild     U ] dev-libs/glib-2.14.1 [2.12.12] USE="-debug -doc -hardened" 3,260 kB 
[ebuild     U ] x11-libs/pango-1.18.2 [1.14.10] USE="-debug -doc" 1,361 kB 
[ebuild     U ] dev-libs/dbus-glib-0.74 [0.73] USE="-debug -doc (-selinux)" 640 kB 
[ebuild     U ] dev-libs/atk-1.18.0 [1.12.4] USE="-debug -doc" 641 kB 
[ebuild     U ] media-libs/gstreamer-0.10.14 [0.10.11] 1,958 kB 
[ebuild     U ] dev-libs/liboil-0.3.12 [0.3.10-r1] USE="-doc" 792 kB 
[ebuild     U ] dev-libs/libIDL-0.8.8 [0.8.7] USE="-debug" 328 kB 
[ebuild     U ] x11-misc/shared-mime-info-0.22 [0.20] 408 kB 
[ebuild     U ] dev-util/desktop-file-utils-0.14 [0.12] USE="-emacs%" 341 kB 
[ebuild     U ] gnome-base/libgtop-2.14.9 [2.14.6] USE="X -debug -gdbm (-static%)" 755 kB 
[ebuild     U ] x11-libs/libxklavier-3.2 [3.1] USE="-doc" 456 kB 
[ebuild     U ] app-admin/gamin-0.1.9 [0.1.8] USE="-debug (-doc%)" 631 kB 
[ebuild     U ] dev-python/pygobject-2.14.0 [2.12.3] USE="-debug -doc -examples%" 353 kB 
[ebuild     U ] net-wireless/bluez-utils-3.19 [3.12] USE="alsa%* usb -cups -debug -examples -hal -old-daemons -test-programs" 869 kB 
[ebuild     U ] gnome-base/orbit-2.14.8-r3 [2.14.7] USE="-debug -doc" 726 kB 
[ebuild     U ] dev-python/dbus-python-0.82.2 [0.81.0] USE="-test%" 478 kB 
[ebuild  N    ] sys-auth/consolekit-0.2.1  USE="pam -debug" 445 kB 
[ebuild     U ] x11-wm/openbox-3.4.4 [3.3.1] USE="nls xinerama -startup-notification (-pango%*)" 731 kB 
[ebuild     U ] gnome-base/libbonobo-2.18.0 [2.16.0] USE="-debug -doc" 1,408 kB 
[ebuild     U ] dev-python/pyorbit-2.14.3 [2.14.1] USE="-debug" 278 kB 
[ebuild     U ] x11-libs/gtk+-2.12.0-r2 [2.10.13] USE="X cups%* jpeg tiff xinerama -debug -doc" 15,364 kB 
[ebuild     U ] gnome-base/gconf-2.18.0.1 [2.14.0] USE="-debug -doc" 1,317 kB 
[ebuild     U ] gnome-base/libglade-2.6.1 [2.6.0] USE="-debug -doc" 339 kB 
[ebuild     U ] x11-libs/libwnck-2.18.3 [2.18.2] USE="-debug -doc" 471 kB [1]
[ebuild     U ] gnome-base/gnome-keyring-0.8.1 [0.6.0] USE="-debug" 439 kB 
[ebuild     U ] x11-themes/gtk-engines-2.10.2 [2.8.2-r1] USE="-accessibility -debug -static" 640 kB 
[ebuild     U ] net-ftp/gftp-2.0.18-r6 [2.0.18-r4] USE="gtk ssl" 1,343 kB 
[ebuild     U ] net-www/nspluginwrapper-0.9.91.5 [0.9.91.4] 267 kB 
[ebuild     U ] x11-misc/fbpanel-4.12 [4.3] 175 kB 
[ebuild     U ] dev-cpp/libglademm-2.6.3 [2.6.2] USE="-debug -doc% -examples%" 548 kB 
[ebuild     U ] dev-cpp/gconfmm-2.18.0 [2.12.0] USE="-debug -doc% -examples%" 286 kB 
[ebuild     U ] x11-misc/notification-daemon-0.3.7 [0.3.6-r1] USE="-debug" 0 kB 
[ebuild     U ] x11-libs/libgksu-2.0.5 [2.0.0] USE="nls -debug -doc" 486 kB 
[ebuild     U ] x11-themes/gnome-themes-2.18.1 [2.16.3] USE="-accessibility -debug" 2,373 kB 
[ebuild     U ] x11-misc/xscreensaver-5.02-r2 [5.02] USE="gnome jpeg opengl pam xinerama -insecure-savers -new-login -offensive" 5,246 kB 
[ebuild     U ] x11-misc/obconf-2.0.1 [1.6] USE="nls%*" 200 kB 
[ebuild     U ] x11-libs/libnotify-0.4.4 [0.4.3] USE="-doc" 387 kB 
[ebuild     U ] dev-cpp/libgnomecanvasmm-2.16.0 [2.12.0] USE="-debug -doc -examples%" 327 kB 
[ebuild     U ] gnome-base/gail-1.18.0 [1.9.3] USE="-debug -doc" 596 kB 
[ebuild     U ] gnome-extra/zenity-2.18.2 [2.16.3] USE="-debug -libnotify" 1,712 kB 
[ebuild     U ] media-video/cinelerra-cvs-20070726 [20070122] USE="alsa opengl (-3dnow) (-altivec) -css -esd -ieee1394 (-mmx) -oss -static -truetype" 23,248 kB 
[ebuild     U ] dev-java/sun-jdk-1.5.0.13 [1.5.0.11-r1] USE="X alsa -doc -examples -jce (-nsplugin)" 42,830 kB 
[ebuild     U ] dev-java/xml-commons-external-1.3.04 [1.3.02-r1] USE="-doc -source" 645 kB 
[ebuild     U ] dev-java/lucene-1.4.3-r3 [1.4.3-r2] USE="-doc -examples% -source -test" 0 kB 
[ebuild     U ] dev-java/jsch-0.1.34 [0.1.33] USE="-doc -examples -source" 259 kB 
[ebuild     U ] app-benchmarks/bootchart-0.9-r2 [0.9-r1] USE="java -acct -debug -doc -source" 0 kB 
[ebuild     U ] gnome-base/gnome-vfs-2.18.1 [2.16.3-r1] USE="avahi hal samba ssl -debug -doc -gnutls -ipv6" 1,872 kB 
[ebuild     U ] gnome-base/libgnome-2.18.0 [2.16.0] USE="-debug -doc -esd (-static%)" 1,058 kB 
[ebuild     U ] dev-cpp/gnome-vfsmm-2.18.0 [2.16.0] USE="-debug -doc -examples" 338 kB 
[ebuild     U ] gnome-extra/gnome-system-monitor-2.18.2 [2.16.1] USE="-debug" 1,694 kB 
[ebuild     U ] dev-cpp/libgnomemm-2.18.0 [2.12.2] USE="-debug" 247 kB 
[ebuild     U ] gnome-base/libgnomeui-2.18.1 [2.16.1] USE="jpeg -debug -doc" 1,428 kB 
[ebuild     U ] gnome-base/gnome-desktop-2.18.3 [2.16.3] USE="-debug -doc" 1,277 kB 
[ebuild     U ] gnome-extra/evolution-data-server-1.10.3.1 [1.8.2] USE="ssl -debug -doc -ipv6 -kerberos -keyring -krb4 -ldap (-nntp%)" 6,953 kB 
[ebuild     U ] www-client/mozilla-firefox-2.0.0.7 [2.0.0.4] USE="gnome java xinerama -bindist -debug -filepicker -ipv6 -mozdevelop -moznopango -restrict-javascript -xforms -xprint" LINGUAS="en_GB -af -ar -be -bg -ca -cs -da -de -el -es -es_AR -es_ES -eu -fi -fr -fy -fy_NL -ga -ga_IE -gu -gu_IN -he -hu -it -ja -ka -ko -ku -lt -mk -mn -nb -nb_NO -nl -nn -nn_NO -pa -pa_IN -pl -pt -pt_BR -pt_PT -ro -ru -sk -sl -sv -sv_SE -tr -zh -zh_CN -zh_TW" 36,702 kB 
[ebuild     U ] dev-libs/gdl-0.7.6 [0.7.1] USE="gnome%* -debug" 439 kB 
[ebuild     U ] mail-client/mozilla-thunderbird-2.0.0.6 [2.0.0.4] USE="gnome xinerama -bindist -crypt -debug -ipv6 -ldap -mozdom -moznopango -replytolist -xprint" LINGUAS="en_GB -be -bg -ca -cs -da -de -el -es -es_AR -es_ES -eu -fi -fr -ga -ga_IE -hu -it -ja -lt -mk -nb -nb_NO -nl -nn -nn_NO -pa -pa_IN -pl -pt -pt_BR -pt_PT -ru -sk -sl -sv -sv_SE -tr -zh -zh_CN -zh_TW" 36,753 kB 
[ebuild     U ] dev-cpp/libgnomeuimm-2.18.0 [2.12.0] USE="-debug" 342 kB 
[ebuild     U ] gnome-extra/gconf-editor-2.18.2 [2.16.0] USE="-debug" 902 kB 
[ebuild     U ] gnome-extra/gcalctool-5.9.14 [5.8.25-r1] USE="-debug" 1,162 kB 
[ebuild     U ] gnome-extra/yelp-2.18.1 [2.16.2] USE="-beagle -debug -xulrunner%" 880 kB 
[ebuild     U ] sys-libs/glibc-2.6.1 [2.5-r4] USE="nls -debug -glibc-compat20 -glibc-omitfp (-hardened) (-multilib) -profile (-selinux) (-build%) (-nptl%*) (-nptlonly%*)" 16,006 kB 
[ebuild  NS   ] sys-devel/gcc-4.2.0  USE="fortran gtk mudflap nls openmp (-altivec) -bootstrap -build -doc -gcj (-hardened) -ip28 -ip32r10k (-multilib) -multislot (-n32) (-n64) -nocxx -objc -objc++ -objc-gc -test -vanilla" 43,093 kB 
[ebuild     U ] app-cdr/cdrtools-2.01.01_alpha34 [2.01.01_alpha27] USE="-unicode" 1,623 kB 
[ebuild     U ] media-video/transcode-1.0.4 [1.0.3] USE="a52 dvdread iconv jpeg mmx mp3 mpeg ogg quicktime sdl sse sse2 vorbis xvid -3dnow -X (-altivec) -dv -extrafilters -fame -imagemagick -lzo -mjpeg -network -oss% -theora -truetype -v4l2 -xml (-gtk%*)" 1,944 kB 
[ebuild     U ] net-wireless/wireless-tools-29_pre22 [28] USE="nls -multicall" 288 kB 
[ebuild     U ] dev-libs/boehm-gc-6.8 [6.7] USE="-nocxx -threads" 740 kB 
[ebuild     U ] app-admin/conky-1.4.6 [1.4.5] USE="X -audacious (-bmpx) -hddtemp -ipv6 -mpd -truetype -vim-syntax" 400 kB 
[ebuild     U ] media-sound/mpc-0.12.1 [0.12.0] USE="nls -bash-completion" 92 kB 
[ebuild     U ] app-arch/rar-3.7.0 [3.7.0_beta1] 758 kB 
[ebuild     U ] dev-java/sun-jdk-1.6.0.03 [1.6.0.01] USE="X alsa -doc -examples -jce (-nsplugin)" 60,724 kB 
[ebuild     U ] dev-python/pygtk-2.12.0 [2.10.4] USE="opengl -doc -examples" 2,105 kB 
[ebuild     U ] gnome-base/gnome-menus-2.18.3-r1 [2.16.1] USE="python%* -debug" 428 kB 
[ebuild     U ] x11-libs/vte-0.16.8 [0.14.2] USE="opengl python -debug -doc" 1,087 kB 
[ebuild     U ] dev-util/git-1.5.2.5 [1.5.1.6] USE="gtk perl -bash-completion -curl -doc -emacs -mozsha1 (-ppcsha1) -tk -webdav" 1,302 kB 
[ebuild     U ] gnome-base/librsvg-2.16.1-r2 [2.16.1-r1] USE="gnome zlib -debug -doc" 0 kB 
[ebuild     U ] x11-terms/gnome-terminal-2.18.1 [2.16.1] USE="-debug" 1,949 kB 
[ebuild     U ] gnome-base/gdm-2.18.4 [2.16.4] USE="pam tcpd xinerama -accessibility -branding% -debug -ipv6 (-selinux)" 3,379 kB 
[ebuild     U ] net-print/cups-1.2.10-r1 [1.2.9] USE="X dbus jpeg nls pam png ppds samba ssl tiff -ldap -php -slp" 3,534 kB 
[ebuild     U ] net-misc/nxclient-3.0.0-r3 [2.1.0-r1] 3,962 kB 
[ebuild     U ] gnome-base/libgnomeprint-2.18.1 [2.12.1] USE="cups -debug -doc" 850 kB 
[ebuild     U ] media-video/mplayer-1.0_rc1_p20070927-r1 [1.0_rc1_p20070824] USE="X a52 aac alsa dts dvb dvd encode gif gtk iconv jpeg mmx mp3 openal opengl png quicktime real samba sdl sse sse2 theora vorbis x264 xinerama xv xvid xvmc -3dnow -3dnowext -aalib (-altivec) -amrnb -amrwb -arts -bidi -bindist -bl -cddb -cdio -cdparanoia -cpudetection -custom-cflags -dga -directfb -doc -dv -enca -esd -fbcon -ftp -ggi -ipv6 -ivtv -jack -joystick -libcaca -lirc -live -livecd -lzo -mad -md5sum -mmxext -mp2 -musepack -nas -nemesi% -oss -pnm -pvr -radio -rar -rtc -speex -srt -ssse3 (-svga) -teletext -tga -tivo -truetype -unicode -v4l -v4l2 (-vidix) (-win32codecs) -xanim -zoran" VIDEO_CARDS="vesa -mga -s3virge -tdfx (-i810%) (-nvidia%*)" 7,562 kB 
[ebuild     U ] media-libs/xine-lib-1.1.8 [1.1.4-r2] USE="X a52 aac alsa dts dvd flac gnome gtk mad nls opengl samba sdl vorbis xinerama xv xvmc -aalib (-altivec) -arts -debug -directfb -dxr3 -esd -fbcon -imagemagick -ipv6 -jack% -libcaca -mmap -mng -modplug -musepack -oss -pulseaudio -real% -speex -theora -truetype -v4l -vcd (-vidix) -wavpack (-win32codecs) -xcb" 7,115 kB 
[ebuild     U ] net-misc/nxserver-freenx-0.7.0-r1 [0.6.0] USE="nxclient -arts -cups -esd" 57 kB 
[ebuild     U ] net-fs/fusesmb-0.8.7 [0.8.5] 118 kB 
[ebuild     U ] gnome-base/libgnomeprintui-2.18.0 [2.12.1] USE="-debug -doc" 642 kB 
[ebuild     U ] dev-util/codeblocks-1.0_pre20070618 [1.0_pre20070404] USE="-contrib -debug -unicode" 8,364 kB 
[ebuild     U ] sys-apps/hal-0.5.9.1-r2 [0.5.9-r1] USE="crypt -acpi -debug -dell -disk-partition -doc -pcmcia (-selinux)" 1,564 kB 
[ebuild     U ] media-gfx/gimp-2.4.0_rc3 [2.3.16] USE="alsa dbus%* gnome jpeg mmx png python sse svg tiff wmf -aalib (-altivec) -curl -debug -doc -gtkhtml -lcms -mng -pdf -smp" 16,745 kB 
[ebuild     U ] app-misc/hal-info-20070618 [20070425] 117 kB 
[ebuild  N    ] x11-libs/e_dbus-9999  USE="X nls -doc" 0 kB [2]
[ebuild     U ] sys-apps/pmount-0.9.16 [0.9.13] USE="crypt hal" 425 kB 
[ebuild     U ] app-emulation/wine-0.9.46 [0.9.41] USE="X alsa cups dbus hal jpeg ncurses opengl -esd -jack -lcms -ldap -nas -oss -scanner -xml" 12,162 kB 
[ebuild     U ] x11-libs/qt-3.3.8-r4 [3.3.8-r2] USE="cups gif mysql opengl xinerama -debug -doc -examples (-firebird) -immqt -immqt-bc -ipv6 -nas -nis -odbc -postgres -sqlite (-pertty%) (-qt-copy%)" 16,986 kB 
[ebuild     U ] dev-python/PyQt-3.17.3 [3.17] USE="-debug -doc -examples" 786 kB 
[ebuild     U ] net-print/hplip-2.7.7-r3 [1.7.4a-r1] USE="X ppds scanner snmp -doc% -fax -minimal% -parport (-cups%*) (-foomaticdb%*) (-qt3%*)" 14,076 kB 
[ebuild     U ] gnome-base/libbonoboui-2.18.0 [2.16.0] USE="X -debug -doc" 959 kB 
[ebuild     U ] dev-python/gnome-python-2.18.2 [2.16.2] USE="-debug -doc" 407 kB 
[ebuild     U ] gnome-base/gnome-panel-2.18.3 [2.16.3] USE="eds -debug -doc" 2,659 kB 
[ebuild     U ] dev-libs/gnome-build-0.1.7 [0.1.4] USE="-debug" 465 kB 
[ebuild     U ] dev-util/anjuta-2.2.0-r1 [2.1.1_beta1] USE="inherit-graph sourceview subversion valgrind -debug -devhelp% -doc -glade" 5,406 kB 
[ebuild     U ] dev-util/meld-1.1.5.1 [1.1.4-r1] USE="-debug -doc -gnome" 589 kB 
[ebuild     U ] gnome-base/nautilus-2.18.3 [2.16.3] USE="X gnome -beagle -debug" 4,230 kB 
[ebuild     U ] gnome-extra/nautilus-sendto-0.12-r1 [0.10] USE="bluetooth eds thunderbird -debug -gajim -pidgin% -sylpheed (-gaim%)" 329 kB 
[ebuild     U ] app-arch/file-roller-2.18.4 [2.16.3] USE="gnome -debug" 1,148 kB 
[ebuild     U ] media-libs/gst-plugins-base-0.10.14 [0.10.11] USE="X alsa xv -debug -esd -oss" 1,588 kB 
[ebuild     U ] media-libs/gst-plugins-good-0.10.6 [0.10.4] USE="-debug" 1,540 kB 
[ebuild     U ] media-plugins/gst-plugins-ffmpeg-0.10.2 [0.10.1-r1] 2,457 kB 
[ebuild     U ] media-plugins/gst-plugins-alsa-0.10.14 [0.10.11] 0 kB 
[ebuild     U ] media-plugins/gst-plugins-xvideo-0.10.14 [0.10.11] 0 kB 
[ebuild     U ] media-plugins/gst-plugins-x-0.10.14 [0.10.11] 0 kB 
[ebuild     U ] dev-db/mysql-5.0.44-r1 [5.0.42] USE="berkdb perl ssl -big-tables -cluster -debug -embedded -extraengine -latin1 -max-idx-128 -minimal (-selinux) -static" 23,869 kB 
[ebuild     U ] x11-libs/qt-4.3.1-r1 [4.3.0] USE="cups dbus gif jpeg mysql opengl png qt3support ssl tiff xinerama zlib -accessibility -debug -doc -examples (-firebird) -glib -mng -nas -nis -odbc -pch -postgres -sqlite -sqlite3" INPUT_DEVICES="-wacom" 42,109 kB 
[ebuild     U ] dev-perl/DBD-mysql-4.00.5 [3.0008] 120 kB 
[ebuild     U ] net-dns/avahi-0.6.21 [0.6.20] USE="dbus gtk python qt3 qt4 -autoipd -bookmarks -doc -gdbm -howl-compat -ipv6% -mdnsresponder-compat -mono -test" 954 kB 
[ebuild     UD] net-wireless/wpa_supplicant-0.5.8 [0.6.0] USE="dbus qt4 readline ssl -gnutls -gsm -madwifi -qt3" 698 kB 
[ebuild     U ] app-text/evince-0.8.3 [0.6.1-r3] USE="dbus gnome tiff -debug -djvu -doc -dvi -t1lib" 1,480 kB 
[ebuild     U ] media-plugins/alsa-plugins-1.0.14 [1.0.14_rc3] USE="pulseaudio -debug -ffmpeg -jack -libsamplerate" 299 kB 
[ebuild     U ] x11-plugins/beryl-plugins-0.2.1-r1 [0.2.1] USE="dbus" 0 kB 
[ebuild     U ] gnome-base/eel-2.18.3 [2.16.3] USE="X -debug" 629 kB 
[ebuild     U ] x11-drivers/xf86-input-mouse-1.2.2 [1.2.1] USE="-debug" 268 kB 
[ebuild     U ] x11-drivers/xf86-video-nv-2.1.5 [2.0.2] USE="-debug" 365 kB 
[ebuild     U ] app-editors/gedit-2.18.2-r1 [2.16.2-r1] USE="spell -acl% -debug -doc -python" 3,374 kB 
[ebuild     U ] app-editors/vim-core-7.1.042 [7.0.235] USE="nls -acl -bash-completion -livecd" 8,642 kB 
[ebuild     U ] app-editors/gvim-7.1.042 [7.0.235] USE="gnome gpm gtk nls perl python -acl (-aqua) -bash-completion -cscope -motif -netbeans -nextaw -ruby" 0 kB 
[ebuild     U ] app-vim/gentoo-syntax-20070506 [20051221-r1] USE="-ignore-glep31" 19 kB 
[ebuild     U ] net-misc/vnc-4.1.2-r4 [4.1.2-r3] USE="server" 16 kB 
[ebuild     U ] dev-lang/php-5.2.4_p20070914-r2 [5.2.2-r1] USE="berkdb cgi cli crypt iconv ncurses nls pcre readline reflection session spell spl ssl xpm zlib (-adabas) -apache2 -bcmath (-birdstep) -bzip2 -calendar -cdb -cjk -concurrentmodphp -ctype -curl -curlwrappers -db2 -dbase (-dbmaker) -debug -discard-path -doc (-empress) (-empress-bcs) (-esoob) -exif -fastbuild (-fdftk) -filter (-firebird) -flatfile -force-cgi-redirect (-frontbase) -ftp -gd -gd-external -gdbm -gmp -hash -imap -inifile -interbase -iodbc -ipv6 -java-external -json -kerberos -ldap -ldap-sasl -libedit -mcve -mhash -msql -mssql -mysql -mysqli -oci8 -oci8-instant-client -odbc -pcntl -pdo -pdo-external -pic -posix -postgres -qdbm -recode -sapdb -sharedext -sharedmem -simplexml -snmp -soap -sockets (-solid) -sqlite -suhosin (-sybase) (-sybase-ct) -sysvipc -threads -tidy -tokenizer -truetype -unicode -wddx -xml -xmlreader -xmlrpc -xmlwriter -xsl -yaz -zip -zip-external" 7,118 kB 
[ebuild     U ] www-servers/lighttpd-1.4.18 [1.4.15] USE="pcre php ssl -bzip2 -doc -fam -fastcgi -gdbm -ipv6 -ldap -lua -memcache -minimal -mysql -rrdtool -test -webdav -xattr" 587 kB 
[ebuild     U ] gnome-base/gnome-session-2.18.3 [2.16.3] USE="branding tcpd -debug -esd -ipv6" 700 kB 
[ebuild     U ] x11-base/xorg-server-1.4-r1 [1.3.0.0] USE="dmx dri nptl sdl xorg (-3dfx) -debug -hal% -ipv6 -kdrive -minimal -xprint" INPUT_DEVICES="evdev keyboard mouse -acecad -aiptek -calcomp -citron -digitaledge -dmc -dynapro -elo2300 -elographics -fpit -hyperpen -jamstudio -joystick -magellan -microtouch -mutouch -palmax -penmount -spaceorb -summa -synaptics -tek4957 -ur98 -vmmouse -void -wacom" VIDEO_CARDS="nv nvidia vesa vga (-amd) -apm -ark -chips -cirrus -cyrix -dummy -epson -fbdev -glint -i128 (-i740) -i810 (-impact) (-imstt) -mach64 -mga -neomagic (-newport) (-nsc) -r128 -radeon -rendition -s3 -s3virge -savage -siliconmotion -sis -sisusb (-sunbw2) (-suncg14) (-suncg3) (-suncg6) (-sunffb) (-sunleo) (-suntcx) -tdfx -tga -trident -tseng -v4l (-vermilion) -via -vmware -voodoo (-xgi) (-fglrx%)" 6,035 kB 
[ebuild     U ] x11-drivers/xf86-input-keyboard-1.2.2 [1.1.1] USE="-debug" 240 kB 
[ebuild     U ] x11-drivers/xf86-input-keyboard-1.1.1-r1 [1.1.1] USE="-debug" 0 kB 
[ebuild     U ] dev-python/gnome-python-extras-2.14.2-r1 [2.14.0-r1] USE="X -debug -doc -firefox -seamonkey -xulrunner%" 344 kB 
[ebuild     U ] x11-base/xorg-x11-7.3 [7.2] 0 kB 
[ebuild     U ] media-tv/mythtv-0.20.2_p14498 [0.20_p13288] USE="alsa dvb dvd mmx opengl perl vorbis xvmc (-altivec) -autostart -backendonly -crciprec -dbox2 -debug -directv% -dts -freebox -frontendonly* -hdhomerun -ieee1394 -ivtv -jack -joystick -lcd -lirc" VIDEO_CARDS="nvidia -i810 -via" 0 kB 
[ebuild     U ] x11-themes/mythtv-themes-0.20.2_p14301 [0.20] 0 kB 
[ebuild     U ] media-plugins/mythvideo-0.20.2_p14282 [0.20_p12824] USE="mplayer -debug (-mmx) -xine" 0 kB 
[ebuild     U ] app-dicts/aspell-en-6.0.0 [0.51.1] 179 kB 
[ebuild     U ] app-text/aspell-0.60.5 [0.50.5-r4] USE="gpm nls%* -examples%" 1,714 kB 
[ebuild     U ] kde-base/kdelibs-3.5.7-r3 [3.5.5-r10] USE="alsa cups spell tiff xinerama -acl -arts -avahi -branding% -debug -doc -fam -jpeg2k -kdeenablefinal -kdehiddenvisibility -kerberos -legacyssl -lua -openexr -utempter (-ssl%*) (-zeroconf%)" LINGUAS="(-he%)" 15,236 kB 
[ebuild     U ] kde-base/kdesu-3.5.7 [3.5.5] USE="xinerama -arts -debug -kdeenablefinal -kdehiddenvisibility" 23,832 kB 
[ebuild     U ] kde-base/kate-3.5.7-r1 [3.5.5-r1] USE="xinerama -arts -debug -kdeenablefinal -kdehiddenvisibility" 20 kB 
[ebuild     U ] gnome-base/control-center-2.18.1 [2.16.3] USE="alsa eds -debug -esd% -hal" 2,100 kB 
[ebuild  N    ] gnome-base/libgnomekbd-2.18.2  USE="-debug" 352 kB 
[ebuild     U ] gnome-base/gnome-light-2.18.3 [2.16.3] 0 kB 
[blocks B     ] net-dns/avahi (is blocking net-misc/mDNSResponder-107.6-r5)
[blocks B     ] <gnome-base/control-center-2.17.0 (is blocking gnome-base/libgnomekbd-2.18.2)
[blocks B     ] =app-dicts/aspell-en-0.5* (is blocking app-text/aspell-0.60.5)
[blocks B     ] net-misc/mDNSResponder (is blocking net-dns/avahi-0.6.20, net-dns/avahi-0.6.21)

Total: 332 packages (316 upgrades, 1 downgrade, 10 new, 5 in new slots, 4 blocks), Size of downloads: 947,731 kB

```

Any guesses at how long its going to take to recompile everything? (answer, so long that im not going to bother until i get a new PC in a few months time :P)

---

### Post by Bachstelze on 2007-10-01
As you can see, the're mostly small libs. How long it will take will depend on your computer but if would take roughly 5~6 hours on mine.

---

### Post by yabbadabbadont on 2007-10-01
A lot of that looks like a Gnome upgrade.  Since you have both Fluxbox and Openbox installed, perhaps Gnome is unnecessary?  ;)

---

### Post by MrHippocampus on 2007-10-01
Thats partly the reason I want to just start again, i really don't use gnome that much but as you can see it has so many packages intertwined with my system (along with other programs that I don't use). And I do like flux/openbox, but whenever other people try and use my PC they tend to get a bit stuck :lolflag:

The one thing I do dislike about portage is thats it isn't that easy to remove a whole set of pacakges, e.g. I could unmerge gnome-light, then do a depclean, but that always removes packages I don't want to remove, then I have to revdep-rebuild, and then I still end up with broken applications and bits of gnome lying around and packages removed which I didn't want removed :( portage really needs to be able to handle removing large sets of pacakges better (aparently paludis handles this well, so I might start off with that next time).

---

### Post by Krieg on 2007-10-10
I used Gentoo heavily for a couple of years, at the end it was a nightmare.   USE variable ... DO NOT WANT!

---

### Post by drbob07 on 2007-10-14
I wanted to try Gentoo, but, I could not get it working with my wireless card for the install. I finally settled on Ubuntu, and, I can't be happier.

---

### Post by raul_ on 2007-10-21
I tried Sabayon (which is Gentoo no matter what), and when I tried to install Firefox and it's dependencies it was already on 40 min before i gave up and reinstalled Arch

---

### Post by Bachstelze on 2007-10-21
```
firas@Nobue ~ $ sudo splat mozilla-firefox
 * www-client/mozilla-firefox-2.0.0.7

        Emerged at: Sun Oct 14 22:47:46 2007
        Build time: 25 minutes, and 34 seconds

 * www-client/mozilla-firefox-2.0.0.8

        Emerged at: Fri Oct 19 22:50:53 2007
        Build time: 25 minutes, and 10 seconds

```

I love my new Athlon FX-62 :D

---

### Post by raul_ on 2007-10-21
> **HymnToLife said:**
> ```
firas@Nobue ~ $ sudo splat mozilla-firefox
 * www-client/mozilla-firefox-2.0.0.7

        Emerged at: Sun Oct 14 22:47:46 2007
        Build time: 25 minutes, and 34 seconds

 * www-client/mozilla-firefox-2.0.0.8

        Emerged at: Fri Oct 19 22:50:53 2007
        Build time: 25 minutes, and 10 seconds

```

I love my new Athlon FX-62 :D

Nice :) what about all the other dependencies?

Anyway, 25 is still a bit :)

---

### Post by rsambuca on 2007-10-21
Methinks you will never like (nor appreciate) gentoo, raul!  No shame in that though.  It certainly isn't for everyone.

---

### Post by raul_ on 2007-10-21
Maybe not :)

Apart from the time it takes to install things, I like everything else!!

I think Arch is perfect for me by now. It's actually similar to Gentoo in terms of philosophy

---

### Post by rsambuca on 2007-10-21
> **raul_ said:**
> Maybe not :)

Apart from the time it takes to install things, I like everything else!!

I think Arch is perfect for me by now. It's actually similar to Gentoo in terms of philosophy

After I settle in to Gutsy, I think my next foray will be either Arch or Foresight.  Right now I have my new Gutsy, my old Feisty, Debian, Gentoo, and Sabayon installed.

---

### Post by yabbadabbadont on 2007-10-21
> **HymnToLife said:**
> ```
firas@Nobue ~ $ sudo splat mozilla-firefox
 * www-client/mozilla-firefox-2.0.0.7

        Emerged at: Sun Oct 14 22:47:46 2007
        Build time: 25 minutes, and 34 seconds

 * www-client/mozilla-firefox-2.0.0.8

        Emerged at: Fri Oct 19 22:50:53 2007
        Build time: 25 minutes, and 10 seconds

```

I love my new Athlon FX-62 :D

I just install the *-bin versions of firefox and thunderbird.

---

### Post by Bachstelze on 2007-10-22
Yep, I used to do that but compiling them and see what time it takes is a good benchmark. Once, I saw that compiling OpenOffice took ~20% longer than usual, it was my RAM dying :p

---

### Post by cotcot on 2007-11-21
It happened to me. Unfortunately I could not repair it yet.

---

### Post by tekknokrat on 2007-12-20
> **Krieg said:**
> I used Gentoo heavily for a couple of years, at the end it was a nightmare.   USE variable ... DO NOT WANT!

neither the devs.

package.use / use.conf ist the place to go with storing your use flags.
Its such a nice feature of gentoo :)

---

### Post by Daeluin on 2008-02-27
I started with debian, but quickly screwed my dependancies and had to start over. There was close to nil documentation and whenever I looked for it I found RTFM. 

Then I tried gentoo, maybe a week later, still very much a  linux newb. The installation guide was long, yes, but very detailed. Anyone who understands how to follow directions can do it just fine.

Over the next couple years I reinstalled 3 or 4 times, but now the box I run on has been going 26 months strong, maybe more. (Some of my oldest files say 2004, but that can't be right?!)

I've taken a job where we use Ubuntu for a lot, and I greatly admire it's polish. Stuff is integrated and customized a bit more, in the effort of making a great computing experience. It's awesome. 

But I miss the simplicity and control I have at home. Ubuntu handles dependencies very well and it's easy not to break stuff now, but it frustrates me how difficult is it to see exactly what the uprade is going to do. Awesome! I'm so glad x package is going to be upgraded, but what version is it and what will it be upgraded to? Sure synaptic will tell me, and that's what I rely on. But can't I have that at the command line too, with just an aptitude install blah? You can see above how much information gentoo gives you. Add a -v to the command and it'll tell you what complilation options are available and which are enabled. Awesome. You may also easily block or update specific packages, something I've tried with poor results in apt/preferences. 

If stuff breaks you've got revdep-rebuild. If that doesn't help, the forums have very specific problems and support for those problems. Very rarely have I encountered a breakage and not found the answer in either the gentoo forums or in bugs.gentoo.org. On top of all of this, I can completely reinstall every installed package if I feel stuff is getting clunky or cluttered. 

Yes compiling can take longer. (it's a lot faster with amd64) But so what? I just run it before I go to bed, or in the background while I browse the web or watch a movie. Compiling really doesn't interrupt regular use of the computer, just intense stuff like gaming. Long compile times for updates really don't bother me, and if I'm installing a new package I want right now, it generally takes five minutes or less. Firefox compiles in about 10 minutes. 

The problem with gentoo's model is that it doesn't scale well. When you're maintaining specific build files for every package covering different dependencies for different compile options it can become complex. Most of the work goes into improving portage and writing ebuilds that work well together. The model allows for you to have a very bleeding edge install, but major upgrades can take longer to implement sometimes.  And I feel a distinct lack for a push in areas of server stability and polished desktop, both of which gentoo could excel at, given the right resources.

In short, an awesome distro with excellent documentation, packaging tools, and potential, but it's unstable management makes me worry. It needs some funding and to be driven by more purpose.

---

### Post by deepclutch on 2008-03-25
does "rolling release" means gentoo needs a super duper internet connection to survive ?I mean that your gentoo hdd installation to be up2date? :D

also,what is the size of daily updates that gentoo needs?(approximate for a Gnome installation?)
Thank You!
I had last tried gentoo on 2004 AFAIK.I have to build from stage 1(pita!) that time which took days for me!.is it the same today also?

---

### Post by Bachstelze on 2008-03-26
> **deepclutch said:**
> 
also,what is the size of daily updates that gentoo needs?(approximate for a Gnome installation?)

It will usually be no more than a few megabytes (and often less than one, especially if you stick with the stable branch). However, when there will be an upgrade for a big package like OpenOffice, gcc or something like that, it will obviously be a much bigger download. Of course, you can always "disable" an upgrade so it won't be in your way when you upgrade the rest of your system, and get the source archive from somewhere else.

---

### Post by SarahKH on 2008-04-16
Have to admit, Gentoo is a loverly distro.  I tend to use it around the house on the MythTV system and 'servers' because well, every ikkle bit I can squeeze out of an EPIA MII10K is a good thing :)  I also love the 'any config file change is NOT automatic' system as opposed to Ubuntu... which can and will blitz a config file without any warning... or creating a .bak version. 

I think it deserved it's reputation for being complicated in the beginning, but with the wiki and much better documentation around it's pretty much point, shoot, wait.

I also think Ubuntu deserves its reputation for degenerative slowness, time will tell if the Heron suffers the same as the monkey did.

---

### Post by insane_alien on 2008-04-30
gentoo is all well and good once you have it up and running. installing it is a nightmare for a newb(as i was when i first tried it.)

---

### Post by deepclutch on 2008-04-30
gentoo installer sucks!I dont want any installer!the olden ways were good!

anyways,I installed manually with /etc/make.conf needed for my needs!

---

### Post by regomodo on 2008-04-30
> **insane_alien said:**
> gentoo is all well and good once you have it up and running. installing it is a nightmare for a newb(as i was when i first tried it.)

yeah. I'd have to agree. I've been using it for about 6weeks now and could not get a properly working system for at least 2 of those. Now it's easy to live with and very little breakage. Only 1 complete system hang so far on 2 systems.

---

### Post by cardinals_fan on 2008-04-30
The graphical installer is awful though.  Why did the Gentoo team decide that it was a good idea?

---

### Post by Redrazor39 on 2008-05-10
Gentoo penguins often become homosexual. That is reason enough for me not to use it.

---

### Post by deepclutch on 2008-05-10
^ROFL! :lol:

BTW,I skipped gentoo for the 4th time.I am comfortable with My Debian Sid and Archlinux :D

But,I appreciate their efforts esp documentation,wiki et al.

For me,its simply not worth compiling with all optimizations. :(

---

### Post by regomodo on 2008-05-12
I'd have to say optimisation is noticeable if your system is rather old. My 9yr old laptop is noticeably fast than anything else i've tried {read as: lots and lots of distro's}.
However, on my fancy PC, the difference in speed isn't. Saying that however,i haven't had such a trouble free setup in such a long time. Apart from a scanner not working (no 64bit Linux OS can use it natively. Needs a chroot env) i haven't an issue. 
Just a *emerge --sync* and *emerge -uav world* daily is all what's needed.

---

### Post by darksong on 2008-05-20
I turned my PC off after Gentoo didn't finish installing after 24 hours. I just use sabayon instead - its the only hope gentoo has of ever being desktop ready.

---

### Post by deepclutch on 2008-05-20
gentoo is anyway for control freaks!gentoo should not go for desktop ready thing!it should shred the installer crap and all for the good!

---

### Post by regomodo on 2008-05-20
> **darksong said:**
> I turned my PC off after Gentoo didn't finish installing after 24 hours. I just use sabayon instead - its the only hope gentoo has of ever being desktop ready.

i really doubt a source based OS would ever have the intention of newbie friendly.

24hours? What you compiling with? P3?

---

