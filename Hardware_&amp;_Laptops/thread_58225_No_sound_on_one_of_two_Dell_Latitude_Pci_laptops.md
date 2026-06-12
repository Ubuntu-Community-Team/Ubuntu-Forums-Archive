---
title: "No sound on one of two Dell Latitude Pci laptops"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by sweeneysmsm on 2005-08-19
I installed Ubuntu 4.10 on two Dell laptops – Latitude cpi. I was unable to get sound. The suggestion was made to install the newest version – 5.04. I did that and was thrilled to get sound on the first laptop. They both appear to be identical. 

The second one gives me occasional beeps as it runs through install or shut down, but no sound in terms of events or playing a CD. I repeated the install with the same result.

If I put a music CD in the CD player the CD Player window opens and shows Unknown Artist/Unknown Album with Track listed as 1-Unknown. When I press the Play button nothing happens. The little slider does not move across the window to indicate that it is playing.

If I click on Places/Computer/CD-Rom Drive: Audio Disc, a window titled hdc opens showing the 5 tracks listed Untitled 1, 2, 3, etc. The icon for each indicates a .wav file. If I click on one of them I get a new window titled Cannot Open Untitled 1, etc. The message reads: 

“The filename ‘Untitled 1’ indicates that this file is of type ‘WAV audio’. The contents of the file indicate that the file is of type ‘unknown’. If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself or received the file from a trusted source. To open the file, rename the file to the correct extension for ‘unknown’, then open the file normally. Alternatively, use the Open with menu to choose a specific application for the file.”

Choosing the Open With option, I tried to use CD Player, but got a message that it could not add application to the application database.

I clicked on Applications/Volume Control and got an Error window with a message saying – No volume control elements and/or devices found.

I clicked on Volume Monitor and got an Error windows (vumeter) saying Cannot connect to sound daemon. Please run ‘esd’ at a command prompt. (I would not have a clue as to where to find a command prompt or how to run ‘esd’, but would be willing to try whatever.)

No volume control appears on the top panel.

I did look for help on the forum. 

I guess my big question is how come it all worked perfectly on one laptop and not the other?...

Any insight very much appreciated. 

Mary

---

### Post by leon_mcnichols on 2006-09-24
Basically, you have to modprobe the CS4236 sound driver, rather 
than the NeoMagic 256 one that most sites indicate: 

modprobe snd-cs4236 index=0 id=CARD_0 port=0x530 cport=0x210 
mpu_port=0x330 fm_port=0x388 irq=5 mpu_irq=9 dma1=1 dma2=-1 isapnp=0v 

Then, re-start ALSA and it should work.

---

### Post by Jules01 on 2007-05-11
Hi there

I am no computer expert but i have had a very similar problem in that i could only receive system sounds, but no sound when playing music cds through my cd rom drive.I had same problems trying to run using windows media also. It drove me mad trying to figure this out and eventually i managed to do it. Hooray!.I clicked onto My Computer and then right clicked on the cd drom drive. Then click properties box- click onto hardware and double click the cd rom drive, go to properties and then i had to disable the digital audio playback box. Hey presto it worked!!!.

Hope this helps for future problems too..
Jules x 

:)

---

