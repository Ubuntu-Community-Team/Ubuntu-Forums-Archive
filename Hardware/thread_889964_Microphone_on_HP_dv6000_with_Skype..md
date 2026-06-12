---
title: "Microphone on HP dv6000 with Skype."
date: 2008-08-14
forum: Hardware
---

### Post by Soupcan on 2008-08-14
I installed Skype earlier today, and used the test call. I can't get the microphone to pick anything up. Is there something I need to do? 
Also:
If this is in the wrong place for this thread, I apologize.

---

### Post by stefanadelbert on 2008-09-02
I'm having a similar problem. I bought the dv6836tx over the weekend and immediately install Ubuntu 8.04 from CD and updated. 

The webcam worked fine in Skype without any fiddling, but the mic didn't. I tried fiddling the capture source in Skype to get input from the built-in mics, but couldn't get any signal.

Anyone had any luck using the built-in mics in Skype?

---

### Post by stefanadelbert on 2008-09-24
I did manage to get this working.

Basically, I opened Volume Control, went to Edit | Preferences and selected all tracks. This provide a few new tabs in the main windows, including Recording and Switches. On the Recording tab, ensure that both Capture and Digital are enabled and their volumes are turned up.

In Skype Options | Sound Devices, set Sound In as HDA Intel (hw:Intel,0) and tick the "Allow Skype to automatically..." checkbox.

Hope this helps.

Stefan

---

### Post by rotnacogeid on 2008-10-12
I have the same problem. I tried changing the Recording tab in the Volume Control. However, it only appears the "digital" option and not the "capture" option. 

I used the sound recorder application to record something. It didn't work either. That makes me believe that this problem is not particular of skype and that it is related to the dv6000 sound card driver for ubuntu

---

### Post by Flag on 2008-10-12
Hi,

Am using Ubuntu 8.04 with Skype on an Acer laptop, with this machine I need to use " front mic " Double click on the volume icon and go to options in Alsa mixer.
Can imagine that on a desktop you can play around with simular choices.

---

### Post by kiddykoff on 2011-02-27
i have a dv6815nr and the mic works fine in skype and other applications just fine. I'm running 9.10 64 bit

---

