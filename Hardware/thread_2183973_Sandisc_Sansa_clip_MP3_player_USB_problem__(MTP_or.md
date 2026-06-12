---
title: "Sandisc Sansa clip MP3 player USB problem  (MTP or MSC) 2013 version"
date: 2013-10-27
forum: Hardware
---

### Post by Finn bjerke on 2013-10-27
The new version of this litle MP3 player has 3 modes for USB filke transfer, however its not really working unless you know this trick. You have to "hardware force" the MP3 into MSC mode 

USB Modes
There are two USB modes used for connecting to MP3 players to computers:[INDENT] &#8226; Mass Storage Class (MSC)
&#8226; Media Transfer Protocol (MTP)
 [/INDENT]
Windows systems support both MSC and MTP mode. Mac systems only support MSC mode. 

MTP Mode
I use Ubuntu 13.04 and set the MP3 to MTP mode  I can "see" the MP3 and appearantly I can copy files to the device, but nothing happens. No files are tranferred, 
MSC mode
I use Ubuntu 13.04 and set the MP3 to MSC mode  I still have problems.
Autodetect mode:
I use Ubuntu 13.04 and set the MP3 to autodetect mode  I still have problems.


So you "hardware force" the MP3 into MSC mode[INDENT]Mounting the Sansa View in MSC Mode:
To  mount the device in MSC mode, you put the device in hold (slide the  power switch down) and then hold down the left button on the direction  pad for about 5 seconds and then connect it to your USB port. The device  should then auto mount into '/media/Sansa View' as a flash drive and an  icon should show up on your desktop.

[/INDENT]
[http://www.micahcarrick.com/sansa-view-ubuntu.html](http://www.micahcarrick.com/sansa-view-ubuntu.html)


You can make playlists in EASY TAG which is a nice little programme (NOT Rhytmbox or VLC)  its a little tricky but possible. New thread about that. 

PROBLEM:
If you use another PC for file transfer the folders are locked, you have to repeat trick mentioned above.

IF you have found other less complicated solutions please write about it here.  Using MSC gives more options since Ubuntu 1304 "sees" MP3 player as a flash drive. 


This works. 
More info [http://kb.sandisk.com/app/answers/detail/a_id/162/~/mtp-or-msc](http://kb.sandisk.com/app/answers/detail/a_id/162/~/mtp-or-msc)




of this little mp3 player [IMG]http://cdn.ubergizmo.com/photos/2009/8/sandisk-sansa-clip-plus-468.JPG[/IMG]

---

### Post by Yellow Pasque on 2013-10-27
Very useful. Thank you.

Be gentle with the headphone jack when inserting/removing the headphones and don't apply pressure on the side of the headphone plug when inserted. I have a couple Clips that are bricked because of shoddy soldering on the headphone jack (and trying to do a self fix didn't work too well because I'm somewhat ham-fisted). It's a shame that the little issue ruins an otherwise great mp3 player :(

---

### Post by Tom_ZeCat on 2013-10-27
I have a Sandisk Clip.  Thus far I've needed to boot my dual boot system (Kubuntu/Windows 7) into Win 7 to be able to put my ogg files onto the Clip.  I did find under the Clip's settings menu where to set the Clip to MSC.  Is that what you mean by hard setting it?  

However, I'm not having any luck in Kubuntu (13.10)  A little menu pops up offering to open the Clip's files with Dolphin.  I do so and can surf into the folders on the device, but I don't see any of my files.  Most are OGGs, but some are MP3s.  I also tried with Krusader without any luck.  Same deal with Nautilus.

---

### Post by Yellow Pasque on 2013-10-27
If you use MTP to put files on a player (which is probably what you used with Windows), then you won't be able to see those files using a file browser. I find it better just to format the player's disk and start fresh only using MSC.

---

### Post by Tom_ZeCat on 2013-10-28
> **Temüjin said:**
> If you use MTP to put files on a player (which is probably what you used with Windows), then you won't be able to see those files using a file browser. I find it better just to format the player's disk and start fresh only using MSC.

Okay, thanks for that info.  I thought of one other thing.  These sound files (most of which are OGG) are an a Micro SD card in the expansion slot.  I wonder if it would work to format the card in a card reader and then copy the files over to it.

---

### Post by Finn bjerke on 2013-10-31
FIrst and foremost:

two possible formats MTP or MSC.  More about that later, try MSC in Ubuntu first becouse it works.
1 . MSC format is for MAC / LINUX if you choose that you will need to do the hardware trick, it will take 5 seconds of your time.  
1a press power 
1b press left arrows 5 secunds display goes out
1c insert USB cabel mp3 display is on again. NOW you can manipulate, copy, make playlists etc. 
2. Deleted files should be deleted in the trash folder on the mp3 or the trashfolder in nautilus. 
3. Dont forget to use the unmount function in nautilus

PS for managing files KRUSADER (what a name...) is very good if you know the filestructure of Ubuntu. 

Playlists:
Ill make another thread obout it but you need easy tag, other programmess can not do it. 



[IMG]http://www.bigplayground.dk/blog/wp-content/sandisk-sansa-clip-plus-dap.jpg[/IMG]

---

### Post by Finn bjerke on 2013-10-31
FIrst and foremost:

two possible formats MTP or MSC.  More about that later, try MSC in Ubuntu first becouse it works.
1 . MSC format is for MAC / LINUX if you choose that you will need to do the hardware trick, it will take 5 seconds of your time.  
1a press power 
1b press left arrows 5 secunds display goes out
1c insert USB cabel mp3 display is on again. NOW you can manipulate, copy, make playlists etc. 
2. Deleted files should be deleted in the trash folder on the mp3 or the trashfolder in nautilus. 
3. Dont forget to use the unmount function in nautilus

PS for managing files KRUSADER (what a name...) is very good if you know the filestructure of Ubuntu. 

Playlists:
Ill make another thread obout it but you need easy tag, other programmess can not do it. 



[IMG]http://www.bigplayground.dk/blog/wp-content/sandisk-sansa-clip-plus-dap.jpg[/IMG]

PS: I have not formattede the MP3 using Ubuntu Gparted, maybe I should try that?

---

### Post by Finn bjerke on 2013-10-31
Well it works without formatting from Ubuntu so I decided agaoinst it. If it works dont fix it.

---

