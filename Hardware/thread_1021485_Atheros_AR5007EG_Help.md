---
title: "Atheros AR5007EG Help"
date: 2008-12-25
forum: Hardware
---

### Post by JJMAC383 on 2008-12-25
Okay i'm new to ubuntu, i wanted to use kubuntu because I was told it was the most like windows and i'm trying to use it frequently.  However my wireless laptop card (an Atheros AR5007EG) won't work.  I really really want to learn linux environments but i can't use it very often if the internet doesn't work at my desk.  Please someone explain to me (a new user as in first time touching linux) how to fix this

---

### Post by ugm6hr on 2008-12-25
Which version of Kubuntu are you using?

If 8.10, then the ath5k driver should work:
[http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)

---

### Post by Jiffyman on 2008-12-25
As far as I know the card isn't supported yet, but I could be wrong. You may be able to use a windows driver with ndis (ndis uses windows drivers for devices under linux.) I'm not sure on how to install windows drivers in Kubuntu or Ubuntu for that matter. 

Here is a link to the windows drivers 

[http://madwifi-project.org/wiki/Compatibility/Atheros](http://madwifi-project.org/wiki/Compatibility/Atheros)

this will help get you started. Someone else who is more skilled will add on. Got to go. Merry Christmas!

(someone beat me to the punch)

---

### Post by JJMAC383 on 2008-12-26
so please remember i am very new to this. I believe i'm running 8.10, but how do i install the driver in kubuntu?

---

### Post by ugm6hr on 2008-12-26
Unfortunately, I haven't used Kubuntu.  But is should be the same as Ubuntu.

Try searching for "linux-backports-modules-intrepid-generic" package on the CD, and double-click it.  If it isn't there, you could download it from:
[64-bit]("http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-intrepid-generic/download")
[32-bit]("http://packages.ubuntu.com/intrepid-updates/i386/linux-backports-modules-intrepid-generic/download")
And double-click.

If Kubuntu is similar to Ubuntu, it should just install it directly.

---

### Post by Jiffyman on 2008-12-26
Use the Synaptic Package Manager, it is located in System>Administration>Synaptic Package Manager 
from there search "linux-backports-modules-intrepid-generic" without the quotes of course.

After that I'm not quite sure which package to select and I don't want you choosing the wrong one for no reason. However if I did have to choose one I would choose the one with the description of "Generic Linux Backported drivers." Hopefully someone else can clarify this.

---

### Post by ugm6hr on 2008-12-26
> **Jiffyman said:**
> Use the Synaptic Package Manager

I believe Kubuntu uses adept rather than Synaptic.  But similar idea.

It should work without adding the backports repository, since it is now in "updates"

In fact - just clicking [here]("apt:linux-backports-modules-intrepid-generic") might install it for you.

---

### Post by JJMAC383 on 2008-12-26
okay clicking that link didn't work.  I got an error saying that the "Protocol not supported
apt"

---

### Post by ugm6hr on 2008-12-27
> **JJMAC383 said:**
> okay clicking that link didn't work.  I got an error saying that the "Protocol not supported
apt"

Obviously, Kubuntu doesn't have apturl.  Just install the package some other way (lots of options above - another below).

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

---

### Post by JJMAC383 on 2008-12-29
i hate to ask even more questions... but i just open up the terminal and type in that code?

---

### Post by Rohan Kapoor on 2008-12-29
That is correct. It will then ask for your password. Type it in, it will appear blank and press enter. It will then go and install it!

---

### Post by Jiffyman on 2008-12-29
Or you can just copy and paste them into the terminal. I usually type in what I read so I can learn the commands

Also remember that when you type your password in you won't see any characters.

---

