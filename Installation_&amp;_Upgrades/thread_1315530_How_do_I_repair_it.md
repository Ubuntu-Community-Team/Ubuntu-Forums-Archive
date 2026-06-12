---
title: "How do I repair it ?"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by biohazardhm on 2009-11-05
I've installed the latest version of Ubuntu. I've a dual boot with vista. I installed it and i think i did a mistake while installing because Ubuntu isn't working now. I'm opening my PC and i can select Ubuntu from dual boot screen. Then i think Ubuntu must start booting. It starts but never ends. It stucks at a terminal screen. I think i did a mistake. So, how can i fix it? I wil give extra information as much as i can. Is there any command to repair my ubuntu. 

NOTE: I've HP pavillion DV6 1229ET. I can use windows vista but I want to use ubuntu...

---

### Post by jimbo99 on 2009-11-05
Not enough info. What is happening in the terminal window?  Flashing ?  Nvidia video drivers?

---

### Post by biohazardhm on 2009-11-05
I'm opening my PC, It's coming GRUB boot screen. I'm choosing Ubuntu. Then It starts boot Ubuntu.
But at this part, progress stays there. I can't use a workspace. My display adapter is ATI Radeon 4650.
I activated its driver when i boot from Ubuntu Live CD and i installed Ubuntu into my harddrive. Now, I can't open it. It asks for password. I entered it true. Login is successful. But i can't reach my workspace. If I don't know, is there any command to open workspace? If not, how can i fix that? (Or how can I remove Ubuntu and reinstall it?)

---

### Post by biohazardhm on 2009-11-06
Is there anyone to help me ?

---

### Post by Bunnybugs on 2009-11-06
I guess you should look for a topic with people explaining how to edit your grub-files...

The problems seems to be here, at least... I guess...

But at first: everyone that can help you needs to know what your screen says... otherwise we're guessing about the problem instead of solving it!

---

### Post by masux594 on 2009-11-06
If u can reach a login in a "terminal" way, it means that Xserver is not started.. First of all, have u already installed the ATI drivers? if yes, i suggest to remove these drivers and look if removing that drivers, X run as well.. if u haven't installed yet, so, try to reconfigure the xserver pakage with that command.. ```
sudo dpkg-reconfigure xserver-xorg
```Sysc, A

---

### Post by decoherence on 2009-11-06
when the computer is booting and GRUB prompts you to hit escape, do so and boot in to a recovery mode kernel (usually the second option in the list.)

You should eventually get to a menu with an option to fix the X server. See if that helps.

---

### Post by biohazardhm on 2009-11-09
> **masux594 said:**
> If u can reach a login in a "terminal" way, it means that Xserver is not started.. First of all, have u already installed the ATI drivers? if yes, i suggest to remove these drivers and look if removing that drivers, X run as well.. if u haven't installed yet, so, try to reconfigure the xserver pakage with that command.. ```
sudo dpkg-reconfigure xserver-xorg
```Sysc, A
Thanks to all. I activated ATI drivers and I get this problem. I think the ATI driver problem was solved in this version of Ubuntu but no such luck:/ 
That's AMD's badness. @BunnyBugs's diagnoses are right. If anyone reads this post I've an advice: 
Do not activate ATI drivers if your driver's model is higher than 6000. Thanks to all again^^

---

### Post by Bunnybugs on 2009-11-09
Yeah, there are indeed some driver issues, such lik the 'Software Modem' driver in Karmic... this one is the origin of all the sound trouble

I've removed the driver in Karmic, rebooted, and the sound was just fine!

But, the other bugs kept on kicking my but, so, back to jaunty!

---

