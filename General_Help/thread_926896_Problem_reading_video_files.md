---
title: "Problem reading video files"
date: 2008-09-22
forum: General Help
---

### Post by kingfourat on 2008-09-22
Hi all,
Since i've installed my ATI video card driver (trough EnvyNG) I'm not able to read video files correcty with any player and for any video format. The player shows me a black screen and only plays the sound of th video:

[IMG]http://img227.imageshack.us/img227/1526/screenshotvlcmediaplayecc7.png[/IMG][

---

### Post by cszikszoy on 2008-09-22
Have you downloaded all of the video codecs from the Medibuntu repos?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by kokkus on 2008-09-22
Have you installed all the divx, xvid and qt codecs you need?

Take a look at these 2 screenshots and go to synatic package manager and install the packages you need.

[IMG]http://www.scumbox.com/ubuntu/video1.png[/IMG]

[IMG]http://www.scumbox.com/ubuntu/video2.png[/IMG]

---

### Post by kingfourat on 2008-09-22
Hi again,
Thank you guys for your fast reply !!! 
I did what you said guys: first I installed w32codecs from the Medibuntu repository, and then I installed all the packages in the screenshots from the Synaptic, after that I restarted but it still not working :(
Should I try to uninstall the ATI driver ???

---

### Post by kokkus on 2008-09-22
Have you ever installed the ubuntu-restricted-extras?

This is ubuntu's extras pack with non-free plugins and addons for i.e video and audio playback.
Go to terminal and paste:
sudo apt-get install ubuntu-restricted-extras

Use the tab key to enter the license OK button when that comes up.

---

### Post by kingfourat on 2008-09-23
> **kokkus said:**
> Have you ever installed the ubuntu-restricted-extras?

This is ubuntu's extras pack with non-free plugins and addons for i.e video and audio playback.
Go to terminal and paste:
sudo apt-get install ubuntu-restricted-extras

Use the tab key to enter the license OK button when that comes up.
I have just done that, but still not working :(
Should I uninstall the ATI driver ??

---

### Post by kingfourat on 2008-09-24
Well I uninstalled the driver and it works fine righ now. So I'm thinking that the driver is not the right one for my video card !
Is there an nother way to install the driver for the graphic card without EnvyNG ????

---

### Post by 3rdalbum on 2008-09-24
Wait! The driver is most likely the correct one for your card.

Some *poorly-written proprietary graphics card drivers* can cause any video files you play to look corrupted, or blank. You can often solve the problem by changing the method that your video player uses to draw the video image to the screen.

In VLC, go to Settings > Preferences. Open up the Video category and click on Output Modules. Click the "Advanced Options" checkbox. Now you can change the video output module from "Default" to one of the following:

X11
Image
OpenGL
Xvideo

Save the preferences, restart VLC, and see if the problem has been solved.

If you want to change the setting for Gstreamer-based video players like Totem, go into Gconf-editor and change the following setting:

/system/gstreamer/0.10/default/videosink

The description shows you the possible choices. Choose one, try it out, and see what happens.

---

### Post by Neodarkness on 2008-09-28
hey man.
I had the same problem with the envyng driver and video, your post solved it for me. Wonder if you can help me set up counter strike to work on wine?, because since i installed the envyng driver i stopped working (i think opengl is not working, because when i tried to set vcl to opengl it didnt work).
I'm not quite positive, but i think the envyng driver actually solves for me a hard-boot problem i've been having a lot.
thanks

---

