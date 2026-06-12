---
title: "I Have No Sound Help!!!!!"
date: 2008-04-27
forum: Hardware
---

### Post by filip33 on 2008-04-27
Hi, I just installed ubuntu 8.04 and I am a complete noob. I have a creative sound blaster sound card and I have NO SOUND please help me I don't want to go back to windows please help.

---

### Post by filip33 on 2008-04-27
come on someone help!!!!!!!!!!!!

---

### Post by filip33 on 2008-04-27
.

---

### Post by stoneage on 2008-04-27
Did you configure it in 'Preferences => Multimedia Systems Selector'?

---

### Post by filip33 on 2008-04-27
sorry but I can't seem to find multimedia systems selector. I should probably let you know I am running Ubuntu 8.04.

---

### Post by filip33 on 2008-04-27
`

---

### Post by stoneage on 2008-04-27
Click on 'System' in the top left corner.
Try 'plugin : ALSA'
'Device : CA0106(the first one)
Then restart and check that the settings are still the same. You may also need to look at 'System => Preferences => Sound' and set 'Sound Playback' on CA0106 this time the last one.
These settings worked for me - though I have no idea if they are the most appropriate.
If it doesn't work out try different combinations, ESD and OSS also work.
Post back if you are still having difficulties.

---

### Post by Kcrsh10 on 2008-04-27
Hello there, Im afraid this is a common problem. I am having similar issues and can only suggest looking around the forums. There are various solutions. This is a good starting point.

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

Hope this help

---

### Post by filip33 on 2008-04-27
Stoneage Thank You!!!!!!!!!!!!! So Much I Have Sound!!!!!!!wooooooooooooo!!!!!!! Thank You For Taking Your Time And Helping Me!!!! Thank You!!!!!

---

### Post by filip33 on 2008-04-27
Hi, stoneage I am getting sound when I play a music off my hardrive but I don't get sound on youtube??? Please help!

---

### Post by stoneage on 2008-04-27
I'm not sure what is causing that. It could be you need to install a Firefox plugin or a system codec.
Look in 'System => Administration => Synaptic Package Manager'
Click search, type in 'mozplugger'(without inverted commas) and see if it is installed(green checkbox).

In Firefox click 'Tools => Add-ons' and look for plugins.
 
Also maybe try searching the forum - this sort of thing comes up occasionally.

Check back if this doesn't help.

(just a thought, but do you have 'Music and Movies' Sound Playback: CA0106 in 'Sound Preferences'?)

---

### Post by filip33 on 2008-04-27
hey that hasn't helped do you know anything else so I can hear some you tube videos. Please help!

---

### Post by filip33 on 2008-04-27
!

---

### Post by filip33 on 2008-04-27
Ooo Man I Have Finally Figured Out The Problem Ubuntu Says Its The Solution But Pulse Audio Is What Was Stopping Me From Watching Youtube Videos Ahahahahah Woow That Was 3 Hours Of My Life I Am Going To Want Back Anyway All You Have To Do Is Go To System Monitor>process>find Pulse Audio And End The Process. Thanks To Everyone That Helped Anyway I Am Going To Watch Some Youtube Videos. 

Best Wishes,

Filip

---

### Post by stoneage on 2008-04-27
To be honest, I'm running out of ideas.
I take it you have checked all the simple stuff like volume levels  and made sure sound still works in other applications etc.

Someone suggested trying installing 'ubuntu-restricted-extras' - a set of sound and video codecs that can't be bundled with the installation for legal and copyright reasons, but are available free. You would probably have to go to 'Administration => Software sources' and check the (multiverse) box.

Do you have Flashplayer installed? Search on 'flashplugin-nonfree' to see whether that would help.

Try a Google search on 'youtube sound linux' or 'youtube sound ubuntu'

Edit - Congratulations! Best of luck.

---

### Post by filip33 on 2008-04-27
`1

---

