---
title: "Network Log Monitor"
date: 2008-09-28
forum: General Help
---

### Post by ShareBuntu on 2008-09-28
Can anyone recommend an application that'll monitor logs for network related messages that may prove to be potential security issues? I found [http://www.qt-apps.org/content/show.php/NetfilterStatsBuilder?content=26867](http://www.qt-apps.org/content/show.php/NetfilterStatsBuilder?content=26867) - but I cannot get it to compile. Does anyone have any ideas?

---

### Post by pavel989 on 2008-09-28
why can't u get it to compile? are there errors messages?

---

### Post by ShareBuntu on 2008-09-28
> **pavel989 said:**
> why can't u get it to compile? are there errors messages?I get the following after running qmake:

```
uic: File generated with too old version of Qt Designer
uic: File generated with too old version of Qt Designer
uic: File generated with too old version of Qt Designer
uic: File generated with too old version of Qt Designer
```And this after running make:

```
/usr/bin/uic-qt4 form1.ui -o ui_form1.h
uic: File generated with too old version of Qt Designer
File 'form1.ui' is not valid
make: *** [ui_form1.h] Error 1
```

---

### Post by pavel989 on 2008-09-28
uhm, u need the qt devel package

---

### Post by ShareBuntu on 2008-09-28
> **pavel989 said:**
> uhm, u need the qt devel package
I have libqt4-dev and qt4-dev-tools installed.

---

### Post by pavel989 on 2008-09-28
either you need to downgrade Qt or maybe find a newer version of the file/app.

Possible edit it yourself?

---

### Post by ShareBuntu on 2008-09-28
I downgraded to the QT3 development files and it worked out great. Thanks for the help. :)

---

### Post by pavel989 on 2008-09-28
No problem, m8

---

