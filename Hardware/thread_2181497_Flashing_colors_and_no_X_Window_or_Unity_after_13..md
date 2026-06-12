---
title: "Flashing colors and no X Window or Unity after 13.10 upgrade"
date: 2013-10-18
forum: Hardware
---

### Post by AJLeuer on 2013-10-18
Hello,
I've recently run into a problem that's making Ubuntu unusable. First, here's my hardware: I have a Z77 motherboard with a GeForce GTX 670. My monitor is a  Korean 27" IPS with only a single DVI Dual-link connection, and a  resolution of 2560x1440. My problem started after upgrading to 13.10 today. When my system rebooted after finishing the upgrade, Unity and the X  Window System were non-functional. After booting up, all I see is a  screen that flashes between red, green, blue, various blacks, greys, and  whites at regular intervals. From here I can switch to command line,  and that displays fine, but starting lightdm takes me back to the flashing colors. I had this problem on 13.04, but I was able to fix it by editing xorg.conf with the proper information about my monitor. No such luck for 13.10. I have tried: 

  
[LIST]
[*]installing different drivers (i.e. nvidia-current, nvidia-experimental) 
[*]plugging into both DVI ports on my GTX 670 
[*]editing xorg.conf myself 
[*]letting the Nvidia package do the xorg.conf configuration automatically 
[/LIST]
  Admittedly I know very little about X Window system, and all my editing was based on xorg.conf  files posted by others that were claimed to work, none of which used  the same combination of monitor and video card as mine. I'm out of ideas  at this point, input from someone who knows what they're doing would be  greatly appreciated.

---

