---
title: "HP Deluxe WebCam KQ246AA on Ubuntu 9"
date: 2010-01-12
forum: Hardware
---

### Post by franrc on 2010-01-12
Hi all,

  I bought a USB WebCam, HP Deluxe Webcam KQ246AA, and I want to make it work under Ubuntu 9.04.

  Any idea? Thanks in advance.

---

### Post by lorsen on 2010-01-13
[FONT=Arial]Did[/FONT][FONT=Arial] you have a look at this page [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)?             [/FONT]

---

### Post by franrc on 2010-01-13
Wow!! Nice response!!
I'll try it as soon as possible!!
Thanks a lot!!

---

### Post by franrc on 2010-01-13
My webcam works fine with Softphone Ekiga and luvcview but it doesn't work under skype 2.1 for linux.
Any idea?
Thanks in advance.

---

### Post by lorsen on 2010-01-14
Did you use Linux-UVC or worked it out of the box with Softphone Ekiga and luvcview?

---

### Post by EnergyEruption on 2010-01-14
Hey franrc,

          I have the same webcam as you, and as a matter of fact, I posted a similar question a few hours ago. Like I said in my post, mine works in skype, but doesn't do anything else. Here's the link to my post, I'll tell you if I get mine to work.

[http://ubuntuforums.org/showthread.php?p=8663114#post8663114](http://ubuntuforums.org/showthread.php?p=8663114#post8663114)

Alex

---

### Post by franrc on 2010-01-14
Hi Lorsen,

  I don't know what you mean :-(

  I have just run Softphone, which is installed by default.

---

### Post by franrc on 2010-01-14
Hi [EnergyEruption]("http://ubuntuforums.org/member.php?u=907957"),

  which version of skype are you using?

  Skype seems to recognize my webcam but when I click on "Preview Video" in "Options" Menu it just does nothing.

  Thanks in advance.

---

### Post by EnergyEruption on 2010-01-14
Hi franrc, 

       I'm using skype 2.1.0.47. Basically, I followed these instructions, posted by lorsen earlier in this post. 

Steps: 

[LIST=1]
[*] Plugged in webcam into available USB. 
[*] Opened up program to use the webcam i.e Skype 
[*] Went to Options -> Video Devices 

[LIST]
[*]Noticed UVC camera at /dev/video0 was selected 
[/LIST]
[*] Clicked the test button and saw video 
[*] Went to Options -> Sound Devices 
[*] Tried to make a Test Call --> No Audio or microphone pick up 
[*] Went to System -> Preference -> Sound selected the Input tab 

[LIST]
[*]Two audio devices were available: 
[LIST]
[*]Internal Audio Analog Stereo (selected) and  0802 Analog Mono 
[/LIST]
[/LIST]
[*] Selected 0802 Analog Mono 
[*] Made some noise, saw it register on the input level meter. 
[*]Closed out Sound 
[*]Re-open Skype Options -> Sound Devices 
[*]Made a Test Call -> Audio works perfectly 
[*]Went to Options -> Video Devices 
[*]Checked to Enable Skype Video, Start Video automatically ..., recieve... video  
[LIST]
[*]from anybody, and show video... to those I have allowed 
[/LIST]
[*]Made a call to a friend, worked flawlessly [IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/biggrin.png[/IMG]
[/LIST]

       After following these instructions, I have no problem using it in skype. I also installed a program called cheese, following the instructions here:
[FONT=Arial][https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)?             
(type in "sudo apt-get install cheese" in the terminal, if I remember correctly) . With cheese, I managed to take photos with the camera, even using the buttons on the camera itself, with a resolution of 1024 x 1280. The only thing I haven't managed to do is record video. When I try to record video with cheese, the picture is shitty and it only records a few seconds. Apparently there's another program for recording video, called ffmpeg, which I managed to install, but I can't run it. 

I hope all this helps you, keep me posted on your progress.

Alex
[/FONT]

---

### Post by franrc on 2010-01-16
Hi,

  Cheese works fine but skype doesn't, I have followed steps as you comment:

[LIST=1]
[*] Plugged in webcam into available USB.
[*] Opened up program to use the webcam i.e Skype
[*] Went to Options -> Video Devices
[LIST]
[*]Noticed UVC camera at /dev/video0 was selected
[/LIST]
[*] Clicked the test button but I don't see video :-(
[/LIST]
  Any idea?

  Thanks in advance.

---

### Post by EnergyEruption on 2010-01-16
Hmm, 

       Try this:

             
In some cases you (VLC, mplayer, amongst others) will need to know the video and audio device files for your webcam. Before you plug in your webcam, try the following two command at a console: 
ls /dev/video*
ls /dev/audio*Make a note of the devices appearing. Now plug in your webcam, allow the system a few seconds to register the device, and run the two commands again. The new appearances should belong to your webcam (for instance, /dev/video0 and /dev/audio2).

     Basically, this tells you what directory your webcam is. Mine says HP Deluxe Webcam KQ246AA (/dev/video0). Also make sure "enable skype video is checked". Other than that, I can't really think of anything else. Hope this works. If not, try to go through all the details on [FONT=Arial][https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)? , you should be able to find a solution. Hope all this helps.

Alex
[/FONT]

---

