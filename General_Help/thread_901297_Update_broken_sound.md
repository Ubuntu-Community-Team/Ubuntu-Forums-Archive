---
title: "Update broken sound"
date: 2008-08-26
forum: General Help
---

### Post by david sousa on 2008-08-26
Hello!

This morning i made an update and i realized that i only can have sound from one program. amsn lost sound and when i go to system -> preferences -> sound and im playing something at amarok i get an error doing a test:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: (here says that i cant play with the device because its in use with other aplication)

please help, bye

---

### Post by david sousa on 2008-08-26
This is really annoying me because i toke weeks to get the sound working with everything. And now with some stupid update i got this error!

Please someone help!

---

### Post by david sousa on 2008-08-27
Now i went to system-> preferences -> sound and i changed Alsa to autodetect everywhere so i can do a test playing some music at amarok at the same time but i still don't get sound from amsn wich is configured to aplay. It was working in the past.

How do i solve this?

---

### Post by arashiko28 on 2008-08-28
I just fixed it by following some simple steps.

1. Go to terminal and write this
> locate amsn | grep sound

2. On the same terminal 
> esdplay /usr/share/amsn/skins/default/sounds/online.wav
 or
> play /usr/share/amsn/skins/default/sounds/online.wav

I had esd uninstalled, so it gave me the message to install it.

choose which one you listen better or at all, and in preference > others, change the sound config to the one it fits you.

esdplay $sound
play $sound

It worked for me, hope it does for you:)

---

### Post by david sousa on 2008-08-28
Thanks a lot :D

---

### Post by splashhtc on 2009-03-29
hey people had the same problem....did the above quotes...same problem continued....

this what i got on the terminal...and same problem continued to exist..



laptop:~$ locate amsn | grep sound 
laptop:~$ esdplay /usr/share/amsn/skins/default/sounds/online.wav 
laptop:~$ play /usr/share/amsn/skins/default/sounds/online.wav 
The program 'play' is currently not installed.  You can install it by typing:
sudo apt-get install sox
bash: play: command not found
laptop:~$ sudo apt-get install sox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vorbis-tools id3v2 libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsox-fmt-alsa libsox-fmt-base libsox0
Suggested packages:
  libsox-fmt-all
The following NEW packages will be installed:
  libsox-fmt-alsa libsox-fmt-base libsox0 sox
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 281kB of archives.
After this operation, 1077kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe libsox0 14.0.1-2build2 [118kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe libsox-fmt-alsa 14.0.1-2build2 [8030B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe libsox-fmt-base 14.0.1-2build2 [93.7kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe sox 14.0.1-2build2 [61.6kB]  
Fetched 281kB in 10s (26.1kB/s)                                                
Selecting previously deselected package libsox0.
(Reading database ... 146706 files and directories currently installed.)
Unpacking libsox0 (from .../libsox0_14.0.1-2build2_i386.deb) ...
Selecting previously deselected package libsox-fmt-alsa.
Unpacking libsox-fmt-alsa (from .../libsox-fmt-alsa_14.0.1-2build2_i386.deb) ...
Selecting previously deselected package libsox-fmt-base.
Unpacking libsox-fmt-base (from .../libsox-fmt-base_14.0.1-2build2_i386.deb) ...
Selecting previously deselected package sox.
Unpacking sox (from .../sox_14.0.1-2build2_i386.deb) ...
Processing triggers for man-db ...
Setting up libsox0 (14.0.1-2build2) ...

Setting up libsox-fmt-alsa (14.0.1-2build2) ...
Setting up libsox-fmt-base (14.0.1-2build2) ...
Setting up sox (14.0.1-2build2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
laptop:~$ play /usr/share/amsn/skins/default/sounds/online.wav 

Input File     : '/usr/share/amsn/skins/default/sounds/online.wav'
Sample Size    : 16-bit (2 bytes)
Sample Encoding: signed (2's complement)
Channels       : 2
Sample Rate    : 44100

Time: 00:00.81 [00:00.00] of 00:00.81 (100% ) Samples out: 39.1k Clips: 0    
Done.
laptop:~$

---

