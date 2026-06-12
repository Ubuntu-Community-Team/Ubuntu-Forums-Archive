---
title: "Dell 1520 webcam problems"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by HIGHLIFE on 2007-12-01
I just got a new dell 1520, but I can't seem to get the built in webcam to work.  I did try this thread with no luck:

[http://ubuntuforums.org/showthread.php?t=501195&highlight=1520+webcam]("http://ubuntuforums.org/showthread.php?t=501195&highlight=1520+webcam")

Could someone help me get this thing working?

Thx ahead of time.

---

### Post by linux23dragon on 2007-12-01
> **HIGHLIFE said:**
> I just got a new dell 1520, but I can't seem to get the built in webcam to work.  I did try this thread with no luck:

[http://ubuntuforums.org/showthread.php?t=501195&highlight=1520+webcam]("http://ubuntuforums.org/showthread.php?t=501195&highlight=1520+webcam")

Could someone help me get this thing working?

Thx ahead of time.

Hello HIGHLIFE

I have written a new thread about installing drivers for your web cam [***_[COLOR="Blue"]here[/COLOR]_***]("http://ubuntuforums.org/showthread.php?p=3642769#post3642769").  It supports Ubuntu-7.04 and Ubuntu-7.10.

You might need to adjust the brightens levels, but your web cam works with the default driver in Gutsy.  The Linux-UVC driver only supports V4L2 applications like Skype-2.0, Ekiga,  aMSN and the latest version of Kopete (in Gutsy). 

Hope this helps

---

### Post by HIGHLIFE on 2007-12-01
No I went through that thread and when I open up ekiga I'm getting:

Error while opening video device Laptop Integrated Webcam


I've also just realised that my sound isn't working in mplayer and vlc, I used the  sudo apt-get install linux-backports-modules-generic method to enable it, is there anyway that I could get my sound to work with these apps?

---

### Post by linux23dragon on 2007-12-01
> **HIGHLIFE said:**
> No I went through that thread and when I open up ekiga I'm getting:

Error while opening video device Laptop Integrated Webcam

Yea, that can happen when you use the default video  plug in.  You did change the video plug in to use V4L2?
Also the driver gets updated a lot, and its possible that ekiga may not correctly work with a updated Linux-UVC Driver.  Tthe V4L2 specs has been changing over the last 6 months or so and the driver developers will try to implement the changed standards and fix bugs at the same time (so I've seen from the dev mailing lists) .  The Gutsy driver (by default) should work out of the box. 

You will find the Video Devices via Edit->Preferences.  Then restart Ekiga, and/or reactivate the web cam. 


> **HIGHLIFE said:**
> 
I've also just realised that my sound isn't working in mplayer and vlc, I used the  sudo apt-get install linux-backports-modules-generic method to enable it, is there anyway that I could get my sound to work with these apps?

I have not used those applications yet (I use Xine myself).  But its possible that they need other sound libs that may not be installed on your system (esound, libalsaplayer0, alsaplayer-player codecs).


Have you used the [[COLOR="Blue"]_***Gutsy Wiki***_[/COLOR]](" http://ubuntuguide.org/wiki/Ubuntu:Gutsy")?  They have lots of solutions that will help you with mplayer and vlc.


EDIT:  This looks like a good solution too : - [ _***[COLOR="Blue"]How_to_get_Mouse_over_preview_of_MP3_files_working[/COLOR]***_]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_get_Mouse_over_preview_of_MP3_files_working").  I found that I needed to install esound, libalsaplayer0 and alsaplayer-player afterwards.


UPDATE:  I've just updated my own web cam driver (for my desktop PC "QC Fusion"), and it works well with ekiga.

---

### Post by HIGHLIFE on 2007-12-01
The cam is still not working and I have all of those packages installed but I'm still not getting sound:mad:.

---

### Post by linux23dragon on 2007-12-01
> **HIGHLIFE said:**
> The cam is still not working and I have all of those packages installed but I'm still not getting sound:mad:.

Are you using a 32bit or 64bit OS?

---

### Post by HIGHLIFE on 2007-12-01
32bit

Just to clarify: I'm getting the system sounds, sound in rythmbox and totem, but nothing else.

---

### Post by linux23dragon on 2007-12-01
> **HIGHLIFE said:**
> 32bit

Just to clarify: I'm getting the system sounds, sound in rythmbox and totem, but nothing else.

Man that is bad luck.  Gutsy 32bit with the 1520 is a good combination.  Well I only have two more options for you (from the top of my head)  

First have a look at post 84 in this [***_[COLOR="Blue"]thread[/COLOR]_***]("http://ubuntuforums.org/showthread.php?t=530374&postcount=84").
If that does not work out for you then ask about your sound issues at this [***_[COLOR="Blue"].thread[/COLOR]_***]("http://ubuntuforums.org/showthread.php?t=577469&highlight=dell+1520") 
Don't forget to detail the hardware specs.

Other than that, all I can think of is reinstalling Gutsy 32bit.  It can be a trial and error sometimes when you are installing Gutsy on the Dell Notebook.

---

### Post by HIGHLIFE on 2007-12-01
I got the sound working with that one post thx!
Ubuntu really needs better support for webcams if I was able to use stickam I would never go back to windows.

---

### Post by linux23dragon on 2007-12-01
> **HIGHLIFE said:**
> I got the sound working with that one post thx!
Ubuntu really needs better support for webcams if I was able to use stickam I would never go back to windows.


Last question about the webcam and ekiga.  

Did you get an error message like this? : - 

Error while opening video device UVC Camera 
(046d:08c1)


Because I've just gotten that error message myself just now, after restoring the default Ubuntu driver.  It did work before I installed an updated version of Linux-UVC.  

That message tells me that the webcam driver is loaded and running but for some reason it won't work with the UVC-control (brightness contrast level controls?).  Well thats what I read from my kernel log : -


```
Dec  2 14:55:53 core2-desktop kernel: [  137.875721] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : -32 (exp. 26).
Dec  2 14:55:53 core2-desktop kernel: [  137.885953] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -32 (exp. 26).
Dec  2 14:55:53 core2-desktop kernel: [  137.889822] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -32 (exp. 26).
Dec  2 14:55:58 core2-desktop kernel: [  143.527327] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:55:59 core2-desktop kernel: [  144.525879] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:56:00 core2-desktop kernel: [  145.524433] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:56:06 core2-desktop kernel: [  151.308325] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:56:07 core2-desktop kernel: [  152.306884] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:56:08 core2-desktop kernel: [  153.305433] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:56:30 core2-desktop kernel: [  175.207208] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:56:31 core2-desktop kernel: [  176.205884] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:56:32 core2-desktop kernel: [  177.204437] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:56:50 core2-desktop kernel: [  195.146939] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:56:52 core2-desktop kernel: [  196.694757] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:56:53 core2-desktop kernel: [  197.693310] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:56:54 core2-desktop kernel: [  198.691863] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:57:08 core2-desktop kernel: [  213.317092] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:57:09 core2-desktop kernel: [  214.315647] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 14:57:10 core2-desktop kernel: [  215.314197] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 15:07:41 core2-desktop kernel: [  844.860440] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 15:07:47 core2-desktop kernel: [  851.135558] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 15:07:48 core2-desktop kernel: [  852.134120] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Dec  2 15:07:49 core2-desktop kernel: [  853.132669] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
```

I'll see what happens after I reboot the PC.


UPDATE : -

O.K the web cam now works again.  But I had to play around with the brightness control, but it works fine now.  However, the kernel log also started to give me the same error messages "Failed to query (1) UVC control", when I started using the brightness control.


This is how I got the web cam working again : -

After restoring the original Linux uvc driver I used Ekiga to turn of the web cam / bouncing ball (pressing the web cam button), then exit out of Ekiga (no phone icon on the top  task bar panel). Opened up a terminal and typed "sudo depmod -ae".  Then reboot. 


HIGHLIFE, have you tried any other web cam application in Ubuntu yet?

---

### Post by HIGHLIFE on 2007-12-02
Linux23dragon,  the only application I've had good results from is cheese. I'll be back in an hour or two to look more at your post above.

---

### Post by HIGHLIFE on 2007-12-02
I checked the system log after trying ekiga and couldn't find any errors.  I might have missed them though.  Its tough to pick them out of a system log..

---

