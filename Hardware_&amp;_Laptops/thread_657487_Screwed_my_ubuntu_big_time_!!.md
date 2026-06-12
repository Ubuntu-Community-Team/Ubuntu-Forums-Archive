---
title: "Screwed my ubuntu big time !!"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by tomtity123 on 2008-01-03
I was tring out a new graphics card (nvidia) and after installing it all on my ubuntu and running it for a while it stopped working ... 
Now ive gone back to my Ati X800 GTO and when i boot to Ubuntu all i get is a mass of horizontal lines on only the top part of the screen. 
I can get to recovery mode but am unsure how i can restore it back to the way it was..
HELP please 
and yes im a bit of a noob! :D

---

### Post by Yellow Pasque on 2008-01-03
Ok. While in the terminal, do:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial --overlay-type=Xv -f
```
Reboot and see if that works. If not, post your /etc/X11/xorg.conf

---

### Post by taurus on 2008-01-03
While in recovery mode, run this command to reconfigure X server again for your ATI card.

```
dpkg-reconfigure -phigh xserver-xorg
```
Now, you can reboot with

```
shutdown -r now
```

---

### Post by tomtity123 on 2008-01-03
hi guys
ive tried both of ur suggestions and neither have worked.
i tried to find my xorg.cong... but i have now dorectory called"etc/x11/"

and when i tried to do the reconfigure ....xserver.. it said xserver is not installed???

thanks for ur help guys! got any more ideas??:confused:
tom

---

### Post by taurus on 2008-01-03
It's /etc/X11.  It should be capital X since Unix/Linux is CaSe SenSiTive.

What was the _exact_ command that you typed in on the prompt?

---

### Post by tomtity123 on 2008-01-03
yep i went into etc and did 'ls' to see if i could see it atall but its not there :confused:

---

### Post by taurus on 2008-01-03
What is the output of this command then?

```
ls -la /etc/X11
```

---

### Post by tomtity123 on 2008-01-03
Ive found the X11/xorg.conf file now sorry was case sensitive and i was being a retard.
 going back to the > sudo apt-get install xorg-driver -fglrx

this is basically what i get :

after unpacking 7807KB of additional disk space will be used .
do you want to continue? i type Y
warning the following packages cannot be authenticated
xorg-driver-fglrx
install without verification? i type Y again
could not resolve 'gb.archive.ubuntu.com'
E:unableto fetch some archives

.......
im having to write everything down and then type it in here so thats y i can't really give you my xorg.conf file. sorry

---

### Post by taurus on 2008-01-03
Which release (Gutsy, Feisty, Edgy, etc.) are you using and can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by tomtity123 on 2008-01-07
Hi 
im using gusty,
im abit of a noob so not sure how i can post it on here when im in windows now???
sorry

---

### Post by PmDematagoda on 2008-01-07
Boot Ubuntu in Recovery Mode, then when you reach the terminal post the output of:-
```
cat /etc/lsb-release
```
and also the command given by taurus if that is possible.

---

