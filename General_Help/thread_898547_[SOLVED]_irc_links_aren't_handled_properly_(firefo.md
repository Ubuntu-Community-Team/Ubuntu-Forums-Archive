---
title: "[SOLVED] irc:// links aren't handled properly (firefox, xchat)"
date: 2008-08-23
forum: General Help
---

### Post by sexyclient on 2008-08-23
Is there a way to make xchat handle irc links (for example irc://irc.server.domain/channel) that come from firefox properly?  As I'm configured right now - the default configuration for Hardy Heron- irc links from firefox only opens a new instance of xchat and ignores the server and channel from the links.

In my common usage of the internets, I often find myself using links from websites to connect to various irc channels on various irc servers and this lack of convenience is quite frustrating.

I'd like irc:// links to be open xchat (only if it isn't already running) and connect to the server in the link (only if I'm not already connected to that server) and open the channel from the link in a new tab.  Is this possible?

---

### Post by Alaric on 2008-08-23
Do you have any options in [Menu]->Edit->Preferences->[Tab]Applications?  If not, try running 'sudo aptitude install firefox-gnome-support'.  Or, using synaptic to install that package.  Firefox should then give you the option of adding xchat as a default program for irc:// links, instead of just complaing about being confused :).  Good Luck!

---

### Post by sexyclient on 2008-08-23
I have an option there, irc is set to be handled by xchat, but all it does is open xchat (whether or not its already running) and ignores the server and channel in the link.  That's the problem.

---

### Post by Alaric on 2008-08-23
Hmm... I don't believe that I have this problem...  I'm getting the exact behavior that you're looking for with my browser version 3.0.1, XChat version 2.8.4, and firefox-gnome-support version 3.0.1+build1+nobinonly-0ubuntu0.8.04.3.  Try updating your system to the latest versions using synaptic.

Also, make sure that you're not running a version that was compiled from source code (usually .tar.gz or .tar.bz2 file extensions when you download them).  These can often be  out of date.  If you are, try uninstalling the program and reinstalling with synaptic.

---

### Post by sexyclient on 2008-08-24
I have those three installed and with the same versions.  I also didn't compile from source, rather I updated from synaptic (right after I installed hardy 8.04 from the liveCD).  I can't figure out why mines is broken.

---

### Post by Alaric on 2008-08-24
Try 'sudo apt-get update && sudo aptitude reinstall xchat firefox-gnome-support'?

---

### Post by sexyclient on 2008-08-24
OK, I've managed to get this working and I'm not really sure how, but I may have some clues.  

After hardys initial install, there's a version of xchat preinstalled but for various reasons I had installed the updated standard version of xchat (2.8.4).  Because ubuntu still pointed to the "old" xchat as the default irc handler, I went into firefox and manually selected the "new" version of xchat to use as the default.

I'm not sure why, but when I switched the programs that firefox used to handle irc from the "new" xchat that I manually selected to the default "xchat", somehow the default xchat became the new version instead of the old one and it works just the way it should so:  PROBLEM SOLVED - though I'm not 100% sure how...

Thanks for all the help guys. *Edit: Rather, thanks Alaric, hehe.*

---

### Post by Alaric on 2008-08-24
No problem!  Always willing to help a sexy damsel in distress ;)  Enjoy :)

---

### Post by sexyclient on 2008-08-24
Eh, I don't know what to say...  But I'll start with: I'm a guy.

---

### Post by Alaric on 2008-08-24
Lol, good thing I wasn't hitting on you then, I've already got a (female) girlfriend.

---

