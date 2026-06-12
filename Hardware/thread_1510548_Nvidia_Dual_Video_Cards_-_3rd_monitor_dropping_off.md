---
title: "Nvidia Dual Video Cards - 3rd monitor dropping offline with PCIe audio card installed"
date: 2010-06-15
forum: Hardware
---

### Post by ikeurb on 2010-06-15
I have dual Nvidia Quadro FX4800's installed on my machine and I am  running three monitors. I am using Nvidia Driver 195.36.15. The two  video cards work great and all three monitors work great as well. The  monitors are set as separate X screens. Screen 1 and 2 are on the first  GPU, screen 3 are on the second card.

My issue started when I installed a PCIe audio card. Now the issue is  that when I reboot, sometimes the second video card will not display  video to the 3rd monitor. I have troubleshot this to be some type of  conflict with the sound card. If I remove the sound card from the  system, the second video card and third monitor again work great. 

Note: This is an intermittent issue. Sometimes I can get both video  cards and the sound card to work together.

When the second video card is not working, I can still see that it is  installed in the system by running lspci | grep VGA.

0f:00.0 VGA compatible controller: nVidia Corporation GT200GL [Quadro FX  4800] (rev a1)
42:00.0 VGA compatible controller: nVidia Corporation GT200GL [Quadro FX  4800] (rev a1)

Also, the Nvidia control panel does not show the second GPU when this  issue arrises.

Thoughts????

---

### Post by ikeurb on 2010-06-24
As a troubleshooting measure, I booted into Windows XP Professional, and everything worked as it should. Both video cards worked as well as the sound card. So its safe to say it is an issue isolated to Linux or Ubuntu specifically.
 
I also tried blacklisting the Alsa "snd-asihpi" driver as well as the vendor supplied "asihpi" AudioScience driver.
 
Added both of the following lines to /etc/modprobe.d/blacklist.conf
blacklist asihpi
blacklist snd-asihpi
 
Upon reboot, both video cards wre working well. Then I manually loaded the  driver using "sudo modprobe snd-asihpi". Audio played after this as well.
 
I then commented out the "snd-asihpi" driver from blacklist.conf and rebooted so that the "snd-asihpi" driver would load upon reboot. Audio played upon reboot but the second video card again stopped working again.
 
Blacklisting both asihpi and snd-asihpi cures the problem. But, I'm not liking the fact that I have to manually load the Alsa snd-asihpi after boot.
 
Ideas?????

---

### Post by Ildanach on 2010-06-25
That's really strange. I have no idea why the sound card should be interfering with that at all. 

I'm trying to configure triple monitors as well, but i'm manually going in and editing the xorg.conf file. 

[LEFT]Try taking a look here ([http://ubuntuforums.org/showthread.php?t=408936](http://ubuntuforums.org/showthread.php?t=408936)[COLOR=Black]) and see if it helps at all. [/COLOR]
[/LEFT]

---

### Post by ikeurb on 2010-06-28
Yea, my xorg.conf is Golden. I used the nvidia-settings tool to create it before adding the sound card. Both video cards and all three monitors are working great, no problems.
 
But, when I installed the audio card and loaded the Alsa drivers, is when the issue started.
 
But, like I said, if I blacklist the audio drivers, all is well. Then after reboot, I can load the audio drivers, and both audio and video work flawlessly.
 
I start the Alsa drivers after boot by adding a line to the /etc/rc.local startup script.
 
sudo modprobe snd-asihpi

---

### Post by Ildanach on 2010-06-28
Hmmm... honestly, just looking through what you've posted, it sounds more like a hardware issue with your second video card more than anything. How old is the card? Are the connections clean?

---

### Post by ikeurb on 2010-06-29
I was thinking that it was a hardware issue too, but...
 
I am working on this as a project for work. I have two of these machines, each with the same two video cards, and audio cards. Both machines have the same behavior. I swapped the card slots, swapped the video cards between one machine and the other. No help.
 
I even updated the firmware on one machine, and had HP send me a new motherboard under warranty. Same behavior.
 
As a troubleshooting measure, I booted to Windows which worked great. No problems at all. Windows recognized all the hardware and loaded the drivers without any issue.
 
With all this being said, Im confident it's a problem with Linux or Ubuntu specifically.

---

### Post by ikeurb on 2010-06-29
I submitted a bug report with Ubuntu.
 
Here is the bug report [https://bugs.launchpad.net/bugs/598167](https://bugs.launchpad.net/bugs/598167)

---

