---
title: "How do I install Skype on usb stick version?"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by Richardah on 2009-10-10
Hi.  I'm sorry if this has already been dealt with 1000 times, but I have tried a search and failed to come up with the goods.

I am an absolute Linux newbie, although I have used W*****s for years.  I have one of the original eeepc's and have experienced multiple problems logging onto wireless networks, so I thought I would try the Ubuntu on a stick distro before installing it on the machine permanently.

Really impressed with the ease of wireless connection.

I want to check out Skype and can't see how to install it.  I have tried various things:

1)  Went to Skype and downloaded latest version.  If I double click or right click I get a box asking me to choose a program to open a deb with, but no options presented.  I downloaded gdebi.tar.gz, but found the same problem.

2) Thought I would try Synaptic, so went to System, but could not see Administration

3) Command line next.  Tried installing the downloaded Skype file from that but that did not work because of missing dependencies.

4) Tried the Medibuntu route.  Typed in about 4 lines into the command line to add the repository, but got a 404.  I double checked spaces etc.

Do I just need to sit down and spend a couple of days reading the book or is there an easy way to install Skype?  It doesn't even have to be that easy as long as it works.

Richard

---

### Post by HarshReality on 2009-10-10
Portable is easy in Win.. not so much in Lin.. might want to give that up

---

### Post by howefield on 2009-10-10
Try downloading the .deb file from 

[http://www.skype.com/intl/en-gb/download/skype/linux/choose/](http://www.skype.com/intl/en-gb/download/skype/linux/choose/)

For Jaunty, you need the 8.10+ 32bit (if you are running 64 bit, then obviously it is the 64 bit you want)

Save the file to your desktop, then double click to start the install process.

---

### Post by Richardah on 2009-10-10
Just to add that Skype now shows on my desktop, but does nothing after saying "starting program".

Perhaps because of the missing dependencies libqt4-core and libqt4-gui

---

### Post by Richardah on 2009-10-10
Thanks for the speedy answers guys.

This is the file that i downloaded, but when I double click it asks me to choose an application.

---

### Post by howefield on 2009-10-10
> **Richardah said:**
> Just to add that Skype now shows on my desktop, but does nothing after saying "starting program".

Perhaps because of the missing dependencies libqt4-core and libqt4-gui

Try opening a terminal and type skype into it, then paste any error(s) back here.

---

### Post by Richardah on 2009-10-10
Thanks Howefield

error while loading shared libraries: libQtDBus.so.4: cannot open shared object file or directory

---

### Post by Richardah on 2009-10-12
Hi

I had another go at medibuntu, and that seemed to work.  My problem now is that the audio output does not work with Skype.  However, as this is a known problem I am getting hopeful.

Richard

---

