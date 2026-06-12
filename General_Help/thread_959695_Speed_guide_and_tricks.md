---
title: "Speed guide and tricks?"
date: 2008-10-26
forum: General Help
---

### Post by uid313 on 2008-10-26
I have a 900 MHz computer with 256 MB RAM.

What tips and tricks are there to speed it up?

This is for my sister, she is not good with computers. The most important thing is for her to have a web browser, so she can use Facebook. She also needs an IM client with MSN support. Preferably one that supports all the features of MSN and lets her see friends on webcam, send nudges, smileys and all that dumb stuff.

Someone should make a speed guide, and a compilation of tips and tricks for performance.

---

### Post by dracayr on 2008-10-26
The problem with this is that the answer is different for every system... you could deactivate the tracker search, and of course desktop effects, but the rest is different for each comp. check which process uses the most cpu, which the most mem...

but, honestly, if the System is only to be used for surfing, Speed isn't that important... the lag between clicking on a link and actually seeing the site only depends on the network connection and the server, after all.

dracayr

---

### Post by uid313 on 2008-10-26
> **dracayr said:**
> 
The problem with this is that the answer is different for every system... you could deactivate the tracker search, and of course desktop effects, but the rest is different for each comp. check which process uses the most cpu, which the most mem...
Thanks for the tip with Desktop Effects and Tracker.

> **dracayr said:**
> 
but, honestly, if the System is only to be used for surfing, Speed isn't that important... the lag between clicking on a link and actually seeing the site only depends on the network connection and the server, after all.
No, the web browser needs to start fast.
You need to be able to have more than one tab open.
It should be able to load stuff into cache, so it doesn't have to trash the disk with swap. The less memory I can run, the better.

---

### Post by uid313 on 2008-10-26
Maybe use some alternative window manager / desktop environment?

I guess I could disable some services...

**Services**
System -> Administration -> Services.
Disable bluetooth, apmd, avahi, apport, winbind.
Perhaps I could get away with disabling anacron, crond, atd.

**Sessions**
System -> Preferences -> Sessions.
Disable Bluetooth Manager, Evolution Alarm Notifier, Print Queue Applet, Remote Desktop, Tracker, Tracker Applet, Visual Assistance.

---

### Post by lswb on 2008-10-26
Another 256 MB of memory would be the most useful mod you can make.

---

### Post by jason.b.c on 2008-10-26
or dump ubuntu altogether and go with puppy linux...

[http://www.puppylinux.org/](http://www.puppylinux.org/)

[IMG]http://www.puppylinux.org/files/images/Picture1.png[/IMG]

---

### Post by oldos2er on 2008-10-26
> **uid313 said:**
> I have a 900 MHz computer with 256 MB RAM.

What tips and tricks are there to speed it up?
  

Put as much RAM in it as it can handle. Use a light-on-RAM distro.

---

### Post by uid313 on 2008-10-27
> **jason.b.c said:**
> or dump ubuntu altogether and go with puppy linux...

[http://www.puppylinux.org/](http://www.puppylinux.org/)
Yeah, maybe so.
But I want it to be user-friendly too.
I have never used Puppy Linux before.
Ubuntu I know is user-friendly, has a nice package manager, and is easy to keep up-to-date, and comes with Firefox, and easy to install Flash.

---

### Post by uid313 on 2008-10-27
I was able to trim down the memory usage to around 140 megabyte.

The problem seems to be performance.

---

### Post by cmapesjr on 2008-10-27
More memory. If it is constantly using swap the performance goes down.

---

### Post by uid313 on 2008-10-28
> **cmapesjr said:**
> More memory. If it is constantly using swap the performance goes down.
Yeah, more memory is nice.
But right now, it uses quite little memory, so it doesn't need to swap.
Yet, its still a bit slow.

There needs to be performance improvements.

---

### Post by EvilRobotDrew on 2008-10-28
try using xfce instead of gnome

sudo aptitude update && sudo aptitude install xubuntu-desktop 

(this command updates the system, then installs xcfe and it's dependancies, it will also probably change the splash-screen at boot, but that is easily put back to the way it was, i believe it is called the usplash theme)

when you login change the session to xfce. i didn't see much of an improvement on my laptop, but i have 2 gb of ram. xfce isn't quite as pretty as gnome, but you can still do everything you need. if you still prefer gnome you can set your sister's user to default to xfce while you still default to gnome.

the only other thing that may help is if you are using your swap space alot and you have an sd card reader on the computer you can use an SD card as a swap space and try to save some wear and tear on your HD.

---

### Post by Ub1476 on 2008-10-28
You can also use the Openbox window-manager in Gnome instead of Metacity. Install Openbox via repos and select it from the gdm session list. 

But the best thing would be to run Xubuntu 8.04.1 (or Intrepid, but it's still in RC).

XFCE is much lighter than Gnome, but has a few less features too. Probably nothing your sister would notice.. All gtk apps look good in it. 

For MSN, you could use Emesene, which is quite good I think. aMSN is also a good alternative, but you have to search Google for a guide to make it look better than its currently (horrible) interface. Probably more out there, but I myself only use Pidgin (mostly because it's simple).

Also, you could try Fluxbuntu, but that might be too "simple" for your sister. Install it in a virtualbox if you wish..

---

### Post by snowpine on 2008-10-28
Crunchbang is a nice distro for a 256mb of ram computer and a user who likes to do a lot of web surfing, chat, webcam, youtube, etc. It's got all the codecs already installed plus some very useful applications.

More ram would help the speed a lot by reducing swappiness.

---

### Post by aktiwers on 2008-10-28
Or try Xubuntu.. its fast too.


If you already installed Ubuntu, you can install it by typing:
```
sudo apt-get install xubuntu-desktop
```In terminal.

Then Logout..  pick XFCE Session and log back in.

Else download the Xubuntu iso

---

### Post by saberz on 2008-10-28
Well after much searching I did find this gentlemen's post on his own website. Followed the instructions and noticed a very nice boost. For a low ram system you could re-profile the system and possibly tune the Swappiness settings. Below is the link to the guys site:

[http://www.sysadminsjourney.com/2008/08/31/quick-painless-ubuntu-speed-tweaks/](http://www.sysadminsjourney.com/2008/08/31/quick-painless-ubuntu-speed-tweaks/)

---

### Post by uid313 on 2008-10-29
I think the developers needs to speed up GTK+, GLib, glibc, Metacity, gnome-panel.

---

### Post by oldos2er on 2008-10-29
There are distros that are optimized for older low-end systems, e.g. DSL, Puppy, Vector Linux, etc.

---

### Post by snowpine on 2008-10-29
> **uid313 said:**
> I think the developers needs to speed up GTK+, GLib, glibc, Metacity, gnome-panel.

You can say "the developers need to do this, the developers need to do that" (and by the way, there are places such as launchpad where you can communicate with them), or you can take matters into your own hands and try some of the tricks and tips you've learned from this thread (add more ram, disable unneeded services, try a speedier distro, etc).

Linux (in my opinion) is all about giving you the toolbox to build your own ideal system. :)

---

