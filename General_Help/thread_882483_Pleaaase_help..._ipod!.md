---
title: "Pleaaase help... ipod!"
date: 2008-08-07
forum: General Help
---

### Post by Ishwar15 on 2008-08-07
Backstory: I got an ipod 2 years ago and used it for sometime. The hard drive on my laptop at that time also corrupted somehow and I lost all the music. Lucky for me, I had all the music on my ipod. I thought I was lucky.

Fastforward a few months, the software on my ipod had corrupted...I never put the music from my ipod back onto any sort of hard drive. Since then, I've just kept this slow moving, always freezing ipod and used it as best I could without any music backup anywhere.



Where we are now:
I installed Ubuntu yesterday and I'm no tech-y person, I just heard good things and I love how fast and smooth it is. So, anyways, I plug in my ipod with the longshot that it might work and all of a sudden, I can access the songs on my ipod through rhythmbox (I've never been able to do this through iTunes) and I see the ipod show up on the desktop. 

Here's my question: How can I get this music onto my hard drive? I have an external hard drive as well as the one with my computer. I'll do anything to save this music somewhere and re-format my ipod so it'll finally work again. 

Remember, I'm not a real tech-y guy. All help is greatly appreciated!

---

### Post by loboc on 2008-08-07
the gtkpod package might let you take the songs back off

---

### Post by dreadmeat on 2008-08-07
can you not just drag the files from the ipod to the desktop [or folder of your choice]?
double click the desktop icon to open it.
remember you have to mount stuff in linux if you want to 'access' it
sounds like it is if rhythmbox opens the files.

libgpod3 may work too.

---

### Post by Ishwar15 on 2008-08-07
Two posts above me:How do I go about trying that out? 

To the poster above me: this is currently what I'm doing. It just takes a long, long time. I guess it's a good option though. 
First thing I thought of was to just copy the ipod hard drive over to my external hard drive...but copying 30GBs takes foreverrr

---

### Post by mb_webguy on 2008-08-07
Open the terminal and type "sudo apt-get install gtkpod-aac".

---

### Post by dreadmeat on 2008-08-07
in your menu find "synaptic package manager" it's like a really intense add/remove software.

you could use the command line

cp -r -v *ipod location* *new location*
copy recursively verbosely from x location to x location
[http://linuxcommand.org/lts0050.php#cp](http://linuxcommand.org/lts0050.php#cp)

---

### Post by loboc on 2008-08-07
> **Ishwar15 said:**
> Two posts above me:How do I go about trying that out? 

To the poster above me: this is currently what I'm doing. It just takes a long, long time. I guess it's a good option though. 
First thing I thought of was to just copy the ipod hard drive over to my external hard drive...but copying 30GBs takes foreverrr

AN IPOD LIBRARY IS RANDOMLY ENCRYPTED WITH A DATABASE SO ALL YOUR SONGS ARE GOING TO BE GARBAGE IF YOU JUST DIRECTLY COPY THEM FROM THE MOUNTED DRIVE.  The mounted drive represents the portion of the ipod not used for music that is still available its got folders in in for Contacts and Calendars etc but the Data and Ipod_control folders are where the music is and its not in there as tim-song.mp3 its in there as akadflsahfhsagfhsdgh


Have you ever installed a program from the repositories

open a terminal and type

```
 sudo apt-get install gtkpod 
```

if that doesnt work amarok has ipod support that letes you copy songs back to your computer


```
 sudo apt-get install amarok 
```

amarok is a great all around mp3 player which is better than rhytmbox in my opinion

---

### Post by Sinkingships7 on 2008-08-07
You can drag the music from the iPod section in Rhythmbox directly into the label titled "Music" on the left panel of Rhythmbox.

---

### Post by loboc on 2008-08-07
> **Sinkingships7 said:**
> You can drag the music from the iPod section in Rhythmbox directly into the label titled "Music" on the left panel of Rhythmbox.

Does this copy th files to the ~/Music Directory or does it add the songs to the Rhythmbox library requiring the the presence of the ipod to play them
?  
I guess i can try it

---

### Post by Ishwar15 on 2008-08-07
oooooh thank you guys, i'll try this out and come back here with how things are working.

---

### Post by loboc on 2008-08-07
> **loboc said:**
> Does this copy th files to the ~/Music Directory or does it add the songs to the Rhythmbox library requiring the the presence of the ipod to play them
?  
I guess i can try it

It total makes a copy of it in ~/Music 

Please mark solved

---

### Post by Ishwar15 on 2008-08-07
Ran into a problem right away in the terminal...

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

??

---

### Post by dreadmeat on 2008-08-07
> **Ishwar15 said:**
> Ran into a problem right away in the terminal...

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

??**dpkg --configure -a** is exactly what you type into the terminal =)

---

### Post by loboc on 2008-08-07
> **Ishwar15 said:**
> Ran into a problem right away in the terminal...

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

??
```

sudo apt-get update
sudo dpkg --configure -a
```

