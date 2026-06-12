---
title: "Sound works...only at login screen!"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by Xgkkp on 2005-04-09
Hi, I just installed Ubuntu, and seem to be having trouble getting sound to work. The strange thing is, the little drum sound at the GDM login screen plays fine, but then nothing will play when actually logged in. I tried using the "Multimedia systems selector" but all of the default sink options fail to work, with a pipeline error.

I don't know what sort of information would be useful here, so if you need, just ask.

Thank you very much!


Much, much later solved Edit: (I didn't feel it was worth bumping)

I reinstalled and it all worked fine, however I believe I know what the problem was. In the installation it took my old home directory, and that had some odd stuff on startup so I moved it and created a new user, however I don't think it had been added to the audio group, At the time I didn't know about the audio groups so I assumed that creating a new user was exactly the same as the default user.

---

### Post by edubarr on 2005-04-09
Do you know if you have the esd daemon running? Ubuntu uses esd instead of ALSA (I don't know why), and this usually creates a conflich between the two. If esd is running and not working you can try and kill it using 'killall esd', then go to the multimedia system selector and try using ALSA. If esd is not working then stop ALSA using '/etc/init.d/alsa stop' and start esd with 'esd &'. 

Try those and see if it works. Hope you can get it fixed soon. :-)

---

### Post by Xgkkp on 2005-04-10
[QUOTE=edubarr]Do you know if you have the esd daemon running? Ubuntu uses esd instead of ALSA (I don't know why), and this usually creates a conflich between the two. If esd is running and not working you can try and kill it using 'killall esd', then go to the multimedia system selector and try using ALSA. If esd is not working then stop ALSA using '/etc/init.d/alsa stop' and start esd with 'esd &'. 

Try those and see if it works. Hope you can get it fixed soon. :-)[/QUOTE]
 killall says "esd: no process killed". Trying to stop alsa shows the stop text, but that doesn't seem to help. runnig esd manually like that results in the multemedia systems selector working on esd when I hit test, but still no sound at all. Except at the login screen :(

---

### Post by edubarr on 2005-04-10
It seems that esd is not running by default. You can try checking the settings on System->Preferences->Sound. See if there is a check on "enable sound server start up" and "sound for events". Maybe this can help you out.

---

### Post by Xgkkp on 2005-04-10
[QUOTE=edubarr]It seems that esd is not running by default. You can try checking the settings on System->Preferences->Sound. See if there is a check on "enable sound server start up" and "sound for events". Maybe this can help you out.[/QUOTE]

Yes, and yes, they are both enabled. Also starting esd didn't actually let me play sounds, just let the test button thing work (I don't know if it is supposed to play sounds with that test button, but it doesn't crash out with an error)

---

### Post by pab on 2005-04-10
Xgkkp, I had the same problem as you: the drumbeat played at the login screen, but sound via esd would not work once logged in. Turns out esd wasn't even installed on the system. One "sudo apt-get install esound" command later, and it runs fine now. 

Sound was working perfectly since I installed Hoary from array 3 or 4 up until a few days ago, so somehow the upgrade to the final version may have triggered the esound package to be removed. *shrug* I've got no other explanation.

[Edit] Having just checked out the sound again, looks like the esound install broke oss and alsa. ](*,)

---

### Post by c_dog on 2005-04-10
[QUOTE=pab]
[Edit] Having just checked out the sound again, looks like the esound install broke oss and alsa. ](*,)[/QUOTE]
 Yep, the esd daemon lately has been breaking a lot of things. Looks like they finally pulled it for the final release. For now you can flip esd on and off by either CLI killing the daemon or System>Preferences>Sound> Enable sound server startup. It's been the first thing I check when either  players like Amarok are't giving any sound or Mplayer or VLC refuse to display video.

---

### Post by Xgkkp on 2005-04-10
Except in my system sound server startup is on, and was by default. You are saying they pulled sound system support for the final release?

If I switch it to ALSA in that thing it also doesn't do anything. However manually running esd allows the music players to work, not many other programs work at the same time, saying that there is no sound device, and games also don't output.

Bear in mind, this is also a fresh install, not an upgrade.

---

