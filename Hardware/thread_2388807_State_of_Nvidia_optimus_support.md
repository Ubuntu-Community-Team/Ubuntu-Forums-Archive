---
title: "State of Nvidia optimus support"
date: 2018-04-07
forum: Hardware
---

### Post by Odisej on 2018-04-07
Dear all,

I am unable to find  any relevant information on the state of Nvidia Optimus support in the latest Ubuntu version (18.04 beta) and Nvidia drivers. The thing is most of the information available online seems to be outdated. I've been using Ubuntu and Manjaro on and off lately. Usually there was an option in Nvidia settings which GPU to use - Intel or Nvidia. With the latest Nvidia drivers and Bionic there is no such option. 

I don''t want to go the Bublebee way as I encountered some problems recently. But I am using Nvidia proprietary drivers. 

I was wondering whether the support changed? Maybe it is better integrated and there is some other way to switch between GPUs. Currently I am not even able to check which is being used as prime-select command does not work.

Does anybody have better information on this. Would be greatly appreciated.

Thank you.

---

### Post by markackerman8@gmail.com on 2018-04-25
I would ALSO LOVE to know if Optimus Support is finally here without SLOPPY Bumblebee,

Any Tip[s - 3 years waiting :(, Mark

---

### Post by linux4me on 2018-04-25
Since nobody who knows more about this than I do (which wouldn't be hard) has responded yet, I'll take a stab at it. 

I'm using Ubuntu MATE 18.04, and there *was* a [bug with the nVidia 390 driver]("https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1764005") related to the Optimus system that caused a black screen after logging in if one was using the proprietary driver, but it is supposedly fixed. There is also an app, I believe it's mate-prime in MATE, that launches an nVidia icon in the notification panel with a link to switch between the Intel and nVidia GPU or to go to nVidia Settings. I suspect other desktops also have it. The odd thing is that I didn't initially have the nVidia icon. It seems like it didn't start loading until after I installed the proprietary driver and then removed it when I had the issue with the black screen, but I do have the icon now, and I'm using the nouveau driver, not the proprietary nVidia 390 driver.

---

### Post by markackerman8@gmail.com on 2018-04-25
W.R.T. The Black Screen after installing the NVidia driver ... If it is in a new install of Ubuntu or other linux system ... a lot of things can cause it after the driver install.  SO purge NVidia and install again with "Additional Drivers" Option and restart it right after, and likely all will be OK.

Just my experience with Ubuntu 17.10 and 18.04

Cheers, Mark

---

