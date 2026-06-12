---
title: "pymedia install failure"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by 3nt on 2009-09-18
I have downloaded the pymedia-1.3.7 tar and expanded it. I have checked I have all the necessary depends :

:/nas/Downloads/pymedia-1.3.7.3# sudo apt-get install python-dev libogg-dev libvorbis-dev libmp3lame-dev libfaad-dev libasound2-dev python-pygame
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-dev is already the newest version.
libogg-dev is already the newest version.
libvorbis-dev is already the newest version.
libmp3lame-dev is already the newest version.
libfaad-dev is already the newest version.
libasound2-dev is already the newest version.
python-pygame is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But when I try to build I get :

root@notebook:/nas/Downloads/pymedia-1.3.7.3# python setup.py build
Using UNIX configuration...

OGG          : found
VORBIS       : found
FAAD         : found
MP3LAME      : found
VORBISENC    : found
ALSA         : found
Continue building pymedia ? [Y,n]:Y
running build
running build_py
running build_ext
building 'pymedia.audio.acodec' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -DBUILD_NUM=1867 -DPATH_DEV_DSP="/dev/dsp" -DPATH_DEV_MIXER="/dev/mixer" -D_FILE_OFFSET_BITS=64 -DACCEL_DETECT=1 -DHAVE_MMX=1 -DHAVE_LINUX_DVD_STRUCT=1 -DDVD_STRUCT_IN_LINUX_CDROM_H=1 -DCONFIG_VORBIS -DCONFIG_VORBIS -DCONFIG_FAAD -DCONFIG_MP3LAME -DCONFIG_VORBIS -DCONFIG_ALSA -DHAVE_AV_CONFIG_H -DUDF_CACHE=1 -INone -INone -INone -I/usr/include/lame -INone -INone -I/nas/Downloads/pymedia-1.3.7.3 -Iaudio/ -I/usr/include/python2.6 -c audio/acodec/acodec.c -o build/temp.linux-i686-2.6/audio/acodec/acodec.o
In file included from audio/acodec/acodec.c:31:
audio/libavcodec/dsputil.h:484: error: static declaration of ‘lrintf’ follows non-static declaration
audio/acodec/acodec.c:249: warning: initialisation from incompatible pointer type
audio/acodec/acodec.c: In function ‘ACodec_Encode’:
audio/acodec/acodec.c:668: warning: pointer targets in passing argument 2 of ‘avcodec_encode_audio’ differ in signedness
error: command 'gcc' failed with exit status 1



I have gcc4.3 installed. 

Any suggestions for troubleshooting would be appreciated.


Thanks

---

### Post by Bremans on 2009-11-03
Hi,

I'm having the same problem.. :-(

---

### Post by Catscrash on 2009-11-03
i think you need gcc-3.4 for pymedia.

i tried using the jaunty packages but it complains about missing c++ compiler and the last g++-3.4 is from hardy which won't install...

---

