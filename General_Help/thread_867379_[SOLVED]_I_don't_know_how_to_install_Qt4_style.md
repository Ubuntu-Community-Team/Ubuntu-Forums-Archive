---
title: "[SOLVED] I don't know how to install Qt4 style"
date: 2008-07-22
forum: General Help
---

### Post by LinuX-M@n1@k on 2008-07-22
I'm on Ubuntu and I need to install a Qt4 style for a Qt4 app. I don't know how. I've managed to install one Qt3 theme, but I don't need Qt3.

Any help will be much appreciated!

---

### Post by Tim Sharitt on 2008-07-23
Try the following
```
sudo apt-get install libqt4-gui
```

---

### Post by LinuX-M@n1@k on 2008-07-23
> **Tim Sharitt said:**
> Try the following
```
sudo apt-get install libqt4-gui
```
It's already the newest version :( Wont this try to install Qt4? I have Qt4 installed, I only need to know how to install any theme/style, so all the apps which are using Qt4 to use that theme/style.

```
[boris: ~]$ sudo apt-get install libqt4-gui
[sudo] password for boris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt4-gui is already the newest version.
libqt4-gui set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
[boris: ~]$ 
```

---

### Post by king.pest on 2008-07-23
try running qtconfig

---

### Post by LinuX-M@n1@k on 2008-07-23
> **king.pest said:**
> try running qtconfig

Then what ????? I see 5 default themes, no Add button, nothing!

---

### Post by king.pest on 2008-07-23
Oh I'm sorry, I thought that this application lets you install themes as well. If not, then just download the theme, and then put it (unpacked) into your $HOME/.qt directory. Then it should become visible in your qtconfig. 

(I'm not 100% sure if this is $HOME/.qt or $HOME/.qt4, and I can't check this now since I'm at work; once I'm home I'll check it on my laptop and confirm:))

---

### Post by LinuX-M@n1@k on 2008-07-23
> **king.pest said:**
> Oh I'm sorry, I thought that this application lets you install themes as well. If not, then just download the theme, and then put it (unpacked) into your $HOME/.qt directory. Then it should become visible in your qtconfig. 

(I'm not 100% sure if this is $HOME/.qt or $HOME/.qt4, and I can't check this now since I'm at work; once I'm home I'll check it on my laptop and confirm:))

I'll check it in a second and, hopefully, confirm too :-P

Edit: The folder is .qt, however, when I download the theme, extract it in ~/.qt it doesn't show in qtconfig-qt4. The theme is in ~/.qt, but not in qtconfig-qt4 and therefore, I can't use it. :( :( :(

---

### Post by LinuX-M@n1@k on 2008-07-23
I'll add that the app is Skype and it have libqt4 as a dependency, so I think it uses Qt4. It looks ugly to me, so that's why I'm looking to change the theme.
[ATTACH]78674[/ATTACH]

*bump*

---

### Post by king.pest on 2008-07-23
what kind of qt theme do you wish to install? is it a kde-qt theme? and what were you putting into $HOME/.qt? because I just realised I was putting theme rc files there, but I also had kde themes installed.

---

### Post by king.pest on 2008-07-23
Hey, just a moment ago, I've downloaded [QtCurve]("http://kde-look.org/content/download.php?content=40492&id=1&tan=54430519") theme (source package), compiled it and installed:
```
 mkdir build && cd build && cmake .. && make && sudo checkinstall 
```
without KDE. After that it showed up in qtconfig and I was able to use it.

---

### Post by LinuX-M@n1@k on 2008-07-23
Thankyou!
The theme I wanted to install was the same, but GTK, not KDE. Just noticed that.

---

### Post by king.pest on 2008-07-23
ok, so it's fine:) i'm a newbie to this forum, but i think you should change the sunbject of this thread to [SOLVED] :) (correct me if i'm wrong)

---

