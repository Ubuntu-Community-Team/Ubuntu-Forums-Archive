---
title: "Install ffmpeg-php  (Error)"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by abasel on 2009-05-03
Following [http://linux.justinhartman.com/FFmpeg,_FFmpeg-PHP,_Lame,_Libogg,_Libvorbis,_FLVtool2,_Mplayer,_Mencoder,_AMR_Installation]("http://linux.justinhartman.com/FFmpeg,_FFmpeg-PHP,_Lame,_Libogg,_Libvorbis,_FLVtool2,_Mplayer,_Mencoder,_AMR_Installation"), I have nearly completed the install that I need, except for the following:

```
cd /usr/local/src/ffmpeg-php-0.5.0/
phpize
./configure
make
make install

```

When I run "make", I get

```
root@rcpm01:/usr/local/src/ffmpeg-php-0.5.0# make
/bin/bash /usr/local/src/ffmpeg-php-0.5.0/libtool --mode=compile gcc  -I. -I/usr/local/src/ffmpeg-php-0.5.0 -DPHP_ATOM_INC -I/usr/local/src/ffmpeg-php-0.5.0/include -I/usr/local/src/ffmpeg-php-0.5.0/main -I/usr/local/src/ffmpeg-php-0.5.0 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/local/include/ffmpeg  -DHAVE_CONFIG_H  -g -O2 -Wall -fno-strict-aliasing   -c /usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c -o ffmpeg_frame.lo
libtool: compile:  gcc -I. -I/usr/local/src/ffmpeg-php-0.5.0 -DPHP_ATOM_INC -I/usr/local/src/ffmpeg-php-0.5.0/include -I/usr/local/src/ffmpeg-php-0.5.0/main -I/usr/local/src/ffmpeg-php-0.5.0 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/local/include/ffmpeg -DHAVE_CONFIG_H -g -O2 -Wall -fno-strict-aliasing -c /usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c  -fPIC -DPIC -o .libs/ffmpeg_frame.o
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c: In function â_php_convert_frameâ:
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c:162: warning: implicit declaration of function âimg_convertâ
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c: In function â_php_crop_frameâ:
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c:215: warning: implicit declaration of function âimg_copyâ
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c: In function â_php_resample_frameâ:
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c:237: error: âImgReSampleContextâ undeclared (first use in this function)
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c:237: error: (Each undeclared identifier is reported only once
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c:237: error: for each function it appears in.)
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c:237: error: âimg_resample_ctxâ undeclared (first use in this function)
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c:263: warning: implicit declaration of function âimg_resample_full_initâ
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c:276: warning: implicit declaration of function âimg_resampleâ
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c:281: warning: implicit declaration of function âimg_resample_closeâ
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c: In function âzif_toGDImageâ:
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c:409: error: âPIX_FMT_RGBA32â undeclared (first use in this function)
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c: In function âzif_ffmpeg_frameâ:
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg_frame.c:495: error: âPIX_FMT_RGBA32â undeclared (first use in this function)
make: *** [ffmpeg_frame.lo] Error 1

```

---

### Post by Partyboi2 on 2009-05-03
Hi, not sure about the errors you are getting but have you tried using the version in the ubuntu repos?
```
sudo apt-get install php5-ffmpeg
```

---

