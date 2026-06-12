---
title: "Quickest way to get MAC fonts (Lucida Grande and more) for Ubuntu (GNOME)"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by cb2410 on 2009-07-22
[LIST]
[*]Applications->Accessories->Terminal
Copy/paste these commands:
[/LIST]

[LIST]
[*]```

wget http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz
tar zxvf macfonts.tar.gz
sudo mv macfonts /usr/share/fonts/
sudo fc-cache -f -v[FONT=Verdana]

[/FONT]
```
[/LIST]
MAC fonts are now installed:

Installed fonts:
 
[LIST]
[*]AppleGaramond
[*]Aquabase
[*]LITHOGRL
[*]Lucida Grande
[*]Lucida Mac
[*]lucon
[*]MacGrand
[/LIST]
 
Now change the default system fonts

+ Right click on your Desktop 

+ Change Desktop Backround 



+ Click on Fonts and select those you like


:popcorn:

---

### Post by raymondh on 2009-07-22
And for possible fonts to use, see attached.  Have fun.

---

### Post by dmsurti on 2009-10-05
Thanks a ton. That saved me a lot of time.

I am a mac user, but in office I use Ubuntu via VBox on a Win XP machine.

Lucida Grande is my favorite text font.

Regards
Deepak:)

---

### Post by abramsov on 2010-08-22
sorry lads is there any chance to pop up them fonts again. 
or explain how to download them because there is an error 403: FORBIDDEN

thx

---

### Post by isbiyanto on 2012-02-17
like this... thanks for sharing... :KS:KS:KS

---

### Post by coldjeanz on 2012-07-10
Anyone else that installed these have trouble with the Lucida Mac font? Everything works fine except all numbers do not have the same bolded, defined look.

---

### Post by gdesilva on 2012-07-10
Has anyone experienced the following problem???


 wget [http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz](http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz)
--2012-07-10 16:21:51--  [http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz](http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz)
Resolving ubuntu-debs.googlecode.com (ubuntu-debs.googlecode.com)... 173.194.72.82, 2404:6800:4008:c01::52
Connecting to ubuntu-debs.googlecode.com (ubuntu-debs.googlecode.com)|173.194.72.82|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2012-07-10 16:21:52 ERROR 403: Forbidden.


Have they blocked access?

---

### Post by blueshead on 2012-07-10
same here 403 forbidden..

---

### Post by oldos2er on 2012-07-10
Try Mirror 1 here: [http://www.webupd8.org/2010/06/how-to-install-apple-mac-osx-fonts-in.html](http://www.webupd8.org/2010/06/how-to-install-apple-mac-osx-fonts-in.html)

With that, this old thread is closed.

---

### Post by StSav012 on 2013-01-21
Look for it here: [https://docs.google.com/file/d/0B7lHOGlpWanGSDFpbHZJUy1mNFk/edit]("https://docs.google.com/file/d/0B7lHOGlpWanGSDFpbHZJUy1mNFk/edit"). I shall keep it as long as I can.

---

