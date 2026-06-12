---
title: "Mic not working on Acer Aspire 1640 laptop"
date: 2008-07-13
forum: Hardware
---

### Post by srippon on 2008-07-13
G'day folks

I'm reasonably new to Ubuntu and am having a little trouble getting the in-built mic or the mic jack to work.  I have an Acer Aspire 1640 laptop running Ubuntu 8.04.

Under: System > Preferences > Sound
The 'Sound capture' option is set to 'ALSA - Advanced Linux Sound Architecture'.
When I click the [Test] button the 'Testing Pipeline' window opens but just sits flashing back and forth not giving any other feedback.

I've tried the other available options.  Had similar results with nearly all except for the follow options which produced an error messages when I tried the test.

OSS - Open Sound System:

---start---
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for recording.
---end---

PulseAudio Sound Server:

---start---
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
---end---

I've been using the [Make a test call] function in Skype to test the mic.
Unfortunately nothing I've tried seems to work :(

Any help would be deeply appreciated.
Thanks in advance.

Cheers,
Scott.

---

