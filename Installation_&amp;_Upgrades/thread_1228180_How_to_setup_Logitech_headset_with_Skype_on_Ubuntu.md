---
title: "How to setup Logitech headset with Skype on Ubuntu"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by philidox on 2009-07-31
I"m in Kuwait waiting to go to Iraq so I don't have all the time in the world but I love you ubuntu guys so much I'll do my best.  They say a picture is worth a thousand words so please take a look at my screenshots and they explain how to put your settings.  I use pulse audio in conjuction with the default sound manager.  Here is the link that shows how to setup pulse audio [http://ubuntuforums.org/showthread.php?t=997506(special](http://ubuntuforums.org/showthread.php?t=997506(special) thx to markubuntu).

Here it is
1. Simply plugin the Logitech usb headset device
2. Go to sound settings(System>Preferences>Sound)
3. Use the drop down box and change "Sound Events" "Music and Movies" all to **Logitech Logitech USB headset USB Audio (OSS)**
4. Use the drop down box and under "Audio Conferencing" change the "Sound Playback to **Logitech Logitech USB headset USB Audio (OSS)** and "Sound Capture" to **Logitech Logitech USB headset USB Audio (ALSA)**
Note: leave the default mixer track to its default
5. Ensure to click on "Test" next to each sound device, its very important that you hear thru your headset when you click test on each device and even more important that you can hear yourself when you click on "sound capture" under "audio conferencing".
6. Startup skype and signin.
7. Go to options or hit "Ctrl+O".
8. Go to sound option Sound devices and change all the sound device to Logitech USB Headset(hw:Headset,0)
9. Click apply and click on "Make a test sound" and "Make a test call".

If it all goes well you should be good to go.  Restart your computer if it doesn't initially work.  Take a look at the screenshots!

---

### Post by merlinus on 2009-07-31
That is my setup, and it works perfectly.  This one was the key:

8. Go to sound option Sound devices and change all the sound devices to Logitech USB Headset(hw:Headset,0)

---

