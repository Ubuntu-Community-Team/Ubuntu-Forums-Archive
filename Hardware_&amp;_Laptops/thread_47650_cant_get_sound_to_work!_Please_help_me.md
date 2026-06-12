---
title: "cant get sound to work! Please help me"
date: 2005-07-09
forum: Hardware &amp; Laptops
---

### Post by JustinJS on 2005-07-09
I cant get my sound card to work i can see it when i go to the Device mangers but cant hear anything and is not in my mixer I have a Audigy LS which i want to work and also integrated which i dont give a crap about so how do i go about getting my Audigy LS to work?
Oh btw if it helps i also have a ATI TV wonder VE

---

### Post by JustinJS on 2005-07-09
bump bump bump it up

---

### Post by Trace Green on 2005-07-10
tell me the result lspci and lspci -n and lsmod :)

---

### Post by DarkManX4lf on 2005-07-10
try this:


type this in console:

alsamixer

and then press the right key to scroll al the way to the right and find soething that says "Audigy A" its the analog port of your card i think, when that is highlighted press m, this will unmute it, once unmuted press "ESC" to get out, and type this in console to save those settings

alsactl store

this shoudl work

---

### Post by JustinJS on 2005-07-10
tried alsamixer
```
justin@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

``` 
and it just lspci

---

### Post by glenn4009 on 2005-07-10
Hi, this might sound really dumb and irrelevant, but do you have a webcam ? if the answer is yes try unplugging it and hitting ctrl alt and backspace (with it still unplugged) the sound might be back then, i say this becuase i had this exact problem no sound, this was becuase with my webcam plugged in, Linux was using my webcam as the sound device. Also have you tried right clicking the volume icon (next to the clock at the top right hand corner) and clicking prefences and choosing which device to monitor. Best of luck and if this has been no help at all, i appologise.

---

### Post by manicka on 2005-07-10
Try going into the bios and disabling the onboard sound card, they are probably conflicting. 

Also, open the volume control panel (right click on volume icon and choose open volume control) and make sure that none of the volumes are muted.

---

### Post by filemanager on 2005-07-11
[QUOTE=JustinJS]tried alsamixer
```
justin@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

``` 
and it just lspci[/QUOTE]
 I get that same error =\

---

