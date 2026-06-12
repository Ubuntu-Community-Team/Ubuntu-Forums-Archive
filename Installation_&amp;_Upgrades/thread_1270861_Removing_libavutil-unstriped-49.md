---
title: "Removing libavutil-unstriped-49"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by mikeym on 2009-09-20
Hi,

I recently upgraded libavutil-unstriped-49 as I was trying to get a program running that reported to need it that I later gave up on. My problem is that I'm trying to compile something that needs the libavutil-dev and that depends on libavutil49 as there is no dev for the unstriped version, but when I try to downgrade to libavutil49 it says it has to remove half my applications.

```
  blender dvdrip ffmpeg gpac gstreamer0.10-ffmpeg libavcodec-unstripped-52
  libavdevice52 libavfilter0 libavformat52 libavutil-unstripped-49
  libmjpegtools-1.9 libpostproc-unstripped-51 libquicktime1 libxine1-ffmpeg
  mjpegtools mpd performous picard subtitleripper transcode ultrastar-ng vlc
  vlc-nox xine-ui

```

How can I downgrade without removing these?


(**[COLOR="Red"]edit[/COLOR]**) I found this [bug]("https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/312898") which seems to describe my problem, but having read it (and being a fairly experienced ubuntu user) I still have no idea how to compile my program against libavutil-dev. 

Is it saying to remove libavutil-unstriped-49 and all the packages above, install libavutil-dev, compile my program, uninstall libavutil-dev, reinstall libavutil-unstriped-49 then reinstall all the packages above? Wont that mess up all the packages that are removed then reinstalled?

---

### Post by mikeym on 2009-09-20
OK, I managed to compile by temporarily breaking my packages with:

```
sudo dpkg --force depends -i libavutil-dev*.deb libavcodec-dev*.deb libavformat-dev*.deb
``` 

after downloading the 'stripped' libav' devs I needed from:

[http://packages.ubuntu.com/jaunty/libavformat-dev](http://packages.ubuntu.com/jaunty/libavformat-dev)
[http://packages.ubuntu.com/jaunty/libavcodec-dev](http://packages.ubuntu.com/jaunty/libavcodec-dev)
[http://packages.ubuntu.com/jaunty/libavutil-dev](http://packages.ubuntu.com/jaunty/libavutil-dev)

and then compiled my package I wanted. Then fixed the whole thing with:

```
sudo apt-get -f install
sudo apt-get install libavcodec-unstripped-52
```

This is NOT RECOMMENDED as it breaks the package tree for a while and from what I understand works because there's no difference between the 'striped' and 'unstriped' libav packages other than a few extra codecs which don't effect things.

---

### Post by FakeOutdoorsman on 2009-09-20
I believe you can have both the repository (un)stripped libav* and a compiled FFmpeg.  Packages from the repository that want libav* will use it from the repository.  Compiled packages can use your compiled FFmpeg libraries.  This is because official packages install to */usr* and compiled packages can be installed to */usr/local*.  This separation allows you to use both at once:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by mikeym on 2009-09-20
The issue wasn't with compiling ffmpeg but compiling a package that needed the headers for liav* and the fact that they have a dependency on the striped version of the libraries which clashes with the unstriped version. 

I.e. you can't have *libavutil49-dev* and *libavutil-unstriped-49* installed at the same time and switching *libavutil-unstriped-49* for *libavutil49* prompted synaptic to demand that I remove the list of packages I mention on my first post.

---

### Post by FakeOutdoorsman on 2009-09-20
You won't need *libavutil-dev* because a compiled FFmpeg will provide the same files as *libavutil-dev*.  Therefore, you can avoid installing *libavutil-dev* and also keep *libavutil-unstripped-49*.

---

### Post by mikeym on 2009-10-09
No. Trying to compile some new apps and finding that they are not including the files properly - it may be to do with the mess my packages are in. 

Is there any way to remove the unstriped packages without removing the packages which have them as dependencies the reinstall the "striped" versions?

---

