---
title: "Xitel Inport"
date: 2008-05-03
forum: Hardware
---

### Post by dafdaf on 2008-05-03
I'm new to Ubuntu and Linux.
Can anyone help me set up a Xitel Inport?
It is a USB device connecting to a turntable to record vinyl LPs.
Any assistance will be greatly appreciated.

---

### Post by tirot on 2009-04-23
I realize this is an old thread, but it seems to be the only one addressing this particular device.

I figured I would respond as I've recently purchased the Xitel INport and I too am fairly new to Ubuntu.

After plugging the device in, Ubuntu immediately recognized it. You can confirm this by using the lsusb command from your terminal. For example my terminal print out after plugging it in was:

ubuntu@ubuntu-desktop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 09ef:3604 Xitel 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu-desktop:~$

Basically I think this means it is now ready to be used. But wait... to use it you will need audio recording software right?

Well, just look through synaptic package manager for an audio recording program. I chose Audacity. After installing Audacity I found the INport selectable as a device inside the Edit>Preferences>Audio I/O menu screen.

I haven't attached the stereo I'll be using yet, but I'm fairly certain that it will output through the INport into Audacity and record just fine. This should allow anyone who wants to digitize their cassettes, LP's or whatever out of their stereo to quickly do so.

I hope this post is helpful to other users who have a Xitel INport and who've tried searching the forums but found surprisingly little on the topic.

---

### Post by dafdaf on 2009-04-24
Thanks, tirot

the INport is listed as is yours when I use lsusb - I still have not learned much about linux - yet.
I have not been able to get it to input to Audacity, although I can do so on my XP machine. i have tried all the available input choices listed in Audacity.
Any more clues??

Thanks again,
I appreciate your input.

daf
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by headcount on 2010-11-17
Bumping an old thread because I finally got this to work.  Browsing the web for solutions brings up this thread, so I'll post the solution here for posterity.

I'm running Ubuntu 10.10, Audacity 1.3.12, and using [Xitel Inport]("http://www.xitel.com/USA/prod_inportpro.htm").

1. First, connect the Inport hardware - one side goes to the RCA audio output of your A/V receiver, the other goes to a USB port.

[IMG]http://imgur.com/fAW2p.jpg[/IMG]




2. Now verify that Ubuntu can see the hardware.  Go to System>Preferences>Sound and the "Hardware" tab.  (I then set mine for input only, but this is optional.)

[IMG]http://imgur.com/oyNCs.png[/IMG]




3. Click the "Input" tab and change the input device from "internal" to "USB" at the bottom.  Also make sure you're using line-in and the input is not muted.

[IMG]http://imgur.com/7yUz3.png[/IMG]




4. Next, open a command window and type 'alsamixer'.  You'll get this screen:

[IMG]http://imgur.com/QrKiY.png[/IMG]




5. Press 'F6' to select the USB device.  Now the important part: move over to the 'PCM Capture' field and press the up arrow to select 'line' (the default is 'mic').

[IMG]http://imgur.com/LCi1Q.png[/IMG]




6. Now fire up Audacity, go to Edit>Preferences>Recording, and select 'USB' as the input device.  

(Forgot to take a screenshot of this, but it's straightforward.)




7. Start recording, play the desired record, and viola!  Sound, just like Windows!

[IMG]http://imgur.com/6CLKa.png[/IMG]




Now it's time to get cracking on the LP's I've accumulated in the meantime trying to figure this out...

[IMG]http://imgur.com/cRrhP.jpg[/IMG]

---

### Post by dafdaf on 2010-11-24
Thank you thank you thank you, headcount!
I have managed to get some sound in following your excellent directions, but am having a few issues with alsa and/or audacity. I'll maybe able to fiddle more next weekend, but in the meantime, thanks for what you have done and, importantly (or should that be INPortantly?) for passing it on.

daf

---

