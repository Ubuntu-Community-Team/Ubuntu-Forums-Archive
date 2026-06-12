---
title: "Again: Compaq Armada 1592DT"
date: 2004-11-15
forum: Hardware &amp; Laptops
---

### Post by MattOnTheNet on 2004-11-15
Guess the opening sentence in my previous cry for help was taken a little bit too litteral (*Probably a retoric question)* 'cause no one answered my mail.

I've installed the Life-Linux Knoppix on the same laptop and behold! the screen resolution was a beautifull 1024x768, switchable to 800x600 and 640x480.

Could anybody take the time to explain this newbie why it is that another Linux installation does recognize the video adaptor and monitor without any problem but Ubuntu does not. 

By the way, during the installation phase, Ubuntu shows astrixes at 1024x768, 800x600 and 640*480 "to be used" resolutions, so something *was* recognized. In the SystemSettings however, only 640x480 is available.

---

### Post by MattOnTheNet on 2004-11-16
[QUOTE=MattOnTheNet]Guess the opening sentence in my previous cry for help was taken a little bit too litteral (*Probably a retoric question)* 'cause no one answered my mail.

I've installed the Life-Linux Knoppix on the same laptop and behold! the screen resolution was a beautifull 1024x768, switchable to 800x600 and 640x480.

Could anybody take the time to explain this newbie why it is that another Linux installation does recognize the video adaptor and monitor without any problem but Ubuntu does not. 

By the way, during the installation phase, Ubuntu shows astrixes at 1024x768, 800x600 and 640*480 "to be used" resolutions, so something *was* recognized. In the SystemSettings however, only 640x480 is available.[/QUOTE]
 Joy and Jubilations! I've found the command and methode to set the Compaq Armade 1592DT to the resolution I wanted it to be: 800x600. I found the answer myself in another thread.

Thanks for all your help!

(sudo dpkg-reconfigure xserver-xfree86)

---

### Post by wallijonn on 2004-11-18
You may want to provide a link in the above posit to give closure to this thread.

---

### Post by spacelynx on 2005-03-11
[QUOTE=MattOnTheNet]Joy and Jubilations! I've found the command and methode to set the Compaq Armade 1592DT to the resolution I wanted it to be: 800x600. I found the answer myself in another thread.

Thanks for all your help!

(sudo dpkg-reconfigure xserver-xfree86)[/QUOTE]

Hmmm, Zeewolde... dus zou je dit ook moeten kunnen lezen....

Ik heb dezefde laptop en (dus) ook hetzelfde probleem. Zou je me kunnen helpen?

Alvast bedankt.

TonKa
De Kwakel

---

