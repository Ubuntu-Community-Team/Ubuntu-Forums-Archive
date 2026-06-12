---
title: "Firefox 3.0.6 &amp; Flash Plugins Problem"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by milkathecow on 2009-02-18
hi everyone, 

I have installed Flash 3.0.6 and am trying to install the flash plugins. 

i go in Add/remove programs and added it, no problem. 

I run firefox fine, 

then i shut down my computer and restart it, restart firefox and he tells me that the plugin is missing and every day i have to reinstall the Flash plugin... 

have tried with the non-free and the free version of the plugins... same issue. 

i am not fully witty with Ubuntu, quite new to it but i can follow instructions on command line and have general IT knowledge (more windows based or command mode). 

can anyone help me please ? 

thanks a lot :)

Olivier

---

### Post by redroad55 on 2009-02-18
This Guide has worked for me several times .. just pay attention to your kernal and purge before new install .. The last method will insure it makes it into proper file ..

> --TROUBLESHOOTING--


ADOBE FLASH PLAYER


On occasion, installing Adobe Flash Player and/or watching online Flash streams successfully isn't as simple as it might ordinarily be. If you have tried installing it already, and are having issues, read on. First of all, please disable any ad-blocking Firefox extensions you have installed, such as Adblock Plus, as they can sometimes interfere with the Flash content you actually want to see. If you are still having issues after disabling the extension(s), you should now completely purge Adobe Flash Player from your system, along with any other packages which may be interfering with it, reinstall only Adobe Flash Player, restart your web browser, and then test Flash performance again. Will both 32-bit and 64-bit users copy and paste this command into the terminal:

sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree

Still no joy? I would suggest following the instructions below for your particular Ubuntu version and architecture.


UBUNTU FAMILY 8.04+ USERS ONLY


Note: You can safely install the Ubuntu package (flashplugin-nonfree), or a Deb archive over the top of the Tar installation method at a later date - I've tested it several times. There's absolutely no need to remove any of the manually installed files, as they will simply be overwritten.

First of all, copy and paste the following command into the terminal and remove the package installed by Ubuntu:

sudo apt-get purge flashplugin-nonfree

32-Bit Users Only: Those of you running the 32-bit version of Ubuntu can install the Flash Player plug-in by selecting and downloading the Deb archive in the drop-down menu on this page of Adobe's site, then executing it and entering your root password when prompted.

32/64-bit Users: Alternatively, 32-bit users can download the Tar archive from the same link provided above and follow my instructions below. If you're a 64-bit Ubuntu user, download the Tar archive of the 64-bit Flash Player plug-in from the bottom of this page to your desktop.

Once downloaded, simply open the Tar archive, look for a file named "libflashplayer.so", copy that file to your desktop, then both 32-bit and 64-bit users execute the following command in the terminal:

sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so

You may now restart your web browser and use the plugin.

Best to you

---

