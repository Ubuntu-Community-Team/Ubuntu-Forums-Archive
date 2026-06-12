---
title: "Well... [game and Skype problem]"
date: 2008-07-24
forum: General Help
---

### Post by Alex K. on 2008-07-24
Well ive just installed Ubuntu, so far im somewhat pleased with it, its a new experience and is pretty fun to tinker with but im having problems with Drivers. 
For games (Diablo 2) It does not detect Direct X at a high version therefore i cant switch the resolution of the game, is there anyway to make my video driver work perfectly? Secondly, im having problems with my sound card, In skype when i try to make a call it gives me an error message saying something like "Problem with Audio Capture". Ive switched around the drivers in the sound option in Skype but still cannot get it to work. Please can i get some help with this!

P.S Ventrilo also gives me an error along the lines of me missing a codec or something?

P.P.S I just noticed i can only hear system sounds and no sounds from any other programs.

---

### Post by Alex K. on 2008-07-24
bump

---

### Post by werries on 2008-07-24
1. dont bump your posts until after 24 hours.
2. for help on diablo2 working correctly, ensure you have the driver enabled for your graphics hard, this can be done by System > Administration > Hardware Drivers or by using the envyng-gtk package to get the same thing (although a little more updated, me thinks). and then for help with edits to make diablo2 work properly, here is the wine application database page, scroll down for help. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=315](http://appdb.winehq.org/objectManager.php?sClass=version&iId=315)
3. for skype, right click on the menu at the top left and go to system/preferences and make sure Multimedia Systems Selector is shown, and use that to configure your sound devices, and test, and then make sure you go to the skype options and select the correct device. also in the sound and multimedia options, make sure you test PulseAudio, ALSA, and OSS separately for compatability with your device, i usually use ALSA
4. due to your configuration with sound and messing with it, you should choose to select one that works with tests, ALSA and PulseAudio have software mixing for using more than one application with sound.
5. im not sure about ventrilo =P

---

### Post by Alex K. on 2008-07-24
Sorry for bumping I didnt know the rules of this forum, ill be sure to read next time :p
Thank you! You've fixed my Skype Problem but as for the graphics card, it shows that it is infact enabled but the game detects the graphics card to be very poor and reccomends a 2d setting (instead of the usual 3d setting I used to get in xp) and this is probobly the reason why i cant switch resolutions in game. Why is my graphics card acting so poorly?

---

### Post by werries on 2008-07-24
do you have ATI or nvidia or intel graphics?
What card?
Are you playing in fullscreen mode or emulating a virtual desktop?

Try going to wine configuration (wineconfig in terminal) and going to the graphics tab. Try turning on "Allow DirectX windows to stop the mouse leaving the window" and turning on "allow the window manager to decorate the windows" and turning off "allow the window manager to control the windows" and turning on "emulate a virtual desktop" with 800x600 in the resolution. 

especially try changing up the 2 last ones i mentioned, see what works for you.

---

### Post by Alex K. on 2008-07-24
It works alot better now thanks alot but there is still one error. Ive up'd the Resolution on the virtual desktop to 1440x900 (my resolution) so that it would emulate at full screen. But my diablo 2 still emulates as if I am running it in windowed mode.
[http://i36.tinypic.com/vpkt1l.png](http://i36.tinypic.com/vpkt1l.png)

---

### Post by inkrypted on 2008-07-24
Try running the game using OpenGL mode as mentioned in this thread.

[http://ubuntuforums.org/showthread.php?t=67147](http://ubuntuforums.org/showthread.php?t=67147)

And this is not meant as a slam but try searching the forums they really do contain alot of useful information.

Good luck.

---

### Post by werries on 2008-07-24
Hm. I don't run it in opengl, works fine, even in 3d mode.

Also, the max resolution of Diablo 2 is 800x600, you will have to either play it fullscreen without virtual desktop, (probably not letting the window manager control it either), or just deal with 800x600.

---

