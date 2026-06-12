---
title: "[SOLVED] Unable to edit Menu."
date: 2008-08-04
forum: General Help
---

### Post by pravin03 on 2008-08-04
Unable to edit menu[In Hardy(8.04)] when right clicking and selecting Edit menu.
It is not possible from system -preferences-Main menu.
I can't also enable SCIM Input choices.(I installed svanalekha)****

---

### Post by mb_webguy on 2008-08-04
What happens when you type "alacarte" in the terminal?

---

### Post by pravin03 on 2008-08-04
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 35, in __init__
    self.locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: ml_IN

---

### Post by mb_webguy on 2008-08-04
Have you tried reinstalling the alacarte and python packages?  There seems to be something wrong with one or the other...

---

### Post by pravin03 on 2008-08-04
apt-get install language-support-ml language-pack-ml language-pack-gnome-ml language-pack-gnome-ml-base language-pack-kde-ml language-pack-kde-ml-base

apt-get install scim scim-gtk2-immodule m17n-contrib scim-m17n

wget [http://download.savannah.gnu.org/releases/smc/Swanalekha/scim-ml-phonetic_0.1.3-1_all.deb](http://download.savannah.gnu.org/releases/smc/Swanalekha/scim-ml-phonetic_0.1.3-1_all.deb)
dpkg -i scim-ml-phonetic_0.1.3-1_all.deb

wget [http://ftp.jp.debian.org/debian/pool/main/t/ttf-indic-fonts/ttf-malayalam-fonts_0.5.4_all.deb](http://ftp.jp.debian.org/debian/pool/main/t/ttf-indic-fonts/ttf-malayalam-fonts_0.5.4_all.deb)
dpkg -i ttf-malayalam-fonts_0.5.4_all.deb

touch /etc/X11/Xsession.d/74custom-scim_startup
chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
chmod 644 /etc/X11/Xsession.d/74custom-scim_startup




[B]
Is there any such job in this? When I did this, it was replied 'abort'.[/B]

---

### Post by pravin03 on 2008-08-04
what should I do now?

---

### Post by mb_webguy on 2008-08-04
Actually, I was thinking more along the lines of selecting for reinstallation the "alacarte" and "python" packages in Synaptic...

I'm not really sure what your X configuration has to do with your problem...

---

### Post by pravin03 on 2008-08-04
what can I do to correct this?

---

### Post by pravin03 on 2008-08-05
I cleared the problem. See

[http://ubuntuforums.org/showthread.php?t=879659](http://ubuntuforums.org/showthread.php?t=879659)

---

