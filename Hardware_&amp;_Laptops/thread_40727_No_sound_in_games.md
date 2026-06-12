---
title: "No sound in games"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by Zingam on 2005-06-10
I have installed hoary on my laptop with Realtek AC'97 codec. ALSA does not seem to be supported but I have sound via ESD. On earlier installation I played NWN with sound. Now I don't have enough space to try this game but all other games I've downloaded do not have sound: tuxracer, chromium, abuse-sdl, frozen-bubble. Abuse reports: that I do not have a sound device. But I hear the system sounds of Ubuntu?

So what's wrong here? I installed sdl-mixer, sdl-sound, etc?

Is this because I have no ALSA?

---

### Post by voidlogic on 2005-06-10
yeah, before most games you need to go into the task manager and kill the esd process. you can run it at the "run" when you are done with the game to restart if for your other apps. If this still dosn't work, you may just need an esd plugin for your app.

voidlogic

--------------------------------
I need help! [http://www.ubuntuforums.org/showthread.php?p=202288#post202288](http://www.ubuntuforums.org/showthread.php?p=202288#post202288)
 ](*,)  ](*,)  ](*,)

---

### Post by duffman25 on 2005-06-13
[QUOTE=Zingam]I have installed hoary on my laptop with Realtek AC'97 codec. ALSA does not seem to be supported but I have sound via ESD. On earlier installation I played NWN with sound. Now I don't have enough space to try this game but all other games I've downloaded do not have sound: tuxracer, chromium, abuse-sdl, frozen-bubble. Abuse reports: that I do not have a sound device. But I hear the system sounds of Ubuntu?

So what's wrong here? I installed sdl-mixer, sdl-sound, etc?

Is this because I have no ALSA?[/QUOTE]

I've enabled oss in my System->Preferences->Multimedia Systems Selector and now both video (totem) & games have sound.

---

### Post by jerrykenny on 2005-06-15
I know it's a kludge,  but I install the XFCE4 desktop, and use it for just gaming . . . . 

It's a bit lighter than gnome, frees up a bit of processor power, and sounds in all games are fine.

Its also a really nice desktop.

---

### Post by jerrykenny on 2005-06-15
Bruce89     has posted the cure for this 

"What I did was installed libsdl1.2debian-all and uninstalled libsdl1.2debain-oss. This fixed the sound in PPracer which is the same as tuxracer."

 I just tried it and it works a charm . . . .  :razz: 

You might still want to try xfce if gaming is a little choppy 'though.

---

### Post by Zingam on 2005-06-17
I solved the problem for some of my games after reading a Readme.txt of an old game Shogo. I had to install libsdl-esd (or whatever it is called). It seems that esd is working for my mashine and not OSS or ALSA. When I set OSS or ALSA, there is no sound at all.

Skype does not have any sound now,

:) It seems to my that multimedia and linux are not compatible. :)

---

