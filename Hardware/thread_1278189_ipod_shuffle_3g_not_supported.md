---
title: "ipod shuffle 3g not supported?"
date: 2009-09-29
forum: Hardware
---

### Post by dmos on 2009-09-29
hi,
i'm new to the forums and linux. so far i love both^^
only downside is that i cant get any players to see my ipod shuffle 3g (yes, the little beauty:) ). as far as i can tell it mounts. i can see the icon on the desktop and everything but that's just about it. it seems as rhythmbox comes closest to communicating with my ipod - i can see my ipod's name on the left (in rhythmbox) but when i click it, it doesnt show any songs on it.
im not sure if this is related but i would usualy put my mp3 in through a windows machine.

---

### Post by Paul41 on 2009-09-29
I have not used a shuffle so unfortunately I won't be much help, but I can say that using it with a Windows machine is not a problem. iPods are formatted in fat32 for use in Windows which is also what Linux (Ubuntu) uses.

---

### Post by dmos on 2009-09-29
[IMG]http://img18.imageshack.us/img18/3360/screenyqc.jpg[/IMG]
This is Banshee^^. I tried a dozen other players and none of them even tried telling what's the problem, but not Banshee. I hope this helps others with the same problem.

EDIT:** Actually (after rebuilding) when i tried to use my ipod it said please sync with itunes and doesnt play. so ****. oh and before i forget: the database rebuild killed all of my playlists too, songs are still there though and i can see them when i hook it up, but i can't listen to them through the ipod.**

So i reached the conclusion that _linux_ so far _doesn't support shuffle 3g_.

Prove me wrong. I beg of you.

---

### Post by echoesofury on 2010-01-04
I managed to get my ma's iPod shuffle 3g to work with Ubuntu, but I had to use a PC...so if you have access to one but all your music is on the Linux machine (or have a friend who would let you use their computer for 10 seconds) you can try this.

1) Boot up iTunes on the PC and make sure it is not set to sync automatically. 
2) Plug the Shuffle into the PC. It will ask you to register your iPod and give it a name. Follow the instructions and wait for it to say "Your ipod is up to date", then eject it (or safely remove)
3) Now go to your Ubuntu computer, and plug it in. Ubuntu should detect the iPod and add an icon to your desktop.
4) I'm assuming you have your music loaded into Rhythmbox already (or you can use another program like GTKPod). Just drag the music from the box on the right to your iPod on the left. Safely eject the iPod again, then go back to the PC one last time.
5) Plug in the iPod and boot up iTunes. Your iPod should show up on the left. Click on it's name and verify that the songs are displayed in iTunes.
6) Enjoy!

I realize this is a very convoluted way of doing things, and requires the use of a PC, but it allowed me to get all the music from my Linux computer to the iPod at least (I'm a Linux newb). From what I have read, the problem is with the song database (it changed between the 2g and 3g.) which isn't supported by any of the music management software for Ubuntu yet. I'm sure it will just take some time to get that working -- but I'm impatient! :P

---

### Post by Floola on 2010-03-12
Floola 5.5 now supports shuffle3G.

Visit [http://www.floola.com](http://www.floola.com)

---

### Post by johneboy on 2010-08-11
I'm running 10.04 (Lucid) and would just like to say that echoesofury's tip worked for me. To re-iterate:

1) Plugged a brand new iPod shuffle 3g into my Ubuntu laptop, Rhythmbox wouldn't register it as it did the 2nd gen shuffle I had. I was presented with a dialog asking me for information, however the iPod version list box was disabled. 
2) Plugged the new iPod into my colleague's MacBook and fired up iTunes
3) Set a name for the iPod and turned off automatic synchronisation and text to speech functionality.
4) Eject the iPod
5) Plugged it back into my Ubuntu box and hey presto it shows up correctly in Rhythmbox and I can now synchronise my music

---

### Post by Neobuntu on 2010-12-30
Um. This is BS. If a new Shuffle doesn't do text to speech, talking of the titles, then it does not work!

I have two Shuffles, both made in Sept, and are December 2010 gifts. Model A1373. Which are, I think, "3G", or Third generation.

I had them partly working (downloaded a new Control folder, and Floola); but not all songs converted. When I then tried Rhythmbox, IT TRASHED THE DATABASE! Same with gtkpod. I'm on 10.05 Ubuntu.

Anyone who thinks Apple is competing fairly, is an idiot! This is solely the cause of, purposeful, and non-standard version changes.

You are never going to be able to explain, this backwards tech, to the average person. Apple wins. You can forget that.

Best course of action, is to tell people, your real portable player, also does FM Radio, and all you do, is drag your free MP3 files onto it. It cost half the price. It's more, for less.

Apple is less, for more. Always has been. Always will be.

Friends don't give friends, Apple stuff. Just look what happened to Adam and Eve!

Prove me wrong, I dare you.

---

