---
title: "[SOLVED] firefox problem"
date: 2008-07-26
forum: General Help
---

### Post by mosty friedman on 2008-07-26
hey everyone,
i got this problem with firefox...it was working fine before but i kinda was doin somethin on the terminal and i messed it up...the stop,refresh,forward,backward icons are grey and i cant use them..also the history has been deleted..anyone familiar with this problem??

---

### Post by PurposeOfReason on 2008-07-26
It'd help to know the terminal commands you did. If you forgot, post the output of

```
 cat ~/.bash_history
```

---

### Post by joel5525 on 2008-07-28
I'm having the exact same problem

Here's some recent commands i've run:
sudo apt-get install ie4linux
sudo apt-get install mozplugger
sudo nano /etc/mozpluggerrc 
sudo gedit /etc/mozpluggerrc 
rm ~/.mozilla/firefox/pluginreg.dat 
sudo rm ~/.mozilla/firefox/pluginreg.dat 
sudo gedit /etc/mozpluggerrc
cd ies4linux-*
./ies4linux
sudo gedit /etc/mozpluggerrc
sudo aptitude autoclean
sudo apt-get install java
sudo apt-get autoclean
sudo apt-get install fbreader
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install tor
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
sudo apt-get install subversion
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd linux-uvc/linux-uvc/trunk
cd /linux-uvc/trunk
ls
cd trunk
dir
make
sudo make install
sudo apt-get install luvcview
luvcview
flashcamwrap firefox Test/webcamtest.html
flashcamwrap flashplayer Test/webcamtest.swf
sudo flashcamwrap flashplayer Test/webcamtest.swf
flashcamwrap firefox Test/webcamtest.html
sudo apt-get install ekiga
sudo apt-get autoclean
ekiga
guvcview
sudo apt-get install guvcview
sudo apt-get install gnucview
tar xvf flashcam-1.1.tgz
cd Desktop
tar xvf flashcam-1.1.tgz
cd flashcam-1.1.tgz
cd flashcam-1.1
make
sudo make install
sudo flashcam -L 
sudo chmod o+rw /dev/video*
flashcamwrap firefox Test/webcamtest.html
sudo flashcam
flashcam
sudo apt-get update
apt-get update
cd vmware-distrib
cd Desktop
cd vmware-distrib
sudo bash vmware-install.pl
cd installer
dir
sudo bash services.sh
sudo apt-get autoclean
apt-cache search
apt-cache search pool
apt-cache search irc
echo $path
echo $PATH
which mount
find /usr -name pidgin
man ftp
sudo apt-get install firefox-3.0
sudo apt-get remove firefox-3.0
sudo apt-get autclean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install firefox-3.0
sudo aptitude remove firefox
sudo apt-get remove firefox

---

### Post by joel5525 on 2008-07-28
figured it out

```
sudo apt-get remove firefox-3.0
sudo rm /home/user/.mozilla
sudo apt-get install firefox-3.0
```

make sure to replace "user" in the second line with your username and everything should be fixed

---

### Post by mosty friedman on 2008-07-29
ahh thanks man..its working great now

---

