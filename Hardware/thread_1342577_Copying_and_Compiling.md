---
title: "Copying and Compiling"
date: 2009-11-30
forum: Hardware
---

### Post by princeofnam on 2009-11-30
Hi!  I found instructions on how to fix the sound for my Ubuntu laptop installation.  Unfortunately, I don't know how to act upon them.

The post is as such
-----
                                                                             Hey Scotty, I was just able to get the sound working, I found the solution here: [https://bugtrack.alsa-project.org/al...ew.php?id=3165]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165") . Just sign in as guest to view the forum.

Kentrosaurus gives his solution and links to where he found it...download the newest alsa driver, utils, and lib (I used 1.0.14rc4), replace hda_proc.c and patch_realtek.c from realtek10.tar.gz (on the page Kentrosaurus linked to, pshou explains how to do this).

Insert the line "options snd-hda-intel model=toshiba" on the end of /etc/modprobe.d/alsa-base. Finally, compile the driver using the directions here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) .

If you have any questions, just ask!

Edit: Interestingly, though, the mute button is now always lit up blue, and it seems to only mute the front audio jacks. On the volume control, the "headphone" slider seems to affect both the headphone and line-out jacks, while "front" affects the built-in speaker. Also, at this point, the speaker does not automatically turn off when headphones are inserted, it needs to be manually muted.
---

The link he provides doesn't have the step by step instructions he said they would.  I don't know how to download the latest alsa drivers, replace those files, or compile. Can anyone help?

---

### Post by BenAshton24 on 2009-11-30
On the linked page it give instructions on how to download/compile the latest driver, if you scroll down a bit! but they're out of date anyways :P if you are using any version equal to, or greater than 8.04 then use the ALSA Upgrade script that can be found here...

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Hope this helps you
Ben.

---

### Post by princeofnam on 2009-11-30
thanks! do you know anything about how to copy and replace those realtek files in the alsa folder? do i have to compile again after replacing them?

[http://www.tonyphamilyman.com](http://www.tonyphamilyman.com)

---

### Post by princeofnam on 2009-11-30
I'm new to Ubuntu and don't know my way around it at all really.  I was giving proper instructions on how to fix Ubuntu to work with my sound card unfortunately there are certain steps i'm not sure how to go about.  The post is as follows:

Hey Scotty, I was just able to get the sound working, I found the solution here: [https://bugtrack.alsa-project.org/al...ew.php?id=3165]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165") . Just sign in as guest to view the forum.

Kentrosaurus gives his solution and links to where he found it...download the newest alsa driver, utils, and lib (I used 1.0.14rc4), replace hda_proc.c and patch_realtek.c from realtek10.tar.gz (on the page Kentrosaurus linked to, pshou explains how to do this).

Insert the line "options snd-hda-intel model=toshiba" on the end of /etc/modprobe.d/alsa-base. Finally, compile the driver using the directions here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) .

If you have any questions, just ask!

Edit: Interestingly, though, the mute button is now always lit up blue, and it seems to only mute the front audio jacks. On the volume control, the "headphone" slider seems to affect both the headphone and line-out jacks, while "front" affects the built-in speaker. Also, at this point, the speaker does not automatically turn off when headphones are inserted, it needs to be manually muted.

---------

I'm not sure how to copy the files though with proper permission in Terminal.  Moreover, I'm not sure how to recompile either.

Thank you,

---

### Post by cariboo on 2009-12-01
Please don't create multiple threads on the same problem. I have merged your two threads.

---

