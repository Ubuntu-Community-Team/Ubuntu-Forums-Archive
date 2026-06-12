---
title: "Sound Card Not Recognized"
date: 2008-08-11
forum: Hardware
---

### Post by Gerald Ford on 2008-08-11
Hi,

I am pretty new to Ubuntu and I like it so far. I've tinkered around a bit to get dual monitors working, but I do not have any sound. When I click on the sound icon at the top of the main page there is a red circle with a line over it on it. What I click on it it gives me the following message: "No volume control GStreamer plugins and/or devices found."

When I go into System - Preferences - Sound - and click test on any of the items there, I get the following error: 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

I am running a Dell XPS with a Soundblaster Audigy sound card. Any ideas on how I can get Ubuntu to recognize my sound card?

Thanks,
Paul

---

### Post by phidia on 2008-08-11
Thank you for providing the error messages and probably the easiest way to work through your sound problem is to follow the [Ubuntu sound troubleshooting guide]("https://help.ubuntu.com/community/SoundTroubleshooting").

If you get stuck on anyone of those steps just post back with the specific error you're getting.

To get the multimedia packages installed (gstreamer & more) check out the guide [here]("http://ubuntuforums.org/showthread.php?t=766683").

---

### Post by haggus on 2008-08-27
Thank you for the link to the ubuntu sound troubleshooting guide. When I did the last kernel upgrade my hda-intel sound stopped working. With this guide it was a simple fix. I'll add this to my ever growing list of subscribed threads for future reference.

---

