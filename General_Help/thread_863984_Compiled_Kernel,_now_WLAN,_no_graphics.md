---
title: "Compiled Kernel, now WLAN, no graphics"
date: 2008-07-19
forum: General Help
---

### Post by Weisswurst on 2008-07-19
Hi!

I compiled the actual kernel with a little fix for my bluetooth headset which i'd like to use with skype.

I used the config file of the kernel from the repositiories. It compiled and installed well. But now the nvidia driver seems missing. The integrated (notebook) wlan isn't working also and I just recognized that my soundcard isn't detected anymore.

The headset seems no to work because when  I start to play a wav file through it, it makes a beeb like it does if I start a phonecall on my phone. But I can not hear the file itself but when the playback finished I hear again that beeb. 

Did  I something wrong with the kernel?
What have I to do to for making my wlan and my soundcard and my nvidia graphics work again?

Thx for helping!

---

### Post by DagMan on 2008-07-19
You might have noticed that there's module packages called ubuntu-modules and restricted-modules or some similar names.  These are kernel modules that are compiled after the kernel installation. You can download the source code and compile them, however I'm not really aware of any good documentation on how to do these packages.  It used to be easier to get them to build and then manually move them, but it seems to no longer be the case, and that was not likely ever the intended way anyway.

It would be good before you go any further to go to a terminal with the old kernel and with your network up and working and video going etc:
lsmod | awk '{print $1}' > kernel1
then reboot 
and 
lsmod | awk '{print $1}' > kernel2

you can compare the two resulting files to see what modules your'e missing.

The sound is usually easy to fix regardless, but it seems irrelevant if you can't get a network interface.
The NVIDIA driver you can get going again by using the appropriate NVIDIA installer on their website.
The wireless is the thing to try to fix here first though if it's going to be worthwhile from the sound of it, and also it would be good to see what else isn't loading when comparing the two files. There will heaps of sound modules most likely so don't feel overwhelmed straight away when you find a lot.

---

### Post by sdennie on 2008-07-19
I don't think the default Ubuntu config has the HDA Intel sound driver or the Intel wireless drivers enabled so you'll have to enable them manually (you can find them in make menuconfig) and, for the wireless, you'll have to make sure the firmware is in the right place.  For the nvidia drivers, you'll have to manually install them.  This nvidia guide has worked for many people: [http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270)

---

### Post by Weisswurst on 2008-07-20
Hey thanks for the answers.

I frogot to mention that I meanwhile compiled the restricted modules.
I installed the .deb files but they it seems that it changes nothing.
In the Hardware Driver Dialog still no proprietary drievers are listened.

I'm going to compare the module lists now.

---

### Post by DagMan on 2008-07-20
Just to expand on the firmware, I forgot this is sometimes the wireless problem and sorry if created extra work, just make a symlink in the /lib/firmware file using the custom kernel name that points at the old kernel number in that directory, or copy the old directory to a new one with the appropriate name.  If it doesn't work then it is missing module.

As for alsa, if you've already recompiled then you've likely enabled those modules which should fix it, but if not, you use module assistant to build them.
```
sudo apt-get install module-assistant
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant a-i alsa
```

---

### Post by Weisswurst on 2008-07-20
Just made the two modulelists. There is a difference of ~300 kb between them... I think I'm going to make a new kernel.

---

