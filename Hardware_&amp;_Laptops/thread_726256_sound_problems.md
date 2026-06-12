---
title: "sound problems"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by rottenpaul on 2008-03-16
hello, Im a complete rookie in linux. I installed xubuntu 7.10 just a few days ago. I have a p5gd1 asus motherboard and i have no sound. The sound card is Intel high definition audio realtek ALC861 8-channel codec with jack-sensing and universal audio jack technology S/PDIF out interface support but when I type aply -l I get nothing in return 

kostas@kostas-desktop:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
kostas@kostas-desktop:~/Desktop$ 

and when i type asoundconf list i get

kostas@kostas-desktop:~/Desktop$ asoundconf list
Names of available sound cards:
SAA7134
kostas@kostas-desktop:~/Desktop$ 

but SAA7134 is the chipset of my TV tuner card and not my sound card.

I also visited [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845) to try to solve my problem by editing /etc/modprobe.d/alsa-base but still nothing.

And i dont think i have a hardware problem. Just a few days ago with windows xp pro everithing was just fine. And i can hear all the annoying bleep bleep from the speakers when i start my pc and when i go to BIOS... 

So I have a problem getting my pc recognise my hardware.. and i dont know why. 

I would appreciate any help from you. 
Thank you in advance.

---

### Post by superprash2003 on 2008-03-17
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

