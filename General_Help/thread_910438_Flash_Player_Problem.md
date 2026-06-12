---
title: "Flash Player Problem"
date: 2008-09-04
forum: General Help
---

### Post by ~Nightingale~ on 2008-09-04
Well, for a while now, I have been trying to install the new Flash Player, and I simply can't get it to work.
Here's what happens;
dirname: extra operand `Documents/install_flash_player_9_linux/flashplayer-installer'
Try `dirname --help' for more information.

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 9 will be installed in your home directory.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...





----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/ian/.mozilla

Proceed with the installation? (y/n/q): y
cp: cannot stat `/libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n): 

I don't understand what to do, and I am the admin!
Is the problem obvious and easy to fix? Am I just being stupid? Is there another way to get Flash Player?

---

### Post by nbayiha on 2008-09-04
Why do you want to install it ?  You already have the flash you need in synaptic .
Just install it from the package manager .

---

### Post by ~Nightingale~ on 2008-09-04
I couldn't find it, how do I get the latest? Synaptic; Can't Find. Update Manager; Hasn't updated it yet. HOW?

---

### Post by nbayiha on 2008-09-04
First what do you want to do with flash ? Watch youtube ?

---

### Post by wolfen69 on 2008-09-04
first go to system>administration>software sources and make sure you have all the repos enabled. then you can search synaptic for flashplugin-nonfree.

---

### Post by ~Nightingale~ on 2008-09-04
First, nbayiha, No, the latest online games require the latest flash plugin
and Wolfen, thank you, I hope it works.

---

### Post by ~Nightingale~ on 2008-11-30
'Sigh' I'm having the same problem with Flash Player 10

---

### Post by ~Nightingale~ on 2008-11-30
Does anyone know what to do?

---

### Post by soro2005 on 2008-11-30
You can try to:
(a) remove the packages flashplugin-nonfree and, if on 64 bit, also nspluginwrapper
(b) locate and delete all instances of libflashplayer.so that may be left somewhere.
(c) if you are on Ibex/32bit, you best just reinstall the package flashplugin-nonfree. It is version 10, and it should be up to date.
(d) if you are on a 64bit system, you may want to check out the [brand new 64 bit flash plugin](http://blogs.adobe.com/penguin.swf/2008/11/now_supporting_16_exabytes.html). If you are on an older 32bit system and there's no v. 10 even in the backports, you check out the tarball from the Adobe site.
(e) if you have checked out the tarball (32bit or 64bit) and want to go with it, you extract it and find the file libflashplayer.so. Copy it (as superuser) into /usr/lib/mozilla/plugins

---

