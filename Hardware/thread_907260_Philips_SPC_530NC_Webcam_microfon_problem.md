---
title: "Philips SPC 530NC Webcam microfon problem"
date: 2008-09-01
forum: Hardware
---

### Post by fadenb on 2008-09-01
Hi.

My Mom purchased a Philips SPC530NC webcam with integrated microfon.
It is working fine on windows xp but since we are migrating her onto ubuntu we need it to work there too :p

Video is working fine only the built in microfon is making problems.
It is detected as USB audio device. I turned up and unmuted the mixer via 'alsamixer -c1' (it is detected as secondary sound device).

I tried to record something with gnome audio recorder but get nothing else then silence. when trying the skype echo test (after configuring skype to use the webcam micro) and shouting as loud as possible into the microfon you can recognize quiet but heavily distorted voice.

Any idea on howto get the microfon working properly?

THX!

---

### Post by fadenb on 2008-09-02
I tested a bit more, perhaps this will help to clear this problem

> konstanze@kh:~$ arecord -D hw:1,0 -f dat -c1
Aufnahme Wave 'stdin' : Signed 16 bit Little Endian, Samplingrate: 48000 Hz, Mono
RIFF$&#65533;WAVEfmt &#65533;&#65533;wdata&#65533;arecord: pcm_read:1347: Lesefehler: Input/output error
konstanze@kh:~$ 

the "arecord: pcm_read:1347: Lesefehler: Input/output error" appears about 5 second after i start arecord ("Lesefehler" equals read error in english).

---

### Post by doug1212 on 2008-09-02
Hi,
Probably easier to ignore the usb mic in the webcam and get a cheap headset/mic and use your sound card.
My logitech one doesn't work either.

Doug.

---

### Post by fadenb on 2008-09-02
> **doug1212 said:**
> Hi,
Probably easier to ignore the usb mic in the webcam and get a cheap headset/mic and use your sound card.
My logitech one doesn't work either.

Doug.

Thats exactly what i was trying to avoid :p

I just noticed that the microphone worked after i booted into windows and used it there. any chance to "initialize" the audio device like windows does it?

---

### Post by fadenb on 2008-09-03
after some more testing i can now say that it is working if i booted into windows before restarting into ubuntu.

any way to simulate a windows boot for the usb devices?

---

### Post by IntuitiveNipple on 2008-09-03
That suggests the Linux driver isn't fully configuring the device. Either it doesn't know how (manufacturer hasn't released documentation to enable developers to do it) or the driver has a bug.

It is also possible the camera needs a firmware upload that isn't done in Linux (possibly same reasons as above). Booting Windows, its driver will upload the firmware image to the device. Rebooting without removing power into Linux, the firmware remains in the device.

---

### Post by fadenb on 2008-09-04
thx IntuitiveNipple, i will try to take a look at the data send to the cam in windows. Perhaps my small c skills are anough to extend the driver with a configuration/firmware upload.

---

### Post by surml on 2008-11-03
any progress so far? having similar problems with SPC900NC...

---

### Post by mn_voyageur on 2008-11-09
Does anyone have a solution?

---

### Post by Aszasz on 2009-03-01
Hi everyone,

I also do have problems with my logitech webcam microphone. I only once managed to record an audio line with wxcam but I don't know why it worked back then. After I downloaded several drivers the video is working excellent, but I still can't get audio recording to work. The strange thing is that skype has no problems with the audio (perhaps because ist set to "let skype mix the audio settings")... 
I tried several recording softwares (gnome recording, audacity, wxcam, cheese kwave) but no success. I also don't understand why the volume control doesn't save my changes... is there a possibiliy to do so?
thankful for any hints...
AszAsz

---

