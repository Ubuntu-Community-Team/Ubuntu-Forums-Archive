---
title: "[SOLVED] Major failure in Software Management System"
date: 2008-09-01
forum: General Help
---

### Post by ragflan on 2008-09-01
**Crap! How come the title came out as '!'. I put the title: Major failure in Software Management System. Sorry!**

But here's the problem: I'm under Hardy Heron. I just installed KDE using sudo apt-get install kubuntu-desktop. And then I changed the session and tried KDE. I didn't like KDE, and I preferred GNOME so I removed KDE using sudo apt-get remove kubuntu-desktop. But that just removed 140kb of something. But all the KDE applications were not removed. So I removed them one by one like Kaffeine, KompoSer, Konversation, Kopete, Adept-Manager, etc. 

But I tried to open Add/Remove Programs ... and I got this error: 

[IMG]http://ramipage.googlepages.com/Screenshot-gnome-app-install.png[/IMG]

Then I used Synaptic and clicked **'Mark all Upgrades'** followed by 'Apply' and it gave me an error: **E: kio-umountwrapper: subprocess post-removal script returned error exit status 2**

I ran a sudo apt-get update and I tried removing kio-umountwrapper which is what Synaptic tried to do, but I got this error: 

[IMG]http://ramipage.googlepages.com/Screenshot-ragflanragflan-laptop~.png[/IMG]

I'd appreciate any help. Thanks!

---

### Post by ragflan on 2008-09-01
Sorry about the title.

---

### Post by p_quarles on 2008-09-01
Fixed it for you. :)

The single character made it hard to click on the thread, so I thought I should make it easier for people.

---

### Post by ragflan on 2008-09-01
> **p_quarles said:**
> Fixed it for you. :)

The single character made it hard to click on the thread, so I thought I should make it easier for people.

Thank you! Anyone know whats wrong with my system?

---

### Post by plucky on 2008-09-01
> **ragflan said:**
> Thank you! Anyone know whats wrong with my system?

See this thread [http://ubuntuforums.org/showthread.php?t=899674&highlight=kio-umountwrapper](http://ubuntuforums.org/showthread.php?t=899674&highlight=kio-umountwrapper)


Good Luck

---

### Post by ragflan on 2008-09-01
Thank you, plucky! That thread solved my problem.

---

