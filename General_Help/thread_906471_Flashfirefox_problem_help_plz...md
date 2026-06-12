---
title: "Flash/firefox problem help plz.."
date: 2008-08-31
forum: General Help
---

### Post by Forcvcr on 2008-08-31
hello guys, im running ubuntu 8 and i have a problem with my firefox/flash and if i go on youtube the video will disappear and stop playing or if i go on myspace the lil music player will not appear and ill hear music playing or the music is playing and the music player disappears and music stops, whenever i restart firefox it works for a lil bit and then turns into a white box and wont work until i restart again or it stays blank. i tried to reinstall but it doesnt work. can anyone help me please.... thank you.

this is what the problem looks like:
Working:
[http://www.geocities.com/zidane11413/Screenshot-1.png]("http://www.geocities.com/zidane11413/Screenshot-1.png")

Not working:
[http://www.geocities.com/zidane11413/Screenshot.png]("http://www.geocities.com/zidane11413/Screenshot.png")

---

### Post by TheLions on 2008-08-31
try instaling Adobe Flash 10 beta or disable compiz

for Ubuntu x64: [http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html)

for Ubuntu x32: download from here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

   1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_10_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

---

### Post by SmokinJuan on 2008-08-31
How did you install flash?  Have you tried un/reinstall?

---

### Post by mb_webguy on 2008-08-31
Try installing Flash 10 from the backports repository.  (Check the link in my signature.)

---

### Post by Forcvcr on 2008-08-31
> **SmokinJuan said:**
> How did you install flash?  Have you tried un/reinstall?
i used the code: sudo apt-get install flashplugin-nonfree

---

### Post by Forcvcr on 2008-08-31
when i check to verify it says i got:
shockwave flash 9 r124 and shockwave flash 10 d569


it still does it =/

---

### Post by SmokinJuan on 2008-08-31
Does video work in other players? Totem, xine, VLC or whatever you use.  You could *probably* rule out a video/compiz problem if other players work.

Is this a new installation or did it just recently stop working?


[sorry about the un/reinstall question. didn't fully read your post. :oops:]

---

### Post by polanin on 2008-09-25
Uhhh...same problem here...!!!:mad:

---

### Post by TheLions on 2008-09-25
try installing firefox32, that will solve flash problems but give you some new! <grins>

[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

