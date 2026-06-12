---
title: "HP dv9500 sound problems"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by Meizulo on 2008-04-10
I have been reading a lot of the forums that deal with this issue and am overwhelmed and confused at this point. Can someone please shed some light on what exactly I have to do to get the sound working for this laptop?

Ben

---

### Post by Meizulo on 2008-04-10
I am running 7.10

---

### Post by Meizulo on 2008-04-10
Anyone have any ideas????

---

### Post by JimmyBEng on 2008-04-13
the short version is install the latest version of ALSA.  The version in the gutsy repositories isn't new enough to support the laptop.   this is what fixed the problem for my dv9500.

you said you have looked through the forums, so you may have figured that out already.  I will look around and see if I can find some more detailed instructions.  I will post what i find.

---

### Post by JimmyBEng on 2008-04-13
I have found something that i think wil be slightly easier for you, and at least worth a shot.  instead of recompiling and installing the newer ALSA modules yourself, there is a package in the backports repo that has them.

**Instructions:**
1 - enable the backports repo
1.1 - open sources.list
```
sudo gedit /etc/apt/sources.list
```
1.2 - uncomment the following line (delete any '#' at the beginning of the line)
```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
```
1.3 - save and close the file

2 - update repository information
```
sudo apt-get update
```

3 - install the backports modules package
```
sudo apt-get install linux-backports-modules
```

Here is the reference where i got this idea.
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

I haven't tried this, but that's because I got sound working long ago, and don't want to mess with it again until I upgrade to hardy after the release.

---

