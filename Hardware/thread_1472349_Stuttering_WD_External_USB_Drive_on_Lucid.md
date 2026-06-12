---
title: "Stuttering WD External USB Drive on Lucid"
date: 2010-05-04
forum: Hardware
---

### Post by mperry on 2010-05-04
This is strange. After never having any issues on Karmic with my WD 250g usb drive formatted as ext3; now with Lucid, the drive stutters when I play music using rythmbox. The disk light starts going bright and not and music just stops. Then it waits for a few moments and it starts playing normally again. I have used this drive for some bit of time now on a variety of systems and have had no problems.

Anyone having issues with USB disconnects when a external USB drive is mounted on a laptop like a Thinkpad T60? 

I'm wondering if the drive is going bad or if there is something I can do with Lucid. I could always just turn off automounting the drives if I felt that was the culprit.

Ideas, suggestions, enlightenment?

---

### Post by hysterix` on 2010-06-21
Hey there!  I'm having the exact same issue as you!

It all started after I upgraded from 8.1 to 9.04; there was the very occasional hiccup or studder when playing music off my external WD hard drive but nothing too noticeable (8.1 played music flawlessly).

The problem really started from 9.04, to 9.1, and now to 10.04.  I have not filed a bug report ever because I see a few there already.  I cannot for the life of me figure out what is going on.

I have tried many different fixes ranging from: totally removing pulseaudio (computer runs faster btw) using alsa instead, using many different music players, changing the priority level on different processes, and a few others I cant really remember.

I've got my system to not do it as much, but it comes and goes randomly.  I'm pretty sure that it is related to having the external hard drive going to sleep (in my instance) because I stress tested mysql and got it to 100% cpu for quite some time and the music did not skip.

Its almost as if the drive is going into sleep mode, and the hiccup is the time it takes for the drive to wake back up and read the next amount it needs.  This begs the question why this never happened with earlier versions of ubuntu?  Seeing as I've been using the same hardware set-up exactly, and have only upgraded software, so I believe it is ubuntu reading the drive that is the problem.

Again, why this never happened with earlier versions is beyond me.
How would someone even go about diagnosing this problem?  

It is amazing how much I rely on music while I work on the computer; once there is a problem with that, it almost stops me totally from productivity.  I'm still using ubuntu of course, but sadly I'm having to play my music off another computer.

If anyone could tell me what I need to do to help provide the proper information to diagnose this problem, I'd love to.  Problem is there is no 'error', so nothing is being picked up in logs (from what I can see).

Any help would be much appreciated.

I just realized this is a two month old thread; perhaps I should make a new post?

---

