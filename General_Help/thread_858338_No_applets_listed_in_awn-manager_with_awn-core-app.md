---
title: "No applets listed in awn-manager with awn-core-applets-bzr installed"
date: 2008-07-13
forum: General Help
---

### Post by Ruazinn on 2008-07-13
Even though I have the following list installed on Ubuntu Hardy, my available applets list in awn-manager only shows the Launcher/TaskManager applet.  

The list of installed items:

awn-core-applets-bzr
awn-manager-bzr
libawn0-bzr
python-awn-bzr

I did a distribution upgrade from Gutsy to Hardy a week ago.  At first, I experienced the white lines that happen when your awn applets crash.  I ended up uninstalling the awn items, compiz, and emerald, then reinstalling to remove the lines.  Awn now works, but I don't have any applets to choose from.  Here's a link to stuff I posted about the white-line issue last week: [http://ubuntuforums.org/showthread.php?t=853735](http://ubuntuforums.org/showthread.php?t=853735)

I'd very much appreciate any info on how to get the applets back.  Probably just a silly configuration file issue.

---

### Post by DJ_Peng on 2008-07-13
It's actually a known issue. reacocard, the person who maintains the PPA packages, said he [needed to rebuild awn-core-applets]("http://ubuntuforums.org/showthread.php?p=5372490#post5372490"), but I'm showing them as fixed as I had the missing applet issue this am and was able to fix it before noon ET.

Btw, the thread I linked to is where most of the discussion on any day to day issues that come up is held. You may want to subscribe to it so you can know when things like this happen. I had issues two out of the last three or so mornings, but each time the info I needed was in my email when I got the latest daily email of posts from the theme. Many days I don't care about the posts in that topic that much, but I can always delete the daily emails that don't concern me.

---

### Post by Tim Sharitt on 2008-07-13
> 
The list of installed items:

awn-core-applets-bzr
awn-manager-bzr
libawn0-bzr
python-awn-bzr



Is avant-window-navigator installed or is avant-window-navigator-bzr installed? I believe avant-window-navigator-bzr is required to use these applets. Atleast thats what worked for me.

---

### Post by Ruazinn on 2008-07-13
Geez, I didn't even know you could subscribe to threads.  Learning that is more helpful than getting the applets!  Thanks.

---

### Post by Ruazinn on 2008-07-13
avant-window-navigator-bzr is what I have installed.

---

### Post by Tim Sharitt on 2008-07-13
Have you tried installing all the -bzr apps today? Apparently there was a problem with the version in the repos in the last couple of days. See: [http://ubuntuforums.org/showthread.php?t=854331]("http://ubuntuforums.org/showthread.php?t=854331")

---

### Post by Ruazinn on 2008-07-13
I just uninstalled and reinstalled everything after updating the repositories.  No change.

---

### Post by DJ_Peng on 2008-07-15
I had some issues with red X's yesterday but I got an update about 15 minutes ago from the PPA that I originally linked to and everything is right on my system. No red X's and a proverbial boatload of applets to choose from.

---

### Post by Ruazinn on 2008-07-17
Problem with the missing applets solved!  I had an old version of awn still cluttering my system and after the dist upgrade, I couldn't uninstall it from Synaptic.  So I manually deleted everything with these commands posted by reacocard:

sudo rm -f /usr/local/bin/awn*
sudo rm -f /usr/local/bin/avant*
sudo rm -rf /usr/local/lib/awn
sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
sudo rm -f /usr/local/share/applications/avant*
sudo rm -f /usr/local/share/applications/awn*
sudo rm -rf /usr/local/share/avant-window-navigator
sudo rm -f /usr/local/lib/libawn*
sudo rm -rf /usr/local/include/libawn
sudo rm -f /usr/local/lib/libawn*
sudo rm -f /usr/local/lib/pkgconfig/awn.pc
sudo rm -rf /usr/local/share/awn-core-applets
sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/

Now I'm a happy awn user again.

---

