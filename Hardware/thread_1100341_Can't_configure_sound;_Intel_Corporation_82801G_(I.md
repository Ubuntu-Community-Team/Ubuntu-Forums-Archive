---
title: "Can't configure sound; Intel Corporation 82801G (ICH7 Family)"
date: 2009-03-19
forum: Hardware
---

### Post by MasterSander on 2009-03-19
I have a 5.1 surround system but I can't get my sound to work on it, I managed to get sound through my headphones and laptop speakers, but I can't configure it to make the mic for example an exit for the front speakers, which I can do on windows. Any ideas?

---

### Post by MasterSander on 2009-03-21
bump

---

### Post by MasterSander on 2009-03-22
bump

---

### Post by MasterSander on 2009-03-23
bump

---

### Post by MasterSander on 2009-03-28
bump

---

### Post by jludeman on 2009-03-30
Welcome to the Ubuntu forums.

Here you'll get all the help you need - if you need no help.

On a serious note:

The problem is caused by a missing piece of code in the driver. It needs to sense a front speaker connection and flip a bit on or off.

I have a laptop that had this chipset working completely under Feisty. Now I have Hardy installed and it no longer works. 

I could revert to Feisty I suppose but there are some improvements in Hardy that I really like.

If I find the solution I will post back.

If you find one please post back in order to help others with the same problem.

The reason it works in Windows is because Windows has a driver written by Realtek who designed the audio portion of the 82801G. 

The 82801G is a multifunction device integrating several chipsets.

Drivers are written by volunteers for Linux. So patience is a must.

---

### Post by jludeman on 2009-03-30
Okay

I got mine working.

I wish I could give credit for the fix. I can't remember where I found it.

I'm pretty sure it was linuxquestions.org.

The trigger was on these forums although the exact answer was not. Link follows

[http://ubuntuforums.org/showthread.php?t=616845&highlight=82801g+front](http://ubuntuforums.org/showthread.php?t=616845&highlight=82801g+front)

Exact fix for my system:

sudo gedit /etc/modprobe.d/alsa-base

added this line:
options snd-hda-intel position_fix=1 model=3stack

Saved the file and rebooted. Success.

---

