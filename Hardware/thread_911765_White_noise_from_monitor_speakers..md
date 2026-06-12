---
title: "White noise from monitor speakers."
date: 2008-09-06
forum: Hardware
---

### Post by Jason2gs on 2008-09-06
Driving me insane...!

I'll be sitting there with my earphones plugged into the monitor, and the earphones in my ears. Then it seems that if I pull up a window that's predominately brightly colored, white crackling noise floods my ears.

Also, after a while of listening to something, portions of audio will seem to alternate between mono and stereo. For instance, I was watching an episode of Black Lagoon just now, and the character's voice was barely distinguishable. While the rest of the audio was fine, for the most part.

Really hoping someone can help me with this.

Thanks,

-Mike

---

### Post by Jason2gs on 2008-09-06
Bump.

---

### Post by Jason2gs on 2008-09-06
Bump.

---

### Post by Crafty Kisses on 2008-09-06
Post the results of this command:
```
lspci
```

---

### Post by Jason2gs on 2008-09-06
*Does the two-finger-Christmas-Haruhi-salute*

Yes sir!

```
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
```

Thank you for replying =] Sorry I didn't respond. I was putting groceries away.

Oh, and cute Pikachu ^_^

---

### Post by Hellkeepa on 2008-09-06
HELLo!

Try to plug the earphones directly into your sound card/chipset, instead of going through your monitor. If you experience the same problem then, it's most likely that the sound card/chipset is poorly shielded. Could also be the drivers, though this is far less likely.
However, if the problem stops, it's your monitor that is the issue. The solution in this case, would be to buy an extention cord for your headset.

PS: This is a forum, not a live chat channel. Replies within the first 24 hours are not always to be expected, and bumping before this time has passed (especially twice within 2-3 hours) is generally viewed negatively upon; It's basicly the same as nagging. Might want to keep that in mind, for the future. ;-)

Happy codin'!

---

### Post by Jason2gs on 2008-09-06
Ah, yes. I've had them plugged into the tower before, and it doesn't happen.

An extension for my headset is certainly possible, because the tower the right up on the desk with me. It wouldn't grab on anything, or anything like that...

However, don't you think it's odd that the white noise/"high frequency", as the problem was stated in another thread ([http://ubuntuforums.org/showthread.php?t=55467](http://ubuntuforums.org/showthread.php?t=55467)), is affected by the luminance on the screen?

Also, my apologizes about the bumping the thread. I've been to many forums, and they're all different. Some don't care if you bump threads, some do. Some whose members don't search back beyond the main page, some do, etcetera. I'll remember the twenty-four hour stipulation for the future :p

---

### Post by Hellkeepa on 2008-09-06
HELLo!

Not really, no. Escpecially not if you're using a CRT. I would guess that the combination of Hz and res in thread you linked to, caused some of the spools inside the monitor to vibrate at an audible level. Quite common issue, especially with TVs. Solution to this problem, is to spray them with a special clear, non-conducting paint. (Don't know the correct word for it, I'm afraid, but ask at any shop that services electronics and they can tell you.)

However, while I suspect your problem is poor shielding of the ports, it is related to the issue you linked to: The more luminance, the more the vibration of some spools change. Which is then picked up by the audio ports and translated into sound, like the rest of the electronic signals the headphones recieve. Leading to the result of white noise when viewing white windows.

I'm not familiar with the intricacies of LCD screens, so I can't say wether or not this would be the case for them too. Though, I suspect it's not too far off. ;-)

Generally, though: Audio ports and speakers on monitors are known to be of rather cheap quality, also when it comes to shielding against electronic interference from the other components.

Happy codin'!

---

### Post by Jason2gs on 2008-09-07
*Shrugs*

I guess there's nothing much I can say to that.

I'll keep an eye out for that paint thingy.

Thanks for your help =]

---

### Post by mbhavaraju on 2008-09-07
Hi,

I have similar kind of problem.

I have a Flat wide screen LCD from NIKO.  It comes with inbuilt speakers to the monitor.  When my monitor is on my speakers give an hissing Dentist instrument noise.:(  When I turn off my monitor its not there.  Sometimes this noise really gets into mind.  

I don't know what is causing it.  I set my Monitor speakers to Mute, I am fine I don't hear that noise.  Ofcourse, I have to sacrifice my audio.

Does any one else have this problem and any solution for it?

I am using Hardy 8.X.  I don't have this problem with Windows(at least I don't remember).  

Any help in this issue is really appreciative, You all have great time.

Raj

---

### Post by mbhavaraju on 2008-09-07
Hi,

I have similar kind of problem.

I have a Flat wide screen LCD from NIKO.  It comes with inbuilt speakers to the monitor.  When my monitor is on my speakers give an hissing Dentist instrument noise.:(  When I turn off my monitor its not there.  Sometimes this noise really gets into mind.  

I don't know what is causing it.  I set my Monitor speakers to Mute, I am fine I don't hear that noise.  Ofcourse, I have to sacrifice my audio.

Does any one else have this problem and any solution for it?

I am using Hardy 8.X.  I don't have this problem with Windows(at least I don't remember).

---

### Post by jreinis on 2008-09-21
Ubuntu 8.04 64 bit.
kernel 2.16 default.
No any updates at all.
all system is in default state.

When I do not watch movies/show/music in speakers I hear a load white noise. 
When I watch them they are barely distinguish among this white noise.

In Windows XP SP2 32 bit and Vista SP1 64 bit I get a very clear, without any noise, sounding.

Any ideas how to fix that issue in Ubuntu?
If possible from your/your friends/job experience because I can not experiment - I work on the computer.
I need proven solution.
Thank you in advance.

---

### Post by markbuntu on 2008-09-21
Is your microphone or capture or line in turned on in the mixer?
Having these on and turned up can create this sort of problem.

---

