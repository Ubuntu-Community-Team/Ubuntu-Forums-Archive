---
title: "udev not creating devices for sound"
date: 2006-04-10
forum: Hardware &amp; Laptops
---

### Post by camorri on 2006-04-10
I am new to Ubuntu, but not to linux. I installed Breezy ( uname -a 1.6.12-10-386 ) on an older Compaq 1245 and this is my second attempt to get sound working.  The sound is on the system board on the laptop, and is an ESS Technologies es1869 chip. 

I had Mandrake 9.2 installed on this for about two years, with sound working. I can also boot Knoppix 3.9, run alsaconf and install sound driver snd-es1688 and it works. 

I downloaded alsaconf form this board, ( it did not come with the distro) it will load the same driver under Ubuntu, but no sound. If I try to start alsamixer, I get an error message, alsamixer: function snd_ctl_open failed for default: no such file or directory. Also installed Kmix, but I don't get any sliders to adjust, or sound to un-mute. 

The sound drivers do load, I can see them with lsmod | grep snd.  Here is what I see.

snd_pcm_oss     46368 0
snd_mixer_oss   16128  1 snd_pcm_oss
snd_pcm            78344  1  snd_pcm_oss
snd_timer           21764  1  snd_pcm
snd_page_alloc   10120  1  snd_pcm
snd                     48644  4 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore             9184  1  snd

I also see an error after I first boot indicating /dev/dsp is not there.

I have looked in the /dev directory, and there is no dsp device, or dsp0 device. 

I think the issue is the hotpluging system is not creating the devices. So my question is, how do I fix this? I am not very familiar with udev and hot plugging. I have never had a problem with it before. 

When I booted Knoppix, and installed the snd-es1688 driver, I did see both /dev/dsp and /dev/dsp0.

---

### Post by christhemonkey on 2006-04-10
You say that in knoppix you had to load the snd-es1688 driver?
It does not look like that driver is loaded, try:
```
sudo modprobe snd-es1688
```

---

### Post by camorri on 2006-04-10
Thank-you for your reply. I inserted the module snd-es1688. I am now able to run alsamixer, and kmix. I can now play mp3 files. 

I'm left a little puzzeled. In Knoppix, when I ran alsaconf, it inserted snd-es1688 and the rest of the necessary modules. In Ubuntu it did not add all necessary modules. I guess I spent too much time on this, and forgot the obvious. 

When I look in /dev, I now have a dsp and mixer. Neither were there until I modprobed the  sound module. How udev is still a mystery to me. 

Once again, thank-you for your help.

---

