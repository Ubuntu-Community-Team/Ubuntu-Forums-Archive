---
title: "[SOLVED] Why  vlc looks like this?"
date: 2008-11-09
forum: General Help
---

### Post by ellalan on 2008-11-09
Hi
I have installed a new theme and customised but all the applications look OK except VLC, could someone please tell me how to make VLC look better.

---

### Post by dragos240 on 2008-11-09
> **ellalan said:**
> Hi
I have installed a new theme and customised but all the applications look OK except VLC, could someone please tell me how to make VLC look better.

You can switch back to the human theme for a better effect, but try downloading the newest VLC, i think it might work better.

---

### Post by Steveway on 2008-11-09
VLC doesn't use GTK anymore. They switched to QT, so you need to change your QT-theme too.

---

### Post by olejon on 2008-11-09
System > Appearance > QT 4 settings

You can dowload another theme, or you can just set the window background color to one that matches.

---

### Post by ellalan on 2008-11-09
I have tried installing newer version of vlc and tried settings in Qt4 and got this(attachment).
I'll keep on looking for a better theme, in the meantime more ideas please.

---

### Post by Occasionally Correct on 2008-11-09
If you want VLC (and other QT4 applications) to use your GTK theme, download and install [QGtkStyle](http://labs.trolltech.com/page/Projects/Styles/GtkStyle):

```
sudo apt-get install libqt4-dev qt4-qtconfig subversion
svn co svn://labs.trolltech.com/svn/styles/gtkstyle
cd gtkstyle/
qmake && make
sudo make install
```

You should be able to select the "GTK" style in System -> Preferences -> Qt 4 Settings. After this, VLC should look fine. :)

---

### Post by ellalan on 2008-11-09
Thank you Occasionally Correct,this did the trick and its much better.

---

