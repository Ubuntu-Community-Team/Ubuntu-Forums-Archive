---
title: "Bluetooth headphones connect but no sound (15.10)"
date: 2015-12-06
forum: Hardware
---

### Post by richard-i-stephens on 2015-12-06
My Sony DR-BTN200 bluetooth headphones were working fine under 15.04 but after installing 15.10 there's no sound. They connect and are shown under the Bluetooth Devices list, but when playing audio the sound still comes out of the attached speakers and not the headphones. 
The PulseAudio Volume Control does not show the headphones as an output option.

I have tried running
[FONT=courier new]pactl load-module module-bluetooth-discover
[/FONT]
But all I get  is the message "Failure: Module initialisation failed".

All software, including Blueman, is up to date.

Cheers,

---

### Post by Seb_007 on 2015-12-28
Hi,

"I have the same problem.
Sony headset MDR-ZX750BN is paired but no audio.
When going to "Output" in the "All Settings -> Sound", I can select the headset but the right side of the window keeps showing the settings for the previous selected output. In my case Digital Output (S/PDIF).
All was working perfectly before 15.10??"

Update:

I reinstalled the Pulse bluetooth stuff via Synaptic, also installed Blueman.
Went to the Pulse Audio volume control and setup the Headset with the audio profile I wanted (A2DP).
In Bluetooth manager I connected the Headset as Headset (right mousebutton) and now it all works

Br,

Seb

---

