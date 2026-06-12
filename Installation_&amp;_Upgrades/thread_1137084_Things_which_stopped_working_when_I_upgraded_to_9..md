---
title: "Things which stopped working when I upgraded to 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Last Tango on 2009-04-25
First, I was using Ubuntu Studio 8.10, but when I upgraded it to 9.04 a LOT of stuff stopped working, so I decided to fresh install Xubuntu 9.04 to my / partition (my /home is on a separate partition)  Which for the most part went smoothly.

So, problems:
#1
Amarok ugraded to Amarok 2, and global hotkeys no longer work except when the Amarok window is open and in focus, so the 'global' part pretty much doesn't work.

#2
Flash stuff still displays, but with no sound.  I can watch youtube and hulu, but I can't hear anything.

#3
Firefox freezes up a lot.

#4
My computer has this miserable Intel GMA950 integrated video card.  By some miracle, before upgrading from Ubuntu Studio 8.10 to 9.04, the card was working well enough to play Warcraft 3 on medium-low video settings without any problems, although the sound never worked (but that's not a problem).  Now, when I open Warcraft 3, a lot of textures display glitchy (black water on title screen etc.,) and the display is really choppy.  I've tried switching to different resolutions, but nothing helps, and often when I try changing the resolution it moves the display so that I can only see the top right quadrant of what it's supposed to display being shown on the bottom left part of the screen.

---

### Post by Convert on 2009-04-25
Better than me...Amarok won't play anything.  It just runs through my 216 songs in about 8 seconds, thinking it is playing them.  No play, no sound, nothing.  And this is with a generic install of 9.04 (I haven't changed anything except to add Amarok and the mp3 codec).

---

### Post by Alex Deez on 2009-04-25
Yeah Amarok won't play anything for me either.  Also, Amarok 2 seems pretty terrible compared to Amarok 1.  Anyone know of a way to run Amarok 1 instead?

---

### Post by kb2tfa on 2009-04-25
Me to no sound anymore. that's a huge bug

---

### Post by Last Tango on 2009-04-26
> **Alex Deez said:**
> Yeah Amarok won't play anything for me either.  Also, Amarok 2 seems pretty terrible compared to Amarok 1.  Anyone know of a way to run Amarok 1 instead?
Agreed.   The new interface is full of clutter that wasn't there before and all of the artists that I had grouped under Various Artists are now displaying in the regular list.  Also, when I first upgraded (now there's an inaccurate description) to version 2, It wouldn't start playback, 4/5 of the time doing nothing and then occasionally giving me some error about 'too many errors in playlist' or somesuch nonsense.  I don't remember how I fixed that, but it involved a lot of google searches and reinstallations of Amarok.  I'd still probably rollback the changes if I knew how though.

---

### Post by JPBodner on 2009-04-26
I'll add my 2 cents as well.  No sound in Amarok or in Firefox.  Rhythmnbox and test tones work fine.  Lots of playing with alsamixer hasn't fixed it.

---

### Post by fishwebby on 2009-04-27
I had the same problem with sound after upgrading from Xubuntu 8.10 to 9.04 - however I think I've found a fix for it. A new item "aumix" has appeared in the "multimedia" menu (I've got my system in Spanish so it might have a different name in English). You can also run it by typing "aumix" at a command prompt. A text interface to set sound options appears, the first of which is the volume, which was set to zero (all the way to the left) for me. I moved it to the right using the right cursor key, and that got my sound working. Press q to exit from the app.

I hope this helps,

Cheers
Dave

---

### Post by xiii_stephan on 2009-04-27
I resolved the problem with sound by **sudo /etc/init.d/alsa-utils start**. It seemed that it did not autostart after the upgrade. Everything worked just fine on the next boot.

As for amarok 2.0 I did not manage to get any sound out of it. I personally dislike amarok 2.0 so I downgraded to amakor 1.4. I suspect this has something to do with xine.

As for aumix I deleted it since there already was an alsa mixer in my xubuntu, no need for another one.

---

