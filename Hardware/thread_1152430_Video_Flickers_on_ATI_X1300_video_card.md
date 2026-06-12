---
title: "Video Flickers on ATI X1300 video card"
date: 2009-05-07
forum: Hardware
---

### Post by 7CarPileUp on 2009-05-07
Hello people,
I will try to explain this as best i can. let me know if i leave any vital info out as i am a noob.

I have a Compaq Presario SR5010NX
3.46Ghz processor
Running Ubuntu 8.10

I recently bought a visiontek ATI X1300 256MB online because it was dirt cheap (40 bucks w/free shipping).  Once i installed the video card on the windows side i popped over to ubuntu and installed the proprietary drivers for it.  Which included the catalyst program.  

Everything was gravy until i played some audio and noticed that the visualisations on totem were flickering badly.  several times a second.  Thinking it was just an issue with that visualisation plug-in I just turned it off for audio.  Then i played a video and noticed it was happening with that as well.  I tried VLC same issue.  Same as rhythmbox's visuals as well, and it also now looks like your trying to watch scrambled porn.  

I saw a thread saying that turning off the desktop effects fix's this and it did. However this is the same time i fell into compiz and now i badly want those desktop effects.  I noticed some videos online of someone using the effects with an ATI X1300 card and i really want to know if someone can give me some pointers to get this working right.

When i turn on compiz it shows this:

bluehat@LN-007:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
-----------END------------

when i run fglrxinfo i get:

bluehat@LN-007:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.1.8087 Release
-----------END-------------

-again i am not sure if this is all the info needed so please let me know if anyone needs more info.

Thanks.

---

### Post by 7CarPileUp on 2009-05-08
bump

---

### Post by DJYoshaBYD on 2009-05-08
go into your preferences in whatever program you are using to watch videos, and look for something that says output or video output.. set it to X11 output... 

do you have Compiz enabled? if you do, then you need X11 to control the vid output.. compiz also causes alot of problems with video playback, specifically with FLASH, but with pretty much anything, it will do that.. go through your compiz settings and see if you can change the video output to be controlled by X11 and not compiz.. I think thats how you say it.. but yeah.. that worked for me..

you can do this in VLC very easily.. actually you should probably try that.. VLC is sooo smooth..

---

### Post by 7CarPileUp on 2009-05-10
Thank you good sir.

You revealed the root issue.  VLC was easily fixed in the GUI. For totem i found another article to keep it in X11.

for those searching i will list it.
press ALT+F2
type "gstreamer-properties" and hit enter
Click on video tab and change to X Window system.


Thanks DJ

---

### Post by NormanFLinux on 2009-08-03
Disable compiz for video playback. Its good for everything else.

---

