---
title: "MSN Messenger 8.1 working in Linux"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by Ray() on 2009-08-29
Hi there,
afters some struggle I managed to get the msn messenger working under linux and thought I'd share it in case anyone else was trying to do so as well.

Like most of you I hate msn messenger but there is one thing that I like about it and that is the various games u can play using it. Unfortunately you can't do so with any linux native messengers like aMSN or KMess, etc...

One of the many tutorial on how to do this I followed was on [this french website]("http://www.commentcamarche.net/forum/affich-12419613-windows-live-messenger-sur-linux"). So here is what you have to do to get it working. I tried it with these versions of these aplication and don't know whether it will work with newer versions.

1. install wine ( I used [1.1.21 i386]("http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.21~winehq0~ubuntu~9.04-0ubuntu1_i386.deb"))
2. get winetricks (write in terminal: wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) )
3. run winetricks (in terminal: sh winetricks) and check these packages to install: riched30, gdiplus, msxml3, gecko, flash and click ok
4. download msn messenger ( [ver. 8.1 worked]("http://www.microsoft.com/downloads/details.aspx?familyid=D78F2FF1-79EA-4066-8BA0-DDBED94864FC&displaylang=en") any other I tried didn't)
5. set your wine windows version to windows 2000 (in terminal: winecfg, choose the win. version and click apply)
6. install msn messenger (in terminal: msiexec /i Install_Messenger.msi or wine Install_Messenger.exe  -depends on what you've downloaded)
7. that's it :) you should be able to run it from the wine applications menu or by typing wine "c:\\Program Files\MSN Messenger\msnmsgr.exe"
 in the terminal

---

### Post by ewan86 on 2009-11-21
it works!!! but it says i have to download the latest version so it wont log in...and that doesn't work :(

---

### Post by Ray() on 2009-11-22
too bad, at the time I tried this it didn't do that :(

---

### Post by ewan86 on 2009-11-22
yeah I assume it's cos they released a new version. I was impressed it came up at all!! Them French people haven't come up with a new solution for the latest version of windows live messenger??

---

### Post by Ray() on 2009-11-22
no idea whether someone has a newer version working... the idea itself - running msn messenger on linux - is quite crazy when you have pidgin, empathy, aMSN and other clients easily available... so only crazy people like us are trying to install MS msn messsenger :-D

when I tried it with the 8.1 version, there was a much newer one available at that time and I don't remember any update prompts and if there were any I just canceled them... I think it should let you use the older version (does it on windows?) ...anyways I don't cared that much, the whole thing was quite annoying and I don't want to loose any more time by installing something I barely need

---

