---
title: "New Installation Failure - Out of Range"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by jase.d on 2009-02-13
I downloaded Ubuntu 8.10 Desktop (the latest version) and then burned it using InfraRecorder to a disk as told. I tested it to make sure I burned it over correctly etc and then put the disc into the computer I was trying to install it on.

I put the disc in, selected the language and then went to 'Install Ununtu' (I had already gone to 'Check CD for defects' and that went through without a problem). After waiting a couple of minutes for the installation to take place a message appeared saying 'Out Of Range'.

I have searched on this forum for other people having problems with 'Out Of Range' however they appeared to have disappeared and not returned with the status. I have also search through the internet and various peoples websites, but no luck.

My question is what am I supposed to do to get pass the 'Out of Range' problem and use the software, or let the software install. I believe it has something to do with the Graphics card, however I have no idea what I need to type and when.

**_Computer Information/Specifications_**
> 
Four Years old
RM All in One (It is one of those that are all together, from four years ago)
Integrated 15" Flat Screen
2.6 GHz Processor
512 MB Ram
40gb Hard Disk



Got it for free from my sons school (as they upgraded all computers) and he is really looking forward to using it himself at home.

Also there is a password on the BIOS menu that I am unable to guess, so I don't think I can get into that area any time soon  - hopefully the fix doesn't require that.

I would like to thank you all in advance for helping me and my son.

---

### Post by avtolle on 2009-02-13
Hopefully, you burned the iso to cd as an image and didn't copy it. If you did a copy, go back and burn it as an image to CD, at a slow speed. 

Presuming you did burn it as an image, from the same menu you used to check CD for defects, if you've not done so, select the option to run Ubuntu without making any changes to your system and see if it loads. It will be slow. If you get the "out of range" message, then it very well may be a graphics card problem. 

But first, be sure you burned it as an image and didn't just copy it.

---

### Post by jase.d on 2009-02-13
> **avtolle said:**
> Hopefully, you burned the iso to cd as an image and didn't copy it. If you did a copy, go back and burn it as an image to CD, at a slow speed. 

Presuming you did burn it as an image, from the same menu you used to check CD for defects, if you've not done so, select the option to run Ubuntu without making any changes to your system and see if it loads. It will be slow. If you get the "out of range" message, then it very well may be a graphics card problem. 

But first, be sure you burned it as an image and didn't just copy it.

Thanks for the quick reply, I should have made it clear that I did burn to the CD using InfraRecorder and also checked it with winMd5Sum and compared the code. [I have now edited my post to make it clear]

I have tried to run it without making any changes, and I am still receiving the same message - 'Out of Range'. I understand that there is way to change that, but I don't know what to do as the computer previously was able to run Windows XP at the school so it seems strange that it can't handle this.

Thanks, any more help is greatly appreciated.

---

### Post by avtolle on 2009-02-13
When at the initial menu, hit F4 to install in Safe Graphics mode to see if that helps. I've a feeling that it is a graphics issue, as I said earlier, and we need to try to avoid it. Another way to avoid during installation would be to obtain the alternate CD which uses a text based installer, and may get you installed, then to go on to work on the graphics problem.

---

### Post by jase.d on 2009-02-13
> **avtolle said:**
> When at the initial menu, hit F4 to install in Safe Graphics mode to see if that helps. I've a feeling that it is a graphics issue, as I said earlier, and we need to try to avoid it. Another way to avoid during installation would be to obtain the alternate CD which uses a text based installer, and may get you installed, then to go on to work on the graphics problem.

Thank you so much, running it in Safe Graphics Mode was exactly what I needed to do to get it running. I have just run through it and it has completed. My son has already gone to sleep, but first thing in the morning when he wakes up he is going to see that I have got it setup.

Thank you once again for your help in getting this running.

To anyone else having this problem, pressing F4 at the menu and selecting Safe Graphics Mode should get it all working for you.

Thanks again

---

