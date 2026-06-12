---
title: "WebCam Logitech C510"
date: 2010-06-15
forum: Hardware
---

### Post by davekenny on 2010-06-15
Just thought I post this information incase someone else was looking for a webcam.

I got the Logitech C510 today..plugged it in and to works..I used skype and cheese..

-dkenny

---

### Post by rayleighjeans on 2010-07-28
is this the logitech hd webcam c510? just making sure. i was thinking of getting it, but wasn't sure if it was going to work right out of the box. i have 10.04 lts. which version did the camera work for you?

---

### Post by RideBMX on 2010-07-29
Yes, the Logitech HD Webcam C510. Just got one and got it set up without a problem; the camera was detected and automatically used, the microphone needed to be selected in Sound Preferences' Input tab. Works with Skype Beta 2.1.0.81 (downloaded through Ubuntu Software Center) on Ubuntu 10.04.

---

### Post by kunal_nba on 2011-03-29
In my case, Ive also got it to plug and play on the spot under 10.10 Maverick.

But.. the thing is that in cheese, I can get the maximum resolution of the webcam to work.. 1600x1200...

However, it has been impossible for me to get this resolution under Skype.. After trying many solutions found in different forums:

 (EDIT, I GUESS SKYPE FOR LINUX STILL DOESN'T SUPPORT HD VIDECALLS, BUT ANYWAY ALL THIS AT LEAST GOT ME FROM 320 x 240 TO 640 x 480)

Solution 1:

edit /$HOME/.Skype/(YourUserName)/config.xml

<Video>
<CaptureHeight>480</CaptureHeight>
<CaptureWidth>640</CaptureWidth>
</Video> 

Solution 2: 

Preload the libv4l library before running Skype
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

Solution 3:

cd /tmp
wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)
tar xvfj tip.tar.bz2
cd v4l*
make
Wait, until it is finished (it will finish with an error).

Now, enter this in the terminal:

gksudo gedit /tmp/v4l*/v4l/.config

Search for this line in the xml file:
CONFIG_DVB_FIREDTV=m

and change it to
CONFIG_DVB_FIREDTV=n

Now click on "Save", close the text editor and get back to the terminal where you enter these commands (one by one):

make
sudo make install


-------------


None of this neither the combination of all solutions has got the webcam to present a decent video quality under Skype. In Cheese thq resolution is excellent, and very clear camera!

While using skype, you can adjust settings in the camera, such as brightness and contrast, using the v4lctl commands:

"v4lctl list"
"v4lctl contrast 20"
v4l-info

more info: "man v4lctl"
...


If someone has got more information on using this webcam under Ubuntu/Skype and getting better image quality/resolution please share the knowledge..

Much Appreciated..

Best Regards!!

---

### Post by nachorevolution on 2011-06-18
Hi, I just purchased the Logitech c510 and plugged it into my box with 11.04 Natty and it does not work. What can I do to try to get it working?

---

### Post by PC_load_letter on 2011-06-18
> **nachorevolution said:**
> Hi, I just purchased the Logitech c510 and plugged it into my box with 11.04 Natty and it does not work. What can I do to try to get it working?

Check this page and let's know how it goes:
[http://askubuntu.com/questions/45441/will-my-logitech-9000-pro-webcam-still-work-with-ubuntu](http://askubuntu.com/questions/45441/will-my-logitech-9000-pro-webcam-still-work-with-ubuntu)

---

### Post by nachorevolution on 2011-06-19
cool, the video is working now, but not the audio from the build it microphone. Any ideas on where to look there?

---

### Post by nachorevolution on 2011-06-19
> **nachorevolution said:**
> cool, the video is working now, but not the audio from the build it microphone. Any ideas on where to look there?

Nevermind, I found the audio input and got it all working now, thanks!

---

### Post by ezwages on 2011-07-22
Thanks, this was just the info I was looking for...quick and to the point

---

### Post by nbr on 2011-07-29
Hi, can anybody give some feedback on HD 720p recording with guvcview?
Can you record at this resolution at 30 fps? How smooth is the video? Is there any lag?

I'm confused, because this girl says no program can handle 720p/30fps recording [http://www.youtube.com/watch?v=hW-ZoKTef_I](http://www.youtube.com/watch?v=hW-ZoKTef_I), but there are videos like that on YouTube.

Thanks!

---

### Post by the aftermath on 2011-08-27
> **nbr said:**
> Hi, can anybody give some feedback on HD 720p recording with guvcview?
Can you record at this resolution at 30 fps? How smooth is the video? Is there any lag?I'm having syncing issues between the audio and the video whenever I record a video. Not really sure what to do at this point.

Does anyone know the best settings for GUVCViewer?

---

### Post by Zeven on 2011-09-11
I tried using my C510 with Google+ not too long ago and the camera worked fine but I simply couldn't get my microphone to work. I tried both Firefox and Opera and I am on Ubuntu 11.04. Any advice would b much appreciated.

---

### Post by mrady on 2011-11-27
> **nachorevolution said:**
> cool, the video is working now, but not the audio from the build it microphone. Any ideas on where to look there?


Hi, my C510 video working but microphone isn't...what did you do to fix it pls?

---

### Post by mrady on 2011-11-27
> **mrady said:**
> Hi, my C510 video working but microphone isn't...what did you do to fix it pls?
oh dear how simple to fix...found I had to select the mic from the  webcam under Input in Sound Settings...for some reason it didn't do this  automatically!


[LIST=1]
[*]Left-click on the speaker icon (by default at the right of the top desktop panel next to the network applet) and select **Sound Preferences**
[*]In **Sound Preferences**, select the **Input** tab
[/LIST]

---

