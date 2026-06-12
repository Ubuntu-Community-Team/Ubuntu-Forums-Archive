---
title: "ubuntu-restricted-extras fails install, breaks all installs"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by Mizutsuki on 2009-05-11
Hello,
I was trying to install ubuntu-restricted-extras package and apt-get install failed.  I have lost the original error, but now I can't install anything else or uninstall anything else and when I do apt-get -f install I get this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-bin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libavcodec52 libavutil49 libpostproc51
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 10.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 107962 files and directories currently installed.)
Removing libavcodec52 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libavcodec52 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libpostproc51 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libpostproc51 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libavutil49 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libavutil49 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 libavcodec52
 libpostproc51
 libavutil49
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
And when I do apt-get install ubuntu-restricted-extras I get this
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-bin
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cabextract flashplugin-installer flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly-multiverse libavcodec-unstripped-52 libavformat52 libavutil-unstripped-49 libmjpegtools-1.9 libquicktime1
  libswscale0 ttf-liberation ttf-mscorefonts-installer
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
Recommended packages:
  w32codecs
The following packages will be REMOVED:
  libavcodec52 libavutil49
The following NEW packages will be installed:
  cabextract flashplugin-installer flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly-multiverse libavcodec-unstripped-52 libavformat52 libavutil-unstripped-49 libmjpegtools-1.9 libquicktime1
  libswscale0 ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras
0 upgraded, 16 newly installed, 2 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/6946kB of archives.
After this operation, 6996kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 107962 files and directories currently installed.)
Removing libavcodec52 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libavcodec52 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libavutil49 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libavutil49 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 libavcodec52
 libavutil49
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Is this a known issue?  Are there workarounds/solutions?

Thanks all.

---

### Post by vikkikanhaua on 2009-05-11
try sudo apt-get install -f
this might work
& then try to install other packages

---

### Post by Mizutsuki on 2009-05-11
> **vikkikanhaua said:**
> try sudo apt-get install -f
this might work
& then try to install other packages

Did sudo apt-get install -f and got this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-bin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libavcodec52 libavutil49 libpostproc51
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 10.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 107962 files and directories currently installed.)
Removing libavcodec52 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libavcodec52 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libpostproc51 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libpostproc51 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libavutil49 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libavutil49 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 libavcodec52
 libpostproc51
 libavutil49
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Then I did "sudo apt-get install gnome-games" and I got the following:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-bin
Use 'apt-get autoremove' to remove them.
Suggested packages:
  python-gtkglext1 python-opengl gnome-hearts gnome-games-extra-data
The following packages will be REMOVED:
  libavcodec52 libavutil49 libpostproc51
The following NEW packages will be installed:
  gnome-games
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 1173kB of archives.
After this operation, 7627kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com jaunty/main gnome-games 1:2.26.1-0ubuntu2 [1173kB]
Fetched 1173kB in 20s (56.0kB/s)                                                                                                                            
(Reading database ... 107962 files and directories currently installed.)
Removing libavcodec52 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libavcodec52 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libpostproc51 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libpostproc51 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libavutil49 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libavutil49 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 libavcodec52
 libpostproc51
 libavutil49
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So I'm still not able to install anything.

---

### Post by Mizutsuki on 2009-05-11
Ok, I think I've got it fixed.  I don't exactly know what I did, but I went into aptitude and I just played around with it a bit and now I can install stuff.  Thank you.

---

