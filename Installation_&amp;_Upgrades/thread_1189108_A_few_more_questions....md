---
title: "A few more questions..."
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by John M2009 on 2009-06-16
Im running the Live CD at the moment,  and all seems to be going well  apart from a few things.  I tried playing an mp3,  and it said I need ti install a plugin?  I would have thought that would come as part of the installation?  Also,  when i tried installing it last night,  I was given a list of several file systems to format my disc,  most of which I have never heard of,  which one should I use?  And something that a friend just told me on msn,  that has got me REALLY worried, is that Ubuntu is command line based,  im just wondering what kind of things I will have to type commands for,  because so far,  Its been plain sailing with no horrible Linux commands to enter.  I dont know Linux and I think I would be pretty stuck if it came to having to use commands.  I need reassurance here!

---

### Post by Amilo1718 on 2009-06-16
just go with the flow of a new experience ;)
the gui has some powers, but the ultimate power is in the command line
in the beginning you don't need it...
but after a while you will want to learn it :D

for the partitioning... do you want to keep files => backup
for the mp3... have you installed ubuntu or used the live-cd?

---

### Post by John M2009 on 2009-06-16
for the partitioning... do you want to keep files => backup

All my files are backed up on an external drive,  plus they are also on my windows partition,  I have an empty partition ready for installation of ubuntu

for the mp3... have you installed ubuntu or used the live-cd?

Im using the Live cd at the moment

---

### Post by kestrel1 on 2009-06-16
> **John M2009 said:**
> for the partitioning... do you want to keep files => backup

All my files are backed up on an external drive,  plus they are also on my windows partition,  I have an empty partition ready for installation of ubuntu

for the mp3... have you installed ubuntu or used the live-cd?

Im using the Live cd at the moment
As you are using the live CD, you could have problems playing MP3 files, but once you get Ubuntu installed you will want to install the Ubuntu-restricted-extras with the following command:```
sudo apt-get install ubuntu-restricted-extras
```
That will download & install various things along with a lot of codecs.

---

### Post by Amilo1718 on 2009-06-16
so you want a dual-boot & don't know what the content of the different partitions is... right?
& for the mp3... i personally never tried a live-cd for audio purposes...
just to see what the display did, the other things can easily be explained after an installation... this forum is very helpful ;)

---

### Post by raymondh on 2009-06-16
> **John M2009 said:**
> Im running the Live CD at the moment,  and all seems to be going well  apart from a few things.  I tried playing an mp3,  and it said I need ti install a plugin?  I would have thought that would come as part of the installation?  Also,  when i tried installing it last night,  I was given a list of several file systems to format my disc,  most of which I have never heard of,  which one should I use?  And something that a friend just told me on msn,  that has got me REALLY worried, is that Ubuntu is command line based,  im just wondering what kind of things I will have to type commands for,  because so far,  Its been plain sailing with no horrible Linux commands to enter.  I dont know Linux and I think I would be pretty stuck if it came to having to use commands.  I need reassurance here!

Hello John M,

Playing a sound/video file will require installing those extra files needed to play various restricted, non-free formats ... as you have now discovered.  It is no hassle to install those to a base install as you'll have the medibuntu repository to get it from.  I don't think that the repository in included in the liveCD.

As for file format, general use is EXT3 which has proven stable.  Some have had success with EXT4 which is faster, but less tested compared to EXT3.

On command line ... YES and NO.  Ubuntu now has various GUI's and managers to assist the user in his/her workings, tweakings, installations etc.  It also has the Terminal which I believe, when proficiently used, is still much faster than the GUI.  So yes, Ubuntu/linux is command line "able" but NO, it is not entirely command line because of the GUI's and managers we have now.

There is a learning curve, John.  And the learning curve may be steep ... depending on how you deal with it.  Remember the learnings you had to go through when you first started with the OS you are using now?  The good thing about Ubuntu is that there are a lot of tutorials specific to ubuntu in the forum as well as the collective talents and skills of about 80,000 members.

May I suggest that you play around with the liveCD some more.  If you decide that Ubuntu is worth your try, set-up a dual-boot configuration so you may have your working, accustomed OS as while learning Ubuntu.  In a dual boot scenario, you can keep the OS you have as your main system until you are comfortable in Ubuntu.

Some more readings for you.

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

As you peruse the forum, you will notice a lot of HOW-TO's and stickies which can be valuable in your learning.

Good luck and have fun with the liveCD :)

---

### Post by Therion on 2009-06-16
> **John M2009 said:**
> I need reassurance here!
Relax.  Ubuntu is not command line based.  It's a good thing to know, and a trained monkey could use it, but I understand to the uninitiated those two words strike cold terror in the farthest recesses of your heart.  Deep breath.

Certain codecs (like those for .mp3) can not be included by default on the LiveCD, or even a default install of Ubuntu, due to legal restraints.  Fear not... The codecs are few keystrokes away and available without having to use the dreaded command line.

[B]
EDIT:[/B]

Oh, and download QuickStart: [http://quickstart.freeforums.org/quickstart-download-pics-t2.html](http://quickstart.freeforums.org/quickstart-download-pics-t2.html) -- It's the Ubuntu n00b's bestest friend.

---

### Post by sanumala on 2009-06-16
Add Mediabuntu repositories by following step by step instructions at 
 
[http://ubuntulady.wordpress.com/2009/02/02/jaunty-has-been-added-to-medibuntu/](http://ubuntulady.wordpress.com/2009/02/02/jaunty-has-been-added-to-medibuntu/)
 
 
After adding mediabuntu repository 
 
click ALT+F2---> type --> ```
gnome-terminal
``` and there
 
Run following two commands. That will install realplayer for you. I use realplayer for mp3 playback
 
```
 
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install realplayer

```

---

### Post by MaWaLe on 2009-06-16
If a persone are not yet sure to put in ubuntu on the hard disk, it can make it with the live USB that let you have a workspace on it. All you have is to make the Live USB on a pendrive with enough space to put the content of the Live CD (700 Mo) and the rest of the space should be marked as a workspace so you can install and save your workdone on it.

Personnaly i always advice people to put Ubuntu as THE operating system by default on their machine and if they still need Windows for some use (i doubt that it will be the case if they try Ubuntu :p ), they should virtualize it with virtualbox.

---

