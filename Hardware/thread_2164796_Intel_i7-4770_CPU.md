---
title: "Intel i7-4770 CPU"
date: 2013-08-01
forum: Hardware
---

### Post by geomcd1949 on 2013-08-01
Am wondering if the kernel used in Ubuntu 13.04 fully supports an Intel i7-4770 CPU. The updated kernel used in 12.04.2 does not.

Thanks.

~George

---

### Post by oldfred on 2013-08-02
With bleeding edge hardware, you probably need the very newest Linux and sometimes that is not fully supported for several months. But some have reported that Haswell works.

       Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)


 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.

If it is a new Mac, not so much.
      
 New Haswell MacBook Air - several issues
[http://www.phoronix.com/scan.php?page=article&item=apple_mba2013_ubuntu&num=1](http://www.phoronix.com/scan.php?page=article&item=apple_mba2013_ubuntu&num=1)

---

### Post by geomcd1949 on 2013-08-02
Thanks for the reply, OldFred. The news is discouraging. I was going to build state-of-the-art computers for sale, with the latest most efficient and powerful components, and run them with Ubuntu operating systems, preferably Long Term Releases. Now I have a couple of rooms filled with components, and I might have to put Windows 7 on the completed machines. Not an encouraging proposition.

My specific problem is that I can't get 12.04 to play sound. Using "sudo apt-get install mesa-utils" gets it to recognize the graphics driver of the i7-4770, but even with the driver recognized, sound won't play, and there is no option in All Settings > Sound for HDMI audio. 

Any suggestions would be appreciated.

~George

---

### Post by oldfred on 2013-08-02
I have not followed sound issues, so I cannot help much. I do see regular posts with that in the title but assume it may be the older models?

---

### Post by gordintoronto on 2013-08-02
> **geomcd1949 said:**
> My specific problem is that I can't get 12.04 to play sound. Using "sudo apt-get install mesa-utils" gets it to recognize the graphics driver of the i7-4770, but even with the driver recognized, sound won't play, and there is no option in All Settings > Sound for HDMI audio. 

Any suggestions would be appreciated.

~George

The CPU doesn't produce sound. What sound chip is on the motherboard you are using? Once again, hardware which was released after the OS might not be supported. This has also been a problem with some Ethernet adapters, support arrived a year after the hardware become available.

Use this command if you're not sure: sudo lshw -class sound

There is a way to install a later kernel into the LTS release, but I would need to Google it.

---

### Post by Yellow Pasque on 2013-08-03
This may get you sound: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by geomcd1949 on 2013-08-05
Problem solved. Thanks very much for the kind assistance.

I installed the latest version of the kernel, then installed PulseAudio Volume Control. Don't know if the new kernel had anything to do with the solution, but I mention it 'cause that's what I did. PulseAudio Volume Control was configured to have "Digital Stereo (IEC958) Output + Analog Stereo Input." 

Joy!

---

