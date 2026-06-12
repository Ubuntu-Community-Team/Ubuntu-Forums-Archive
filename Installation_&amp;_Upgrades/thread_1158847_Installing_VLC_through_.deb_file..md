---
title: "Installing VLC through .deb file."
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by Gagansharma200 on 2009-05-14
Hi ,
I tried to install VLC player from precompiled .deb package(In offline mode ,without internet) but when I clicked to icon after installation to launch it ,nothing turned up on screen.
No matter how many times I double clicked on icon, VLC was not launched.
What could go wrong.

---

### Post by ad_267 on 2009-05-14
Go to applications - accessories - terminal, enter "vlc" (without the quotes) and press enter. You should get some error messages telling you why vlc could not be run.

First you should make sure you have all of the dependencies listed at [http://packages.ubuntu.com/jaunty/vlc](http://packages.ubuntu.com/jaunty/vlc) installed.

---

### Post by mac9416 on 2009-05-14
Gagansharma200, without the Internet, installing software in Ubuntu can be a real pain. When you install something like VLC there are going to be dozens ofr **dependencies**, other .debs needed to install the depending package.
    However, there's software to get the dependencies: [Keryx]("http://keryxproject.org"). It'll make your life much simpler. ;)

---

