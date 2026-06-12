---
title: "Integrated Web Cam on Lenovo u330 and Ubuntu 8.10"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by milhouse07 on 2008-12-04
Hey anyone,
I have installed Ubuntu 8.10 on my Lenovo U330 successfully and gloriously. However, I can't seem to get the integrated web cam to work. I don't think Ubuntu even sees the web cam. Need help, please! 

I'm relatively new to Linux environment, but i can get around, so any help is appreciated! camera

---

### Post by firecow on 2008-12-05
I'm having the same issue.

---

### Post by iggijeffrey on 2009-02-05
I'm planning to install Ubuntu on my Lenovo Ideapad U330, the last I heard the wireless on the laptop wasn't working. Could you tell me if that problem has been fixed. I would like to wipe the computer completely and install Ubuntu on it but want to make sure before.

---

### Post by Ryan B on 2009-04-09
I haven't done this yet since it looks a bit more than 5 minutes effort, but to find out what type of webcam at the command line type:

[FONT="System"]lsusb[/FONT]

My u330 tells me that my webcam is a 'bison' webcam. Search the forums for 'bison webcam' and you will get some instructions about how to install the drivers for the Bison.

The wireless and ATI drivers get detected out of the box on 8.04, as does bluetooth. I haven't had any problems with that. The only thing you need to do is set the graphics card to 'discrete' in the BIOS.

Hope that helps. R

---

### Post by Ryan B on 2009-09-18
Okay, 5 months later I finally got my webcam and mic working on my lenovo u330 and wooohooo skype test call works (with 9.04 Jaunty). Thought others would find this useful.

(1) Get webcam working
(a) This step might not be necessary but this is exactly what I did
To get the webcam working I followed the instructions in this link

[http://forums.linuxmint.com/viewtopic.php?f=49&t=31374](http://forums.linuxmint.com/viewtopic.php?f=49&t=31374)

This got the webcam working in Cheese and Ekiga but was upside down

(b) Flip webcam (this might also do step (a) when it compiles the kernel but don't know) I followed the instruction in this link

[http://radu.cotescu.com/2009/07/31/resolving-vertically-flipped-images-from-webcams-in-ubuntu/](http://radu.cotescu.com/2009/07/31/resolving-vertically-flipped-images-from-webcams-in-ubuntu/)

Woohoo webcam the right way round (I used option flip_webcam 1)

(c) Get the internal microphone to work.
*Open Volume control (right click on volume icon and select)
*Select preferences > check input source (this gives you an extra tab called options)
*Select the options tab and change the input source to 'int mic'

The volume of the microphone is still a bit weak, but it works!

Hope this helps someone. R

Edit: As ragad3 pointed out in another thread the volume instructions don't work on Karmic. I haven't tried the webcam stuff as I am finish my PhD on this computer and can't afford to mess it up at the moment, but ragad3 found that the webcam instructions does not work either on Karmic...
[http://ubuntuforums.org/showthread.php?t=1319756&highlight=u330](http://ubuntuforums.org/showthread.php?t=1319756&highlight=u330)

---

