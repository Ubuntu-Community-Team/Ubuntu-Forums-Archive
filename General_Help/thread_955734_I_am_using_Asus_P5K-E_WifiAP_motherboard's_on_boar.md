---
title: "I am using Asus P5K-E Wifi/AP motherboard's on board sound."
date: 2008-10-22
forum: General Help
---

### Post by Fr0zen89 on 2008-10-22
Sound used to work just fine in Gutsy. After I upgraded to Hardy, sound has stopped working.

Codec: Analog Devices AD1988B
Address: 0
Vendor Id: 0x11d4198b
Subsystem Id: 0x1043829b
Revision Id: 0x100400

Farhad Shakiba : please use pnpacpi=off in kernel option. This bug is in 2.6.24.xx version. In 2.4.25 is fully fixed

somone posted this in another forum.... and it seems to be a fix for the audio driver but iam new to linux and iam not sure how to get in the kernel option :s

---

### Post by Fr0zen89 on 2008-10-22
bump... stiill need help

---

### Post by Bodha on 2008-11-04
Hi,
Ive got less then a week on Linux so take this post with due caution. Im using Ubuntu Hardy and the above Motherboard. 

I had trouble with sound out initially and the solution I stumbled upon might help new users to Ubuntu Hardy having sound problems (regardless of the MoBo model)

My problem was getting a digital stream out via SPDIF through the Toslink on the rear of the MOBO but the solution may be generalisable to different playback means. 

If I recollect correctly  the breakthru :guitar:came by setting preferences on the Volume Control. Before that I read the official help page and mucked around in System- Preferences-Sound to no avail. Now experienced users can have a big chuckle at this noobish naivety but it really wasnt intuitively apparent that this was the problem. 

If this is new to you then you could try this:
1. Double left click on the speaker symbol in the top right. A single click is useless as it only brings up a volume slider.
You want a full dialog window to come up called Volume Control via double clicking.
2. Left click on the Edit option and then click on Preferences
3. Select what you want - you can turn on the Headphones out at the front panel (if you plugged that into the MoBo) and there are lots of options for the multi channels at the rear of the MoBo
4. For a digital stream out via SPDIF check IEC958 and PCM. The IEC958 seems to really control the stream out as unchecking it kills my external Benchmark DAC1 signal. This is a bit buggy and can need a few clicks on and off to wake up and work. Under options set the IEC958 to PCM for usual listening to CD/FLAC/mp3 etc...

I tried the Asus P5KE WiFI MOBO on board sound with my headphones for fun. Its got pretty good sound for an internal sound card let alone this integrated sound on the MoBo. It has the power to drive Sennheiser HD 650 to higher volumes then I want but not with the clarity or revelation of the Benchmark external DAC.

Now im on a roll one more off topic rave - Ive succumbed to going back to Foobar under Wine. I tried heaps of other Players offered by Linux but none of them had the flexibility and depth of Foobar. Maybe this could get sorted as its really weird that a free player for Windows can outclass the Linux offerings.

Be happy

---

