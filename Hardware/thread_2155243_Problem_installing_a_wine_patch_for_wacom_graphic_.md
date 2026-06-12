---
title: "Problem installing a wine patch for wacom graphic tablet"
date: 2013-06-17
forum: Hardware
---

### Post by zaly on 2013-06-17
Hi!
I have ubuntu 12.04 LTS and wine 1.4 (installed from the software center) and a wacom volito 2. To solve a [bug]("https://bugs.launchpad.net/wine/+bug/151448/") that wine has when it comes to reading/interpreting the pen pressure of graphic tablets in programs like painttool SAI (or photoshop, but I have SAI) I wanted to try and install the patches mentioned in comments [#71]("https://bugs.launchpad.net/wine/+bug/151448/comments/71") and [#72]("https://bugs.launchpad.net/wine/+bug/151448/comments/72") and then attached in posts [#75]("http://bugs.winehq.org/attachment.cgi?id=39528") and [#76]("http://http://bugs.winehq.org/attachment.cgi?id=39527") 
To install the two patches I copied the text in a file I saved with the extension .patch, copied the two .patch files in the .wine folder in my home and then ran 

cd /home/myhome/.wine
patch -p1 < patch1.patch

the result was 

can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/dlls/winex11.drv/wintab.c b/dlls/winex11.drv/wintab.c
|index ba33732..21b6e6f 100644
|--- a/dlls/winex11.drv/wintab.c
|+++ b/dlls/winex11.drv/wintab.c
--------------------------
File to patch: ^C


Could anyone help with this?
Thanks in advance!

---

### Post by RevPobanz on 2013-06-17
> cd /home/myhome/.wine

The source code for wine from git is usually stored in: 
/home/myhome/wine-git
  not in the ".wine" directory. 
Do you have the source code downloaded? If not see
[http://wiki.winehq.org/GitWine](http://wiki.winehq.org/GitWine)

Once you have this source code downloaded, put your patch files in this same directory '~/wine-git' and apply the patches before compiling the code.

---

### Post by RevPobanz on 2013-06-17
By the way, when you install from source, you will not be able to use software center to install or update wine. First remove wine 1.4 through the software center.

---

### Post by zaly on 2013-06-18
Thanks for answering!
 Those two patches are for 1.4 and they don't work with newer versions of wine. I already have installed git (version 1.7.9.5) but there's no wine-git folder in my home (the only 'w' folder is .wine).

---

### Post by zaly on 2013-06-20
I tried on my laptop I installed ubuntu 12.04 on it a few days ago (for the firs time) I hadn't installed wine yet, I added wine ppa and then ran

To install wine 1.4:
```

sudo apt-get update && sudo apt-get install wine1.3
sudo dpkg --configure -a
sudo apt-get install -f

``` 

then i don't remember why but I followed these instructions [http://askubuntu.com/a/269374](http://askubuntu.com/a/269374)
```
gksu gedit /etc/apt/preferences.d/base-files
sudo apt-get dist-upgrade
``` 

then I got wine-git
```
sudo apt-get build-dep wine
sudo apt-get install git
git clone git://source.winehq.org/git/wine.git ~/wine-git
```

and installed the patches
```
cd ~/wine-git
patch -p1 < 39527.patch
patch -p1 < 39528.patch
./configure && make depend && make
./configure --enable-win64  && make depend && make
```

Nothing changed, the patches don't work. Did I make a mistake with something?

---

