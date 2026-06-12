---
title: "Poor Audio on newly built computer running Kubuntu"
date: 2016-11-28
forum: Hardware
---

### Post by jlb001 on 2016-11-28
Built a new mini ITX computer over the weekend, I'm running a 6700k on an asus z170i pro gaming motherboard using supremefx audio. Everything seems to be working fine however the audio is horrendous. At first I thought it might have my headphones but the nI switched to a nice pair of sennheiser's but I get the same result. On youtube I can hear the audio cracking and the voice super low its quite odd really. 

Digging online I tired everything from using an equalizer to installing dkm's and I can't seem to get it working normally. One thing I noticed which might be the culprit is that under the audio tab it reads "built in analog stereo" is there something I'm completely missing? I have enough experience with linux to be comfortable with it though I have never ran into any audio issues. 

Also almost forgot to mention not sure if it might help but I'm using an HDMI connected display and as of now I'm just running on intel integrated graphics until I can afford a solid gpu.

edit: I downloaded kmix (not sure why it was preinstalled but oh well) from the main window I went to file(?) -> audio setup and the second tab from there it allowed me to change the setting for the input which was originally in analog as mentioned before. Oddly "analog surround 5.1 ...." worked but what was weirder is that my headphones only sounded "normal" being plugged in the back directly through the motherboard not the front panel audio jack which is odd. 


still confused about this but somewhat made progress.

Really digging Kubuntu but the audio problems are wonky, if I sort this out I just might stay with this distro

---

### Post by gordintoronto on 2016-11-29
What version of Kubuntu? With really up-to-date hardware, you need to run a really up-to-date OS. Maybe even the development version.

---

### Post by jlb001 on 2016-11-29
> **gordintoronto said:**
> What version of Kubuntu? With really up-to-date hardware, you need to run a really up-to-date OS. Maybe even the development version.


latest 16.10 Yakkiy Yak, It seems to be "half" fixed by selecting "5.1 surround analog.." , audio sounds normal with I plug in my headphones directly to the motherboard in the green colored jack but it still sounds horrible via the front panel audio jack.

---

### Post by oldfred on 2016-11-29
I have a Z170 but did not notice any audio issues in 16.04. But then I only use audio to stream radio.

There was this older issue with previous generation motherboards. I would think it should not apply.
       Audio issues on Z97
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421)
[http://ubuntuforums.org/showthread.php?t=2234198](http://ubuntuforums.org/showthread.php?t=2234198)

---

