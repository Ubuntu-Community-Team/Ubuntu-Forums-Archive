---
title: "ubuntu 8.10 alpha-6, 64-bit is good for Acer Aspire 2930"
date: 2008-10-02
forum: Hardware
---

### Post by jeecol on 2008-10-02
Hi, 

It seems only few discussions about this item on the forum, let me share my "raw" testing results here.


It is painful for me of using 8.04 on this new-born laptop,

Wrong screen resolution setting (only at 1024*768)
No wireless
No sound
No touchpad response
No webcam
and a strange net-card (I needed to reboot at least twice to get the net working)

However, after the trials of 8.10 alpha-6, the resolution problem was totally solved (could be due to new, version 2.4, of xserver-xorg-video-intel, and that was version 2.2 for Uubntu 8.04). But the touch pad still does not work. I am learning how to control the webcam. About the wireless, it works well even in the live-CD model. The sound finally comes, but I do not know how to stop the speakers and use earphone only. Sure, I still need to test more issues and make the testing report complete. 

My suggestions to ubuntu fans: try 8.10 or later for this laptop, but never 8.04. 

By the way, the 8.10 i386, alpha-6 seems unstable (I could not boot it after installation)

Best,  

------------
"jeecol" means one dollar, in my mother language, Taiwanese.

---

### Post by phidia on 2008-10-02
I'm using ibex on my desktop and it does work very well-including improved xserver configuration.

Getting main speakers to mute on your laptop may require installing or setting up jack sense. Some people have claimed getting that feature to work so you could search your laptop model in sound forum.

---

### Post by perlluver on 2008-10-02
Intrepid Alpha 6, is an Alpha, not yet ready for everyday use.  It will be released on October 30th.

---

### Post by jens83 on 2008-10-09
I have 32-bit 8.04 running on my 2930. after install i had no sound, wired or wireless internet. fixed these, but still have no webcam/mic. also some graphics problems like black after boot (before login window) every other boot. did upgrade kernel to 26.5
maybe these problems are easy fixes,, havent tried much yet.. newbie as i am

looking forward to 8.10 though, should i go for 64 or 32? not sure

---

### Post by Yellow Pasque on 2008-10-09
> The sound finally comes, but I do not know how to stop the speakers and use earphone only.
Try configuring alsa-base: [http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)

---

### Post by jeecol on 2008-10-09
thanks for Temüjin's suggestion.

I will try that soon, or I will wait until the final version of 8.10.



To jens83, 


I already use 8.10, 64-bit (due to the poor hardware support from 8.04)

So far, no 8.10, i386 alpha and beta could be successfully installed on this 2390 (including Ubuntu and Kubuntu). I do not know why. That's why I use 64-bit (works, but not quite stable. Some apllications crash). Also the same problem on one desktop in my home and one desktop in my lab.


The problem I encounter on this beta 64-bit OS

1. I need Adobe reader, however, I could not find 64-bit version deb from the official webside. And other PDF readers have poor support for Asia characters.

2. No 64-bit package from skype website.

3. No 64-bit package from Realplayer website.


And some applications are not for 64-bit when using "add/remove"

I am a postdoc in the field of earth science (not in computer science), and I do not need 64-bit OS. So I plan to return to 32-bit when the final version comes (and then report more details of testing this laptop).


by the way, when I was using 8.04, one day I failed to compile xserver-xorg-video-intel-2.4.2. But one day I selected recovery model in the grub menu, then selected to fix X (then booted as normal). Suddenly, the graphic was set at 1280*800, and I could also use the jello-effects. But the whole system got dead as long as I played video (then I went to 8.10 beta). 


Best, 

------------
jeecol is one dollar, I live in Taiwan.

---

### Post by cariboo on 2008-10-09
All the programs you are looking for are available in the Medibuntu repositories. Go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

For instructions on how to enable the Medibuntu repositories.

If you are looking for a Forum for Intrepid, go here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

Jim

---

### Post by Yellow Pasque on 2008-10-09
> I will try that soon, or I will wait until the final version of 8.10.
I hate to disappoint you, but the final version of 8.10 isn't going to magically fix jack sensitivity in ALSA. You need to configure your alsa-base file.

---

