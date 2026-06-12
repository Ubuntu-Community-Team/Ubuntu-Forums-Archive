---
title: "Flash player 10 upgrade problems"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by haydemon on 2009-10-09
I'm having a terrible time upgrading Flash player to the new 10.0 version. It shows has being installed, but I can't get the new Shockwave flash plugin to install (v.10.0 r22). I've tried EVERYTHING! From installing directly from Adobe (.deb version--I'm running Ubuntu 8.04 64bit) to an .rpm version (after installing .rpm, but this didn't help either). I'm running out of options. The latest attempt was to follow a script that I found in one of these Forums from an Alejandro that was as follows:

$ wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)
$ sudo chmod U+x flash10_en.sh
$ sudo sh ./flash10_en.sh

and this is what I get:[INDENT]mhayden@mhayden-desktop:~$ sudo sh ./flash10_en.sh
sudo: unable to resolve host mhayden-desktop
Closing Firefox
sudo: unable to resolve host mhayden-desktop
firefox: no process killed
Downloading and instaling Getlibs for required libraries
--09:13:41--  [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
           => `getlibs-all.deb'
Resolving [www.boundlesssupremacy.com]("http://www.boundlesssupremacy.com")... 174.132.151.2
Connecting to [www.boundlesssupremacy.com|174.132.151.2|:80]("http://www.boundlesssupremacy.com%7C174.132.151.2%7C:80")... failed: Connection refused.
sudo: unable to resolve host mhayden-desktop
dpkg: error processing getlibs-all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 getlibs-all.deb
Removing previous installs of flash:
sudo: unable to resolve host mhayden-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
Package libflashsupport is not installed, so not removed
E: Couldn't find package nspluginwrapper
sudo: unable to resolve host mhayden-desktop
sudo: unable to resolve host mhayden-desktop
sudo: unable to resolve host mhayden-desktop
sudo: unable to resolve host mhayden-desktop
sudo: unable to resolve host mhayden-desktop
Installing ia32-libs and nspluginwrapper
sudo: unable to resolve host mhayden-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs
Getting libs
sudo: unable to resolve host mhayden-desktop
sudo: getlibs: command not found
sudo: unable to resolve host mhayden-desktop
sudo: getlibs: command not found
sudo: unable to resolve host mhayden-desktop
sudo: getlibs: command not found
Installing Flash Player 10
--09:13:43--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
           => `install_flash_player_10_linux.tar.gz.2'
Resolving fpdownload.macromedia.com... 96.17.50.70
Connecting to fpdownload.macromedia.com|96.17.50.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,044,751 (3.9M) [application/x-gzip]

100%[====================================>] 4,044,751    676.32K/s    ETA 00:00

09:13:50 (640.97 KB/s) - `install_flash_player_10_linux.tar.gz.2' saved [4044751/4044751]

libflashplayer.so
sudo: unable to resolve host mhayden-desktop
cp: cannot stat `install_flash_player_10_linux/libflashplayer.so': No such file or directory
sudo: unable to resolve host mhayden-desktop
sudo: nspluginwrapper: command not found
Linking the libraries so that firefox can see them.
sudo: unable to resolve host mhayden-desktop
sudo: unable to resolve host mhayden-desktop
Done :-)
You may re-start Firefox now
[/INDENT]Can somebody PLEASE HELP??? BTW, I recently upgraded to Firefox 3.5 with no problems. I'm somewhat of a beginner, so please be patient. :( Thanks in advance!!!

---

### Post by jeremyswalker on 2009-10-09
As you are running 64-bit, you should try and install flash from here -> [http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

---

### Post by haydemon on 2009-10-09
> **jeremyswalker said:**
> As you are running 64-bit, you should try and install flash from here -> [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

I've tried; several times; several different ways. I won't install; better yet, it will install the player but not the plugin itself (doesn't show up on the list of plugins like it's supposed to: as Shockwave flash 10.0 r22). What's more, the newest version of Flashplayer is already in the list of programs available thru Synaptic, and I can even install it through there, but not the plugin itself (in parenthesis above). I tried going to the link you provided (which is one of the links I've used before), and going through the steps as indicated, but either one of 2 things happen: (1) if I choose the .deb version, it comes up with the error "a newer version is already installed," so it won't install anything; or (2) if I choose the .tar.gz version, it won't create the directory that the instructions say it will; all I get is a "binary file" called libflashplayer.so, and that's as far as get.

I'm going bananas over this!!! But I won't give up. Thanks! ](*,)

---

### Post by jeremyswalker on 2009-10-09
In Synaptic, search by name only for 'flash'. Does it show 'flashplugin-nonfree' or something similar installed?

---

### Post by haydemon on 2009-10-09
yes, but it only shows the old version (9.0.246), not installed (purposely), but I need the NEW version (10.0.r22), which is not on the list. Because if I install the older version, FF will NOT recognize Flash 10 at all, regardless.

---

### Post by kev0168 on 2009-10-09
> **haydemon said:**
> I've tried; several times; several different ways. I won't install; better yet, it will install the player but not the plugin itself (doesn't show up on the list of plugins like it's supposed to: as Shockwave flash 10.0 r22). What's more, the newest version of Flashplayer is already in the list of programs available thru Synaptic, and I can even install it through there, but not the plugin itself (in parenthesis above). I tried going to the link you provided (which is one of the links I've used before), and going through the steps as indicated, but either one of 2 things happen: (1) if I choose the .deb version, it comes up with the error "a newer version is already installed," so it won't install anything; or (2) if I choose the .tar.gz version, it won't create the directory that the instructions say it will; all I get is a "binary file" called **libflashplayer.so**, and that's as far as get.

I'm going bananas over this!!! But I won't give up. Thanks! ](*,)

Put the libflashplayer.so file in the ~/.mozilla/plugins/ directory then restart Firefox. It works for me this way.

---

### Post by draxx9000 on 2009-10-14
hi im rell new to this and ov cores i am all reddy having problems 
i have ben trying to figer out how to get this swfdec thing installd for the last fuw weeks 
and am tierd of fighting it i just whant it to work 
i have chekt pkg maniger or what ever it is for the flash nonfree and it is installd but not working right 
its not leting me wach any thing on the web and all i get wen i do try is ether a blank box or a bunch of garbidg that you cant do any thing with 
so after i tryd doing that i thot i wood try terminal and i got most of the way throw it till it was reddy for the (make install) comand and thats wer im having problems now 
the last fuw lins in terminol wen it fails is 


libtool: install: /usr/bin/install -c .libs/libswfdec-0.9.so.2.0.0 /usr/local/lib/libswfdec-0.9.so.2.0.0
/usr/bin/install: cannot create regular file `/usr/local/lib/libswfdec-0.9.so.2.0.0': Permission denied
make[4]: *** [install-libLTLIBRARIES] Error 1
make[4]: Leaving directory `/home/ken/swfdec'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/ken/swfdec'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/ken/swfdec'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/ken/swfdec'
make: *** [install-recursive] Error 1

 plzzzzzzzz help me

---

### Post by yomobro on 2009-10-30
Haydemon,

There were some typo's in the script you tried to run.  I've corrected them here for you.  The former path for getlibs is now defunct.  I've changed it.  This should work now.:

#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba [email]romeo.cioaba@spotonearth.com[/email]
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
#wget [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
wget [http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb)
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
tar zxvf install_flash_player_10_linux.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

rm -rf ~/install_flash_player_10_linux.tar.gz
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/

sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"

Let me know how this works for you...;)


Cheers,
YMB

---

