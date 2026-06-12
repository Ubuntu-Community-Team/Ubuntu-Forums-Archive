---
title: "[SOLVED] Problem reinstalling flashplugin-nonfree"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by thk123 on 2009-01-04
Running Ubuntu 8.04 on a dell mini architecture:IPIA

Earlier today I tried to upgrade to Flash 10, and during this quest, I was told to uninstall flashplugin-nonfree. I saw no problem with this, as I could simply reinstall it through the Synaptic Package Manager. However, having failed to install flash 10 (wrong architecture, using Dell Mini with  Ipia architecture) I thought I would revert back to flashplugin-nonfree. 

However, when I did this through Synaptic Package Manager it did not work. It installed no problems, however, when I launched Firefox, not only did it not work, but firefox does not even recognize there is a flash player installed (I did about:plugins and Tools>Addons) 

I do not know what to do or how to solve this problem, any help would be much appreciated.

Thanks,

---

### Post by jrusso2 on 2009-01-04
Make sure there are no parts of flash 10 left in your plugins directory.

---

### Post by Moop on 2009-01-04
Flash is usually installed to /usr/lib/mozilla/plugins. The file is named libflashplayer.so

You can also download the correct version from adobe and extract the libflashplayer.so file. Then open your home directory and ctrl-h to view hidden files. Open the .mozilla folder and create a folder named plugins. Drop the libflashplayer file in the plugins folder.

---

### Post by thk123 on 2009-01-04
> **Moop said:**
> Flash is usually installed to /usr/lib/mozilla/plugins. The file is named libflashplayer.so

You can also download the correct version from adobe and extract the libflashplayer.so file. Then open your home directory and ctrl-h to view hidden files. Open the .mozilla folder and create a folder named plugins. Drop the libflashplayer file in the plugins folder.

Removed all references Flash 10. I did a search on my disk for libflashplayer.so and found two things. One was from the tar.gz file from Flash 10 still saved on my desktop (that shouldn't effect anything should it?) and the other was called: npwrapper.libflashplayer.so. Is that the file? If so, which of those two folders do I need to put it in? Home/.mozzila/plugins (which currently contains npica.so or usr/lib/firefox-3.03/plugins which currently contains nppdf.so (I don't think I can paste in to this) 

The npwrapper.libflashplayer.so file currently resides in /usr/lib/xulrunner-addons/plugins

---

### Post by Moop on 2009-01-04
It would work in either place but putting it in  /home is just easier. The libflash player file sounds like the right one but I'm not sure. It won't hurt anything to copy it into the mozilla plugins folder in /home. If it doesn't work just delete it.

I think those other files are for a adobe pdf reader plugin. 

I'm not sure about your architecture. You should go ask in the Dell part of Ubuntu forums if you can't find the solution.

---

### Post by thk123 on 2009-01-06
OK found the solution (lost the link, but printed it off) Basically, I decided to install Flash 10. After getting past the LPIA problem (using a command dpkg --force-architecture nameOfDeb.deb) and doing a complete removal (through Synaptic Package Manager) of flashplugin-nonfree I did this. I had these files at the end of the previous steps, so if you don't, I'm sorry but this probably won't help.

In the Terminal, run these commands. Basically, they create links so that Firefox can find them  

```

sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libnplds4.so
sudo ln -s /usr/lib/libnplc4.so.0d /usr/lib/libplc4.so

```

---

