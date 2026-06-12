---
title: "Installed Ubu 11 on Dell Inspiron 1721 - desktop doesn't show"
date: 2011-06-15
forum: Hardware
---

### Post by smokinfish on 2011-06-15
nstalled Ubu 11 on my sister's Dell Inspiron 1721 (after destriping the hdds into two seperate hdds of 160 gb each, don't think this is the issue, i previously installed windows xp on on of them and it was fine, if a little sluggish.)

 

After install, smoke test and it fires up right to the point of drawing the background and telling me wifi networks are available - close but no cigar -

 

The desktop icons/startbar/anythingatall don't appear. Just the mouse cursor.

 

After some initial poking around the net, tried "ctrl alt f1 > startx" and got the following:

 

xauth: file /home/naya/ .Xauthority does not exist

Fatal server error:

Server is already active for display 0

If this server is no longer running, remove /tmp/.X0-lock and start again

 

Please consult the X.Org Foundation Support (I assumed that was here?)

ddxSigGiveUp: Closing log

XIO: fatal IO error 11 (Resource temporarily unavailable on X server ":0" afer 7 requests (7 known processed) with 0 events remaining

 

>

 

Any ideas?

I just wanna get it running to show her Ubu is better than Windows...!

Best

SmokinFish

---

### Post by StrayEddy on 2011-06-15
Try:

etc/init.d/gdm start

---

### Post by smokinfish on 2011-06-15
Thanks Eddy, but:

-bash etc/init.d/gdm no such file or directory

..?

---

### Post by StrayEddy on 2011-06-15
Try:

sudo aptitude install ubuntu-desktop

Then post result of:

whereis gdm

---

### Post by smokinfish on 2011-06-15
sudo: aptitude command not found

---

### Post by StrayEddy on 2011-06-15
k....

Something bad must have happened during installation.

Try instead:

sudo **apt-get** install ubuntu-desktop

If it doesn't find the command **apt-get** this time:

I d suggest to get a new ubuntu live-cd [here]("http://www.ubuntu.com/download") and reinstall it.

---

### Post by smokinfish on 2011-06-15
OK, 

it is already latest version

whereis gdm

gdm: /usr/sbin/gdm /etc/gdm /usr/lib/gdm /usr/share/gdm

>

---

### Post by StrayEddy on 2011-06-15
Do:

sudo apt-get install gdm

Then try again etc/init.d/gdm start

---

### Post by smokinfish on 2011-06-15
Ok it upgraded gdm

then 

-bash: /etc/init.d/gdm no such file or directory

---

### Post by smokinfish on 2011-06-15
sorry i meant 
-bash: etc/init.d/gdm no such file or directory

---

### Post by StrayEddy on 2011-06-15
Sorry i m out of ideas here, you should try reinstalling it with your liveCD, maybe something went wrong during the installation before.

---

### Post by smokinfish on 2011-06-15
Thanks for your help man

I'm gonna try the alternate cd

Is 11 stable or should I go back to 10?

---

### Post by StrayEddy on 2011-06-15
The current LTS is 10.04. If you still have problems with 11.04, you could try it, works great !

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

