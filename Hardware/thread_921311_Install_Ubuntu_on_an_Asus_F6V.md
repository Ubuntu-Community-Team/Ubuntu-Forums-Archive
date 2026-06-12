---
title: "Install Ubuntu on an Asus F6V"
date: 2008-09-16
forum: Hardware
---

### Post by ramomamo on 2008-09-16
When I first installed (yesterday) Ubuntu Hardy (8.04) on this laptop I realized that there was no sound coming out of it, and the wireless card was not detected.

These are the steps I followed to solve it. Just thought it might help someone.

In order to make the wireless card work, I had to update to Ubuntu 8.10 (this is still in testing state). I followed [*this*]("http://www.ubuntu.com/testing/intrepid/alpha5#Upgrading%20from%20Ubuntu%208.04") to do so.

After that, the system couldn't run into graphical mode, don't worry, reboot in safe mode, if needed, and select the option to fix the X server.

The next step was to solve (better said, to avoid) the audio issue with ALSA (maybe solved in future releases); so I just followed the steps described in [*here*]("https://help.ubuntu.com/community/OpenSound") to replace ALSA by OSS4.

Maybe you need to install the necessary plugins so your player can use OSS afterwards, I didn't have much trouble.

I hope this helps someone. I know this is not a resolution of the problem but a dribbling for it. :-\"

---

### Post by Ken Martin on 2008-09-16
Most interesting and helpful. I have decided to be kept up to date about new Ubuntu versions thanks to you. Cheers.

---

### Post by visit on 2008-09-16
Hi!
I try for my asus f6v install ubuntu intrepid alpha5. Everything work fine, expect ati vga on 3D. 
But if I enable daily update (at this moment 294...), after restart I have no GUI.
Thereford I use only alpha5.
(My f6v is buliding 3G modem.)

---

### Post by pjkevm on 2008-10-12
Thankyou very much, I am running windows vista atm(unfortunately) but this is great to know that intrepid will get my sound working(with oss4), which is why I instlled/uninstalled ubuntu on this laptop when i first revieved it.

Thanks again

---

### Post by cenoura on 2008-10-31
Hy there,
Does anyone tried out the 8.10 (the final version) on F6V?

Thanks in advance

---

### Post by pjkevm on 2008-11-02
I'm running ubuntu 8.10 on my asus f6v.

It was easier to get things working than on 8.04, but still took some time. I installed the 64 bit version which, even though i'm sure some programs work faster i would recommend using the regular i386 architecture. I've had to install too many fixes to get things compatible.

Sound works using oss4. I still cant get ubuntu os sounds to work. But all the programs Im using are working with minor changes in code.

There is also a problem with the video card in that certain videos flash constantly. It's only a problem with Gstreamer video player right now, not with vlc movies or adobe flash, but i haven't tried videogames or anything yet.

I haven't gotten the mic to work yet either, but webcam works without issue.

---

### Post by pjkevm on 2008-11-02
mic was an easy fix, i just had it on output instead of input in gnome sound options

---

### Post by Shabbir Ahmed on 2008-11-05
its amazing.. i got my FV6 recently and did install the new Ubuntu 8.10 desktop version on it.. but i have soo many things not working.. i am absolutely delighted to find this forum.. currently trying to work out the sound issue.. no sound on my laptop.. have been reading ur suggestions.. will try them soon and get back... cheers!

---

### Post by Shabbir Ahmed on 2008-11-05
.. the sound thing didnt work.. the thing is i am totally new to linux..

---

### Post by ramomamo on 2008-11-05
If you installed oss4 following the steps, try to open ossmixer and check the settings.

---

### Post by thebearot on 2008-11-05
Hey guys,

