---
title: "Nvidia GT 9500 GT - driver confusion for a newbie"
date: 2008-10-19
forum: Hardware
---

### Post by briggs on 2008-10-19
I am working on my first real Kubuntu box and have been trying to get my Nvidia 9500 GT video card working correctly. After searching around these forums I was able to download the 177.80 driver from the Nvidia website and after lots of trial and error I was able to run the NVIDIA-Linux-x86-177.80-pkg1.run file (took me forever to figure out how to not get the X server is running error). I also had installed EnvyNG and tried that.

Here is my confusion;

If I look at the Nvidia X Server Settings panel it lists my 9500 GT card and the 177.80 drivers. If I go to System Settings > Monitors & Display > Hardware it says that I am using the Nvidia legacy drivers and I don't see anything there about the 9500 GT. If I try to run EnvyNG it only shows the 173.14.12 driver or earlier even after trying ```
apt-get install envyng-gtk && sudo update-pciids
```that I saw in another post.

I am running at the resolution that I want and it looks fine, but I guess I am just not sure if I have the driver installed correctly or not.

Any input is appreciated.

Thanks!

---

### Post by cariboo on 2008-10-19
If it works, why worry about it. To check the fps in a terminal run glxgears. I get about 1800 fps with a Nvidia 6150 on board graphics adapter.

Jim

---

### Post by briggs on 2008-10-19
Thanks for the reply. According to glxgears I am getting about 6700 fps.

My reason for asking is that I want to learn about the process and make sure I am doing things correctly - even if it is working right.

---

### Post by briggs on 2008-10-19
...and now that I have been messing around trying to get my sound card working, the video is all jacked up again. If I restart, I only get a terminal session. I found a post about reconfiguring xserver and that gets me back, but the video is back to a vesa driver and the Nvidia control panel says that I am not using a Nvidia driver.

and I still don't have sound.

---

### Post by ardvark71 on 2008-10-19
> **briggs said:**
> ...and now that I have been messing around trying to get my sound card working, the video is all jacked up again. If I restart, I only get a terminal session. I found a post about reconfiguring xserver and that gets me back, but the video is back to a vesa driver and the Nvidia control panel says that I am not using a Nvidia driver.

and I still don't have sound.

Hi..

How did this happen? :confused:

What is your sound card exactly and is it integrated? I'm hoping you can get your graphics the way you had it. :(

Best Regards...

---

### Post by briggs on 2008-10-19
I'm not sure what I did to lose the video, but I did get it back. I'm still confused on the video driver, but the 177.80 seems to work the best for me. I still can't get the sound to work - my audio is integrated:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I went through this:
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

and this:
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

and I did a dmesg and found this:
[   45.085347] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...

and then came across this:
[http://ubuntuforums.org/showthread.php?t=778541]("http://ubuntuforums.org/showthread.php?t=778541")

but still no sound.

---

### Post by briggs on 2008-10-19
and now after going into the alsamixer I have sound again.

no idea...

---

### Post by ardvark71 on 2008-10-19
Hi...

Well, I'm glad you got everything working! :KS

Best Regards...

---

### Post by briggs on 2008-10-20
I spoke too soon, sound is gone again after a reboot.

---

