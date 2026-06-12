---
title: "Any way to disable ports on nVidia via GRUB?"
date: 2022-08-05
forum: Hardware
---

### Post by libertyspike138 on 2022-08-05
I have a multi boot system set up and dealing with issues regarding the nVidia GTX 770. I use an old VGA KVM switch so I need to use a DVI to VGA adapter or cable for my main monitor. The problem that I get into is that MacOS does not work with DVI-I, I only get a black screen once the GUI loads so I'm running a secondary DisplayPort to HDMI cable to my monitor so it switches to that once the GUI loads. I tried using DVI-D and that worked fine in MacOS but in Ubuntu 22.04 my screen would randomly go black and was triggered by certain events such as it always going black every time I opened Libre Math as well as it having issues with video and audio stuttering so I have to use DVI-I in Ubuntu. I have tried a number of different cables, adapters, configurations etc. but can't get it sorted due to some limitations or configuration in 22.04.
I currently have a DVI-I to VGA as my main display that works without the blackouts or stuttering in Ubuntu.
I have a DVI-D to HDMI as my mirror on the TV.
I have a DisplayPort to HDMI as my secondary cable to the main monitor so I don't get a black screen in MacOS considering I get no signal over the DVI-I.
So there are 3 cables plugged into the card.
If I boot MacOS it ignores the DVI-I line on my KVM but the monitor switches over to the secondary cable and all is fine on my main display and my TV mirror.
In Windows I am able to disable the secondary DisplayPort line used for MacOS and all is fine on my main display and my TV mirror.
In Ubuntu however it shows 3 monitors even though 2 of them go to the same display. When there are 3 monitors you lose the option to mirror a display and everything is all jacked up. It is irritating to have to unplug this secondary line before booting Ubuntu instead of just having the system disable it like in Windows. I have been looking for a way to disable it but haven't had any luck. I saw a post about passing off GRUB arguments such as video=DP-0:d video=DP-1:d video=DVI-D-0:d to disable the various ports reported by xrandr but I don't know if that is just for onboard Intel video or what because it has no effect here.

---

### Post by libertyspike138 on 2022-08-05
I figured I would also mention that if I use nvidia-settings I can disable the monitor on DisplayPort or even just tell it to mirror all 3 displays even though there are only 2 monitors. I can apply it and see it instantly. I then save it but if I try to open up the Ubuntu display settings it says changes cannot be applied. As soon as I log out and back in again my displays are no longer mirrored...

---

### Post by bert89 on 2022-08-05
Unfortunately, probably not, I tried to do it in all ways and unfortunately it failed, maybe and there is some way that I do not know, maybe someone else will tell you because I would like to know how to do it

---

### Post by libertyspike138 on 2022-08-05
Scratch that configuration as well. I found out that if I use the DVI-D port for the mirror to the TV it also causes audio / video stutter only in Ubuntu just like when I tried it with the main display. So I swapped the 2 cables that are not going to main display.
Main monitor is still on DVI-I to VGA.
Mirror to TV is now the DisplayPort to HDMI.
DVI-D to HDMI is now secondary cable to monitor that I have to unplug before booting Ubuntu. Note: Tested audio / video in MacOS and there is no stutter or blackouts.

---

### Post by libertyspike138 on 2022-08-06
So apparently the audio / video stutter is unrelated to the blackout issue I was having. It has to do with a bug in the audio jack detection but I believe I have resolved it. As far as disabling video ports I'm still stuck with having to remove the cable from my monitor before booting Ubuntu. [https://ubuntuforums.org/showthread.php?t=2477755&p=14107029#post14107029](https://ubuntuforums.org/showthread.php?t=2477755&p=14107029#post14107029)

---