First, great job for ramomamo for starting a thread like this so newbies like me out here can work our ways to the solutions. (F6V'ers)

I followed this thread here: [http://ubuntuforums.org/archive/index.php/t-916985.html]("http://ubuntuforums.org/archive/index.php/t-916985.html") and the problem with sound was fixed without using oss4 which takes a bit of work to setup.

Hope this helps a bit.

I'm still having problems with flashy streaming videos and clips at the moment so if any of you have any ideas, please fire at well and make my (or ours) life easier.

---

### Post by cenoura on 2008-11-24
> **thebearot said:**
> Hey guys,

First, great job for ramomamo for starting a thread like this so newbies like me out here can work our ways to the solutions. (F6V'ers)

I followed this thread here: [http://ubuntuforums.org/archive/index.php/t-916985.html]("http://ubuntuforums.org/archive/index.php/t-916985.html") and the problem with sound was fixed without using oss4 which takes a bit of work to setup.

Hope this helps a bit.

I'm still having problems with flashy streaming videos and clips at the moment so if any of you have any ideas, please fire at well and make my (or ours) life easier.

hy,
About the flashy videos and stuff I've experienced the same. After some searches I've found that was a problem with compiz. If you disable it, you won't have that problem..although no fancy effects =\

---

### Post by Kaho on 2008-12-13
Thanks for the OSS thing, it worked great with my asus f6v !
Even if OSS is not yet compatible with the system sounds, I'm glad I can finally use Ubuntu on my laptop after having tried to set up audio for ages !! 


As for flashy video, the problem is indeed related to Compiz.
But I found a solution better than disabling Compiz each time you want to watch a video !

Open a terminal :
```
gstreamer-properties
```
And in the **Video** tab , for the default ** Output** choose **X Windows System ( no XV )**
This solved the problem with G-streamer based apps just like Totem player and ... Cheese for the webcam :D


And if you use VLC player you may also need to go in 
**Preferences > Video > Output Modules > Advanced Options > Video output module **
 and choose** X11** instead !

Hope it helps :)

---

### Post by cenoura on 2008-12-13
Nice! I'll try that
hey, does any one of you noticed that the laptops battery can only run about 2h or less? In vista I can have it at almost 3h.. Can battery management be enhanced? Ubuntu's Power Manager options seems a bit limited

Thanks

---

### Post by Kaho on 2009-03-03
Yeah, there aren't many options in Ubuntu to save some battery easily and efficiently ...
I heard about "PowerTOP" (  available in repositories  )  for Intel processors which monitors a Linux system and gives suggestions on reducing power consumption
Maybe it worths give it a try...


Anyway, I would like to know if the **internal mic is working for someone ?**
I'm using OSS which works fine except for recording...
Maybe it works with ALSA ?

I'd really like to be able to use the mic and not having to switch to Vista when I want to use Skype T_T ...

---

### Post by Kaho on 2009-03-04
Okay, after tweaking some options in ossxmix, I finally **got my internal mic and any jack-in mic to work **for recording ( tested it with gnome-sound-recorder, audacity and Skype ! )

And it was rather simple, I can't believe I haven't done it before T_T

If someone using OSS is interested, here is what I modified :

Check in ***gnome-sound-properties*** that you have **OSS4 -HD Audio rec mix** enabled for Sound Capture : 
[[IMG]http://img9.imageshack.us/img9/433/screenshot2hu3.th.png[/IMG]](http://img9.imageshack.us/my.php?image=screenshot2hu3.png)

Mic should work after you set, in ***ossxmix***,  int-mic in **input mode**.
Don't forget to **_check on the mix-mute option for your front output_**, unless you want to have some very unpleasant high-pitched noise !!

[[IMG]http://img9.imageshack.us/img9/7970/screenshot1lo8.th.png[/IMG]](http://img9.imageshack.us/my.php?image=screenshot1lo8.png)

And the microphone seems to work better with Skype in Intrepid than Vista :D

Now my only problem unsolved on my Asus F6V is about the flickering video with Compiz activated, in some application where I can't change video output mode...(  such as Skype... )
Hope that new ATI drivers will fix this in the future...

---

