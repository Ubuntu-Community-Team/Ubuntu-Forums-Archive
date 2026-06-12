---
title: "Installing Adobe Flash Player Firefox 3.04 in ubuntu 8.10"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by nabilalk on 2008-12-19
Hi, I'm trying to play music via Pandora.com in Firefox. I downloaded the Adobe Flash Player Firefox Plugin from the Adobe website. Then I installed install_flash_player_10_linux.deb using the Ubuntu built in debian package installer. I restarted Firefox, and I still cant listen to music on Pandora. I then restarted Ubuntu and still no joy.

What do I need to do after the Debian package installer is finished to complete the installation?

Thanks,
nka

---

### Post by BrandonBan6 on 2008-12-19
I have troubles with getting anything to work from GUI installers and deb packages...but I'm a bit of a newbie myself. 

I like to use:

```

sudo apt-get update
sudo apt-get install flashplugin-nonfree

```

Restart Firefox....also, I like Slacker.com over Pandora, but to each to their own I suppose.

---

### Post by nabilalk on 2008-12-21
> **BrandonBan6 said:**
> I have troubles with getting anything to work from GUI installers and deb packages...but I'm a bit of a newbie myself. 

I like to use:

```

sudo apt-get update
sudo apt-get install flashplugin-nonfree

```

Restart Firefox....also, I like Slacker.com over Pandora, but to each to their own I suppose.

Hi, thanks for the suggestion. Unfortunately, Pandora still is not loading. It says that it is loading but stops. Any other ideas? Perhaps I should reinstall firefox and start with a new profile?

Also, Slacker.com won't play either. What am I missing to get these two sites to play?

---

### Post by BrandonBan6 on 2008-12-22
Hmm, I'm sorry, not to sure myself what is going on there. Perhaps try another browser to see if it is just firefox? Opera or Flock...I think they both have linux compatible browsers.

---

### Post by hyperdude111 on 2008-12-22
This is a solution for all codecs ; dvd, divx, mp4, flash, mp3.....
It is also really easy.

Go Application-Accessories-Terminal

Type without quotes " sudo apt-get install ubuntu-restricted-extras "

If you just want flash download the tar.gz from adobe, unpack it, close firefox, and run installflashplayer.sh (i am not sure on the name there should be two files try them both)

~hyper~

---

### Post by nabilalk on 2008-12-22
> **hyperdude111 said:**
> This is a solution for all codecs ; dvd, divx, mp4, flash, mp3.....
It is also really easy.

Go Application-Accessories-Terminal

Type without quotes " sudo apt-get install ubuntu-restricted-extras "

If you just want flash download the tar.gz from adobe, unpack it, close firefox, and run installflashplayer.sh (i am not sure on the name there should be two files try them both)

~hyper~

I think the problem might be that I already tried to install an alternative flash player plugin from the plugin list. How can I uninstall all flash player plugins and then start from scratch? Once I have done that, I should be able to use the "sudo apt-get install ubuntu-restricted-extras " command.


Thanks!

---

### Post by nabilalk on 2008-12-22
> **hyperdude111 said:**
> This is a solution for all codecs ; dvd, divx, mp4, flash, mp3.....
It is also really easy.

Go Application-Accessories-Terminal

Type without quotes " sudo apt-get install ubuntu-restricted-extras "

If you just want flash download the tar.gz from adobe, unpack it, close firefox, and run installflashplayer.sh (i am not sure on the name there should be two files try them both)

~hyper~

Ok, so I downloaded the archive. How can I install it from Terminal?

> Linux (x86)

Installation instructions for .deb

       1. Click the download link to begin installation. If a dialog box appears, follow the instructions to save the installer to your desktop.
       2. Save the .deb package to your desktop, and wait for it to download completely.
       3. Double-click on the .deb package and follow the instructions to complete installation.

          -or-
          Issue one of the following commands from the terminal:
              * dpkg --install [filename].deb
              * dpkg -i [filename].deb
       4. To verify the plugin is installed in Mozilla, launch Mozilla and choose Help > About Plug-ins from the browser menu.

Installation instructions for tar.gz

       1. Click the download link to begin installation. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage the file. A directory called install_flash_player_10_linux will be created.
       4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
       5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

---

### Post by nabilalk on 2008-12-22
> **BrandonBan6 said:**
> Hmm, I'm sorry, not to sure myself what is going on there. Perhaps try another browser to see if it is just firefox? Opera or Flock...I think they both have linux compatible browsers.

Opera worked. Still can't get this to work with Firefox. Thanks.

---

