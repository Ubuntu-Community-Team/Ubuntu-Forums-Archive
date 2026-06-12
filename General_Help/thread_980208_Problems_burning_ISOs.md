---
title: "Problems burning ISOs"
date: 2008-11-12
forum: General Help
---

### Post by snkngshps on 2008-11-12
I'm having a problem burning ISO's. I am just right clicking on the file and selecting "Write to disc" and I get the immediate error "Unable to create CD/DVD this file is not a valid disc image". I downloaded the ISO so there is the possibility that it's corrupt but this is the third different ISO it has happened with. If I open brasero and burn the ISO the burning takes place successfully but the disc doesn't work. If I create an ISO from a video file it has no problem burning. My guess is that somehow the file is corrupting during the download. Does anyone know why this might be? Or how I could check? Or how I could fix it?

---

### Post by bgs100 on 2008-11-12
Just check your ISO file:
[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")
And to see what the code means:
[https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by iKonaK on 2008-11-12
1 > check the md5 (openssl dgst -md5 *.iso)
2 > try download the iso via p2p (torrent)
3 > try it in virtual box first

---

### Post by snkngshps on 2008-11-12
Well it's actually not a Ubuntu disc-image. I downloaded them from torrent sites, I've tried three completely different ISOs and all of them have given me the same error message.

---

### Post by bgs100 on 2008-11-12
Try uninstalling and re-installing "Brasero"
```
sudo apt-get autoremove brasero
sudo apt-get clean
sudo aptitude clean
sudo apt-get install brasero
```

---

### Post by iKonaK on 2008-11-12
> **bgs100 said:**
> Try uninstalling and re-installing "Brasero"
```
sudo apt-get autoremove brasero
sudo apt-get clean
sudo aptitude clean
sudo apt-get brasero
```
sudo apt-get [COLOR=DarkRed]install[/COLOR] brasero ;)
* i still believe there must be something with the iso's

---

### Post by exploder on 2008-11-12
Which version of Ubuntu are you running, 8.04 or 8.10? I might be able to help.

---

### Post by snkngshps on 2008-11-12
Reinstalling brasero didn't work. I'm 99% sure it's the ISO files, but what I don't understand is why they are all corrupting. The comments on them all say that they are good files and I tried three completely different ISOs. I am running 8.10 Ibex. Now that I think about it, I don't think I've burned an ISO since upgrading to Ibex. Maybe something got messed up during the upgrade?

---

### Post by bgs100 on 2008-11-12
You've *only* tried torrents?  If so, maybe you should try a normal download.

---

### Post by iKonaK on 2008-11-12
> **snkngshps said:**
> Well it's actually not a Ubuntu disc-image. I downloaded them from torrent sites, I've tried three completely different ISOs and all of them have given me the same error message.
so if there's not ubuntu are at least os-es ?
what are they media ? try [gmount-iso ]("apt:gmountiso?section=multiverse")to see what's inside

---

### Post by exploder on 2008-11-12
I am thinking that something got messed up from upgrading. Ubuntu 8.04 had problems burning DVD iso files with Brasero but the native gnome app could get the job done. 8.10 is supposed to have the issue resolved.

My suggestion is to back up your data and do a clean install of Intrepid. At least with a fresh load you will not have a bunch of old libs in the system causing problems.

---

### Post by snkngshps on 2008-11-12
One of the ISOs was the linux-live "Boot n play" dvd. I was also trying to burn some ISOs of homebrew for my wii. I didn't have success with any of them. That sucks if my only option is to format my hard drive and start fresh but I guess that's what I'll have to do.

---

