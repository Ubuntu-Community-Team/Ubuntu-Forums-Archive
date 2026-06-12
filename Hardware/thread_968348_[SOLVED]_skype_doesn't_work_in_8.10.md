---
title: "[SOLVED] skype doesn't work in 8.10"
date: 2008-11-02
forum: Hardware
---

### Post by giuspen on 2008-11-02
I have an acer TravelMate 2300 with integrated intel audio and video cards, with ubuntu 8.04 skype worked great both audio and video calls, but now with 8.10 i can't even do normal calls, i receive instead a "problem with audio playback".
Do somebody have my same problem? Do anybody can advice me something I can do except to reinstall 8.04?

---

### Post by ThaRabbit on 2008-11-02
> **giuspen said:**
> I have an acer TravelMate 2300 with integrated intel audio and video cards, with ubuntu 8.04 skype worked great both audio and video calls, but now with 8.10 i can't even do normal calls, i receive instead a "problem with audio playback".
Do somebody have my same problem? Do anybody can advice me something I can do except to reinstall 8.04?

1.Go to Options
(you can do this By Pressing Ctrl + O when the skype window is active, or by right clicking the taskbar icon and selecting options)

2. Go to sound Devices

3. Set all devices to pulse

4. Use the test buttons to test this, you should hear sounds from skype now

5. Apply and restart Skype, all should be fine now.

---

### Post by robert114 on 2008-11-02
I couldn't record with pulse. So after trial and error I found the correct input device in Skype.

Oh, please click apply first and then test the settings

Robert

---

### Post by giuspen on 2008-11-03
Thanks a lot, I will try later and mark as solved if it works.

---

### Post by giuspen on 2008-11-03
> **ThaRabbit said:**
> 
1.Go to Options
(you can do this By Pressing Ctrl + O when the skype window is active, or by right clicking the taskbar icon and selecting options)

2. Go to sound Devices

3. Set all devices to pulse

4. Use the test buttons to test this, you should hear sounds from skype now

5. Apply and restart Skype, all should be fine now.

it works. thanks a lot again. :KS

---

### Post by giuspen on 2008-11-09
> **robert114 said:**
> I couldn't record with pulse. So after trial and error I found the correct input device in Skype.

Oh, please click apply first and then test the settings

Robert

Robert was right... I also had a problem with "Sound in" device and so I changed from pulse, trying all available till I found the right one.

Finally I advice to put everything on pulse in the beginning but if then there is a problem with one device just try all possible associations only for it leaving others on pulse.:guitar:

---

### Post by ynilesh on 2009-02-17
its not working for me. i have same version of ubuntu.

thanks in advance. 

nilesh

---

### Post by giuspen on 2009-02-19
> **ynilesh said:**
> its not working for me. i have same version of ubuntu.

thanks in advance. 

nilesh

sad to say but I switched back to ubuntu 8.04 to have skype working regular (audio + video).
regards.

---

### Post by gjosef on 2009-03-07
Even though I seem to find the "right" input device, I still can not hear my own voice in the playback of the echo/test call. I use a HP NX9420. Could it be my mic's recording volume that is wrong?

---

### Post by gjosef on 2009-03-23
> **gjosef said:**
> Even though I seem to find the "right" input device, I still can not hear my own voice in the playback of the echo/test call. I use a HP NX9420. Could it be my mic's recording volume that is wrong?

I think it was. Got it to work after a bit of fiddling around (also uninstalled and reinstalled pulseaudio, so I'm not 100% sure about what it was that helped...)

---

### Post by giuspen on 2009-03-26
I tried skype on 8.10 of my cousin's laptop (acer, like mine) and also on theirs skype doesn't work.
So I installed for them 8.04 too, and advice 8.04 to who has an acer and use skype a lot (hoping that in 9.04 skype will work properly both audio and video)

---

