---
title: "Headphones not detected through 3.5mm audio jack"
date: 2019-01-01
forum: Hardware
---

### Post by deathlor12 on 2019-01-01
I am dual booting Ubuntu and Windows 10 and my headphones haven't been working with Ubuntu. They work perfectly on Windows and I have tried finding a fix for it but most of the fixes say to go to alsamixer and change the volume of the headphone slider, but there is no headphone slider for me, and when I go into sound settings the only options for output are 'Speakers - Built-in Audio' and 'Digital Output (S/PDIF) - Built-In Audio'. The first one works with my laptop's speakers and the second one makes no noise with anything. I have tried other pairs of headphones and they didn't work either.

---

### Post by Yellow Pasque on 2019-01-01
I used to tell people to run this script to get good, detailed audio info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Unfortunately, folks seem to be having issues running this nowadays. But give it a try anyway.

If, for some reason, the audio driver is not identifying your headphone jack as a headphone jack, you may want to investigate 'hdajackretask' (found in alsa-tools-gui package). That is a workaround solution though. The ideal solution involves getting the driver fixed at the kernel level so you don't have to resort to such hacks.

---

### Post by deathlor12 on 2019-01-01
I ran that script and it gave me this link: [http://www.alsa-project.org/db/?f=b7c4f34eba1edab9edb5196d874d414f4535ca1e](http://www.alsa-project.org/db/?f=b7c4f34eba1edab9edb5196d874d414f4535ca1e)
I've already tried using hdajackretask but I'm not sure which pin to override and even if I try one of them I get this error: 'tee: /sys/class/sound/hwC0D0/reconfig: Device or resource busy' and another error pops up in terminal: [https://imgur.com/a/DfRFbXE](https://imgur.com/a/DfRFbXE)

---

### Post by mikasu on 2019-01-01
I'm having a similar issue. Though, I use a headset in my single 3.5mm audio jack and the mic of the headset is not working, only the internal mic of my laptop. I couldn't find out any solutions yet... I tried hdajackretask too but it didn't change anything and I got the same error. I'll tell you if, by chance, I come across a working fix.

---

### Post by clementc on 2019-01-02
Hi [**deathlor12**]("https://ubuntuforums.org/member.php?u=2115234"),

First of all, can you please try adding ```
options snd-hda-intel model=asus-mode5
``` to ```
/etc/modprobe.d/alsa-base.conf
``` then reboot your PC and try again.

Second, in hdajackretask, chances are that pin 0x16 should be the headphones one.

Please try step 1 first and confirm if this has helped at all or not.

@[**mikasu**]("https://ubuntuforums.org/member.php?u=2115175"), we need to know your hardware specifications the same way [**deathlor12**]("https://ubuntuforums.org/member.php?u=2115234") provide them to us. I would also recommend that you create your own thread to avoid hijacking [**deathlor12**]("https://ubuntuforums.org/member.php?u=2115234")'s one for better visibility.

Edit: looks like you already did [here]("https://ubuntuforums.org/showthread.php?t=2409284"). I will investigate and reply back to you there.

---

### Post by mikasu on 2019-01-02
Yes I'm sorry. It's a Acer Aspire v3-572pg. I have a Realtek ALC283 codec. My model is pretty much the base one except I added more ram because 8 wasn't enough but that shouldn't affect sound. My problem as I said is my mic not being detected. I couldn't find the pin in hdajackretask. I tried model=acer , acer-aspire, dell-headset-multi and dell-headset-dock in alsa-base.conf and none of them worked.

For more specific about the hardware :
InsydeCorp BIOS version 1.32
Intel Core i5-5200U CPU
Intel HD 5500 Integrated Graphics
nVidia GeForce 840M 2GB GPU

Edit: Didn't see that you mentioned my post. We'll continu in it indeed. I apologize for the slight hijacking

---

### Post by deathlor12 on 2019-01-19
Hi, sorry for the late reply, I was gone for a week or so and some other person said this was a hardware issue so I wasn't sure if this would work. I tried the asus-mode-5 thing and it worked! Thank you so much.

---

### Post by deathlor12 on 2019-01-23
Update: I was using my computer like normal and I realized sound was coming out of the laptop speakers as well as the headphones. I'm nearly positive that wasn't happening at first, but I tried to fix it by going into alsamixer and muting the laptop speakers but I don't know what I changed but it stopped making any sound out of the headphones. I restarted the computer multiple times but it still wont play sound through the headphones. Any ideas on how I can fix this?

Edit: there are 3 audio jacks on my laptop, 1 headphone, 1 mic, and the last one I have no idea what it is. Nothing changes in alsamixer when I plug it into either of the first 2 but the third registers it as a headphone but still no audio. I still have options snd-hda-intel model=asus-mode5 added to /etc/modprobe.d/alsa-base.conf

Edit again: lmao I'm sorry my headphones have a little adjust knob thing and i accidentally had it all the way muted. It still plays audio out of both the speaker and headphone jack if I use the headphone jack, but if I use the third jack it works perfectly, so I'll stick with that.

---

