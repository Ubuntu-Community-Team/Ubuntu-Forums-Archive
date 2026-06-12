---
title: "Ubuntu 12.04 LTS recomended 319 driver does not work?"
date: 2013-10-18
forum: Hardware
---

### Post by ns6TBHp on 2013-10-18
I have read threads on this forum as well as others, i have asked questions on the Ubuntu irc help. Mostly people just refer me to a Youtube video where the creator of Linux tells Nvidia to go "F" themselves. So I created this thread to hopefully just get an answer.

I installed 12.04 LTS and the driver prompt came up.  installed the recommended Nvidia 319 driver and then was unable to boot into the OS after a restart. I did this twice and twice had to reinstall the OS (i am a noob and ctrl+alt+f1 did not work)

So two questions really:

1.) should I expect the 319 post release updates driver to be any different?

2.) Am I just not gonna be able to use the new drivers?

Thanks for your help, I'm sure you heard it before...

---

### Post by grahammechanical on 2013-10-18
I stopped using Nvidia drivers 2 years back when a buggy Nvidia driver broke 12.04 for several weeks. The open source driver Nouveau has improved considerably since the days when it could not run 3D effects. I use Nouveau all the time. I experimented about a year ago with different versions of Nvidia drivers but I decided to stick with Nouveau. 
 
Do, you have a special reason for using Nvidia drivers? I do not.

Next time a video driver breaks the reboot do this.

At the Grub menu select Recovery mode. At the Recovery menu select Resume. That should get you to a desktop without using the proprietary video driver. Then you can continue to experiment. Which is what it is, an experimentation. 

Regards.

---

### Post by ns6TBHp on 2013-10-19
Thanks for the reply. To answer your question, I use a graphic intensive program similar to a game so FPS etc.. are key. I assumed Nvidia would be the way to go over Nouveau. In fact I do not see a single Nouveau driver offered in application drivers :o

Also, as far as i know, I am unable to select anything really when reboot breaks. I see a flashing cursor top left of the screen but I am able to type characters but they show up delayed. Then if i wait it goes to a checklist with many "OK" marks on the right but doesn't go any further and nothing seems responsive. CTRL+Alt+F1 was non responsive. How would I get to Grub menu in this state and select Recovery mode?

thank you

---

### Post by ns6TBHp on 2013-11-07
SOLVED

I chose the 319 driver and installed, then i ran 
sudo apt-get purge nvidia-304 nvidia-304-updates and then sudo apt-get autoremove and sudo apt-get autoclean

i then rebooted and it now boots with the updated driver!

---

