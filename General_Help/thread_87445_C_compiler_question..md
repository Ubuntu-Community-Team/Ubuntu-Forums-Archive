---
title: "C compiler question."
date: 2005-11-08
forum: General Help
---

### Post by Bachstelze on 2005-11-08
I already asked this in the VLC thread but I think the probles isn't from vlc. Here's he problem : the Ubuntu VLC build isn't able to read MKVs. Given that on every other system I tried, it worked just fine and that some Ubuntu users get the same problem, I was told on the VLC forum that there was something wrong with the build and that I would have to compile it myself. Fair enough, I went to the VLC "HowTo compile", downloaded the three packages I need (gcc, automake, autoconf) and the VLC source. But the problem occurs whn I type in the ";/config ..." line, it says : 

> checking for C compiler default output file name... configure: error: C compiler cannot create executables

So I think I have to download some extra packages but I dunno which ones. Can anyone help me ?

---

### Post by kalin on 2005-11-08
Install the "build-essential" package.

---

### Post by Bachstelze on 2005-11-08
It works, thanks :)

EDIT : Actually not, here's what I get :

> configure: error: Missing header file ffmpeg/avcodec.h

I have the ffmpeg package installed. What's the problem ?

---

### Post by az on 2005-11-08
[QUOTE=HymnToLife]It works, thanks :)

EDIT : Actually not, here's what I get :



I have the ffmpeg package installed. What's the problem ?[/QUOTE]

I think the debian/ubuntu version of the ffmpeg has split some libraries to make a better distinction between free and non-free software:

You need:
[http://packages.ubuntu.com/breezy/libdevel/libavcodec-dev](http://packages.ubuntu.com/breezy/libdevel/libavcodec-dev)

Or maybe other packages, too:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ffmpeg&searchon=all&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ffmpeg&searchon=all&subword=1&version=breezy&release=all)


Yep.   The ffmpeg source provides:
Binary: libavformat-dev, libavcodec-dev, libpostproc-dev, ffmpeg

I think it will be further split in Dapper and some of the packages will end up in multiverse...

---

### Post by Bachstelze on 2005-11-08
I managed to configure it but when I try to build it using the 'make' command, it says : 

> `-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
ffmpeg.c:49:44: error: libpostproc/postprocess.h: No such file or directory
make[6]: *** [libffmpeg_plugin_a-ffmpeg.o] Error 1
make[6]: Leaving directory `/home/mfb/vlc-0.8.2/modules/codec/ffmpeg'
make[5]: *** [all-modules] Error 1
make[5]: Leaving directory `/home/mfb/vlc-0.8.2/modules/codec/ffmpeg'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/mfb/vlc-0.8.2/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/mfb/vlc-0.8.2/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mfb/vlc-0.8.2/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mfb/vlc-0.8.2'
make: *** [all] Error 2

Before anyone asks, YES, I've installed the libpostproc-dev package. Any ideas ?

---

### Post by Bachstelze on 2005-11-08
bump

---

