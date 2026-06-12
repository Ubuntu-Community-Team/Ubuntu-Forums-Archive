---
title: "Black screen after suspend on Presario R3000, 9.10"
date: 2009-12-30
forum: Hardware
---

### Post by jackdesert on 2009-12-30
The good news is this: She hibernates just fine. Suspend to RAM, however, always leaves me grimacing at a black screen of nothingness :( Perhaps one of you can help me.

I am running Karmic Koala 9.10. 
On a Compaq Presario R3000
And the video card is the Radeon Mobility 9100IGP

Here is my xorg.conf file. It came with no such file, and making the additions shown here didn't seem to change anything:
> Section "Device"
    Identifier "Radeon Mobility 9100IGP"
    driver "ati"
    Option     "NvAGP"   "1"
   Option  "VBERestore" "true"
EndSectionI also looked into the proprietary ati driver, FGLRX, but my video card does not seem to be supported. If someone could point me in the right direction, or at least verify whether it's the video driver that's at issue, that would be great. 

Cheers to all of you,

J

---

### Post by derekmbarnes on 2009-12-31
Same problem on my Toshiba Satellite M500; graphics card is also ATI Radeon.

---

### Post by jackdesert on 2010-01-07
After some further experimentation, I did get my Presario R3000 to suspend properly once. I disabled the network, clicked "suspend", then toggled the caps lock button a few times while she was suspending. She woke up just fine. 

However, I cannot reproduce the results. Most attempts give me the black screen, and CapsLock does not toggle the CapsLock light. Which means there's more going wrong than the video  card just not being on. 

Could someone point me in the right  direction of how to track this down? 

-Jack

---

