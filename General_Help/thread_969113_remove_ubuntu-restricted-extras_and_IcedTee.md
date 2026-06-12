---
title: "remove ubuntu-restricted-extras and IcedTee"
date: 2008-11-03
forum: General Help
---

### Post by chaosdesigner on 2008-11-03
Hi,

I was pretty dumb and installed "ubuntu-restricted-extras", since i really dont like it. How do I remove it? I have found a few Threads about this Topic but nothing that helped. I also want to remov IcedTea because I want the real Java, but I dont know how to remove this either.

Thank you

---

### Post by aysiu on 2008-11-03
> **chaosdesigner said:**
> Hi,

I was pretty dumb and installed "ubuntu-restricted-extras", since i really dont like it. How do I remove it? I have found a few Threads about this Topic but nothing that helped. I also want to remov IcedTea because I want the real Java, but I dont know how to remove this either.

Thank you Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get remove cabextract flashplugin-nonfree freepats gsfonts-x11 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse java-common liba52-0.7.4 libavcodec-unstripped-51 libavformat52 libavutil49 libcdaudio1 libdc1394-22 libdvdnav4 libdvdread3 libfaac0 libfaad0 libfftw3-3 libfreebob0 libgmyth0 libgsm1 libid3tag0 libiptcdata0 libjack0 libmad0 libmjpegtools0c2a libmms0 libmp3lame0 libmpcdec3 libmpeg2-4 libmysqlclient15off libneon27-gnutls libofa0 libopenspc0 libpostproc51 libquicktime1 libsidplay1 libsoundtouch1c2 libswscale0 libwildmidi0 libx264-59 libxvidcore4 msttcorefonts mysql-common odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ubuntu-restricted-extras unixodbc unrar xutils-dev icedtea6-plugin icedtea-gcjwebplugin && sudo apt-get install --reinstall sun-java6-plugin
```

---

