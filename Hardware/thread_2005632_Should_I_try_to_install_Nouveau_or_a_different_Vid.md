---
title: "Should I try to install Nouveau or a different Video graphics Driver?"
date: 2012-06-17
forum: Hardware
---

### Post by brevardo on 2012-06-17
I just installed Ubuntu 12.04 LTS on my Dell Laptop D620. I had Windows XP on this machine for the past year however I've had Ubuntu on here before. The only issue I seem to be having is that the laptop seems to get hotter much faster and I'm pretty sure from what Ii remember the last time it's because of the Nvidia Video Graphics card. When I go to settings and run the additional drivers it doesn't recommend that I upgrade? I also noticed though when I go to my system info it says unknown for the video card. So ubuntu 12.04 must not be recognizing that Ii have an Nvidia graphics card. What is the best way to do this and is Nouveau the propreitary driver that I should go to or should I mess with that Fglrx? Also how can I run a terminal command to be sure that the hardware I have is Nvidia and not ATI/AMD. I just want to be sure.

---

### Post by Shadius on 2012-06-17
To be sure of what hardware you have you could run in Terminal:
```
lspci | grep VGA
```

---

### Post by brevardo on 2012-06-18
Shadius- Thanks for the quick response. I guess I have something different than I thought. I ran that command in Terminal and here's what I got:
rich@rich-Latitude-D620:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

I had Ubuntu on this same Laptop before ( around two years ago ) and it just seemed that I needed to do something in order to make the video graphics card run normally. It seemed that after installing Ubuntu out of the box it was making my laptop run hot very fast and you could hear it getting louder. Once I found the proprietary driver it seemed that it ran much quieter. Since I just recently installed Ubuntu on this again it seems like I'm getting the hot computer again especially when I watch a video like on You Tube or have a lot of flash playing. So that's why I'm feeling I still need to do an extra step with this new install in order to have the proper driver work with this laptop.   Thanks again,  Rich

---

### Post by Yellow Pasque on 2012-06-18
The best video driver is already installed.

Flash video is a flat-out CPU hog on Linux and has overheated many laptops. That doesn't really have anything to do with the video driver. Flash isn't accelerated by the GPU in Linux unless you have an nvidia GPU and use the binary driver (and that's not without its issues either).

Check out Flashvideoreplacer add-on for Firefox.

---

### Post by brevardo on 2012-06-20
Okay Temujin. Will do as that does make sense. Thanks, Rich

---

### Post by brevardo on 2012-07-01
I still feel like there is something else I should be doing? My computer laptop with ubuntu 12.04 is definitely making more noise then it did with Windows. Shouldn't I run and install a proprietary driver? I just went into settings and clicked "additional drivers" and it said that I am only running open source drivers and no proprietary drivers have been installed. Isn't that the issue. It seems as if it's always getting hot fast and the fan comes on quick. I dealt with all of this a couple of years ago when I previously ran Ubuntu on this same laptop. I know it was a pain and I had to go through many steps to try and get it from getting so hot. The only thing I'm concerned about is if I try and install a new proprietary driver and it doesn't work right meaning I boot my computer and I can't see the screen or it has a bunch of characters that don't make sense because the graphics card isn't recognized by the driver. is there a way to easily revert back so I don't have to do a complete re-install of the OS? Any steps as to do this would be appreciated.  Thanks,  Rich  H

---

### Post by Yellow Pasque on 2012-07-01
> **brevardo said:**
> Shouldn't I run and install a proprietary driver? 
No. Intel graphics don't have a proprietary driver...

---

