---
title: "how to install"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by salim.madni on 2009-04-27
hello gurus

can some one let me know i have installed a new ubuntu 9.04 desktop edition

i wish to know and learn step by step

- how can i install,download INTERNET EXPLORER which use in windows xp,vista since some of the sites does not work in firefox

- where to find cube effects, where to download from pacakages and how to install and use it on screens

- how we can create .docx office 2007 types documents using openoffice, where can i find update,plugin,addons is someone can help and how to install it

regards
salim

---

### Post by Mark Phelps on 2009-04-27
You're not going to be able to use Internet Explorer  v7 or v8 in Linux (unless you install Wine) -- it's strictly an MS Windows tool.  There is an "old" version of IE (I think it's version 4) that runs in Linux, but that won't give you anywhere near the capabilities you're used to in IE 7.

---

### Post by Partyboi2 on 2009-04-27
You should be able to use wine to install IE6 or IE7
[http://maketecheasier.com/how-to-install-safari-internet-explorer-opera-on-ubuntu/2008/04/01](http://maketecheasier.com/how-to-install-safari-internet-explorer-opera-on-ubuntu/2008/04/01)

For the cube you will need to go to System>Pref>Appearance>Visual Effects and select 'Extra' then you will need to install compizconfig-settings-manager package, you can do this by opening a terminal (Applications>Accessories>Terminal) and typing
```
sudo apt-get install compizconfig-settings-manager
```once it is installed go to System>Pref>compizconfig-settings-manager and  tick the box for "Desktop Cube" and "Rotate Cube" under "Desktop" then click on "General>General options>Desktop Size"  and change "Horizontal Virtual Size" to 4. Then close and try it out by pressing Ctrl+Alt+left or right arrow key.

---

