---
title: "Deactivate Speaker (Tower speaker)"
date: 2018-08-17
forum: Hardware
---

### Post by jsorella on 2018-08-17
[FONT=verdana][COLOR=#212121]Hello how are you?
This is my first post in this forum!

It's been a long time since I've been looking for a solution to this problem and I still do not hit the nail.

In my work's office I have a **Dell Optiplex 9020** desktop PC with built-in speaker.
This Speaker is the default sound system.
The bad thing about the Speaker is that whenever I disconnect the headphones, the Speaker becomes the default sound system and the sound comes out there, bothering my co-workers.

I followed several tutorials and I could not achieve anything. I have **Ubuntu 16.04** xenial.
I am attaching a screenshot showing how the Speaker looks like on the sound control panel:
[/COLOR][ATTACH=CONFIG]280766[/ATTACH]

[COLOR=#212121]If you can give me a hand I would thank you infinitely![/COLOR][/FONT]

---

### Post by #&amp;thj^% on 2018-08-17
Have a look here: [https://wiki.archlinux.org/index.php/PC_speaker#Disable_PC_Speaker](https://wiki.archlinux.org/index.php/PC_speaker#Disable_PC_Speaker)

Turning off a particular instance of a sound, while leaving the others operational, is possible if and only if one can identify which portion of the environment generates the particular sound. This allows customizing the selection of sounds.
EDIT: Blacklisting it on the kernel command line is probally the best way. Simply add "**modprobe.blacklist=pcspkr**" to your bootloader's kernel line.

---

### Post by jsorella on 2018-08-17
This Speaker is not the *beeps* speaker, this is mostly an audio device attached to the PC tower. I can listen music with it!

---

### Post by #&amp;thj^% on 2018-08-17
Of course I should have known that>>>but the beeps are pesky also. ;)
This is kind of a clunky way to make it work the way you want but as a workaround.
use 'alsamixer' to change this setting, you will have to select the right hardware device first (press F6), Then "Mute the Master" which should be the first option now be sure Headphone is not Muted. 
**IMPORTANT:** Test with "alsamixer" still open.
Now your sound will only be available with the headphones plugged in. 
To make this setting permanent, run as root:
```

sudo alsactl store
```
Use the same above code to reset back.
EDIT: Also if you have option to pull the wire (Jack) to the speakers out.

---

### Post by jsorella on 2018-08-21
Yay that have worked! Thanks buddy :D

---

