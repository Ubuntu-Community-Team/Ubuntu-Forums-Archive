---
title: "Fresh 12.10 no sound in build-in speakers, sound on headphones. Worked in 12.04"
date: 2012-10-22
forum: Hardware
---

### Post by yngvewb on 2012-10-22
I have a strange problem after upgrading from 12.04 to 12.10. (Now I have also done a fresh install, and the problem persist) I have sound in headphones/line out but not on the build in speakers. I have checked alsamixer and everything seems to be working (I can see the volum indicater jumping up and down while playing music). Nothing is muted, sound in headphones but no sound on the speakers. It works when I use the Lubuntu 12.04 live CD. I am on Macbook air 1.1. Does someone have an idea what could be wrong?

I have gone through [http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/)

And [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by Nasair on 2012-10-27
First sorry no one got back to you sooner...I know how it feels.

Anyways, I'm not sure what you searched for but I found this thread helpful: [http://askubuntu.com/questions/106224/no-sound-after-lubuntu-installation]("http://askubuntu.com/questions/106224/no-sound-after-lubuntu-installation")

All you might need to do is turn up the system speakers:
In the terminal:
```
alsamixer
```
From there just adjust your sound levels

For me I get no sound when installing 12.04 or 12.10 until I switch the sound cards:
```
sudo su
cd /usr/share/alsa 
cp -p alsa.conf alsa.conf.dist 
sed -i 's/card 0/card 1/g' alsa.conf
```

Just paste that into the terminal and run the whole thing, of course after hitting enter enter your password.

I still don't get a sound button on my panel, but I haven't tried this yet:
```
sudo apt-get install xfce4-mixer gstreamer0.10-alsa
```

I will after my updates and installs finish. I just finished the install last night for Lubuntu and am waiting for all of my applications now. If I get to it before you I'll let you know how it goes.

Cheers,

Nasair

---

### Post by cmavr8 on 2012-10-27
> **Nasair said:**
> 

For me I get no sound when installing 12.04 or 12.10 until I switch the sound cards:
```
sudo su
cd /usr/share/alsa 
cp -p alsa.conf alsa.conf.dist 
sed -i 's/card 0/card 1/g' alsa.conf
```

Just paste that into the terminal and run the whole thing, of course after hitting enter enter your password.


These commands, along with a restart fixed it!!!(running "service pulseaudio restart" did not do anything)

Thanks so much!

---

### Post by Nasair on 2012-10-27
Glad I could help. For me doing my last command to run the install and then manually adding volume control to the panel gave me the volume control!

---

### Post by rrajath on 2012-11-01
It worked. Thanks a lot :)

---

### Post by yngvewb on 2012-11-08
Thanks for the help. But I do not have two sound cards, as the commenter says "look to see if you have two sound cards - if you have, sometimes swapping the cards works".

I have sound on headphones but not on the speakers

---

### Post by yngvewb on 2012-11-08
I tried 
```
sudo su
cd /usr/share/alsa 
cp -p alsa.conf alsa.conf.dist 
sed -i 's/card 0/card 1/g' alsa.conf
```

and

```
sudo apt-get install xfce4-mixer gstreamer0.10-alsa
```

But I still get no sound from the speakers, just the headphones.

---

### Post by Nasair on 2012-11-09
Did you try:
```
 
alsamixer

```
You can manually adjust all levels. Also, if you have HDMI than you have two sound cards. Lubuntu or any OS for that matter should send sound to only one or the other at a time. If you have HDMI try the two sound card trick as well...that was my problem.
Let me know how the alsamixer goes.

---

### Post by Lignamorren on 2012-11-13
Add me to the list of sufferers. 12.10, MacBookAir1,1. Kernel at 10.5.0.17 because 10.5.0.18 seems to have broken the wl WiFi driver. I've tried all the fixes folks have mentioned, to no avail. Sound works on headphones but not on built-in speakers.

---

### Post by Nasair on 2012-11-15
> **Lignamorren said:**
> Add me to the list of sufferers. 12.10, MacBookAir1,1. Kernel at 10.5.0.17 because 10.5.0.18 seems to have broken the wl WiFi driver. I've tried all the fixes folks have mentioned, to no avail. Sound works on headphones but not on built-in speakers.

