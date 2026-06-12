---
title: "How to setup Logitech headset with Skype 2.1"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by samuraitor on 2009-08-30
hi,

I have a logitech usb headset which does not work in skype 2.1, but it worked perfectly in the non-beta skype. 

I have tried to change all the setting in sound for the logitech headset.I hear the sound through the headset and I can also speak, but when I start skype, the sound comes from the laptop and not from the headset.

How do I go about fixing this?

Thank you.

---

### Post by ghostwriter78 on 2009-10-21
Hi,

i have the same problem.

had a working skype 2.0.x without pulseaudio (100%cpu fix), ubuntu 9.04 up to date,  voice going over headset, ringing on speaker.

Now after installation of 2.1 there is only pulseaudio, and no way to select the usb headset!

what can we do?

we need skype for business calls overseas and are now in trouble because the update broke the call functionality.

regards
Tibor

---

### Post by hifly1231 on 2009-11-02
I'm having the same problem.  I use the Logitech ClearChat Wireless USB Headset sometimes for Skype calls, and cannot get Skype 2.1 to work with them.  I'm currently still using Skype 2.0, but would like to be able to use the newest version.

HELP!!!

---

### Post by gorade on 2009-11-05
I had the same problem. After some monkeying i got it to work at some level at least with the following: 
In terminal:  gorade@Hippocampus:~$ alsamixer -c 1
You get a GUI where you move around with arrow keys and turn mic and spkr on or off with the m-key.
00 means turned on and MM off.
Hope someone more nowlegeable can give a better advice but now it works anyway.):P

---

