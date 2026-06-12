---
title: "Default sound device for Skype?"
date: 2010-07-18
forum: Hardware
---

### Post by darkmaxa on 2010-07-18
I'm using Asus Xonar DX PCIE sound card as a default output device (on board audio chip is disabled in BIOS), but only for Skype I'm using Logitech **USB** headset.

Everytime when I want to use Skype, I must go to Sound Preferences and manually switch output from Xonar DX to Logitech headset.

Is there any way to set default sound device (Logitech headset) for Skype?

In Win7, when I connect Logitech headset, it becomes default device for Skype automatically.

If is not possible to link particular app with sound device, is it possible that Logitech headset become default sound device just after plugging into USB port.

---

### Post by kostkon on 2010-07-18
Install the *PulseAudio Volume Control* utility. It will allow you to set an input and an output device for Skype (just make sure it is running before opening the volume control).

PulseAudio will remember your choice and will redirect the sound coming from Skype to your headset, every time you connect it to your pc (like in Win 7).

---

### Post by aidenscool09 on 2010-07-18
Try the solution here, 
```
http://ubuntuforums.org/showthread.php?t=1326505
``` 
I had exactly the same problem as he did, what it does is makes your sound settimgs keep the same on restart so you don't have to do it every time you restart your computer, it works. Basically, all you need to do is do
```
sudo gedit /etc/init.d/alsa-utils
```
 and then comment out the line where it says
```
mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```
Now it should keep your configuration when you restart.

      Aidenscool09

---

### Post by aidenscool09 on 2010-07-18
And yes, it does do the same thing as kostkon said, but i would think his is probably easier and safer. But good luck with Ubuntu (in a good way) anyway.

---

### Post by darkmaxa on 2010-07-18
> **kostkon said:**
> Install the *PulseAudio Volume Control* utility. It will allow you to set an input and an output device for Skype (just make sure it is running before opening the volume control).

PulseAudio will remember your choice and will redirect the sound coming from Skype to your headset, every time you connect it to your pc (like in Win 7).

Thx, that's it! Works even better than on Win7! \\:D/

---

### Post by HotForLinux on 2010-08-09
> **darkmaxa said:**
> I'm using Asus Xonar DX PCIE sound card as a default output device (on board audio chip is disabled in BIOS), but only for Skype I'm using Logitech **USB** headset.

Everytime when I want to use Skype, I must go to Sound Preferences and manually switch output from Xonar DX to Logitech headset.

Is there any way to set default sound device (Logitech headset) for Skype?

In Win7, when I connect Logitech headset, it becomes default device for Skype automatically.

If is not possible to link particular app with sound device, is it possible that Logitech headset become default sound device just after plugging into USB port.

I have the same problem you had, but in Lubuntu Lucid Lynx, so I started a thread:

[http://ubuntuforums.org/showthread.php?t=1547899](http://ubuntuforums.org/showthread.php?t=1547899)

There you will see a way to asign a card to an application like Aqualung  (I don't think that's always possible) in the paramenters of the  application's call.
I would like to know the path you followed to solve your problem step by step so that I can try it in Lubuntu.

---