And you tried the
```
sudo su cd /usr/share/alsa  cp -p alsa.conf alsa.conf.dist  sed -i 's/card 0/card 1/g' alsa.conf
```

and the messed with
```
aslamixer
```
?

Can you get it to work with the live CD of Ubuntu? I'd suggest you make a new thread with your computer hardware info if you answer no to both.
If it works with the live CD than you'll need to just delve deeper into the issue and in that case I'd suggest you again you make a new thread with your computer hardware.

Good luck!

---

### Post by yngvewb on 2012-11-26
Lignamorren: Thanks, finally someone with the same problem! :-) 

Live CD Lubuntu 12.10: sound in headphones, not in speakers
Live CD Lubuntu 12.04: sound in headphones and speakers

---

### Post by yngvewb on 2012-12-10
> **Lignamorren said:**
> Add me to the list of sufferers. 12.10, MacBookAir1,1. Kernel at 10.5.0.17 because 10.5.0.18 seems to have broken the wl WiFi driver. I've tried all the fixes folks have mentioned, to no avail. Sound works on headphones but not on built-in speakers.

Did you find a solution?

---

### Post by Yellow Pasque on 2012-12-10
You should file a bug and note that other people with the same system have the same issue. Please link us to the bug and I will confirm it for you and mark it as a regression.

---

### Post by Ghostlych on 2013-01-21
> **Nasair said:**
> First sorry no one got back to you sooner...I know how it feels.

Anyways, I'm not sure what you searched for but I found this thread helpful: [http://askubuntu.com/questions/106224/no-sound-after-lubuntu-installation](http://askubuntu.com/questions/106224/no-sound-after-lubuntu-installation)

All you might need to do is turn up the system speakers:
In the terminal:
```
alsamixer
```From there just adjust your sound levels

For me I get no sound when installing 12.04 or 12.10 until I switch the sound cards:
```
sudo su
cd /usr/share/alsa 
cp -p alsa.conf alsa.conf.dist 
sed -i 's/card 0/card 1/g' alsa.conf
```Just paste that into the terminal and run the whole thing, of course after hitting enter enter your password.

I still don't get a sound button on my panel, but I haven't tried this yet:
```
sudo apt-get install xfce4-mixer gstreamer0.10-alsa
```I will after my updates and installs finish. I just finished the install last night for Lubuntu and am waiting for all of my applications now. If I get to it before you I'll let you know how it goes.

Cheers,

Nasair

I tried this as well, while this did not work i got audio after "configuring" another audio device and going back to the original Analogue Stereo Duplex. So atleast that fixes the audio for that session alone... Annoying but at least it works somewhat. 
however after running the commands in terminal Alsamixer stopped working properly.. All i get now is "cannot open mixer: No such file or directory" ugh.. For some reason 12.10 is giving me a lot more problems then what i expect from Ubuntu and i consider going back to 12.04 to get things working as they should.

---

### Post by Mip5 on 2013-01-23
> **cmavr8 said:**
> These commands, along with a restart fixed it!!!(running "service pulseaudio restart" did not do anything)

Thanks so much!

That worked for me too! Thanks!

---

### Post by Nasair on 2013-01-28
> **Ghostlych said:**
> I tried this as well, while this did not work i got audio after "configuring" another audio device and going back to the original Analogue Stereo Duplex. So atleast that fixes the audio for that session alone... Annoying but at least it works somewhat. 
however after running the commands in terminal Alsamixer stopped working properly.. All i get now is "cannot open mixer: No such file or directory" ugh.. For some reason 12.10 is giving me a lot more problems then what i expect from Ubuntu and i consider going back to 12.04 to get things working as they should.

Still having this problem?
Try uninstall/installing alsamixer, maybe it isn't installed correctly?
```
sudo apt-get install Alsamixer 
```
You might find it easier to do a format, re-install of Lubuntu if you're having problems running alsamixer after it is installed.

---

### Post by yngvewb on 2013-02-27
I reinstalled Lubuntu 12.04.  
As a noted earlier, sound works on fresh install in Lubuntu 12.04, but not in Lubuntu 12.10, fresh install. I am on Macbook air 1.1. It is not the Alsamixer :-(

---

