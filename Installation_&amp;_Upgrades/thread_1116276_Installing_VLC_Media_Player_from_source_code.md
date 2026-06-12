---
title: "Installing VLC Media Player from source code"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by infernus_crusher on 2009-04-04
I just downloaded VLC 0.99 coz the Ubuntu repo only has 0.94 as the latest version, and it won't play my new DVD. I'm having trouble configuring the source code because there are so many dependencies I need to resolve (I need to configure and install the dependencies one by one).

Can you use the command line to resolve all dependencies at once?

---

### Post by tommcd on 2009-04-04
VLC is fairly difficult to compile from source. As you have noticed there are a lot of dependencies.

Suggestion #1:
Would VLC .098a solve your problem? Ubuntu Jaunty will use VLC 0.98a:
[http://packages.ubuntu.com/search?keywords=vlc&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=vlc&searchon=names&suite=jaunty&section=all)
Jaunty is in beta now. The final version will be released in 19 days. You could consider upgrading to Jaunty if VLC 0.98a will do the job.

Suggestion #2:
Compile VLC from source, then run it from the terminal by typing **vlc**. You will get errors that will list what dependency is missing. Install each dependency with apt-get. When all dependencies are installed VLC should run from terminal with no errors. The only problem with this is that the newest VLC *may* require newer versions of those dependencies than the ones in the Intrepid repos. You can check the dependencies on the videolan website. Or just try and install all the dependencies from the Intrepid repos with apt-get and see if it works.

What kind of DVD is this that won't play on VLC 0.94? Have you tried using **Xine** or **MPlayer** to play it?

---

### Post by majamba on 2009-04-04
update from ubuntu early version to 9.04

use this command lines:
aptitude update
aptitude install vlc

that should give you the lastest vlc  in 9.04

don't know if this any help because this is about complilng an old vlc

[http://ubuntuforums.org/showthread.php?t=323855](http://ubuntuforums.org/showthread.php?t=323855)

---

### Post by SuperSonic4 on 2009-04-04
Well Version 1.0 pre has a configure script in it - I'd suggest you install the repo version to solve dependencies and then simply remove the vlc player then compile

---

### Post by infernus_crusher on 2009-04-04
It was a music DVD was imported from Japan. It plays with absolutely no problem under VLC 0.99 in Windows. The only problem is getting it to run in Ubuntu. And no, Totem and MPlayer didn't work either.

---

### Post by taurus on 2009-04-04
I suppose you have already installed the codecs?

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by infernus_crusher on 2009-04-04
Nevermind I did it. I installed all dependency packages as mentioned in [http://ubuntuforums.org/showthread.php?t=323855](http://ubuntuforums.org/showthread.php?t=323855) plus libqt4-dev and VLC 0.99 compiled without any problems.

When Jaunty comes out I'll just do a clean install and start anew again.

Thanks again.

---

### Post by albinootje on 2009-04-04
> **infernus_crusher said:**
> Nevermind I did it. I installed all dependency packages as mentioned in [http://ubuntuforums.org/showthread.php?t=323855](http://ubuntuforums.org/showthread.php?t=323855) plus libqt4-dev and VLC 0.99 compiled without any problems.


Just wondering, did you have libdvdcss2 installed or not ?

---

### Post by sundar_ima on 2009-04-21
you may want to install ubuntu restricted extras offline installer which has all codec including libdvdcss2 which can be downloaded from here [http://rapidshare.com/files/222192270/ubuntu-restricted-extras_offline_installer.tar.gz]("http://rapidshare.com/files/222192270/ubuntu-restricted-extras_offline_installer.tar.gz") (install instructions are given in the folder) then download and install VLC oflline installer from here [http://rapidshare.com/files/222292699/VLC_offline_installer.tar.gz]("http://rapidshare.com/files/222292699/VLC_offline_installer.tar.gz") hopefully it should work for you...

---

### Post by mitchellweston23 on 2009-04-21
i would just go to applications add/remove applications
go to all available applications then search vlc 
it plays mpeg, mpeg2 , mpeg4, divx, mov, wmv, quicktime, mp3, ogg/vorbis files , dvds, vcds and more

---

