---
title: "Microphone Not Working"
date: 2010-11-28
forum: Hardware
---

### Post by Tchoob on 2010-11-28
So I'm completely new to ubuntu. I'd always heard great things, and decided to try it out. I'm running ubuntu 10.04, on an HP Pavilion laptop. My webcam works, speakers work, and I seem to have everything working fine, except my microphone.

I have checked all sliders, it's not muted. I've downloaded Default Sound Card and PulseAudio Volume Control/PulseAudio Device Chooser. Nothing is working. I'm sure that my Alsa is fine. I'm just not sure what to do at this point. Skype is a necessity to me, so my microphone is crucial.

Thanks in advance.

---

### Post by miegiel on 2010-11-28
> **Tchoob said:**
> So I'm completely new to ubuntu. I'd always heard great things, and decided to try it out. I'm running ubuntu 10.04, on an HP Pavilion laptop. My webcam works, speakers work, and I seem to have everything working fine, except my microphone.

I have checked all sliders, it's not muted. I've downloaded Default Sound Card and PulseAudio Volume Control/PulseAudio Device Chooser. Nothing is working. I'm sure that my Alsa is fine. I'm just not sure what to do at this point. Skype is a necessity to me, so my microphone is crucial.

Thanks in advance.

For most laptops the trick is to unbalance the mic input. That is to make the left mic input softer then the right mic input.

This is just speculation on my part, but it seems to me that in the windows drivers the left channel of the microphone is used to cancel out noises from your laptop. With many laptops in linux when both the left and right channel are at the same level, the left channel almost completely cancels out the right channel. If you put the left channel to 0% and the right channel to 100% your microphone will pickup a lot of noise. I have my left channel at 50% and the right at 100%, but you'll have to try and see what level works best for you.

edit: assuming your talking about your internal mic ;)

---

### Post by Tchoob on 2010-11-28
> **miegiel said:**
> For most laptops the trick is to unbalance the mic input. That is to make the left mic input softer then the right mic input.

This is just speculation on my part, but it seems to me that in the windows drivers the left channel of the microphone is used to cancel out noises from your laptop. With many laptops in linux when both the left and right channel are at the same level, the left channel almost completely cancels out the right channel. If you put the left channel to 0% and the right channel to 100% your microphone will pickup a lot of noise. I have my left channel at 50% and the right at 100%, but you'll have to try and see what level works best for you.

edit: assuming your talking about your internal mic ;)
I had tried this before, probably should've mentioned that. I've messed around with the sliders for awhile, and nothing is working. And yes, it is an internal mic.

Someone has to know how to fix this problem. My microphone works fine in win7, so it's not a hardware issue.

---

### Post by miegiel on 2010-11-28
> **Tchoob said:**
> I had tried this before, probably should've mentioned that. I've messed around with the sliders for awhile, and nothing is working. And yes, it is an internal mic.

Someone has to know how to fix this problem. My microphone works fine in win7, so it's not a hardware issue.

Test your microphone with *audacity* (it's listed in the software center). It's a sound editor, like office for docs or gimp for pictures, obviously you can also use it to record sound from your microphone.

In audacity I don't need to use the unbalance trick, it just works as you would expect with a stereo mic. In audacities preferences you can select different recording devices (pulse/alsa might not be using the right mic as deault).

If you have an external microphone see if that does work.

---

