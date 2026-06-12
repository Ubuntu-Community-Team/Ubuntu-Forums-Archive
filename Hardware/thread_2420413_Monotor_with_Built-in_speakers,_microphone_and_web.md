---
title: "Monotor with Built-in speakers, microphone and webcam"
date: 2019-06-05
forum: Hardware
---

### Post by hgkrug1 on 2019-06-05
Dear All,

I have a HP EliteDisplay E273m 27-inch Monitor with Built-in speakers, microphone and webcam. Ubuntu 19.04 installed. The system does not seem to pick these components up.

I don't seem to find a solution for this. Anyone with advice? 

It seems to me I may have to pass my monitor on to a colleaque and try to purchase a monitor (or separate equipment) which is known to work with Ubuntu? If this is the only solution, any advice would be much appreciated.

Best wishes
Gert Kruger

---

### Post by howefield on 2019-06-05
Thread moved to the "*Hardware*" forum.

---

### Post by CatKiller on 2019-06-05
You haven't said how you've connected the monitor to your computer, nor how you're testing it.

VGA can't carry audio; while DisplayPort and HDMI can carry audio, the manual says that to use the speakers you need to use a jack-to-jack cable that isn't included. You haven't said which sound output devices you've tried at the computer end. 

The manual also doesn't say how (or, indeed, if) the video and audio might travel from the webcam to the computer. While that data could go down the USB cable, you haven't said that you've connected that. The manual lists a requirement of Skype For Business; you haven't said which software you're using for testing instead.

---

### Post by hgkrug1 on 2019-06-05
Thanks, your reply indeed assist me! I had a VGA cable as well as a HDMIcable connected to the monitor. When I added a USB cable (provided with the monitor) I was able to see the webcam work with Cheese. It does not work with normal Skype. The sound also works but is extremely soft. 

It also picked up the microphone as I was able to talk to a colleague on Skype.  I see theer are several posts about webcam working for Cheese but not for Skype.  Will see if I find one to fix my issue. 

When I run the command: pacmd list-cards

I see: alsa_card.usb-HP_E273m_00000000-00

I will see if I can get hold of a jack to jack cable for better sound.

Any more advice you can offer?

---

### Post by CatKiller on 2019-06-05
Glad to hear that everything's started to work now. 

> **hgkrug1 said:**
> Any more advice you can offer?
The speakers are only 2 W: they aren't going to go very loud. 

According to the manual, there's a volume rocker at the bottom-left of the monitor, as well as a volume scale in the menu system.

The sound settings part of the volume widget may let you boost the volume further.

I've never used a webcam, so I can't help you with that. I understand that the Linux version of Skype was already pretty neglected before it got bought by Microsoft. I have no idea what difference there may be between Skype and Skype For Business.

---

### Post by hgkrug1 on 2019-06-06
The Skype issue was also solved (ubuntu 19.04).  I found the answer from Shag00 (entry #3) at [https://ubuntuforums.org/showthread.php?t=2370169&highlight=webcam+skype](https://ubuntuforums.org/showthread.php?t=2370169&highlight=webcam+skype) 

Just downloaded and isntalled the latest DEB version of Skype from [https://www.skype.com/en/get-skype/](https://www.skype.com/en/get-skype/) 

Initially the webcam was not seen.  There were 2 identical HP HD Camera options for the settings (under Audio and Video).  When I chose the second one, the camera started to work.

I guess this threat can be closed!

---

### Post by CatKiller on 2019-06-06
Awesome. Thread Tools at the top of the page to mark a thread as Solved.

---

