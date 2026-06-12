---
title: "rational application developer 7.5 on ubuntu 9.10 karmic koala 64bit"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by corep105 on 2009-10-30
this is a quick writeup of what i had to do to get rad 7.5 running on ubuntu 9.10 64bit. Latest RAD is currently 7.5.4.

install ubuntu 9.10 karmic koala 64bit and update everything
install java 1.6
download jaunty libstdc++5 (both 32bit & 64bit) - [http://packages.ubuntu.com/jaunty/libs/libstdc++5](http://packages.ubuntu.com/jaunty/libs/libstdc++5)
install libstdc++5 64bit with debi (just doubleclick on it and install)
extract libstdc++5 32bit and copy files manually to /usr/lib32/

change from dash to bash with: sudo dpkg-reconfigure dash

install rad 7.5 from the install kit :-)

if using subclipse version 1.6 seems to give "unable to load default svn client" - use version 1.4 instead.

i think that was all. Hope it will save other people some time installing.

So far it is running very well.

Regards
corep

---

### Post by corneil on 2009-10-31
Installed libstdc++5 64 and 32 bit. 
Installed sun java 6
Ensured bash is default shell

I launch the installer and check the radio button to accept license agreement.
The Next button becomes available but clicking it does nothing.
I have launched the installer with -log but the log is not created, I do not know how to find out what might be wrong.

Any ideas?

---

### Post by corneil on 2009-10-31
No error messages that indicate a problem in /var/ibm/InstallationManager/logs

---

### Post by Gabejazz on 2009-11-04
Press the Space key or Enter key. It seems that it's a problem with the GTK version or something else.

---

### Post by kobe.hsu on 2009-11-06
googled from someone's article,

export GDK_NATIVE_WINDOWS=true

before you launch RAD or eclipse

seems some bug issues about current GTK

---

### Post by Gabejazz on 2009-11-11
That's right, so I do found the fix, just create a *.sh file, and paste the follow:

export GDK_NATIVE_WINDOWS=true
/opt/ibm/rad/eclipse -product com.ibm.rational.rad.product.ide

The second line is the same command that you can find in the menu of your RAD, for me (RAD 7) is that above.

Then replace the *.sh command in your RAD menu.

---

