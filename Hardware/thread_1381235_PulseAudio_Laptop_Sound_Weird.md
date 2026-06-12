---
title: "PulseAudio Laptop Sound Weird"
date: 2010-01-14
forum: Hardware
---

### Post by Albatrosses on 2010-01-14
I've got Ubuntu Karmic freshly installed (and fully updated) on my Dell M90, and I'm having some... difficulty with the audio.  Basically what happens is that when I adjust the speaker volume, I have no audio from 0-30%, then the speakers become insanely loud and remain at a constant volume from 30% - 100%.

After some fiddling in the "Sound Preferences" window, I managed to get volume shifting working (there were some volume sliders maxxed out; an adjustment seemed to fix them).  Now I have a new problem - PulseAudio brings my onboard subwoofer from 0-100% in the first third of the volume control range, then after I hit 33% it slowly brings the main speakers up.  Unfortunately, this causes horrible audio distortion, and the laptop only sounds acceptable at 100% volume level (which is wayyy too high).  What should happen is that both outputs are sync'd; i.e. at 30% volume, Master and LFE should both be at 30%.  I have confirmed what PA is doing by watching alsamixer while playing with the volume.

Also, when I restart I get the first behavior again (constant level), and I have to go poking around with sliders to get the second.  Which is still broken.

Any ideas?

---