then 
```

sudo apt-get update && sudo apt-get dist-upgrade 
```

to get all the new hotness

By the way rhythm box totally does what you want it to I attached a picture.  The songs will end up in /home/yourname/Music or ~/Music for short

The noob is a little harsh I didnt know rhytmbox had this built in. I am an amarok user and i highly recommend it just for the interface, it doesnt try to copy itunes. just cuz apple made it did doesnt mean its good. 

Case in point you had no idea it could do this looking at it.  In amarok I right clicked on the ipod playlist and in the context menu it had a Option: Copy to Collection

---

### Post by dreadmeat on 2008-08-07
loboc is awesome @ gimp :p

---

### Post by Sinkingships7 on 2008-08-07
loboc: You have the same taste in Music as me :D

---

### Post by /////// on 2008-08-07
If none of this works, you can try downloading a shareware program called 'Music Rescue'. Install this via WINE and follow the instructions to get your music off your iPod.

Hope this helps

---

### Post by loboc on 2008-08-07
> **Sinkingships7 said:**
> loboc: You have the same taste in Music as me :D

[http://last.fm/user/loboc](http://last.fm/user/loboc)

---

### Post by Ishwar15 on 2008-08-07
I appreciate the help. Again, i'm moving 30 gigs of music from my ipod and right now, it says it's 11 tracks through meaning 6248 remaining... 

It's been on 11 for a while now, though.

---

### Post by Sinkingships7 on 2008-08-07
> **loboc said:**
> [http://last.fm/user/loboc](http://last.fm/user/loboc)

And that confirms it. I listen to almost every band in your Library. Bright Eyes, Coheed, and Brand New, I'm huge fans of. Only like one song by the Get-Up kids. Death Cab and TBS are a big YES. Along with Saves the Day.

And Fall Out Boy is my favorite band :guitar:

---

### Post by Sinkingships7 on 2008-08-07
> **Ishwar15 said:**
> I appreciate the help. Again, i'm moving 30 gigs of music from my ipod and right now, it says it's 11 tracks through meaning 6248 remaining... 

It's been on 11 for a while now, though.

Sometimes, it gets stuck because Rhythmbox doesn't quite have that technology down. As someone mentioned above, gtkpod should be more cut out for this kind of task, though I've never used it myself.

---

### Post by loboc on 2008-08-07
made me get on last and realize i had an awful picture of myself up, those kind of things belong on facebook.  If the one song you like by the get up kids is slow and acoustic you should check out the new amsterdams if the song is fast and synthy you should check out reggie and the full effect

---

### Post by loboc on 2008-08-07
> **Sinkingships7 said:**
> Sometimes, it gets stuck because Rhythmbox doesn't quite have that technology down. As someone mentioned above, gtkpod should be more cut out for this kind of task, though I've never used it myself.

If you got the time you could drag the albums one at a time, i didnt realize you had 6000+ songs gtkpod-acc might be the most up to date version with support for the most ipods

---

### Post by Ishwar15 on 2008-08-07
Sorry to be a complete moron with this stuff here, but apart from the terminal stuff, how do i use gtkpod? I'm not really sure what it is/how it works, etc...

---

### Post by loboc on 2008-08-07
> **Ishwar15 said:**
> Sorry to be a complete moron with this stuff here, but apart from the terminal stuff, how do i use gtkpod? I'm not really sure what it is/how it works, etc...

[http://www.gtkpod.org/about.html](http://www.gtkpod.org/about.html)

If it doesnt show up int the menu under sound and video run it from the terminal with

gtkpod&

---

### Post by Ishwar15 on 2008-08-07
Don't have it in the apps menu and when i input that into the terminal, the window simply closes and I'm left with nothing.

---

### Post by loboc on 2008-08-07
I am going to bed good luck even with gtk pod i would break up the transfers into a few albums at a time usb 2.0 or firewire only has so much throughput ,

Use google, learn the Command Line, read and post in the forums and you'll be giving advice in instead of taking it.

---

### Post by loboc on 2008-08-07
> **Ishwar15 said:**
> Don't have it in the apps menu and when i input that into the terminal, the window simply closes and I'm left with nothing.

really?
 hmm
does gtkpod -h show the help stuff?

---

### Post by loboc on 2008-08-07
did that dpkg --reconfigure -a ever complete maybe it didnt get fully installed.  I would try 

sudo apt-get install gtkpod-aac 

If any of your songs were in mp4 (aac) format youll get them.  I cant speculate about songs downloaded from the itunes store as they are DRM sacked and a whole nother kettle of fish

---

### Post by Ishwar15 on 2008-08-07
So both gtkpod and amarok were "freezing" /moving way too slowly, so I just ejected my ipod and gave up on it all. 

One of them erased all the music off my ipod. 

Thanks guys. :(

Edit: Just want to say there's no hard feelings, no one expected this to happen... Just losing my music put me in a really bad mood. I still appreciate all the help.

---

