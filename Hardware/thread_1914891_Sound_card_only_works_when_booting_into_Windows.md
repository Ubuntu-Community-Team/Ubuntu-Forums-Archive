---
title: "Sound card only works when booting into Windows"
date: 2012-01-25
forum: Hardware
---

### Post by HeartAttack on 2012-01-25
First off, some prerequisite information:
I dual-boot, with Ubuntu Lucid on one partition next to Windows XP on a second one. The sound card in question is a **Creative Sound Blaster 5.1 VX**.

Now, I'm not saying the sound card doesn't work under Lucid - it absolutely does. But not if I turn on the computer and go to Ubuntu right away. If I do that, all that comes out of the speakers essentially boils down to *kkkhrzkhkhkhrzzzz*. You get the idea. It's horrible. To fix it, I have to boot into Windows once, and I can basically reboot right away when the system is up and go to Linux if I want to. From there on, I have no sound issues until I turn off the computer, even just for a few seconds.

It's actually not even all that annoying, I'm just curious as to what the heck could have caused this insanity. I could honestly not think of any good reason.

---

### Post by madvinegar on 2012-01-25
I found the following info for your card.:

[RIGHT][COLOR="Blue"]Not all features on all models supported. On the VX, white noise on playback unless initialized in Windows first. One quirky (but permanent) workaround is to enable the old oss modules, specifically the 100% sound blaster compatible module (sb). You don't have to load the oss modules. The alsa module snd-ca0106 works fine somehow if the old sb module is compiled in the kernel as a module (no white noise).[/COLOR][/RIGHT]

source: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)


You can try this.
Open a terminal and write:

```
gstreamer-properties
```


On the window that will open, the first tab is audio. Change the "plugins" (output and input) to ALSA or to OSS. You can also experiment changing the "devices" options. See if that will help at all.

---

### Post by HeartAttack on 2012-01-28
Okay, I actually read your answer right away, but I told myself "I'm not  shutting the computer off just for the sake of this", set it up and  then planned to respond once I finally turn the computer off and back  on. Which has not yet happened. That would never have happened under Windows, Linux is corrupting me!
Heh. It will happen eventually though. And then I will provide feedback.

---

### Post by HeartAttack on 2012-01-31
Oh well. The only change was that instead of white noise whenever I tried to play any audio there'd be white noise all the time, and louder white noise when trying to play any audio. Success? Not quite, I'm afraid.

---

