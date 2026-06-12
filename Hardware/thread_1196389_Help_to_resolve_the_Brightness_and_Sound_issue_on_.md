---
title: "Help to resolve the Brightness and Sound issue on dell studio laptop"
date: 2009-06-24
forum: Hardware
---

### Post by abhijeetnayak on 2009-06-24
Hi,

Two days back I have installed ubuntu 9.04 on my dell studio 1555 laptop. But I found that the speaker and the brightness adjustment keys are not working. 

I went through lot of forums but did not find any suitable answer to it. 
Could anyone help me to resolve these issues?

Here is the sound card details:
cat /proc/asound/card0/codec#0|grep -i codec
Codec: IDT 92HD73C1X5 

 cat /proc/asound/cards
 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc500000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfc010000 irq 17

System Details:
WLED Screen 15.6",
processor: P8600 (2.4 Ghz)
Graphics: Ati Radeon 512 MB

Thanks
Abhijeet

---

### Post by abhijeetnayak on 2009-06-24
after the update i am able to resolve the sound issue but still facing the non functioning brightness(up and down) keys...

---

### Post by cneil on 2009-06-26
I am having the exact same issue with my Dell Studio 17.  I just purchased it this week.

Just a few minutes ago I started this thread without thoroughly searching the forums.  

[http://ubuntuforums.org/showthread.php?t=1197859](http://ubuntuforums.org/showthread.php?t=1197859)

I wonder if I should delete it.

---

