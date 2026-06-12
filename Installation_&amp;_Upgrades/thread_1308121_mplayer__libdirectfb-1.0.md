---
title: "mplayer / libdirectfb-1.0"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by TrevorBradley on 2009-10-31
Hey there, I've just upgraded from Jaunty to Karmic, and am having problems getting mplayer working...

I'm having the exact same problem as described in this closed post here:

[http://ubuntuforums.org/showthread.php?p=8130586](http://ubuntuforums.org/showthread.php?p=8130586)

if I run mplayer I get this error:

trevor@pergamon:/usr/lib$ /usr/bin/mplayer
/usr/bin/mplayer: error while loading shared libraries: libdirectfb-1.0.so.0: cannot open shared object file: No such file or directory

trevor@pergamon:/usr/lib$ ldd /usr/bin/mplayer
	<edited>
	libdirectfb-1.0.so.0 => not found
	libfusion-1.0.so.0 => not found
	libdirect-1.0.so.0 => not found
	<edited>

The version of mplayer I have installed is 2:1.0~rc3+svn20090426-1ubuntu10

The version of libdirectfb I have installed is 1.2.7-2ubuntu1

I thought it might be a problem because of the mediabuntu repository, but I've now reactivated the mediabuntu repository and see no change in the mplayer version.

I must be missing something obvious here... any help?

Thanks in advance!

---

### Post by TrevorBradley on 2009-10-31
Poked around with this a bit more... Tried installing and uninstalling mplayer and mplayer-nogui from synaptic.  The version on mplayer-nogui in synaptic is still 2:1.0~rc3+svn20090426-1ubuntu10...  If you click on properties it claims it depends on libdirectfb 1.2, but the actual binary downloaded to /usr/bin/mplayer depends on libdirectfb 1.0.  I've verified that the binary is actually being deleted and replaced with the same broken binary.

I could just go with the svn, but I'd prefer it to be fixed at the repository level.  Or I could still be screwing something basic up.

Help!

---

### Post by TrevorBradley on 2009-10-31
OK, this is getting ridiculous.  I've compiled mplayer svn on my machine, and *it* complains that directfb-1.0 is missing and wont run!  

Obviously I've misconfigured something so that everything wants to look for directfb-1.0 when directfb-1.2 is there and working.  

Giving up for today.. too frustrating.

EDIT: Best way to give up.. Install directfb-1.0 from source. It's working now, but it's no solution.  Perhaps a fresh install would have been better than upgrading.. :(

---

### Post by jim_charlton on 2009-11-04
SOLVED
I have/had the same problem.  After Karmic upgrade I have 
/usr/lib/libdirectfb-1.2.so.0
/usr/lib/libdirectfb-1.2.so.0.7.0
but no 
/usr/lib/libdirectfb-1.0.so.0.
Seems as though the problem is with mplayer.  `apt-cache show mplayer` says 
Package: mplayer                              
Priority: extra                               
Section: multiverse/graphics                  
Installed-Size: 5280                          
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Debian multimedia packages maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: amd64                                                                                             
Version: 2:1.0~rc3+svn20090426-1ubuntu10                                                                        
Depends: debconf | debconf-2.0, mplayer-skin, mplayer-nogui, libasound2 (>> 1.0.18), libatk1.0-0 (>= 1.20.0), libaudio2, libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1), libavformat52 (>= 3:0.svn20090303-1) | libavformat-extra-52 (>= 3:0.svn20090303-1), libavutil49 (>= 3:0.svn20090303-1) | libavutil-extra-49 (>= 3:0.svn20090303-1), libc6 (>= 2.7), libcaca0 (>= 0.99.beta15-1), libcairo2 (>= 1.2.4), libcdparanoia0 (>= 3.10.2+debian), libdirectfb-1.2-0, libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35), libfaac0 (>= 1.26), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libfribidi0 (>= 0.10.9), libgcc1 (>= 1:4.1.1), libgif4 (>= 4.1.6), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.8.0), libjack0 (>= 0.116.1), libjpeg62, liblircclient0, liblzo2-2, libmp3lame0, libncurses5 (>= 5.6+20071006-3), libogg0 (>= 1.0rc3), libopenal1, libpango1.0-0 (>= 1.14.0), libpng12-0 (>= 1.2.13-4), libpostproc51 (>= 3:0.svn20090303-1) | libpostproc-extra-51 (>= 3:0.svn20090303-1), libpulse0 (>= 0.9.19), libsdl1.2debian (>= 1.2.10-1), libsmbclient (>= 3.0.24), libspeex1 (>= 1.2~beta3-1), libstdc++6 (>= 4.1.1), libsvga1, libswscale0 (>= 3:0.svn20090303-1) | libswscale-extra-0 (>= 3:0.svn20090303-1), libtheora0 (>= 0.0.0.alpha7.dfsg-1.1), libx11-6, libx264-67 (>= 1:0.svn20090502), libxext6, libxinerama1, libxt6, libxv1, libxvidcore4 (>= 1:1.0.0-0.0), libxvmc1, libxxf86dga1, libxxf86vm1, zlib1g (>= 1:1.1.4)
Suggests: mplayer-doc, ttf-freefont, netselect | fping, bzip2, fontconfig
Filename: pool/multiverse/m/mplayer/mplayer_1.0~rc3+svn20090426-1ubuntu10_amd64.deb
Size: 2303408
MD5sum: 48deb579c16325c702fcbc871ffc85b7

so the "Depends" line shows the most recent mplayer depends on the libdirectfb-1.2.

Tried `locate bin/mplayer' and it gives 
/usr/bin/mplayer
/usr/local/bin/mplayer

Ahah!  When one launches mplayer it looks first in /usr/local/bin and launches the old version instead of the newly loaded (Karmic) version in /usr/bin.  Rm the old version in /usr/local/bin.  I must have compiled mplayer at some point in the past and it installed it in /usr/local/bin.  You must have the same problem.

I have been bitten with the same problem when I have installed libraries in /usr/local/lib.  They will be used by most programs before the /usr/lib libraries.  You must delete them when you upgrade (or recompile them under the new kernel).  At least that is my read on the matter.  Hope this helps

---

### Post by churingao on 2010-06-12
thanks jim_charlton,

great answer =D

---

