---
title: "Seamonkey upgrade"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by anafshalom on 2009-03-16
The Seamonkey website says that there is a new version.  How can I upgrade?
Reuven

---

### Post by Partyboi2 on 2009-03-16
To install the latest stable version ( seamonkey-1.1.14) from the website you downloaded it then open a terminal (Applications>Accessories>Terminal) and change directory to where the downloaded file is eg. if its located on your Desktop
```
cd ~/Desktop
```then extract it
```
tar xvzf seamonkey-1.1.14.en-US.linux-i686.installer.tar.gz 
```then change into the newly created source directory
```
 cd seamonkey-installer
``` then
start the install
```
./seamonkey-installer-bin 
```

---

### Post by premamotion on 2010-01-11
What about SeaMonkey 2.0.1? Does not have a directory like
seamonkey-installer

---

### Post by nanotube on 2010-01-11
you can use the ubuntuzilla repository to install seamonkey:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by erniej on 2010-01-14
I'm having the same problem trying to install 2.0 upgrade.

Following the instructions on that site, I copied and pasted the line

deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

prefaced by sudo. I got the following message:

sudo: deb: command not found

Where do I go from here?

---

### Post by erniej on 2010-01-14
Sorry, it pasted the url rather than the command. It's the one that begins deb: and ends in all main.

---

### Post by nanotube on 2010-01-14
> **erniej said:**
> I'm having the same problem trying to install 2.0 upgrade.

Following the instructions on that site, I copied and pasted the line

deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

prefaced by sudo. I got the following message:

sudo: deb: command not found

Where do I go from here?

please follow instructions on the ubuntuzilla website more carefully.

either add the line starting with 'deb' into your sources.list, using a text editor,  or use the command given (the one with 'echo' in it) which will automatically append that line to your sources.list. 

the actual sources.list line, (the one that starts with 'deb') is /not/ a terminal command, so you can't execute it in a terminal.

---

### Post by erniej on 2010-01-14
Thanks, nano. I'm afraid I've been spoiled by 20 years of Windows one-click installs. I've been trying to install SeaMonkey 2 for the better part of the day and still no luck. I'll read the instructions more carefully, although, since I'm a guy, I've always considered instructions to be a last resort. :-)

---

### Post by nanotube on 2010-01-14
> **erniej said:**
> Thanks, nano. I'm afraid I've been spoiled by 20 years of Windows one-click installs. I've been trying to install SeaMonkey 2 for the better part of the day and still no luck. I'll read the instructions more carefully, although, since I'm a guy, I've always considered instructions to be a last resort. :-)

heh well have fun - and let me know if you run into any further problems.

---

### Post by gradinaruvasile on 2010-01-14
Just go to their site-there is a linux archive - just unpack wherever you want and run it from there. That version also supports in-browser upgrades just like on Windows.

---

### Post by nanotube on 2010-01-14
> **gradinaruvasile said:**
> Just go to their site-there is a linux archive - just unpack wherever you want and run it from there. That version also supports in-browser upgrades just like on Windows.

nothing wrong with that either... 

but with the repository you don't have to manually create the menu item, the symlink in /usr/bin, and you get updates through the standard update manager.

---

### Post by erniej on 2010-01-15
It worked perfectly. Many thanks. I guess the old saying RTFM! still applies.

---

### Post by nanotube on 2010-01-16
> **erniej said:**
> It worked perfectly. Many thanks. I guess the old saying RTFM! still applies.

cool!

indeed, there's nothing quite like some rtfm to get one through the day :)

---

