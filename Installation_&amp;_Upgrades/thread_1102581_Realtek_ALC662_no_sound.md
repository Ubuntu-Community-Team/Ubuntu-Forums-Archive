---
title: "Realtek ALC662 no sound"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by lordy on 2009-03-21
Hi,

I have recently installed mythbuntu and then proceeded to upgrade the kernel to 2.6.28 (i believe? intrepid?) to have my Dvico dual tuner recognised.

I'm a newbie when it comes to this...

Anyway, I have the problem where I am using the motherboard D945GCLF2 and am trying to get the onboard sound working.

According to 'alsamixer' i am using:

Card: HDA Intel
Chipset: Realtek ALC662 rev1

I have turned everything up and made sure nothing is muted, I have also gone through 'mixer' through the gui and made sure everything was fine there.

The only output I get is the sort of squealing sound you get when things are too loud :)
Unfortunately nothing else seems to come out.

Could someone give me a hand troubleshooting this?  Is there a simple test I can run to try to get some output?  Are there any commands etc for some output to help you figure out what's happening?

Thanks!

---

### Post by lordy on 2009-03-21
Just a note - I have muted the microphone options and no longer get the squealing.  Still no sound coming out though...

---

### Post by lordy on 2009-03-21
Solved!

If anyone else happens across my thread, I found the answer in [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Specifically - 

# webbca01 figured out how to get AC'97 work with the help of the second last post here and this post. Basically, if you have an intel8x0 module, you can get AC'97 working by
Code:

sudo nano /etc/modprobe.d/alsa-base

and adding this as the last line:
Code:

"options snd-intel8x0 ac97_quirk=3"


the only exception being i added it to the .conf file that was already there....

---

