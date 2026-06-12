---
title: "Streaming Media Server"
date: 2008-09-27
forum: General Help
---

### Post by thegodfaza on 2008-09-27
I am looking for a web app that can show me my music library and let me stream any song or video over the internet. I have found one but it is flawed in that every request takes a long time (300 seconds for me). It's called Jinzora. This is a flaw that apparently everyone has when they use it with a large number of songs. I would like to know if anyone knows of something else like this that can be installed on a web server and that can stream content.

---

### Post by thegodfaza on 2008-09-27
[BUMP]
Wonder why no one ever replies to me....

---

### Post by plonka2000 on 2008-09-28
I'm interested in this too...

---

### Post by Vivaldi Gloria on 2008-09-28
I have never tried it but vlc has that capability. I prefer mounting remote folders using sshfs as local ones. Then a remote folder becomes no different than a local one.

---

### Post by Jose Catre-Vandis on 2008-09-28
We use GNUMP3d at home and away, in the repos, easy to set up, configurable interface, tried others but always come back to "gunump" (as my kids call it)

---

### Post by Sir_Brizz on 2008-10-23
GNUMP3d 3.0 is definitely the best web-based music streaming server I have found for Linux. the only problem is, it is no longer maintained, and I hate how it reports filenames. I use Songbird and it puts all the file information into the "Title" metadata field, so I can't use my Web Media History to play the music from there.

I've tried Jinzora and it is alright, but it makes Songbird's memory usage skyrocket.

---

### Post by skyshock21 on 2008-10-23
Squeeze center from Logitech.  It's free, it's OSS, and it runs on damn near everything.  

There's also Andromeda.php (google it), but it costs $20.  It's a simple PHP script you copy onto your web server and runs stand alone.  It's nifty.  

What I _REALLY_ want is a music server that streams your music directly through your web browser using a flash player front end.  I've used a flash front end to stream using SqueezeCenter, but all the flash front-ends COMPLETELY PWND my network because they do some retard polling in the js code I think that causes a ******* 3-way handshake non-stop and spiked my network connection to a steady 250 k/sec.  **** that noise, VLC didn't do that.  :(

Anyone have a good Flash streaming web app recommendation?

---

### Post by porteclefs on 2008-10-24
Oh, I love GNUMP3d. I played around with SqueezeCenter but the truth there hurts. If you didn't have Slimserver and then perform an update to Squeezcenter, then the easy fix isn't there (a .conf file). If you've played with SqueezeCenter, then you probably know what I mean.

Gnump3d is super easy. I use my Samba server to move files from my windows pc's into the music directory for Gnump3d. it's pie. i love it.

---

### Post by iamgod on 2008-11-26
I've been using Ampache for years now and love it.  You can find more information here:
[https://help.ubuntu.com/community/ampache]("https://help.ubuntu.com/community/ampache")

---

### Post by cjssmo on 2009-03-05
Ampache is a great music server.  Video streaming is being added

---

### Post by Keith_Beef on 2009-05-25
I have Squeezecenter running on a NAS (IP 192.168.0.4) in the basement machine room, and a Squeezebox in the living room.

What I want, is to run some program on a laptop in another room to catch the stream from Squeezecenter and replay it as audio, like the Squeezebox is doing. Teh hope is that the two playbacks will be in synch.

I tried pointing Xine at [http://192.168.0.4:9000/stream.mp3](http://192.168.0.4:9000/stream.mp3) and tried the same with VLC. Both of these report "Bienvenue sur le SqueezeCenter" (yeah, I set up Squeezecenter in French), so I know that some connection is being established and that both clients (Xine and VLC) are able to catch the stream and at least decode the text... but I get no sound... :(

I can play back local files through both clients, so that shows that there is no ALSA/OSS/PuleAudio confusion; but how can I get the clients to catch and decode this audio and play it back?


K.

---

