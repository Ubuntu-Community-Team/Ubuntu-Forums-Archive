---
title: "Black Screen flashes on and off continuously: Cannot use ubuntu 9.10 after updates"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by server_3249 on 2009-09-15
Hi

I am a novice Ubuntu user (have been trying to learn it for the past 1 week).  I have Ubuntu 9.10 installed with some apps inside Wubi on a separate partition in Windows.   
I have also installed the xubuntu GUI inside Ubuntu.  

The problem stated immediately after last night's update of around 15 patches, I installed them and rebooted as recommended.  The xubuntu loading screen (progress bar) completes its work and then I get a black screen that flashes on and off continuously and forever.  I cannot get to the login screen.  I have the nvidia restricted drivers installed, but I didn't see any updates for that in what I installed.  IIRR there was some compiz stuff though.

I have tried booting in 'recovery' mode and repairing incomplete installations but there is nothing to repair.  

What should be the correct procedure to proceed with this?  I am a novice and I really don't want to format this and start over and make all those settings and download all that stuff again (I will probably be too lazy and go back to windows, which I don't want to do this time.)

system: Dell xps m1530, 4GB, nvidia 8600m gt.. etc.

---

### Post by juancarlospaco on 2009-09-15
Fix released already, wait for updates tomorrow...

:)

---

### Post by server_3249 on 2009-09-15
And how do i get to the desktop to install the update?

---

### Post by server_3249 on 2009-09-15
Can anyone else please help me with this?  Or can someone point me to the website where the bug is being tracked so I can follow it?

---

### Post by star3am on 2009-09-15
Bleek :( 

Why push updates if it's going to brake things like X .. ? I just don't understand, no matter how much I dig using open source, every time an update brakes my system, i just think, WTF ? 

Anyway .. for me to get into a working system, after all I have to work, and for that I need a browser, and so I need X .. I just did, mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Restarted my system and I was able to log in, albeit without direct 3d, using the nv driver.

---

### Post by alienclone on 2009-09-15
**** me

---

### Post by star3am on 2009-09-15
> **alienclone said:**
> if you are only 1 week new to Ubuntu i think maybe you should go with a more stable version than 9.10,  try 8.04, 8.10, or 9.04 first.

How would he even know the difference between these versions when he is such a new user ? Thing is, the updates broke my system too, no matter what you say, this should not happen. 

It's frustrating when updates brake things that was working just fine,

---

### Post by alienclone on 2009-09-15
**** me

---

### Post by star3am on 2009-09-15
I'm running 9.04 and the updates broke my system :\

---

### Post by alienclone on 2009-09-15
**** me

---

### Post by server_3249 on 2009-09-15
> **star3am said:**
> Bleek :( 

Why push updates if it's going to brake things like X .. ? I just don't understand, it's probably the thing that pisses me off the most* about open source, no matter how much I dig using open source, every time an update brakes my system, i just think, WTF ? 

Anyway .. for me to get into a working system, after all I have to work, and for that I need a browser, and so I need X .. I just did, mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Restarted my system and I was able to log in, albeit without direct 3d, using the nv driver.

Where do I enter this stuff?  Some sort of recovery mode?  Can anyone else help?  I am sure this update broke a lot of systems.

---

### Post by server_3249 on 2009-09-15
> **alienclone said:**
> if you are only 1 week new to Ubuntu i think maybe you should go with a more stable version than 9.10,  try 8.04, 8.10, or 9.04 first.

OK.  So that was your rant.  Now where is your contribution? (I presume you would have one?  Since you're a more advanced user?)

---

### Post by alienclone on 2009-09-15
**** me

---

