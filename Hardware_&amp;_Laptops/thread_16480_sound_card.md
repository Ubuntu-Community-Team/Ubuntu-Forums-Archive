---
title: "sound card"
date: 2005-02-21
forum: Hardware &amp; Laptops
---

### Post by t3rm1n8r1x on 2005-02-21
i need help getting my osund card installed. it's a soundmax integrated digital audio card. I've already been to alsa-project.org, and can't find what i need. any help would be appreciated.

---

### Post by kassetra on 2005-02-21
[QUOTE=t3rm1n8r1x]i need help getting my osund card installed. it's a soundmax integrated digital audio card. I've already been to alsa-project.org, and can't find what i need. any help would be appreciated.[/QUOTE]

sure, I can help you!  :)
First off, what kind of motherboard do you have, VIA, Intel, or ATI?

---

### Post by t3rm1n8r1x on 2005-02-21
i need to install it into ubuntu, not onto the motherboard. if the motherboard still matters, i need to know how to find out.

---

### Post by kassetra on 2005-02-21
[QUOTE=t3rm1n8r1x]i need to install it into ubuntu, not onto the motherboard. if the motherboard still matters, i need to know how to find out.[/QUOTE]

I understand that you are trying to install your sound into ubuntu; I need to know the motherboard type because there are three different sound drivers for your sound chipset -- based upon which motherboard the sound chipset is on.

We can possibly narrow down your motherboard type options if you have an AMD cpu (AMD will not work on an intel motherboard.)

---

### Post by t3rm1n8r1x on 2005-02-21
i've got an intel cpu

---

### Post by kassetra on 2005-02-21
[QUOTE=t3rm1n8r1x]i've got an intel cpu[/QUOTE]

Ok... you need to open a terminal and type this command:
 ```
lspci
``` 

And then, down at the bottom, you should see something that says "Multimedia audio controller" and some letters to the right.  If you could tell me the text that's to the right of that line, I'll know which sound driver you need.

---

### Post by t3rm1n8r1x on 2005-02-21
do you know a way i can do it through windows xp? cuz' otherwise it'll be a while

---

### Post by kassetra on 2005-02-21
[QUOTE=t3rm1n8r1x]do you know a way i can do it through windows xp? cuz' otherwise it'll be a while[/QUOTE]

Try this (I'm looking for the exact hardware device name -- I know it's a SoundMAX):
Control Panel->System->Hardware Tab->Device Manager

Then scroll down to Sound, video, and game controllers, and click on the plus to expand the tree, and you should see your sound card's device name in that list.

---

### Post by t3rm1n8r1x on 2005-02-21
SoundMAX Integrated Digital Audio

---

### Post by kassetra on 2005-02-21
[QUOTE=t3rm1n8r1x]SoundMAX Integrated Digital Audio[/QUOTE]

Ok, right click on it and then click on properties.  Does it have a manufacturer name?

---

### Post by t3rm1n8r1x on 2005-02-21
how about this?
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB (ICH4) AC'97 Audio Controller (rev 02)

---

### Post by kassetra on 2005-02-21
[QUOTE=t3rm1n8r1x]how about this?
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB (ICH4) AC'97 Audio Controller (rev 02)[/QUOTE]

Yes yes yes!  That's what I needed to know!

You have an intel board, so your sound driver will be snd-intel8x0!
Ok, now we're cooking!

To actually install this driver, you'll need to be in linux (or able to use a linux terminal)

---

### Post by t3rm1n8r1x on 2005-02-21
[QUOTE=kassetra]Yes yes yes!  That's what I needed to know!

You have an intel board, so your sound driver will be snd-intel8x0!
Ok, now we're cooking!

To actually install this driver, you'll need to be in linux (or able to use a linux terminal)[/QUOTE]
 tell mo how now, and i'll just copy it to a text file to read when i boot back into linux

and maybe you could help me with another problem? read my conexant modem post

---

### Post by kassetra on 2005-02-21
[QUOTE=t3rm1n8r1x]tell mo how now, and i'll just copy it to a text file to read when i boot back into linux[/QUOTE]

