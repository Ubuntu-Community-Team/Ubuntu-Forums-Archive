---
title: "Logitech music anywhere USB"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by castorjay on 2006-12-08
I am currently running kubuntu, but i am positive this isnt a kde problem, so it should apply to ubuntu as well.  i have a set of wireless logitech usb headphones, im sure you all have seen them, the black and silver ones that got discontinued because the headband kept snapping in half.  anyway, i cannot get them to play in linux.  i have went to google hit after google hit only finding threads applying to headsets, as in with microphones built into them.  a friend suggested to map my alsa output to a new dsp, i figured out that the logitech is dsp2, so i remapped it but sound still only comes through speakers (dsp0).  he also suggested to do alsamixer -c 2 which should have changed the alsa output to the usb device, and when i type that command it does indeed show me that its a logitech music anywhere usb, and theres 2 control options.  one for the microphone (which my headphones dont even have a mic) and the other for volume.  the mic volume is at 80 by defult i believe, and i can lower or raise it.  the sound control will not allow me to increase or decrease the volume.

i am fresh out of ideas, and if anybody can point me in some direction id be grateful.

---

### Post by bayonetblaha on 2007-12-18
I have a Logitech Music Anywhere, but it isn't a headphones, it's a device to send music to a stereo system. I finally got it to work this way: I typed "asoundconf list" to show all the available sound devices ("Tra" and "Intel"). Then I typed "asoundconf set-default-card Tra" and reopened Amarok. Works great! Yours is probably a USB sound card like that.

---

### Post by king20878 on 2008-04-21
Just a note.  The USB adapter works wonderfully with Pulseaudio.  It shows up as a second audio card and you can switch the output to it on the fly on an application by application basis with pavucontrol.  It's great.

---

