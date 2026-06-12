---
title: "Logitech webcam mic doesn't work"
date: 2009-02-13
forum: Hardware
---

### Post by Elphizo on 2009-02-13
Hi everyone. Yesterday I bought a new webcam, a Logitech Quickcam S5500. I read that it was compatible with linux, but now I can't get the microphone to work. The video works good, but I can't get no audio from the microphone, wich works good under windows. The strange thing is that it seems to be detected, because in KMix there's a new tab titled "USB Device 0x46d:0x9a1" which contains the level for the webcam microphone, but I can't find a way to choose this device in the input source. I searched around the net but I haven't found any help. Can someone please help me? I'm running Kubuntu 8.10 with KDE 4.2.

---

### Post by Elphizo on 2009-02-14
Found something. In Audacity now I can record from the microphone, setting the input source as ALSA: USB Device. Same thing with skype. But in other programs like Kdenlive I don't know how to do, i suppose that I must insert a different path where /dev/dsp is, but I don't know what.

EDIT: Solved: must use /dev/dsp1 for my computer.

---

### Post by Aszasz on 2009-02-27
Hello, 

although the thread has been solved, anybody has also troubles running the microphone of a logitech quickcam? I get the audiodevice detected by kwave, audacity and wxcam but I just can't get a recording result. The cam is also showing after lsusb...
the mic works on skype,the video works always. I think I do have all the necessary drivers. Has anybody an idea to fix this?
Thanks in advance for any hint on this

p.s. I'm a bloody IT-newby, just starting to work myself into Linux, yet not afraid to run a terminal

---

### Post by oregonbob on 2009-04-21
Yes, I have the same problem. I have Ubuntu Intrepid (8.10) with Gnome with Logitech Quickcam S5500. It works fine in Skype after I adjust the settings, but that is the only application. Where I would really get it working is on Seesmic.com . I understand it uses flash for recording video/audio realtime. It works great under Windows, but on Linux the built in mic does not work. It only displays a choice for audio of "Linux Mic", which I think is the regular audio, not the Quickcam.

What is so strange is that it works just great in Skype.

---

### Post by oregonbob on 2009-05-04
I have a Logitech S5500. I can get webcam mic to work in sound recorder and other apps if I do menu -> Preferences -> Sound -> 
  Sound Capture = USB Device 0x36d:0x9a1 USB Audio (ALSA)
I also set default mixer tracks to USB Device 0x46d:...... (Also mixer)

After that sound recorder works perfectly.

Now if I could just get AdobeFlash 10 plugin to recognise the above as the "Linux Microphone" device I would be thrilled. I use a web app to record video chats on a webcam (seesmic.com).

---

### Post by makifer on 2009-12-14
Hello,

I am a newbie, and to be honest I didn't understand how you solved your problem (/dev/dsp1 ???).  

I am using ubuntu 9.04  and my  logitec 5500s mic does not work.  I tried  

Preferences -> Sound -> 
  Sound Capture = USB Device 0x36d:0x9a1 USB Audio (ALSA)
I also set default mixer tracks to USB Device 0x46d:...... (Also mixer)

and still it didn't work.  Then I realized that my usb audio alsa microphone is muted under volume control, and whatever I do, I couldn't unmute it.  

Any help is appreciated.

---

### Post by mrhhug on 2011-03-09
had to ```
sudo /etc/init.d/alsa-utils stop
```

THEN

> **oregonbob said:**
> I have a Logitech S5500. I can get webcam mic to work in sound recorder and other apps if I do menu -> Preferences -> Sound -> 
  Sound Capture = USB Device 0x36d:0x9a1 USB Audio (ALSA)
I also set default mixer tracks to USB Device 0x46d:...... (Also mixer)

After that sound recorder works perfectly.


worked for me perfectly - ububntu did not like fore me to remove my logitech C200 webcam - when i reconnected the USB, the video worked fine but i had to stop and restart the mic

---

