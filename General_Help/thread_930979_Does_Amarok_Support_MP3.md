---
title: "Does Amarok Support MP3?"
date: 2008-09-26
forum: General Help
---

### Post by zohaib on 2008-09-26
I've installed Amarok player today. I thought it supports MP3 files but when I drag An mp3 song in it, It says no support for MP3 ., but I saw on wikipedia n they say it supports MP3 then why My amarok says no MP3 support?

whats the deal., does it really support MP3s or not?

or do I have to download plugins for this?

thanks

---

### Post by Don Giovanni on 2008-09-26
have you installed the restricted extras?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

see the guide here for adding playback for mp3, dvd and many other proprietary formats for ubuntu in general

---

### Post by cariboo on 2008-09-26
Or even easier, to install all the audio and video codecs except for the dvd dycrpter in a terminal type:

```
sudo apt-get install ubuntu-restricted-extras
```

Jim

---

### Post by zohaib on 2008-09-26
> **Don Giovanni said:**
> have you installed the restricted extras?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

see the guide here for adding playback for mp3, dvd and many other proprietary formats for ubuntu in general

yea I followed the instructions it downloaded an engine n installed it ., but it still says no mp3 support :(

any other solution?

---

### Post by zohaib on 2008-09-26
> **cariboo907 said:**
> Or even easier, to install all the audio and video codecs except for the dvd dycrpter in a terminal type:

```
sudo apt-get install ubuntu-restricted-extras
```

Jim

I tried that it says all packages are already installed

---

### Post by ad_267 on 2008-09-26
Are you sure it's actually an mp3 file you're trying to play? Not just some other codec with an mp3 extension.

---

### Post by SuperSonic4 on 2008-09-26
> **cariboo907 said:**
> Or even easier, to install all the audio and video codecs except for the dvd dycrpter in a terminal type:

```
sudo apt-get install ubuntu-restricted-extras
```

Jim

What about 
```
sudo apt-get install kubuntu-restricted-extras
``` since amarok is a KDE app. 

I believe amarok uses the gstreamer plugin, I'd just suggest looking for gstreamer in synaptic


```
sudo apt-get install libgstreamer-plugins-base0.10-0
```

That code is what I have installed under gstreamer in adept (I use Kubuntu)

---

### Post by zohaib on 2008-09-26
****Amarok Is working now

thanks everyone., I Appreciat that

How The Problem Solved

I clicked on the link Which DON GIOVANNI have provided in the second post of this thread n went to that website n then clicked on this link [http://packages.medibuntu.org/feisty/index.html](http://packages.medibuntu.org/feisty/index.html)., n downloaded amarok engins n then ffmpeg as well I installed them ., Then an update notification appeared on the top of the screen., I updated it restared my PC n then once again try to run an MP3 On Amarok file this time it played it.,

Works perfect

Great Player:guitar:

---

### Post by bigbrovar on 2008-09-26
FYI u could show your appreciation by thanking those who helped you solve the problem. You can do that by clicking on the little yellow star below their post :)

---

### Post by Crafty Kisses on 2008-09-26
AmaroK does, and it also has iPod support. :)

---

