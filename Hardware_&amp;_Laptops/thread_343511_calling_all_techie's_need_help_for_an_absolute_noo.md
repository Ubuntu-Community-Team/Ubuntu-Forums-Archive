---
title: "calling all techie's need help for an absolute noob"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by rojcherian on 2007-01-21
Hey guys, i have just started using ubuntu two days ago..and this is my first time using linux. i have a Acer 5100 and i installed ubuntu 6.06, installation ran fine, now there are couple of problems. I see couple of podcasts out there to help me out, but the prob is my sound. At first my sound is all good, next day the volume was very low i turned up everything but to no avail. the strange thing is that if the sound file is on my desktop and if i just click it once and the  mouse is still on that file the volume is all normal and at this time no programs are opened, and if point the mouse away from the file the file stops playing...weird!!!...and i need help installing other softwares like Java, Azureus...any help at all will be greatly appreciated

---

### Post by allwin on 2007-01-21
I think when you put the mouse over a sound file icon, the default is to play it...only so long as you are pointing to it.  That's been my experience (in some cases).  I guess it's a little "extra" you get with this OS, kind of like a preview.

I have crummy sound on two different older PC's.  And on one, the sound in KDE is distorted, but in GNOME it's OK.  One PC has the left and right channels swapped and when it boots, the volume for only one channel is turned on.  It's not great at remembering volume settings between reboots, either.

On the JAVA/Azureus thing...look for a package called AUTOMATIX2.  Install that and automatix will install all the other goodies for you.  No terminal commands to speak of, either.

Once you do get the sound working, at least for me...I find that it cuts out with a high CPU load, unlike the competing OS'es.  Think this whole sound thing is a dark corner of the basement for U, IMHO.

---

### Post by rojcherian on 2007-01-22
hey thanks automatix helped....now about the sound...yea it does play the file aut when i point at the file....(not complaining)..but the confusing part s that the volume appears to be normal when i am pointing at the file...but when i use any softwares to play it the volume is real low then.....same goes with trying to watch DVD's or any other video files......and the volume control on the specific player does no use to the sound level.....very confusing indeed...

---

### Post by aysiu on 2007-01-22
The sound preview thing is something you can turn off in the Nautilus preferences. Go to the file browser and go to **Edit** and **Preferences** > **Preview** > **Sound Files**.

---

### Post by allwin on 2007-01-22
> **rojcherian said:**
> hey thanks automatix helped....now about the sound...yea it does play the file aut when i point at the file....(not complaining)..but the confusing part s that the volume appears to be normal when i am pointing at the file...but when i use any softwares to play it the volume is real low then.....same goes with trying to watch DVD's or any other video files......and the volume control on the specific player does no use to the sound level.....very confusing indeed...

Right click on the GNOME panel or taskbar thing and see if you can add an item to the panel...look for the volume control.  OK, I have noticed that the volume slider in most Linux apps DOES NOT change the volume, but the volume control that you add to the panel will ultimately control the applet.  Actually, I get the feeling that the application's volume control sends a command in to the mixer, which then later on actually changes the volume coming from the sound card.  It's not immediate when it does work.  IF you get the volume control thing working, set the MASTER volume to 100% and the PCM volume about 80% or the sound will be distorted.

I've just learned to use the volume control in the panel instead of the one in the app.

---

### Post by rojcherian on 2007-01-23
hey i tired that, it still doesn't work...although at the beginning i did something similar i went to keyboard shortcuts and found the volume control on there which controlled....from what i can think of it is softwares...because the little preview thing for the file works well in terms of sound...also real player and audacity has good sound too...its just the other softwares..now this could be a software compatible issue...i don't know alot about linux software compatibility...my main problem now is playing DVD'S...the video players are doing the same thing for audio....

---