### Post by xiii_stephan on 2009-04-27
If anyone wonders how to roll back to amarok 1.4, have a look at this:
[http://ubuntuforums.org/showpost.php?p=6961716&postcount=74](http://ubuntuforums.org/showpost.php?p=6961716&postcount=74)

I used the solution from here:
[https://edge.launchpad.net/~bogdanb/+archive/ppa](https://edge.launchpad.net/~bogdanb/+archive/ppa)

---

### Post by Last Tango on 2009-04-27
> **xiii_stephan said:**
> If anyone wonders how to roll back to amarok 1.4, have a look at this:
[http://ubuntuforums.org/showpost.php?p=6961716&postcount=74](http://ubuntuforums.org/showpost.php?p=6961716&postcount=74)

I used the solution from here:
[https://edge.launchpad.net/~bogdanb/+archive/ppa]("https://edge.launchpad.net/%7Ebogdanb/+archive/ppa")
Thanks!  Usually I'm not so strongly opposed to drastically different new versions of stuff, but Amarok 2 seems to have destroyed everything that I liked about Amarok 1.4

EDIT: okay, so 1.4 installed with no problems, but it doesn't show up on the App menu that is accessed by right clicking the desktop in xcfe, which is my sole means of launching applications right now (something which pleases my computer-OCD greatly).  Is there somewhere I can edit what it shows?  Rhythmbox is installed, and also doesn't show up there.

---

### Post by nevernamed on 2009-05-06
I am having a similar problem.

When I first upgraded to ubuntu 9.04, Flash did not work at all and I had to install a new flash plugin. The last couple of nights, I've been getting the flash videos (like on youtube) to play, but with no sound. However, Rhythmbox worked fine.

Today, flash animations are just dandy and Rhythmbox "plays" the songs in my library, except without sound. Listen Music Player does that thing where it plays all the songs in your library really fast.

Has anyone had any conclusive results?

---

### Post by Last Tango on 2009-05-06
For me, getting rid of the open-source flash thing and replacing it with the sun-microsystems one for linux seems to have fixed the problem.

---

### Post by nevernamed on 2009-05-06
> **Last Tango said:**
> For me, getting rid of the open-source flash thing and replacing it with the sun-microsystems one for linux seems to have fixed the problem.

It fixes the whole flash issue, but not the issue with the media players.

---

### Post by bobbiescap on 2009-05-06
Well I lost USB pendrives,USB headset, NVidia graphics driver, lots of hair, time and patience. But I still like it. I ditched Ubuntu a while ago because of these problems with upgrading and decided to give 8.10 a try. 

I liked it and made it my main distro but now have this crap with upgrading to Jaunty. 

Get it right please guys or you are going to put a lot of people off, you put the upgrade fair in people's faces and when they do the computer doesn't work like it did. 

There must be a better way - like try Mandriva, openSUSE, Sabyon etc.

---

### Post by nevernamed on 2009-05-10
> **bobbiescap said:**
> Well I lost USB pendrives,USB headset, NVidia graphics driver, lots of hair, time and patience. But I still like it. I ditched Ubuntu a while ago because of these problems with upgrading and decided to give 8.10 a try. 

I liked it and made it my main distro but now have this crap with upgrading to Jaunty. 

Get it right please guys or you are going to put a lot of people off, you put the upgrade fair in people's faces and when they do the computer doesn't work like it did. 

There must be a better way - like try Mandriva, openSUSE, Sabyon etc.


Gee thanks. That was helpful.

---

### Post by shimi on 2009-05-12
Look at these cases. 
The first case is about [sound problems with Flash and audio files after upgrading from ubuntu 7.10 to 8.04]("http://mylinuxnotebook.blogspot.com/2008/07/ubuntu-sound-flash-problem.html") 
The second case is a similar [sound problem after upgrading from ubuntu 8.04 to 8.10 and after installing 9.04]("http://mylinuxnotebook.blogspot.com/2008/11/ubuntu-810-flash-sound-problem.html").

---

### Post by nevernamed on 2009-05-12
I have come to the conclusion that the sound works just fine UNTIL I use flash. Then it doesn't anymore.

---

### Post by ezsit on 2009-05-12
I knew there was a reason not to upgrade to Jaunty. I'm sticking with Intrepid until Koala comes along and then test it thoroughly before updating anything. Thanks for all the warnings.

---

### Post by nevernamed on 2009-05-12
> **shimi said:**
> Look at these cases. 
The first case is about [sound problems with Flash and audio files after upgrading from ubuntu 7.10 to 8.04]("http://mylinuxnotebook.blogspot.com/2008/07/ubuntu-sound-flash-problem.html") 
The second case is a similar [sound problem after upgrading from ubuntu 8.04 to 8.10 and after installing 9.04]("http://mylinuxnotebook.blogspot.com/2008/11/ubuntu-810-flash-sound-problem.html").


With the first "solution" I ran into this:
```
Package libflashsupport is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libflashsupport has no installation candidate
```

The second one talks about a "flashplugin-nonfree-extrasound".

What is this? And I think it will only help with the flash player... which seems to be working fine for me. It's system audio and music that I'm having trouble with.

---