Ok. (if you're installing ubuntu it should auto-detect and install, but if not here you go... you'll need a terminal command line to do these things):

1. Check to see if the sound card got loaded:
 ```
sudo lsmod |grep snd*
``` 

If snd-intel8x0 is in that list, your sound card driver was installed just fine.
If it's not in that list do this:
 ```
sudo uname -a
``` 
(to get your kernel_version)
 ```
sudo modprobe /lib/modules/kernel_version/kernel/sound/pci/snd-intel8x0
``` 

Your sound should be setup at this point...

---

### Post by kassetra on 2005-02-21
[QUOTE=t3rm1n8r1x]tell mo how now, and i'll just copy it to a text file to read when i boot back into linux

and maybe you could help me with another problem? read my conexant modem post[/QUOTE]

Ok, let me eat some dinner here first, and then I'll take a look at your modem post.  :)

---

### Post by t3rm1n8r1x on 2005-02-21
[QUOTE=kassetra]Ok, let me eat some dinner here first, and then I'll take a look at your modem post.  :)[/QUOTE]
 thank you!

---

### Post by t3rm1n8r1x on 2005-02-21
apparently, the sound card was installed, but then why can't i change the volume level so i can hear a cd?

---

### Post by kassetra on 2005-02-21
[QUOTE=t3rm1n8r1x]apparently, the sound card was installed, but then why can't i change the volume level so i can hear a cd?[/QUOTE]

AHHH!  I'm guessing that you're changing the sound volume from the top panel, and it's not doing anything?

---

### Post by kassetra on 2005-02-21
[QUOTE=t3rm1n8r1x]thank you![/QUOTE]

