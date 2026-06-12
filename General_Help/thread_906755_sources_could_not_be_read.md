---
title: "sources could not be read"
date: 2008-08-31
forum: General Help
---

### Post by maverickdy on 2008-08-31
I was following this threads suggestions [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) and typed > sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

Afterwards I started getting this error > E: Type '=>' is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

when I went on to the next step which is to type > sudo apt-get remove gnash gnash-common libflash-mozplugin libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea-gcjwebplugin liblame0 non-free-codecs openjdk-6-jre unrar
I then went to the file and checked out what was inside it which is this
> --16:34:15--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `hardy.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

    0K                                                       100%   43.54 MB/s

16:34:15 (43.54 MB/s) - `hardy.list' saved [226/226]

I have 2 days of Linux experience so I have no idea how to troubleshoot it.

---

### Post by drs305 on 2008-08-31
Run these commands to redo your medibuntu repository list. They will reinstall the Medibuntu Repository following the guidance from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"). Although it looks like you ran the proper command something got messed up and it's easier just to redo it.

```

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list-old 
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by maverickdy on 2008-08-31
Great! Your a life saver! I moved from Fedora 9 to Ubuntu because Fedora 9 was giving me a headache of problems. So far my experience with Ubuntu has been a million times better.

---

