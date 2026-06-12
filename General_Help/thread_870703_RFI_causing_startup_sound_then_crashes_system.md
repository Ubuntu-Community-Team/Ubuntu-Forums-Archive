---
title: "RFI causing startup sound then crashes system"
date: 2008-07-26
forum: General Help
---

### Post by bthoward on 2008-07-26
This is a strange issue...

When I transmit with my ham radio rig I end up having issues with my Mythbuntu box.  This is a mythbuntu box with gnome-desktop installed so that I can use it as a desktop and the TV portion is on a second display.  

Anyway the issue is that when I transmit the system ends up playing the startup sound.  (you know the tribal default startup sound thing)...  I have the startup sound disabled and it should never play so I'm not sure how it could possibly be "remotely" triggered.  Right after this sound plays the system locks up completely.  Mouse won't move and the system won't respond to remote connections.  

This system has zero issues when booted into Windows.  This is the same system in the same location with no change other than the fact that its booted into Windows or Linux.  

I have installed ferrites around the coax at the antenna.  I have installed ferrites on ALL cables entering the PC.  I have added RF gasketing material to the enclosure.  The entire system is well and properly grounded.  I'm not sure what to do from here but I'm certain that is some sort of strange BUG in Ubuntu as it ONLY has this problem when booted into the Linux install.  Unfortunately I never use the windows partition as this is the MAIN backend for the whole house.

---

### Post by Kevbert on 2008-07-26
That's an interesting problem.  I'd have thought that the RFI would effect both Windows and Linux as computers and transmitters aren't supposed to mix.  Some things you could try.  It you have loads of long (unused) connecting cables, try bundling the excess in a figure of 8, and use a cable tie or something similar to hold it in place.  This will cancel out any radiation on the cables.  Another thing that may help is a mains filter preferably to the PC.

---

### Post by bthoward on 2008-07-26
All cables have been properly bundled and have been kept to a minimum.  The ferrites installed at the PC does MUCH more to remove common mode radio interference than good cable management would.  

I'm an electrical engineer and work with RF quite often.  I've gone to greath lengths to minimize RFI to the computer.  There are 3 other computers in the same room running Mandriva with no troubles to any of them.  This box while running Windows has no problems yet when running Ubuntu it has a problem.

---

### Post by bthoward on 2008-07-27
Just figured out that transmitting on 80 meters 3.5 to 4 Mhz results in the computer playing the startup sound everytime.  If I start a long bit of morse code transmission it waits until I'm done but once I'm done it plays the startup sound.  However it doesn't crash when I transmit here.  I'm only using 10 Watts here.  On 40 meters 7 to 7.3 Mhz I have fewer problems and so far on 20 meters 14.0 to 14.35 Mhz it seems to be the worst. 

Seems very odd that I can VERY consistently make the computer play the startup sound even when that sound is completely disabled and the "Play System Sounds" box is unchecked.  Even just one dit (a couple hundred milliseconds at worst) causes this sound to play EVERY time.

---

### Post by bthoward on 2008-07-28
New piece of info...  When the system is booting if I transmit on 80 meters (the worst of the bands so far) I get an error that says USB Hub Disabled Port 1 (EMI?), re-enabling.  (I'm paraphrasing as I don't have the log where I wrote down exactly what it said).  Anyway thought this may be another clue.  I have a feeling its somewhere in the USB nugget.  I should also mention that I do have a USB sound card and the sound card is installed with a USB extension.  There is a dongle on the computer end that goes into the computer and has a RJ45 jack.  Then I run standard UTP Cat5 to the other room where there is another dongle with a RJ45 and a female USB connector.  Then I plug in a USB sound card and a USB IR receiver.  This allows me to use the remote in the other room and use the sound card to get direct fiber out into the stereo.  

There is another USB IR blaster in the same room as the computer to control two digital cable boxes.  Both the mouse and the keyboard are USB.  Then there are two USB hard drives attached for backup purposes.  I think that's all the USB devices if I remember correctly...

I'm sure the rest of the system doesn't so much matter but its an Intel Core 2 Duo 3Ghz running Mythbuntu 64-bit.  4G RAM (shielded) the memory is 1066 stuff but I've told the board to run it one tick slower for design margin.  2.5TB of diskspace across 3 SATA drives.  Nvidia Gforce 8400GS by ASUS silent version.  Asus P5K Pro motherboard.  The case is a very nice Antec and I've added quite a lot of RF shielding tape and gasketing material.  Its a nearly perfect Faraday cage.  All systems are tied to a central grounding bar which runs out through copper braid to a dedicated 8 foot grounding pole.

Once this issue is found it won't be the first time I've solved an EMI problem with software! :)

---

### Post by cmapesjr on 2008-07-28
I have no problems from dc to light here. Two Ubuntu boxes in the shack. The only USB stuff I use is a printer and bluetooth. The rest is ethernet and wireless. I will do some testing and see if I can help.


'73 de K5PHW

---

### Post by bthoward on 2008-07-28
Now that I'm thinking its probably a USB issue I'll post this:

```
Last login: Mon Jul 28 13:21:29 2008 from 157.245.80.14
brett@myth:~$ lsusb
Bus 008 Device 002: ID 04fc:0c15 Sunplus Technology Co., Ltd 
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 005: ID 059b:0155 Iomega Corp. 
Bus 007 Device 003: ID 04a9:1713 Canon, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 0471:0815 Philips 
Bus 005 Device 003: ID 0d8c:0103 C-Media Electronics, Inc. Turtle Beach Audio Advantage Micro
Bus 005 Device 002: ID 0409:005a NEC Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 003 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 10c4:0003 Cygnal Integrated Products, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c215 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
```

I think the Logitech, Inc thing is a game controller.  Thats the only Logitech thing I can think of that is in the house at the moment.  As soon as I get home I'll go and jerk that out.  I'm not using it so its not needed at all.  It WAS port 1 that was going south too!  the Cygnal Integrated Products thing I'm thinking is my USB IR Blaster by CommandIR.  I'm not certain of this but in my quick search they make small integrated processors with USB cores and thats what I'd choose if I was making a CommandIR type device...  The Microsoft things make themselves clearly known.  The NEC Corp thing I can't for the life of me think of what it is.  The C-Media thing and the Phillips thing on port 5 is the Microsoft IR RX and the USB to Toslink sound card in the other room.  the Canon, Inc thing is a MP830 All-in-one printer.  The IOMEGA thing is a DVD burner (the only CD-ROM Drive on the system).  the Sunplus technology thing I'm not 100% on but I think that is the USB hard drive.  Perhaps the NEC thing is the hard drive and I'm all wet on the Sunplus thing.  

I'll post more information as I find more.

---

