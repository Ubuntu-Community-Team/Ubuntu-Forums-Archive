---
title: "GeForce 8400GS"
date: 2012-04-13
forum: Hardware
---

### Post by terryds on 2012-04-13
Good Day Everybody,
 
I am very new to this, and this is my first post; I have manged to load Ubuntu 11.10 successfuly, but decided to replace the old ATI X550 Graphics card with a GeForce 8400GS that after a lot of checking everybody says is compatible.
 
However I seem to be in a chicken and egg situation, and after reading literally scores of posts to no avail, I am still struggling - if I install the 8400GS the PC locks just after the BIOS page so I can't get in to load the correct drivers, and of course I can't load the drivers in advance because Ubuntu says I haven't got a Nvidia card while the X550 is installed.....
 
Is there anybody who could help me please, preferrably someone who actually has got this card with this version of Ubuntu? Simple instructions would be greatly appreciated!
 
Many thanks in advance, and I know the card is OK because I installed it in various Windows PCs and it worked a treat. I've got a feeling I'm going to be stuck with the X550 unless there is another cheapo card that someone can recommend or hopefully get me going with this card.
 
Kind Regards
 
Terry

---

### Post by Yellow Pasque on 2012-04-13
Put the X550 in and install the nvidia driver:
```
sudo apt-get isntall nvidia-current
```
Then, shutdown and install the nvidia card.

---

### Post by terryds on 2012-04-14
Thank you for your reply, and I have done that, and the computer has now booted to a desktop. 
 
However, everything has slowed down to a crawl, the mouse is a jerky, and opening the Home Folder now takes over half a minute whereas before it was instantaneous. Firefox took over 2 minutes to open and even closing it took another 60 seconds.
 
Obviously progress from where I was, as the card is actually displaying a picture now, but odd that a IGB card takes seems worse than the old and very basic 64Mb X550.
 
Is there something else I should have done/ should do - I checked in 'Additional Drivers' and it says I am using the Recommended Nvidia accelerated graphics card (version current).
Machine is a P4 3GHZ with 2GB RAM.
 
Again many thanks in advance for any assistance
 
Kind Regards
 
Terry

---

### Post by kurt18947 on 2012-04-14
I'm not much help but did you install drivers for the X550?  If so, you might have a conflict between the X550 drivers and Nvidia drivers.  If you didn't install X550 drivers then I have no idea.  I have an Nvidia 8400GS and no problem but this card has been the only card installed since my current 12.04 install.

---

### Post by terryds on 2012-04-14
Thanks for that, but no, I have not knowingly installed any drivers for the X550, it was in the PC when I loaded Ubuntu and it worked straight off. What is nice to know is that the 8400GS can work, and I did at one point try loading 12.04 Beta 2 from scratch with the 8400GS in place but still no change so I went back to 11.04 as a clean install.
 
Reckon I'm just unlucky and not meant to use this card, but thanks for your input, and glad yours is working.
 
Kind Regards
 
Terry

---

### Post by kurt18947 on 2012-04-15
Terry I wish I had a better suggestion.  Does your motherboard have integral video?  If so, is it disabled in BIOS?  I've installed a few distros including 12.04 (Twice!! :p) on the machine with the BFG 8400GS card installed and no trouble.  If you powered down, uninstalled the X550, installed the 8400GS then did a fresh install I don't know what to suggest.  I hope you're able to figure it out.

---

### Post by terryds on 2012-04-16
Kurt,
 
Again thanks for replying, no there is no integral video on the motherboard. Decided to cut my losses and have ordered bits to build a new machine and install Ubuntu on that...without the 8400GS. 
Bit drastic but it will presumably solve the problem and as I said the PC was a bit old anyway so time to move on.
Thanks for your time,
Kind regards
Terry

---

