---
title: "How Do I Configure My Soundcard"
date: 2005-11-13
forum: General Help
---

### Post by CompleteNewb on 2005-11-13
I am Getting an error when i try to play sound, i clciked on the volume control button and got this error:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

so I guess i need to configure my soundcard, which i dont know hot to do or even how to get started becuase i know nothing about Ubuntu, or Linux for that matter but seeing as how im getting a ntldr compressed error when trying to run xp, and dont have a xp install cd im kinda stuck with ubuntu, but if anyone could help me figure out why my soundcard isnt wokring then ill be ok. Thanx for your guys help

---

### Post by zodium on 2005-11-13
Which soundcard do you have?

---

### Post by nszabolcs on 2005-11-13
see if your soundcard is detected:
```
lspci | grep audio
```
see if snd modules are loaded:
```
lsmod | grep snd
```

if these are ok then test if you get sound with other applications.
```

apt-get install mpg321
mpg321 some_mp3_file.mp3

```

if it's ok then there is a problem with gstreamer output plugin
(sound otput can be oss, alsa, esd/esound, arts, polypaudio,...)
use alsa or esound (i think it can be configured in the preferences of gstreamer somewhere)

---

### Post by CompleteNewb on 2005-11-13
hey my soundcard i guess is being detected, the first code came up ok
"josh@ubuntu:~$ lspci | grep audio
0000:00:0d.0 Multimedia audio controller: Rockwell International: Unknown device 4310"

With the  second code nothing happened

When i entered sudo apt-get install mpg321 i recieved this:

"Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  mpg321
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.5kB of archives.
After unpacking 131kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe mpg321 0.2.10.3 [34.5kB]
Fetched 34.5kB in 1s (21.6kB/s)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

Preconfiguring packages ...
Selecting previously deselected package mpg321.
(Reading database ... 70968 files and directories currently installed.)
Unpacking mpg321 (from .../mpg321_0.2.10.3_i386.deb) ...
Setting up mpg321 (0.2.10.3) ...

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems"


So, where do i go from there?

---

### Post by az on 2005-11-13
If it is an older soundcard, try this:

[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

---

### Post by CompleteNewb on 2005-11-13
nope the commands output a bunch of errors

---

### Post by nszabolcs on 2005-11-13
[QUOTE=CompleteNewb]
With the  second code nothing happened
[/QUOTE]
now that's a problem
find out what is the module needed for your card
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)
and try to modprobe it
if it's soundblaster compatible then try the sb16 module
```

modprobe sb
#or
modprobe sb16
#or
modbrobe snd-sb16

```

[QUOTE=CompleteNewb]
When i entered sudo apt-get install mpg321 i recieved this:
... warnings here ...
[/QUOTE]
run apt-get update to get rid of the warnings.
mpg321 is just a simple/small commandline mp3 player, you can use other player (like alsaplayer, xmms, beep-media-player ...) 
i wrote it just to make sure the sound works and the problem is not within gstreamer.

---

### Post by CompleteNewb on 2005-11-13
Hey, thanx alot, i will try that, and let you know how it goes.

---

### Post by CompleteNewb on 2005-11-13
Well, it seems i ahve another problem, the soundcard that i have is a "Rockwell Chameleon combo card" it is a modem/ audio card, i can not find it on the list of that site. Also i should note that i have a hp xl768 just in case someone can find more info. thanx for your guys' help.

---

### Post by SomeGeekyGuy on 2008-04-20
I opened a terminal and logged in as root and tried the commands, but nothing happened. It just gave me another prompt. Any ideas?

---

