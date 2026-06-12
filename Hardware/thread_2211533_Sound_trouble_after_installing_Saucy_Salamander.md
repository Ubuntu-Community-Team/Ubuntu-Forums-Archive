---
title: "Sound trouble after installing Saucy Salamander"
date: 2014-03-16
forum: Hardware
---

### Post by emma5 on 2014-03-16
After (fresh) installing Saucy Salamander on my Fujitsu Siemens Amilo La1703 the built-in speakers haven't been making a sound, I got the sounds working through my loudspeakers which now I suspect have broken down because the sounds simply vanished and the loudspeakers didn't work on another computer either. Well, in an attempt to revive the built-in speakers I did something stupid, I tried to apply the instructions from this (closed) thread: 

[http://ubuntuforums.org/showthread.php?t=2074897](http://ubuntuforums.org/showthread.php?t=2074897)

"
For me I get no sound when installing 12.04 or 12.10 until I switch the sound cards:
 	Code:
 	sudo su
cd /usr/share/alsa 
cp -p alsa.conf alsa.conf.dist 
sed -i 's/card 0/card 1/g' alsa.conf 
Just paste that into the terminal and run the whole thing, of course after hitting enter enter your password.
"

I followed the instruction above, 
Actually I'm not even sure if I did it right because the first line was somehow repeated (?) (I'm such a newbie) :

emma@***:~$ sudo su
[sudo] password for emma: 
Sorry, try again.
[sudo] password for emma: 
root@***:/home/emma# sudo su
root@***:/home/emma# cd /usr/share/alsa 
root@***:/usr/share/alsa# cp -p alsa.conf alsa.conf.dist 
root@***:/usr/share/alsa# sed -i 's/card 0/card 1/g' alsa.conf
root@***:/usr/share/alsa# 

and I guess that was what made my access to alsamixer disappear. When I write alsamixer in terminal, I get a "cannot open mixer: No such file or directory" response.
I went on to try and install alsamixer anew, 

sudo apt-get install Alsamixer

but was greeted with this answer:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package Alsamixer

Another thing that I managed to do by committing the above mentioned was that the devices for sound output disappeared from the Sound Settings Output view (accessible from the sound icon at the right in the upper panel).

In terminal (lspci | grep -i audio), I checked my sound device to be

04:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)

How to reverse the damage done and to get my built-in speakers working?

Any help greatly appreciated, thank you!

E

---

### Post by Yellow Pasque on 2014-03-16
Run this to restore original file:
```
cd  /usr/share/alsa 
sudo rm alsa.conf
sudo mv alsa.conf.dist alsa.conf
sudo alsa force-reload
```

After that, get alsa info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

