---
title: "webkit installing and running error ~_~"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by kevinskliu on 2009-10-06
Hi guys ,
I am trying to install webkit on Ubuntu 9.04 and following is my steps 

1) sudo apt-get install libqt4-dev libxslt-dev gperf bison libsqlite3-dev flex build-essential subversion
2) svn checkout [http://svn.webkit.org/repository/webkit/trunk](http://svn.webkit.org/repository/webkit/trunk) WebKit
3) QTDIR=/usr/share/qt4/ WebKit/WebKitTools/Scripts/build-webkit

I got a error message like this 

[COLOR=Red]In file included from ../../../WebCore/platform/graphics/MediaPlayer.cpp:49:
../../../WebCore/platform/graphics/qt/MediaPlayerPrivatePhonon.h:27:29: error: phononnamespace.h: No such file or directory
In file included from ../../../WebCore/platform/graphics/MediaPlayer.cpp:49:
../../../WebCore/platform/graphics/qt/MediaPlayerPrivatePhonon.h:123: error: ‘Phonon::State’ has not been declared
../../../WebCore/platform/graphics/qt/MediaPlayerPrivatePhonon.h:123: error: ‘Phonon::State’ has not been declared
make[1]: *** [obj/release/MediaPlayer.o] Error 1[/COLOR]

I am wondering is there anyone success to install webkit into ubuntu 9.04 ? might give me some suggestions .
Thanks a lot !
BRs
Kevin ...

---

### Post by Partyboi2 on 2009-10-06
> [COLOR=Red] ../../../WebCore/platform/graphics/qt/MediaPlayerPrivatePhonon.h:27:29: error: phononnamespace.h: No such file or directory[/COLOR]

If you have not already got libphonon-dev package installed, try installing it.
```
sudo apt-get install libphonon-dev
```

[B]
[/B]

---

### Post by kevinskliu on 2009-10-06
:guitar: thanks a lot , it's working now .

---