Have you read this?
[http://ubuntuforums.org/archive/index.php/t-1906.html]("http://ubuntuforums.org/archive/index.php/t-1906.html")

It seems that if you follow those instructions you'll be able to have your modem working, correctly.

I don't think it is installed or working properly from the errors you had while trying to install the package.

also, if you ever want to find out what kernel you're running type this:
 ```
uname -a
``` 
that way you can make sure that you have the correct headers installed.

---

### Post by t3rm1n8r1x on 2005-02-22
yeah, that's where i was trying to change the volume. why, is that not where i'm supposed to change it?

and that link about the modem is confusing as hell. can u put it in less-technical english?

---

### Post by kassetra on 2005-02-22
[QUOTE=t3rm1n8r1x]yeah, that's where i was trying to change the volume. why, is that not where i'm supposed to change it?[/QUOTE]

Oh no that's not it at all, having your sound not change from the little volume icon is totally different than not having your sound driver installed!  :)  (and much easier to fix!)

Ok, I'm assuming that you have been clicking on the little volume icon and moving the slider all the way to the top, but no sound?

---

### Post by t3rm1n8r1x on 2005-02-22
yeah, i move it and it just goes back to the bottom, which is crap because i can hear the ubuntu "ready to logon" sound where u put your username in. also re-read my last post, plz.

---

### Post by kassetra on 2005-02-22
[QUOTE=t3rm1n8r1x]yeah, i move it and it just goes back to the bottom, which is crap because i can hear the ubuntu "ready to logon" sound where u put your username in. also re-read my last post, plz.[/QUOTE]

We'll deal with your modem in just a second here.
First, right click on your volume icon and then left click on "Volume Control"

does it open?

---

### Post by t3rm1n8r1x on 2005-02-22
[QUOTE=kassetra]We'll deal with your modem in just a second here.
First, right click on your volume icon and then left click on "Volume Control"

does it open?[/QUOTE]
 where it brings up the audio channels? yes, but there's no channels there.

---

### Post by kassetra on 2005-02-22
[QUOTE=t3rm1n8r1x]where it brings up the audio channels? yes, but there's no channels there.[/QUOTE]

I was going to have you check those preferences next, but first see if you can click on "Open Volume Control" right under mute.

Also, did you install warty or hoary?

(p.s. the reason you hear sound when ubuntu first starts is because that is running on the ESD daemon... your volume control, I think, is running on ALSA... which is what I'm having you check right now...  Also, what were you trying to play when you discovered you didn't have any sound?)

---

### Post by t3rm1n8r1x on 2005-02-22
when i click on open volume control, it brings up the audio channels box. installed warty. was trying to play a cd.

---

### Post by kassetra on 2005-02-22
[QUOTE=t3rm1n8r1x]when i click on open volume control, it brings up the audio channels box. installed warty. was trying to play a cd.[/QUOTE]

Ok, here's a list of stuff I want you to try so that I can figure out what's up:
1. Have you tried playing a music file from your computer (other than from cd)?
2. In a terminal, type the following and press enter:
 ```
gst-register-0.8
``` 
(and try to run your cd again)
3. Open synaptic and search for "alsa" (without the "") ... and then tell me what it finds.

---

### Post by t3rm1n8r1x on 2005-02-22
[QUOTE=kassetra]Ok, here's a list of stuff I want you to try so that I can figure out what's up:
1. Have you tried playing a music file from your computer (other than from cd)?
2. In a terminal, type the following and press enter:
 ```
gst-register-0.8
``` 
(and try to run your cd again)
3. Open synaptic and search for "alsa" (without the "") ... and then tell me what it finds.[/QUOTE]
 that'll be awhile
the only other music files i have are mp3, which i can't play(no package)

---

### Post by kassetra on 2005-02-22
[QUOTE=t3rm1n8r1x]that'll be awhile
the only other music files i have are mp3, which i can't play(no package)[/QUOTE]

let me get you the package you need to install to hear mp3:
install [this file]("http://www.linuxpeach.com/ubuntu/gstreamer0.8-lame_0.8.2-2_i386.deb") with this command:
 ```
cd /path/to/downloaded file
sudo dpkg -i gstreamer*
``` 

That will give you mp3 playback.

I'll be back in a few hours to help you finish this and the modem problem.

If you run into ANY problems installing that file while I'm out, here is the[ ubuntu starter guide]("http://ubuntuguide.org") to help you... read the first part and the bit about the extra repositories and multimedia players.

---

### Post by t3rm1n8r1x on 2005-02-22
i know about the package, but i need to update some others due to version dependencies

---

### Post by kassetra on 2005-02-22
[QUOTE=t3rm1n8r1x]i know about the package, but i need to update some others due to version dependencies[/QUOTE]

Then you need the warty-backports repositories included in your synaptic!
do this:
 ```
sudo gedit /etc/apt/sources.list
``` 
when the file comes up, add the following lines to the bottom:

deb [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") warty universe  
deb-src [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") warty universe  

deb [http://security.ubuntu.com/ubuntu/]("http://security.ubuntu.com/ubuntu/") warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/]("http://security.ubuntu.com/ubuntu/") warty-security main restricted 

deb [http://backports.ubuntuforums.org/backports/]("http://backports.ubuntuforums.org/backports/") warty-backports main universe restricted multiverse  

deb [http://backports.ubuntuforums.org/backports/]("http://backports.ubuntuforums.org/backports/") warty-extras main universe restricted multiverse  

save the file, close it, open synaptic and reload, and you'll be able to upgrade gstreamer.  (plus a whole host of other apps)

---

### Post by t3rm1n8r1x on 2005-02-22
that'll be helpful when we get the modem working so i can get online with linux :)

---

### Post by t3rm1n8r1x on 2005-02-22
[QUOTE=kassetra]Ok, here's a list of stuff I want you to try so that I can figure out what's up:
1. Have you tried playing a music file from your computer (other than from cd)?
2. In a terminal, type the following and press enter:
 ```
gst-register-0.8
``` 
(and try to run your cd again)
3. Open synaptic and search for "alsa" (without the "") ... and then tell me what it finds.[/QUOTE]

entered command, bunch of stuff scrolled. ~150 items, >200 features.

alsa-base
alsa-utils
gstreamer0.8-alsa
libpt-plugins-alsa

still cant change volume

---

### Post by papageno on 2005-02-23
I have the same problem.
If i launch the command: aplay -l the result is: aplay: device_list:199: no soundcards found...
What i must do please?
Thank you

---

### Post by fastluck on 2005-05-31
[QUOTE=kassetra]Ok, right click on it and then click on properties.  Does it have a manufacturer name?[/QUOTE]

The manufacturer's name is Analog Devices, Inc.  I'm trying to get my Soundmax Integrated Digital Audio hardware working on my Vaio.  I haven't been able to find anything either.  I'll try what's discussed here to see if I can get anywhere.  You mentioned that the installer should detect the sound hardware--it does not.

Fastluck

---

### Post by strawberry on 2005-06-07
Dear Kassetra,
I respect and admire your fight for the onboard sound card on 22.02.2005.
That was great!
strawberry
 =D>

---

### Post by simoncullen on 2005-08-24
[QUOTE=kassetra]Ok. (if you're installing ubuntu it should auto-detect and install, but if not here you go... you'll need a terminal command line to do these things):

1. Check to see if the sound card got loaded:
 ```
sudo lsmod |grep snd*
``` 

If snd-intel8x0 is in that list, your sound card driver was installed just fine.
If it's not in that list do this:
 ```
sudo uname -a
``` 
(to get your kernel_version)
 ```
sudo modprobe /lib/modules/kernel_version/kernel/sound/pci/snd-intel8x0
``` 

Your sound should be setup at this point...[/QUOTE]

I have the same problem, but when I enter that final command I get this message:

> simon@ahimsa:/lib/modules/2.6.10-5-686/kernel/sound/pci$ sudo modprobe /lib/modules/2.6.10-5-686/kernel/sound/pci/snd-intel8x0

When I ls in that directory I see this:

> simon@ahimsa:/lib/modules/2.6.10-5-686/kernel/sound/pci$ ls
ac97     korg1212        snd-atiixp-modem.ko  snd-ens1371.ko    snd-maestro3.ko    vx222
ali5451  mixart          snd-azt3328.ko       snd-es1938.ko     snd-rme32.ko       ymfpci
au88x0   nm256           snd-bt87x.ko         snd-es1968.ko     snd-rme96.ko
cs46xx   rme9652         snd-cmipci.ko        snd-fm801.ko      snd-sonicvibes.ko
emu10k1  snd-als4000.ko  snd-cs4281.ko        snd-intel8x0.ko   snd-via82xx.ko
ice1712  snd-atiixp.ko   snd-ens1370.ko       snd-intel8x0m.ko  trident


I've tried the command with "snd-intel8x0m.ko" instead of "snd-intel8x0m" and it gives the same error.  I have the same sound card too....

BTW I'm using Hedgehog 5.04

Any ideas?  Thanks!

---

### Post by fastluck on 2005-08-24
If you haven't tried it without specifying a sound card, do that. 

Here's my directory setup in usr/src/alsa:

```

fastluck@roadrage:/usr/src/alsa$ ls
alsa-driver             alsa-lib           alsa-utils            tars
alsa-driver-1.0.9rc4a   alsa-lib-1.0.9rc4  alsa-utils-1.0.9rc4a  usb
alsa-firmware           alsa-oss           buildalsa
alsa-firmware-1.0.9rc4  alsa-oss-1.0.9rc4  input
fastluck@roadrage:/usr/src/alsa$
fastluck@roadrage:/usr/src/alsa$

```

Here's a bash script that I use to build alsa.  I've had to run it four or five times--every time I update my kernel. It hasn't let me down yet.  It depends on creating symlinks to the actual directories, or you can change the names of the directories in the script to add the version info:

```
#!/bin/bash
cd alsa-driver
make clean
./configure --with-oss=yes
make
make install

cd ..
cd alsa-lib
make clean
./configure
make
make install

cd alsa-oss
make clean
./configure
make
make install

cd ..
cd alsa-lib
make clean
./configure
make
make install

cd ..
cd alsa-firmware
make clean
./configure
make
make install

cd ..
cd alsa-utils
make clean
./configure
make
make install

```

---

