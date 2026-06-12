---
title: "Install adobe Flash Player 10 in Ubuntu (Ubuntu 32 and 64 bit)"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by Tclarkie on 2009-08-03
[B](courtesy of [http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html))

[/B][CENTER]***_[B]DO NOT REPLY TO THIS POST**_[/B]* 
(but please use the poll)

This is to everybody who's posting how to install Flash


** Install adobe Flash Player 10 in Ubuntu (Ubuntu 32 and 64 bit) **
[/CENTER]
**Method 1**
 First you need to download the .deb package from [here]("http://www.adobe.com/shockwave/download/alternates/")
 Click the download link to begin installation. If a dialog box appears, follow the instructions to save the installer to your desktop.
 Save the .deb package to your desktop, and wait for it to download completely.
 Double-click on the .deb package and follow the instructions to complete installation.
 or
 Use the following command from your terminal[INDENT]sudo dpkg -i install_flash_player_10_linux.deb
[/INDENT]This will complete the installation.
 **Method 2**
 **Using apturl**
 First you need to make sure you have installed apturl using the following command[INDENT]sudo apt-get install apturl
[/INDENT]Now you need to go to the download page mentioned above click on [linux[IMG]http://images.intellitxt.com/ast/adTypes/mag-glass_10x10.gif[/IMG]]("http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html#") section from dropdown box select APT for Ubuntu 8.04+ Click the download link and follow the instructions to complete installation.
 To get the most up-to-date Flash Player in the future, issue the following commands from the Terminal:[INDENT]sudo apt-get update
 sudo apt-get install adobe-flashplugin
[/INDENT]**Verify your plugin Installation**
 To verify the plugin is installed in Mozilla, launch Mozilla and choose Help > About Plug-ins from the browser menu.
 or
 In your broweser enter the following command and check[INDENT]about:plugins
[/INDENT]**For 64 bit Users**
 Thanks to Alejandro for this nice script.First you need to Download shell script from [URL="http://queleimporta.com/downloads/flash10_en.sh"]here
[/URL] Using the following command
 wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)
 Now you need to give execute permissions using the following command
 sudo chmod +x flash10_en.sh
 Run the script now
 sudo sh ./flash10_en.sh

---

### Post by dhylands on 2009-08-26
I tried method 3, and I had to edit the flash10_en.sh script to use:

[FONT=Courier New]sudo cp libflashplayer.so /usr/lib/mozilla/plugins/[/FONT]

instead of looking in the install_flash_player_10 directory (I guess Adobe updated their tar file and didn't include the directory any more).

I also had to install getlibs, as described in this thread:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Guilden_NL on 2009-08-31
IMHO, for 64 bit users, you should point out that this is installing 32bit Flash.

For 64 bit Flash which supports smooth full screen video, they should use the script available here: [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=7877239#post7877239[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7877239#post7877239")

---

