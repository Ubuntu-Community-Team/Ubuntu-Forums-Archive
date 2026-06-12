---
title: "How to fix flash plugin problem"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Lachinchon on 2009-04-25
This is not my recipe, but I could not find the thread and poster I got it from -- whoever you are, thanks.  Anyway, if you are having problems with the flash plugin for firefox failing (nice alliteration, eh?), this seems to fix the problem:

THIS TO CLEAN UP OLD STUFF:
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

THEN GET DEB PACKAGE FROM ADOBE AT: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

THIS SHOULD DOWNLOAD TO THE DESKTOP.  JUST DOUBLE CLICK THE DEB PACKAGE TO INSTALL

I can now listen to my tunes on Lala.com. Fixes Youtube video problems, too.  ...and remember: there are some things it is impossible to know, but it is impossible to know these things.

---

### Post by mooz123 on 2009-04-27
This works, thank you for this post.

I upgraded to 9.04, and had to reinstall the restricted extras. I clicked on the 'wrong' flash plugin, and from then on many websites where not functioning. 

The only thing this sequence of commands did at my computer was to remove swfdec-mozilla, I already had the adobe plugin installed. I found it difficult to figure out what code is executed when a .swf file pops up at a site, and help like this is like shooting in the dark. Where does it say that swfdec is used, not in the plugin list?

Commands starting with rm I always study suspiciosly, but these are harmless. It solves the problem too.

---

### Post by axlotxlikexvegas on 2009-04-27
I had the same problem after a clean install of Ibex. This worked perfect, thanks.

---

### Post by timstone on 2009-04-27
very nice, fixed my FF flash problem...now i need to fix my Opera flash problem...it was doing the same thing :(

---

### Post by zippy_uk_2001 on 2009-04-27
THanks for that - worked a charm!

---

### Post by caveman59330 on 2009-04-28
I still didn't get that to work.That version of Adobe works if you have the 32 bit version but I am running the x64 bit and it wont install says wrong **architecture.Still I have no sound and I am about to give up I have been researching it all night.This really sucks I might go back to a older version that works.My Jaunty experience has been frustrating I really had high hopes and I feel let down. **

---

### Post by gatorbrit on 2009-04-28
> **caveman59330 said:**
> I still didn't get that to work.That version of Adobe works if you have the 32 bit version but I am running the x64 bit and it wont install says wrong **architecture.Still I have no sound and I am about to give up I have been researching it all night.This really sucks I might go back to a older version that works.My Jaunty experience has been frustrating I really had high hopes and I feel let down. **

I am running 64 bit also.  I followed the instructions above, and then went to synaptic and installed flash plugin nonfree.   It seems to be working fine now...

---

### Post by KILLUMINATI on 2009-04-28
IT WORKED!!!  I am running a thinkpad X60 and as soon as I upgraded from 8.10 to 9.04 i experienced sound and video issues with regards to flash.  thanks for the fix.

---

### Post by bhishan on 2009-05-01
> **Lachinchon said:**
> This is not my recipe, but I could not find the thread and poster I got it from -- whoever you are, thanks.  Anyway, if you are having problems with the flash plugin for firefox failing (nice alliteration, eh?), this seems to fix the problem:

THIS TO CLEAN UP OLD STUFF:
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

THEN GET DEB PACKAGE FROM ADOBE AT: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

THIS SHOULD DOWNLOAD TO THE DESKTOP.  JUST DOUBLE CLICK THE DEB PACKAGE TO INSTALL

I can now listen to my tunes on Lala.com. Fixes Youtube video problems, too.  ...and remember: there are some things it is impossible to know, but it is impossible to know these things.

Thanks man. I really needed this.

---

### Post by Dark Samurai on 2009-05-08
Thank you so very much!
Fixed it perfectly ;)

---

### Post by hman1169 on 2009-05-12
I wrestled with it for a while, uninstalled - reinstalled, added on, removed, got the video to work, and the only way to get the audio to work was to kill PulseAudio... But now, Thanks to you [Lachinchon]("http://ubuntuforums.org/member.php?u=656375") it is all up and running!

Your clean up worked and everything is humming along like it should... Hulu now plays video and audio!

Thank you!

---

### Post by LinuxBob on 2009-08-30
This has not worked for me  with 9.04 and firefox 3.0.13

I did the terminal commands and installed Adobe latest flash 32 bit deb, no change


Rythmbox provides sound but nothing on firefox.  HELP???!???

---

### Post by cliff01 on 2009-08-31
Another big "Thank You"

---

### Post by Mudbutt on 2009-08-31
I got same problem as you LinuxBob.. 

someone please help?

---

### Post by kbtarl on 2009-11-14
I did the clean up and when I launch a flash movie the circle spins around a couple of times then stops........screen turns grey and only way out is to kill firefox.

Any help?

---

### Post by tbone7 on 2009-11-14
> **caveman59330 said:**
> I still didn't get that to work.That version of Adobe works if you have the 32 bit version but I am running the x64 bit and it wont install says wrong **architecture.Still I have no sound and I am about to give up I have been researching it all night.This really sucks I might go back to a older version that works.My Jaunty experience has been frustrating I really had high hopes and I feel let down. **

I would advice 64-bit users to install Adobe's alpha version of the flash plug-in for 64-bit systems:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Extract the .so file and put it in /usr/lib/mozilla/plugins/

Remember to remove any previous versions of flash.

---

### Post by presence1960 on 2009-11-14
> **tbone7 said:**
> I would advice 64-bit users to install Adobe's alpha version of the flash plug-in for 64-bit systems:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Extract the .so file and put it in /usr/lib/mozilla/plugins/

Remember to remove any previous versions of flash.

another 64 bit Flash solution from our 64 bit users section of the forum- [http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

---

### Post by Lofnes on 2009-11-20
> **Lachinchon said:**
> This is not my recipe, but I could not find the thread and poster I got it from -- whoever you are, thanks. Anyway, if you are having problems with the flash plugin for firefox failing (nice alliteration, eh?), this seems to fix the problem:
 
THIS TO CLEAN UP OLD STUFF:
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
 
THEN GET DEB PACKAGE FROM ADOBE AT: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
 
THIS SHOULD DOWNLOAD TO THE DESKTOP. JUST DOUBLE CLICK THE DEB PACKAGE TO INSTALL
 
I can now listen to my tunes on Lala.com. Fixes Youtube video problems, too. ...and remember: there are some things it is impossible to know, but it is impossible to know these things.
  
 
I have had ubuntu for only a few weeks and know nothing. Could someone explain what the above instructions mean because it sounds like just what I need:KS

---

### Post by goldsniper on 2010-02-19
You could install latest plugins manually.

Just download the plugins at Adobe and put it in firefox plugins folder.

Instructions is in my blog.

---

