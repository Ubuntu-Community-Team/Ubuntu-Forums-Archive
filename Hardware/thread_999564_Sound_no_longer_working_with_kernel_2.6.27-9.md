---
title: "Sound no longer working with kernel 2.6.27-9"
date: 2008-12-02
forum: Hardware
---

### Post by mitchellcipriano on 2008-12-02
My system was working great. I was running 8.10 on my ThinkPad R51. It was upgraded from 8.04. Everything worked fine under 8.10. Then I updated to kernel 2.6.27-9. At first I could not get the machine to shutdown. I noticed it was hanging on ALSA shutdown. After forcing the shutdown, I no longer have sound. Any ideas?

---

### Post by prshah on 2008-12-02
> **mitchellcipriano said:**
> 
I updated to kernel 2.6.27-9. At first I could not get the machine to shutdown. I noticed it was hanging on ALSA shutdown. After forcing the shutdown, I no longer have sound. Any ideas?

Does sound work with the previous -7 kernel? (The GRUB menu at bootup will have the option to boot using the previous kernel).

As a point of interest: Did you "mute" your audio before, or during, the kernel upgrade? Did you notice any problems during the "Building modules for the 2.6.27-9-generic kernel, please wait..." phase (which appears on the first (re)boot after the kernel is upgraded)?

---

### Post by yonas on 2008-12-02
I have the same problem. I might have muted my audio.

I only hear static noise, low in volume.

uname: Linux yonas-laptop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686

---

### Post by mitchellcipriano on 2008-12-02
> **prshah said:**
> Does sound work with the previous -7 kernel? (The GRUB menu at bootup will have the option to boot using the previous kernel).

As a point of interest: Did you "mute" your audio before, or during, the kernel upgrade? Did you notice any problems during the "Building modules for the 2.6.27-9-generic kernel, please wait..." phase (which appears on the first (re)boot after the kernel is upgraded)?

Thanks for the ideas. Yes, the old kernel worked great. I will try booting it again.

When the system boots, the speaker icon indicates mute. The sound is still off even when I unmute it. By experimenting I figured out that the sound was not only mute, but also the slider was re-calibrated so that even if it was showing full scale, there was no sound. Buy repeatedly pushing the volume buttons I eventually got the sound back. The shut down issue is still here and the sound is muted each time I reboot. Could this be caused if I had the sound muted when installing the new kernel?

For now the old kernel works great, so I can just stick with it.

---

### Post by shantanubhadoria on 2008-12-02
I might have muted my sound too during kernel upgrade to 2.6.27-9

The problem I have is stranger. in the newer kernel during bootup I get startup sound but after sometime when i try to play something in any media players the sound is gone. The sound plays for sometime even in players if i do it immidiately after bootup. Then it arbitarily goes out and no more sound will play. some daemon crashing?? Not sure wht i need to look for here. I had to compiled madwifi drivers into the new kernel to make WLAN work just like i did in 2.6.27-7 but the sound problem occured even before i did that. I am using a Compaq presario. Any ideas?  C700(770TU)

---

### Post by bgunter on 2008-12-03
Some additional details:

I have a similar problem -- The sound works with the 2.6.24-19 generic kernel but **not** the 2.6.24-22 generic kernel. Further, I am also fairly sure that sound was muted when the later kernel version was updated. Other than manually intervening to use the older kernel at bootup, any suggestions of how to fix? 

Further details: sound device is Intel 82801H (ICH8 Family).

In the sound preferences menu, the error message I get is "connect stream: Invalid argument" under the "autodetect" option; or "No devices found" under the ALSA option.

-- Bert

---

### Post by prshah on 2008-12-03
> **mitchellcipriano said:**
> Could this be caused if I had the sound muted when installing the new kernel?


> **shantanubhadoria said:**
> I might have muted my sound too during kernel upgrade to 2.6.27-9


> **bgunter said:**
> Further, I am also fairly sure that sound was muted when the later kernel version was updated.

Don't want to cause a storm in a teacup, but maybe muting the sound during a kernel update is a cause? In any case, can you try the troubleshooting steps in my thread ( [[SOLVED] No sound device detected in Fujitsu Lifebook P5010 in 8.10]("http://ubuntuforums.org/showthread.php?t=995725") ) and post back with your results?

---

### Post by yonas on 2008-12-03
I needed to run "sudo alsaconf" to fix this problem and use PulseAudo in Preferences-->Sound.

/etc/asound.conf:
pcm.pulse {
	type esd
}

ctl.pulse {
	type esd
}

---

### Post by yonas on 2008-12-03
> **prshah said:**
> Don't want to cause a storm in a teacup, but maybe muting the sound during a kernel update is a cause? In any case, can you try the troubleshooting steps in my thread ( [[SOLVED] No sound device detected in Fujitsu Lifebook P5010 in 8.10]("http://ubuntuforums.org/showthread.php?t=995725") ) and post back with your results?


Btw, I don't see any troubleshooting steps in that thread :confused:

---

### Post by mitchellcipriano on 2008-12-04
After the update to the 2.26.27-9 kernel, I had sound problems and shutdown issues. My sound problem was solved by turning the sound up. Even with the mute off and the slider showing full volume, I had no sound. If I muted it in that position and then turned it up, I would get sound.

Each time I rebooted the system would hang and I would need to force the shutdown. I noticed it was hanging when shutting down ALSA. At the same time I found a discussion thread about the ownership of files in the home folder being switched to root. I then checked and found the .dmrc file was owned by root. So, I ran ran Nautilus with sudo rights and gave myself ownership of all the files in home. This seems to have solved all my problems - sound and shutdown.

---

### Post by bgunter on 2008-12-04
Would you care to translate your response? While I appreciate your efforts, I am using Ubuntu precisely because I do not want to spend a lot of time learning how to use Linux from the command line. That I am unable to do much without this is highly unsatisfactory.

-- Bert

---

### Post by bgunter on 2008-12-05
Ah -- I figured it out. nautilus not Nautilus. But there was no .dmrc file.

---

### Post by mitchellcipriano on 2008-12-05
> **bgunter said:**
> Ah -- I figured it out. nautilus not Nautilus. But there was no .dmrc file.

You need to set nautilus to show hidden files. Go to view and check "Show Hidden Files." Now you should be able to see the file.

---

### Post by ProNux on 2008-12-12
Here's what I did that worked for me.

My Kernel version now is 2.6.24-22 after updating my Hardy heron.  I discovered I have no audio during ONLINE streaming.  What I did was change the ALSA to PulseAudio on Preferences-Sound.  Nothing happened.

But when I switched back to ALSA, my sound resumed back.  :-)

---

### Post by dakid on 2008-12-22
I am having the same problem. I am running  2.6.27-9-generic kernel on my HP dv7t series. And, when I boot, I hear sound on the login screen. However, I don't hear no sound when I try to play music. Or, when I try to listen to music online, I have no sound either.

---

### Post by 10101011 on 2008-12-22
> **dakid said:**
> I am having the same problem. I am running  2.6.27-9-generic kernel on my HP dv7t series. And, when I boot, I hear sound on the login screen. However, I don't hear no sound when I try to play music. Or, when I try to listen to music online, I have no sound either.

You might want to take a look at [http://ubuntuforums.org/showthread.php?t=1014836]("http://ubuntuforums.org/showthread.php?t=1014836")

The HP dv7t has a known issue with sound.

---

