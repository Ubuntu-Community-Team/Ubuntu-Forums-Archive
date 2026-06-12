---
title: "possible to use Feisty Fawn still?"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by reakin on 2009-01-24
Hi,

All versions of Ubuntu since Feisty Fawn run poorly on my laptop - the touchpad is erratic, the video card conflicts with the linux-rt module, firewire audio runs poorly, etc.  

I tried going back to Feisty Fawn today, after giving up on trying to configure Intrepid.  But, the repositories seem to be no more, so I cannot use apt at all.  Is this so, or is there somewhere where the updates are residing?

Its really amazing how problem free my computer runs on this version (Feisty), and then I switch to anything later, even Gutsy, and I have headache after headache from hardware problems.

regards,
Rich

---

### Post by Pumalite on 2009-01-24
Support is no more.

---

### Post by howefield on 2009-01-24
The feisty repositories are no more, given that this version has reached the end of it's life, (last October I think).

---

### Post by reakin on 2009-02-01
Well this is a sad thing that I have to ditch Ubuntu now because the newer versions are too buggy on my laptop, yet when I first started using Ubuntu things ran great.

I'll try posting my bugs again before, but I cannot take my mouse clicking 1000 times in random places any more.

And the thought of getting Debian Sid working with all my proprietary hardware for audio/music production... there goes a week of productivity.

---

### Post by kostkon on 2009-02-01
Officially the repos are down, but the repositories continue to exist in
```
http://old-releases.ubuntu.com/
```
but, obviously, they are not updated anymore.

Just edit your *sources.list* file to point to the new url. To edit your *sources.list* file, open a terminal and do
```
gksudo gedit /etc/apt/sources.list
```
when you finish, in a terminal again, do a
```
sudo apt-get update
```

---

### Post by reakin on 2009-02-02
Okay, that is what I was hoping.  From there I can compile what I need from source (without having to update everything).

I'm currently trying out Sid, ahh the things that Ubuntu makes so easy that I miss.  But it doesn't have the same bugs that I have noticed in Ubuntu for the last couple years.

regards,
Rich

---

### Post by snowpine on 2009-02-02
Have you checked out Sidux? It's kind of a Debian Sid remix, very easy to use (relatively speaking) and has pretty good hardware detection.

---

