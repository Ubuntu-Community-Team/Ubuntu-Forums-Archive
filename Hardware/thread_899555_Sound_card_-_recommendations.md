---
title: "Sound card - recommendations"
date: 2008-08-24
forum: Hardware
---

### Post by Gabt on 2008-08-24
Hey,

Ive been trying to install enemy territory and teamspeak on my system, with no luck in getting them both to run, at the same time, with sound.

Tried every how-to and tut i can find, wont work, ive read that sometime its easier to just get a new card, wich, might not be a bad idea, since currently i use onboard sound. 

So...my question is, if i bought a new cound card, would it then maybe easier to get these apps to work together? is it worth spending money on hardware?

and secondly, if the answer to the above is yes, wich cards are known to "just work" ubuntu 8.04 x86_64.

Cheeeeers.

---

### Post by markbuntu on 2008-08-24
Well, getting those to work together and play through your speakers is more likely a setup problem with the pulseaudio padevchooser which configures your newtwork sinks and sources and pavucontrol which sets your computers sinks and sources than a sound card issue. 

It would be better to figure that out now  rather than confuse the issue even further by adding another sound card.

---

### Post by Nepherte on 2008-08-24
To fix pulseaudio: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
Specific enemy territory/pulseaudio problem: [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup) (at the very bottom)

---

### Post by Gabt on 2008-08-24
After trying those: i get this output from terminal now:

```
------- sound initialization -------
Sorry but your soundcard can't do this
------------------------------------

```

So my question still sticks, any sound card recommendations?

---

### Post by Yellow Pasque on 2008-08-24
Before spending money, see if your game will work with OSS4 instead of ALSA/P.A.

See the link in my sig and I'd recommend following step 6a and building OSS4.1 beta from source instead of installing the .deb as OSS 4.0 is getting long in the tooth.

---

### Post by Yellow Pasque on 2008-08-24
Actually, after examining further, I'm wondering if you have the following installed:
```
sudo apt-get install libsdl1.2debian libsdl1.2debian-pulseaudio
```

---

### Post by Gabt on 2008-08-25
```
kev@kev-desktop:~$ sudo apt-get install libsdl1.2debian libsdl1.2debian-pulseaudio
[sudo] password for kev: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsdl1.2debian is already the newest version.
The following packages will be REMOVED
  libsdl1.2debian-alsa
The following NEW packages will be installed
  libsdl1.2debian-pulseaudio
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 203kB of archives.
After this operation, 4096B disk space will be freed.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com hardy/universe libsdl1.2debian-pulseaudio 1.2.13-1ubuntu1 [203kB]
Fetched 203kB in 0s (587kB/s)                  
dpkg: libsdl1.2debian-alsa: dependency problems, but removing anyway as you request:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-1ubuntu1) | libsdl1.2debian-all (= 1.2.13-1ubuntu1) | libsdl1.2debian-esd (= 1.2.13-1ubuntu1) | libsdl1.2debian-arts (= 1.2.13-1ubuntu1) | libsdl1.2debian-oss (= 1.2.13-1ubuntu1) | libsdl1.2debian-nas (= 1.2.13-1ubuntu1) | libsdl1.2debian-pulseaudio (= 1.2.13-1ubuntu1); however:
  Package libsdl1.2debian-alsa is to be removed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-arts is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.
(Reading database ... 103641 files and directories currently installed.)
Removing libsdl1.2debian-alsa ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libsdl1.2debian-pulseaudio.
(Reading database ... 103633 files and directories currently installed.)
Unpacking libsdl1.2debian-pulseaudio (from .../libsdl1.2debian-pulseaudio_1.2.13-1ubuntu1_amd64.deb) ...
Setting up libsdl1.2debian-pulseaudio (1.2.13-1ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kev@kev-desktop:~$
```

Seems theres alot missing?

---

