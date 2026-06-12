---
title: "What is the /dev name for my microphone?"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by diablo75 on 2007-05-20
I just put xvidcap on my laptop and intend to make some demonstration and tutorial videos of Ubuntu in action for my website.  In the preferences, under audio input, it asks for a device name to be entered.  Currently, it has the following device listed:

/dev/dsp

What is this DSP device?  It is able to record the microphone, but there's this hissing noise.

I was using a separate sound recording piece of software earlier, which you could use a GUI config to select the microphone out of a list of input devices, and doing this produced a much cleaner audio recording from the microphone.  But this DSP device just isn't going to cut it.

So, I suppose if worse comes to worse, I could make these screencasts with two seperate pieces of software, but that would just be too much "fun", if you know what I mean, ha ha.

Any help would be appreciated.  Thanks guys!

---

### Post by Tilo on 2007-05-31
/dev/audio

---

### Post by diablo75 on 2007-05-31
That made no difference.  There is still this terrible noise (high pitched scratch like sound) that is in the background with my voice being recorded.  The audio recording software that I've been using outside of xvid "Sound Recorder" records audio perfectly.  Might this be a problem with XVidcap itself?

---

### Post by Tilo on 2007-05-31
you could try to connect an exernal microphone and check if that sounds different, 
and you could also try alsamixer or xaumix to check what the levels on the sound devices
are..

---

### Post by diablo75 on 2007-06-01
An external microphone is what I have been using.  There is no built-in microphone on this laptop.

---

### Post by charly4711 on 2007-06-01
Well, what device name DID you select with the other sound recording application?
What are the bitrate, channel, sample rate settings in xvidcap?

---

### Post by diablo75 on 2007-06-01
Attached are two screen shots.  One from the sound selection setting for Sound Recorder (the quality behind the menu is CD quality, mp3), and then the screen shot from Xvidcap, showing the recording device as "dev/dsp"

---

### Post by taikonaut on 2008-02-11
EXACTLY the same problem here!

Any solution yet?

---

### Post by diablo75 on 2008-02-11
I ended up using gtkrecordmydesktop for what I was trying to do and it seemed to solve the problem...

---

### Post by gigaferz on 2008-02-14
anybody figured it out yet?

  vlc
 since my webcam is dev/video0
  what is the microphone dev name?? 

  How can i figure it out?

  I can record with my mic using soundrecorder but how to make it work on vlc?

---

### Post by mw44118 on 2008-03-08
I own a Dell Inspiron 1420N and I want to use xvidcap with an external microphone.  The microphone built into the laptop is too quiet.

Anyway, when I record with arecord, my box uses the external microphone.  But when I use xvidcap, it uses the built-in microphone instead.

I am speculating, but I think that xvidcap doesn't use ALSA.  Instead, it is using something lower-level, so the settings that I apply with alsamixer are irrelevant.

---

