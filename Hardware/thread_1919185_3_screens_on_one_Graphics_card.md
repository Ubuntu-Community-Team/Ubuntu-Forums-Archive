---
title: "3 screens on one Graphics card"
date: 2012-02-02
forum: Hardware
---

### Post by tep200377 on 2012-02-02
Hi! I'm currently using an ATI HD 5770 and am running 3 screens with twinview. The only problem is the lagg and det jerky window dragging. So I just bought a new card, an GTX 560 1GB ram. With two DVI and one DP, just like the ATI.

I was actually hoping that the Nvidia driver was better than the ATI driver. Ive had that experience from before. 

But when i Run nvidia-settings, I can only manage to activate two screens. Nvidia-settings halts if I try to enable the thrid one.

Is there someone out there who uses 3 screens on one card that dont have any of my problems as mentioned above?

What HW should i buy to have a simple desktop ( no gaming ) with 3 screens in twinview. I do not want to have 3 separate screens. 

This is beginning to be a dealbreaker for me and linux. I'm tired of the low priority multiple desktops have on linux.

---

### Post by Maddmaxx on 2012-07-29
Amen to that brother! I'm currently running 2 HD 5770 cards, and managed to get all 3 monitors working, with no compositing, 2 1920x1080 monitors on card 1, and a 52" TV on the second card (HDMI). For the most part video performance is reasonable. I used CCC to set it up, took a LOT of playing around, but now experience the same lagging you describe when dragging windows between monitors. 

If I could just have XBMC running on the TV, off the second card and the rest the way it is, I'd be okay with that, but XBMC doesn't give me the option to select one monitor, instead it spreads over all 3 monitors. So VLC it is with the video window on the TV, with the playlist undocked on monitor 2, and the file manager in monitor 1. Classic setup I've used for years. I'm too afraid to do any more at this point until someone comes up with a surefire way. Found out the hard way and through 3 reinstalls that backing up the xorg.conf file isn't enough. 

I'm also getting message "Xlib:  extension "RANDR" missing on display ":0.0"." when installing packages with Synaptic. Since I got this setup working reasonably acceptably I haven't been able to open the CCC as user or superuser so it's probably WAY too much to ask if compositing will work with this setup huh?

This is probably 3 threads worth of questions, but let's see where it goes. Thanks!

---

### Post by Jagoly on 2012-07-30
Bar the 590, all 5xx series nvidia cards will only run two screens per card. 3 screens is not possible with a single 560.

---

### Post by Gentox on 2012-08-09
> **tep200377 said:**
> The only problem is the lagg and det jerky window dragging. 

No idea if it works but i found this in another thread to fix the lag.

> To fix the lag, you need to set a parameter in Grub2

[LIST=1]
[*]Edit /etc/default/grub[INDENT] 	Code:
 	sudo vi /etc/default/grub 
[/INDENT]
[*]Look for GRUB_CMDLINE_LINUX_DEFAULT=
[*]Add "iommu=pt" to the string after the variable[INDENT]It will look like:[INDENT]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash iommu=pt"[/INDENT][/INDENT]
[*]Now save the file and update your grub[INDENT] 	Code:
 	sudo update-grub2 
[/INDENT]
[*]Now all you have to do is restart your machine and everything should be working!
[/LIST]


Thanks to Arjenzwerver

original post:
[http://ubuntuforums.org/showthread.php?t=1999966](http://ubuntuforums.org/showthread.php?t=1999966)

---

