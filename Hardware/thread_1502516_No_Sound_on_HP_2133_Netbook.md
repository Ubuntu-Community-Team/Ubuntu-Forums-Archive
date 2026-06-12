---
title: "No Sound on HP 2133 Netbook"
date: 2010-06-05
forum: Hardware
---

### Post by junderdown on 2010-06-05
I did a fresh install of 10.04 on my HP 2133 netbook a couple of weeks ago, but after a recent update the sound is completely broken, and nothing shows up in the devices tab of the Sound Preferences dialog.  It worked perfectly for a couple of weeks.

I ran the alsa info script and the results are at:
[http://www.alsa-project.org/db/?f=d3358755f652ddd5dc5f0aaccc6a24e7649c817d](http://www.alsa-project.org/db/?f=d3358755f652ddd5dc5f0aaccc6a24e7649c817d)

---

### Post by lidex on 2010-06-06
Try upgrading alsa via the alsa-upgrade link in my sig.

---

### Post by redraven on 2010-06-07
Seems like a lot of people are having trouble to get sound working correctly one the Ubuntu 10.04. I found one solution I am testing right now : 
At the end of the /etc/modprobe.d/alsa-base.conf add the following line: 
[FONT=Courier New]
[/FONT][FONT=Lucida Console][FONT=Courier New]options snd-hda-intel position_fix=1[/FONT]
[/FONT]
source: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/536699](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/536699)
See response #19

I did not update my alsa drivers. The sound is working now. :guitar:
There may be some minor differences between the hp2133, hope this works for you.

---

### Post by lidex on 2010-06-07
> **redraven said:**
> Seems like a lot of people are having trouble to get sound working correctly one the Ubuntu 10.04. I found one solution I am testing right now : 
At the end of the /etc/modprobe.d/alsa-base.conf add the following line: 
[FONT=Courier New]
[/FONT][FONT=Lucida Console][FONT=Courier New]options snd-hda-intel position_fix=1[/FONT]
[/FONT]
source: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/536699](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/536699)
See response #19

I did not update my alsa drivers. The sound is working now. :guitar:
There may be some minor differences between the hp2133, hope this works for you.

And that relates to OP's sound issue how??

---

### Post by redraven on 2010-06-08
I got a hp2133 myself. I tried this myself ad the sound is working. But I am worried that HP have created minor different versions of the hp2133. 

BTW, I've been experimenting a bit further, this seem to be a better configuration at the /etc/modprobe.d/alsa-base.conf:
[FONT=Courier New]
options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1[/FONT]

The sound now works after suspend and hibernate. The power_save option may case the sound to need a short second to wake up after it has been idle.

---

### Post by redraven on 2010-06-10
Sorry, my configuration proposal DOES NOT WORK !:oops:
I did test it after waking up for both suspend and hibernate. But yesterday I left my laptop in suspend mode over the night, the result; well, NO SOUND. 

My conclusion is that this is not a configuration issue.

---

