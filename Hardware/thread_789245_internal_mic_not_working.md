---
title: "internal mic not working"
date: 2008-05-10
forum: Hardware
---

### Post by cubastreet on 2008-05-10
Hi,
Nearly everything is working in my hp dv6736nr now, but not the mic.

Audio out works fine. can anybody offer any help? I'd love to get it working for voice calls.

---

### Post by cubastreet on 2008-05-10
I just tried with a mic plugged into the jack, and that works. Still no luck with the internal one.

---

### Post by roma2 on 2008-05-10
If you already haven't, try this - taken from the Lenovo Thinkpad wiki ([http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#Audio)]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#Audio")

  > Audio

Works great out of the box, just the microphone has to be activated, it is considered a generic capture source and is muted by default.

To unmute the microphone:

    * Right Click on the volume icon next to the clock and click on "Open Volume Control" 

    * Click Edit -> Preferences. A list of devices will be displayed, you should check the following (Do not uncheck any existing items): 

     Input Source
     Capture

    * Click Close and there should be two additional tabs "Recording" and "Options". - 

    * Click Recording and click on the microphone under the Capture slider so that it no longer has a red line through it, and put the slider up as it may be deactivated. 

    * Click Options and under capture source select internal mic. 

To test your mic using Sound Recorder select Capture as the sound source.

This solution has been tested with Sound Recorder and Skype. 

---

### Post by cubastreet on 2008-05-10
No luck with that, but thanks anyway.

---

### Post by pandre45 on 2009-03-04
cubastreet,

have you had any luck in getting your internal mic to work?

---

### Post by wasabishot on 2010-06-08
Hello

I'm having a distorted sound on my internal mic...
using hp pavilion dv9730us
everything works great.... but the internal mic sound is fuzzy... people complain when talking in skype... so can't really enjoy the facility... any idea how to fix it?

---

### Post by flying_174 on 2010-06-09
This is what solved the issue for me.

From Ubuntu Software Center 
Install Default Sound Card and Pulse Audio Volume Control 
Then, open Pulse Audio Volume Control. Select Input Devices. There  should be 2 sliders, and a input tester at the bottom. Speak into the  mic. you will know if it is working. If it is not, slide the slider that  says Front Left, to 0%. Now speak. If the mic works here your good to  go. 

Hope this helps.

---

### Post by lidex on 2010-06-09
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```

---

### Post by wasabishot on 2010-06-14
Hey!
thanks for your replies!!

so lidex- i did exactly what u said, but after reboot it just doesn't load any sound card. 

It's important I mention that since a while I don't use pulseaudio as i removed it according to this thread: 

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273")

I also saw your message in the other thread I opened for this problem.

so maybe more details will help. I'm working only with alsamixer, and thanks to some new gnome-applets I have a volume control designed for alsa.

when I open gstreamer-properties I can choose in the input tab between Alsa or OSS.

when I choose Alsa I can control the amount of noise in the mic with the "Digital" Scroll in the mixer, but it never stops at all, only when down to zero, but then I can't hear my voice either.

When choosing OSS I can't control the amount of noise but it is not too noisy, but still noisy, so can't use the internal mic.

I should say that in both cases when using an external mic (jack) so I can't hear noise at all, only when choosing Alsa and "digital" gain up to max.

any other ideas?

---

### Post by wasabishot on 2010-06-14
here I direct you all to the thread I opened for my problem

[http://ubuntuforums.org/showthread.php?p=9425501#post9425501]("http://ubuntuforums.org/showthread.php?p=9425501#post9425501")

I hope someone can go there and advice me.

cheers.

---

