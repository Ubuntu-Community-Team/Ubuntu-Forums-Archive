---
title: "OSX Hard drive icon?"
date: 2008-09-30
forum: General Help
---

### Post by KTMDirtFace on 2008-09-30
I just installed ubuntu on my laptop. Anyway for fun I tried to get it to look like Mac OSX.

Here it is so far.
[http://i272.photobucket.com/albums/jj169/KingClucker/Screenshot.png](http://i272.photobucket.com/albums/jj169/KingClucker/Screenshot.png)

How do I make a desktop shortcut with the cool looking hard drive icon?

Oh I'm using Mac4Lin theme/icons/cursors, and Cairo-Dock.

---

### Post by nkri on 2008-10-01
To show the desktop shortcut, hit Alt+F2, and type
```
gconf-editor
```
When the window pops up, navigate to apps>nautilus>desktop and check whichever icons you want shown (computer_icon_visible, for example, will show a link to the detected drives/file system; home_icon_visible will link you to your home folder, etc).  [_This_]("http://http://www.elettra.trieste.it/IT/uploads/MacHD.png") is a link to a good OS X hard drive icon; right-click, and go to Save Image As...save it where you want, and go back to the desktop.

Right-click on the icon you want to change, and click Properties.  Click the button on the left showing the current icon.  It should bring up a screen where you can open a different file.  Navigate to the file, and double-click it.  Voila:D

Good luck!
-nkri

---

