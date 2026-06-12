---
title: "Running Opera Mini on Linux?"
date: 2008-11-16
forum: General Help
---

### Post by pointyblue on 2008-11-16
Hi,

Any ideas on how to make the Opera Mini browser run on Ubuntu? (Or on Linux i general...)

I think it might provide a better surfing experience for people on a low bandwith connection or for people who have to pay per mb.

---

### Post by justutkarsh on 2009-03-06
You can run it using various mobile emulators available some are:

1.Microemulator
2.Sun WTK
3.Mpowerplayer
4.Kemulator

I have used all of them 
using opera-mini microemulator is very easy and popular but it does not allow saving of  files and cookies on local filesystem
more info here:
helpforlinux.blogspot.com/2008/12/use-opera-mini-in-ubuntu.html

I personally use Kemulator which is as far best in emulating any j2me application.
installing it on windows is easy but on ubuntu

1. Install wine  sudo apt-get install wine 
2. Get KEmulator lite 0.9.7 use google
3. you need to install jre in your wine installation 
   just download this file j2re-1_4_2_19-windows-i586-p.exe
   and right click open with wine installer
4. run kemulator.exe  it will exit if you open 
   opera-mini-4.2.13337-advanced-en-in.jar from file menu
5  I use following command to launch
```

 env WINEPREFIX="/root/.wine" wine "C:\Program Files\Java\j2re1.4.2_1\bin\java.exe" -cp "Z:\etc\kemulator\KEmulator.jar" emulator.Emulator -jar "Z:\etc\mobileapps\opera-mini-4.2.13337-advanced-en-in.jar " -awt -lwj
```

kemulator allows saving of file and cookies with UCWEB 6.3 which is equivalent to operamini

---

### Post by itagomo on 2012-04-08
3 yr old post but very helpful ! thanks !

---

