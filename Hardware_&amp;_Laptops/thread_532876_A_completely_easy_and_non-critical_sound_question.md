---
title: "A completely easy and non-critical sound question"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by wyth on 2007-08-23
Hiya -- this one should be a snap, and isn't critical.

Ever since I started using ubuntu/kubuntu, every time I fire up my laptop, the sound is very quiet and tinny.  I click on the mixer, slide the master and the pcm up and down, and it's back to perfect (sometimes it takes the master, sometimes the pcm).  

I can't recall if this happened on other distros -- I've been pretty much with k/ubuntu for a few years now -- but I believe so.  It happens in both Gnome and KDE. 

It's not a huge thing, it's just a weird thing that I'm curious about.

Any thoughts?

---

### Post by heimo on 2007-08-23
You could try to run this command after you've setup your volume levels as you want it. 
```
sudo alsactl store
```

I've seen a bug report about "alsactl restore" not always working correctly, that's the command which should restore your audio settings after boot.

---

### Post by wyth on 2007-08-24
RIGHT ON -- that seemed to do the trick.  Thanks man, I knew it'd be a snap.

Cheers,
wyth

---

### Post by wyth on 2007-08-28
heimo's trick worked for one reboot, but I'm back to no sound when I boot up.  When I fiddle with the PCM or Master volume in the mixer, it always comes back -- it just won't save those settings.

---

