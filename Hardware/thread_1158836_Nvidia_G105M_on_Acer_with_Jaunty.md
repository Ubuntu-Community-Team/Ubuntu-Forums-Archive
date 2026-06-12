---
title: "Nvidia G105M on Acer with Jaunty"
date: 2009-05-14
forum: Hardware
---

### Post by dedalonet on 2009-05-14
hi all,
I have a laptop acer with Graphics card Nvidia G105M, aspect ratio of laptop's lcd is 16:9 with max resolution 1366x768 but ubuntu don't let me set this resolution, i can set only 1280x720 so I installed restricted drivers for nvidia.
Now my lcd is splitted in 6 parts with resolution 640x480 for each part, i tried to set manually my xorg.conf but nothing changed. 
what should I do? 

thanks

---

### Post by pro003 on 2009-05-14
did you try to set your resolution in System > Preferences > Display ?

And uncheck Mirror screens...

---

### Post by dedalonet on 2009-05-14
yes i tried but nothing changed

---

### Post by pro003 on 2009-05-14
just how did you get 6 parts of your desktop each 640x480???

can u post a screenshot?

---

### Post by dedalonet on 2009-05-14
ok now i'm working, after i'll post it.
thanks for support :D

---

### Post by pro003 on 2009-05-14
[http://ubuntuforums.org/showthread.php?t=1158622](http://ubuntuforums.org/showthread.php?t=1158622)

---

### Post by ahurt on 2009-05-14
Can you please advise me on how you got it working? I have an ASUS N51Vf with nVidia GT 130M and a 1366x768 panel. I too have the "6 screens" issue. I've tried myriad xorg.conf tweaks as well as trying every nVidia beta driver as soon as it hits.

Cheers,
Andy

---

### Post by fabianb on 2009-06-03
I also have the "six screens" issue when I enable the nvidia driver on an acer laptop with a nvidia GeForce G105M, using Jaunty.

I can however reach the full resolution under the standard driver, so I am happy for now. Though if someone finds an answer for this I would be very interested.

---

### Post by fabianb on 2009-06-04
btw the EnvyNG method linked to in post #6 yields the same (six screens) result.

---

### Post by ZeroXtreme on 2009-06-06
Have the same video card and same resolution on an Acer Aspire 4937G, I have installed Jaunty x64 successfully, and everything works fine except for the display, and I haven't tried to install the restricted drivers or tried the EnvyNG method.

Any speculations on the issue? Is it the video card or the resolution? Both are fairly new, in fact Nvidia does not have an official release for the 100 Mobile series.

Any comments? 

EDIT:

I apologize, apparently the restricted drivers work just fine, it detects the proper resolution and I have even enabled Compiz on it without any problems.

Its managed through the Nvidia control panel though, not the built-in screen settings panel, which of course is not an issue.

Again I apologize...

---

### Post by haaglin on 2009-06-20
Hi. 

I have an aspire 5738z with G105m, and have the same issues. Both the restricted and envy's driver give me the "6 screen" problem. In nvidia config, max resolution is 640x480. Could you post your xorg.conf?

---

### Post by ZeroXtreme on 2009-06-21
> **haaglin said:**
> Hi. 

I have an aspire 5738z with G105m, and have the same issues. Both the restricted and envy's driver give me the "6 screen" problem. In nvidia config, max resolution is 640x480. Could you post your xorg.conf?

Below is my xorg.conf:

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

Nothing special about it, from what I understand, jaunty no longer uses the xorg.conf file for display configuration. Please correct me if I am wrong.

---

### Post by klueze on 2009-08-24
hi

I'm using gateway laptop with Nvidia G105M too

After the 6 screen problem when installing the driver

I tried to install the driver manually but it didn't work either

and I can't start the effect anymore

usually if i installed automatically n restore the setting to normal

I still can active the effect even with the 6 screen problem

can anyone help?

---

### Post by Gillian00 on 2009-08-24
hey :)  

I had the same problem and I looked on  nvnews.net   and found this :  [http://www.nvnews.net/vbulletin/showthread.php?t=132041](http://www.nvnews.net/vbulletin/showthread.php?t=132041)

Envy do not fix this problem 



Enjoy

---

