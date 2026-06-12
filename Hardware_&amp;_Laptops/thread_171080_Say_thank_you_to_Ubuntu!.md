---
title: "Say thank you to Ubuntu!"
date: 2006-05-05
forum: Hardware &amp; Laptops
---

### Post by srap on 2006-05-05
Hello,
I'm a vietnamese student and i'm very interesting of linux. I installed Ubuntu in my laptop T23 IBM and it works so great, it can detect my network, modem and PCMCIA DWL 650 Wireless card althought the drivers are still not correct. Firefox  is so cool, an eye-candy desktop from gnome-look, pdf, office, easily install from synaptec,... such annoying things i've never met in windows. That's all, i thinks, ubuntu is one of the best distros linux i've known. Thank you, thanks and thanks. My OS XP becomes an yesterday from the time i setup ubuntu dapper beta. So crazy but a big problem that i cannot hear the music (1Gbs) that i've bought from Itunes music store (throuht Itunes) before. Are there any one of you, my friends, know how to install it to play these suck DRM songs?
But anyway, say thank you is all of i want you to know.
(sorry my bad english, :razz: don't laught :KS )

---

### Post by IYY on 2006-05-05
I believe VLC can open these files!

sudo apt-get install vlc

---

### Post by srap on 2006-05-05
[QUOTE=IYY]I believe VLC can open these files!

sudo apt-get install vlc[/QUOTE]
Thanks, I'll give it a try, but my Itunes 6.0.4.2 seems to be not supported from vlc.

Have tried. But vlc cannot not play itunes 6 protected aac songs.

---

### Post by Sef on 2006-05-05
> So crazy but a big problem that i cannot hear the music (1Gbs) that i've bought from Itunes music store (throuht Itunes)

First make sure universe and multiverse are enabled.

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

Next open the Terminal (Applications > Accessories > Terminal) and type this:

```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
```

if you still can't hear your itunes, then go here:

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by srap on 2006-05-05
[QUOTE=Sef]First make sure universe and multiverse are enabled.

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

Next open the Terminal (Applications > Accessories > Terminal) and type this:

```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
```

if you still can't hear your itunes, then go here:

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")[/QUOTE]
Thanks sef, I've installed all the gstreams plugins but I still couldn't hear it. I thought i must install itunes in Wine emulator. However, i've lost the wine folders (contains programs files folder and windows folders) because i deleted thems. I reinstalled it, but these folders weren't be installed again. So i cannot emulate anything. Some one can help me reinstall these folders? 
Thanks
bests.

---

### Post by eddie303 on 2006-05-06
As far as I know, it should re-make its folders on the next run, if you delete it. Usually there are in your home directory/.wine/c_drive

---

