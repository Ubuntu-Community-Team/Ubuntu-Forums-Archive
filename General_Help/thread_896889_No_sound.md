---
title: "No sound"
date: 2008-08-21
forum: General Help
---

### Post by t4l0 on 2008-08-21
Ehhh, yeah... I'm not really sure what to do to get the sound. The sound icon on the toolbar shows a sideways speaker with an 'X' next to it. It says something about a GStreamer or something. Here's a picture.

[IMG]http://img229.imageshack.us/img229/4654/volumenz3.png[/IMG]

This is what shows up when I double-click on the volume control. So any ideas of what I need to do to fix this?

---

### Post by ilovelinux33467 on 2008-08-21
Hello I don't know if this will help you, but look here:

[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

---

### Post by t4l0 on 2008-08-21
Well, thanks for that guide. It probably does help, but I have no idea what my sound card is and I'm not sure how to find out. I'm guessing I'll have to restart and enable it in the system BIOS like it said. But I think I would need to know it's name or at least what I was doing lol

---

### Post by loboc on 2008-08-21
the terminal command
 
```
lspci | less
```

will list all the devices on the pci bus in your system such as your sound card

```
lsmod | grep snd
```

will list the kernel modules (drivers) associated with your sound system

```
aplay -L
```

will list the sound devices that the alsa system knows about which is like the sum of device + driver = alsa device

if you have a defult device listed in aplay then 


```
aplay /usr/share/sounds/alsa/Noise.wav

```

can test your sound card

if alsa works then its a matter of getting gnome to use the card

IN sound preferences you can tell gnome to uses alsa

ADVANTAGE: quick
DISADVANTAGE:  One sound at a time, if your playing mp3's then the pidgin wont make noise when a message is recieved etc 

or you can set up  a sound server

ESD ADV: easy reliable
DIS: old more memroy intensive than :

PULSEAUDIO

ADV: Fancy does things like multiple cards and sound over a network
DIS: NEw and buggy takes some hacking to get it to wwork usally

---

### Post by starving030 on 2008-08-21
I got it to work. It was a matter of messin with the volume or running a few commands. Don't know which one did it but thanks.

---

