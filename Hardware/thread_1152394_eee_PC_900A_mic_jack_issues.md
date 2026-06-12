---
title: "eee PC 900A mic jack issues"
date: 2009-05-07
forum: Hardware
---

### Post by smatz on 2009-05-07
hey all,

my issue seems to be the opposite of what most users are having, and i can't really find anything out on my own...  I'm running Ubuntu Jaunty, and though the internal mic works fine, ALSA seems not to recognize that the external mic jack exists.  Here's the info I got from that ALSA script thingy: [http://www.alsa-project.org/db/?f=a57a190eb29523bc2c68fc9c30f8e09e584e371c](http://www.alsa-project.org/db/?f=a57a190eb29523bc2c68fc9c30f8e09e584e371c)

Any help/advice is greatly appreciated.

Thanks!

---

### Post by jaiwithani on 2009-06-26
I have the exact same issue.

---

### Post by barrieluv on 2009-06-26
Not sure what you've tried, so:

Right click the volume icon > Open Volume Control > Preferences > make sure everything is ticked > Options tab > change the input device to Mic.  Then adjust your levels accordingly.  You'll probably have to fiddle with the Capture levels in the Recording tab.

---

### Post by Captain Rotundo on 2009-07-21
There is no option to change the input on capture for me.  Therefore I have this issue as well.

---

### Post by tarvik on 2009-08-27
i am having this exact same issue and i've been working on it for a couple hours. i'm pretty much a linux newbie so please forgive me if i'm not looking in an obvious spot :-) 

i do not see any references to 'microphone' or 'front mic' or anything like that in *any* of the sound-related areas... has anyone figured this one out? i'd greatly appreciate it!

---

### Post by Sven6210 on 2009-10-12
I had to patch the ALSA configuration file. I also had to make this patch when I installe Ubuntu 9.10 on my system. By the way, even though it is only a Beta yet I really like it. The look & feel is great and the system feels faster.

**Patching of the ALSA configuration file (/etc/modprobe.d/alsa-base.conf)**

1. Open a terminal window
2. Enter 'sudo gedit /etc/modprobe.d/alsa-base.conf'
3. Search in the file whether a line including 'snd-hda-intel' exists, if so please delete that line
4. Add the following two lines to the configuration file:

===start here===
# eeePC 900a patch
options snd-hda-intel index=0 model=quanta
===end here===

If you still have problems please let me know and I will send you an overview of all the changes I made on Ubuntu 9.04. In version 9.10 Beta I only needed to patch the ALSA configuration file and all the rest worked out of the box.

---

### Post by nilson on 2009-10-28
Thanks for that tip, but Im still getting the same errors :/ Any clues? Thanks so much. I bought this machine to run Audacity and record our "band"

Edit: using Linux Mint, but if you can fix it in Ubuntu, Im sure that will still apply

---

