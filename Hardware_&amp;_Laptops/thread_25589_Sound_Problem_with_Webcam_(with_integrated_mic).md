---
title: "Sound Problem with Webcam (with integrated mic)"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by amerigo5 on 2005-04-10
I have a sound problem (no system sound, music player sound, etc)  when my laptop/computer starts/boots with the USB Logitech Notebook Pro webcam plugged in. But if the laptop/computer starts/boots without the webcam plugged in and then plug in the webcam after the system starts/boots, the sound works fine.

So with the above observation, the problem might be in the way the webcam module is being loaded. Is it possible that there's a difference between how the webcam module is loaded during and after the boot-up process? Could that cause the sound not to work (when the computer boots up with the webcam plugged in)? Or am I missing something here?

Thanks.

Note: This is a continuation of my prior post: [http://www.ubuntuforums.org/showthread.php?t=22827](http://www.ubuntuforums.org/showthread.php?t=22827)

---

### Post by kombipom on 2005-05-05
I found the following on another website so can't take any credit (or blame) for it. 

add the following lines to /etc/rc.local

# fix for audioproblem webcam, by aRTee:
rmmod snd-usb-audio
service sound stop
service alsa stop
rmmod audio
modprobe snd-emu10k1
modprobe snd-usb-audio
modprobe audio
service sound start

Then reboot with webcam plugged in.

If it doesn't work it might be that your soundcard is not using the emu10k1 driver and you need to change this line to match your driver. 

Hope this helps

Kombipom

---

### Post by amerigo5 on 2005-06-09
[QUOTE=kombipom]I found the following on another website so can't take any credit (or blame) for it. 

add the following lines to /etc/rc.local

# fix for audioproblem webcam, by aRTee:
rmmod snd-usb-audio
service sound stop
service alsa stop
rmmod audio
modprobe snd-emu10k1
modprobe snd-usb-audio
modprobe audio
service sound start

Then reboot with webcam plugged in.

If it doesn't work it might be that your soundcard is not using the emu10k1 driver and you need to change this line to match your driver. 

Hope this helps

Kombipom[/QUOTE]

I tried it but it didn't work. I used "snd_intel8x0" instead of "emu10k1". Maybe "snd-usb-audio" should be "snd_usb_audio". 

However, I tried adding "snd_intel8x0" to the /etc/modules file. (Refer to this post: [http://www.ubuntuforums.org/showthread.php?p=55102)](http://www.ubuntuforums.org/showthread.php?p=55102)). This one worked!!!

---

