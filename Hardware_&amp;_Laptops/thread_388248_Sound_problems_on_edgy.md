---
title: "Sound problems on edgy"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by rohandhruva on 2007-03-19
Hi,

I have an Acer TravelMate 3260 laptop. The sound on ubuntu 6.10 edgy and 6.06 daper works out of box. However, when I connect a headphone in the jack, the sound continues to play from both the laptop speakers as well as the headphones. On windows, the sound from laptop speakers stops the moment I insert the headphones, which is the intended behaviour. This problem occurs in both edgy and dapper, one the live cd as well as after installing.

Any pointers or solutions, please ? The sound card in Intel HDA Audio Realtek ALC883. 

The problem occurs in both gnome and kde. The respective mixers - kmix and gnome-mixer - show a different channel for normal speaker audio, and one for the headphone. Is that correct ? 

The above behaviour, is it a bug, or a configuration problem ? I mean, should a file a bug on Launchpad describing this ?

Thanks a lot !

---

### Post by qamelian on 2007-03-19
The automatic switching off of the speakers when headphones are plugged in is a feature of the manufacturer's Windows drivers. You may be able to get this working by running alsamixer in a terminal. It has a setting for headphone detection that may be switched off by default.

---

### Post by rohandhruva on 2007-03-19
Is there anyway I can emulate that behaviour in linux ? It works if I manually mute the "Surround" channel, so is there a way I can define that "Whenever headphone is inserted, run command foo, that will mute the mixer channel" ?

In alsamixer, I see no option to enable or disable headphone detection.

---

### Post by qamelian on 2007-03-19
Except for alsamixer I don't no of any other way. The switch in alsamixer is to the right of the headphone volume meter and is labeled headphon and the item label near the top of the display refers to it as Headphone Jack Sense.

---

### Post by rohandhruva on 2007-03-20
Again, I think it's a driver problem. Since I have no volume bar for headphone - it is only a switch, mute or unmute. There is no option labeled "Headphone Jack sense". 

Any other ideas, please ?

---

### Post by udienz on 2007-09-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/128241](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/128241) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 > **rohandhruva said:**
> 
Any other ideas, please ?
rohandhruva, i have same problem with you... see [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/128241](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/128241)
refer for this bug you must recompile alsa-drivers

---

### Post by rohandhruva on 2007-09-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/109882](https://bugs.launchpad.net/bugs/109882) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yes, I'm currently on feisty. However, running arch linux I see that headphone automute has been implemented in the latest alsa, and works out of the box. 

Any instructions where I can see how to recompile those alsa drivers which arch uses .. presumably the latest .. for Ubuntu Feisty ? And can I check whether gutsy already implements this fix ?

Cheers..

---

### Post by braddock on 2007-09-06
I am also having this problem of the main speakers not muting when the headphone is plugged in on the official Dell "Ubuntu Laptop" E1505n running feisty.  

It occurs about once in three times that I plug in the headphones, and once it happens I need to reboot to get the main speakers to properly mute again.

---

