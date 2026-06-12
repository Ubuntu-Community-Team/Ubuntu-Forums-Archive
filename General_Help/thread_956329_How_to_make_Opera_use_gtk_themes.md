---
title: "How to make Opera use gtk themes"
date: 2008-10-23
forum: General Help
---

### Post by king.pest on 2008-10-23
Dear all, 

I know there must be a number of Opera users/lovers among you, and even if one doesn't like this browser, one may be forced to use it from time to time (testing purposes for example). The problem with Opera is, that it uses Qt interface, and that one doesn't look good under Gnome/Xfce. Here are some tricky tips on howto make Opera look like any other gtk app. 

First you got to have Qt4 installed, because it's only possible with Opera build with Qt4 support. Then you got to have some header files for both Qt and Gtk, and a subversion client. Easy way to install all that:

```
sudo apt-get install libqt4-devel libgtk2.0-dev build-essentials subversion
```

this should pull all the necessary dependencies. Now we have to download and compile gtk style: 

```
svn co svn://labs.trolltech.com/svn/styles/gtkstyle
cd gtkstyle
qmake && make && sudo make install
```

Once qgtkstyle is installed, we have to enable it with qtconfig-qt4 (see attachment), and then all our Qt4 apps will use a gtk theme. All except Opera. 

The distributed package of Opera contains a binary statically compiled with its own Qt4 lib copy. There was however one snapshot published sometime ago, that contained a dynamically linked binary, and you can get it [here]("http://snapshot.opera.com/unix/snapshot-2436/intel-linux/"). This isn't the newest release (it's a 9.60 snapshot), so it may not be very stable, but until now this is the only Qt4 dynamically compiled Opera binary ever published. Since Opera Software plans on dropping Qt3 support in their browser sometime in the future, there probably will be more Qt4-shared packages. Until then, enjoy using this snapshot (which is quite stable).

(thank you's go to [Hadret]("http://hadret.com/2008/10/22/aplikacje-qt-jak-gtk/trackback/"), a Polish blogger who showed me there's something like qgtkstyle)

---

### Post by Piraja on 2009-09-26
Thanks! Small corrections to the install command: 

```
sudo apt-get install libqt4-dev libgtk2.0-dev build-essential subversion
```

That is, at least when I try to install these packages, it is not libqt4-devel but libqt4-dev and not build-essentials but build-essential (I have myself made the latter typo/mistake in trying to help someone).

---

