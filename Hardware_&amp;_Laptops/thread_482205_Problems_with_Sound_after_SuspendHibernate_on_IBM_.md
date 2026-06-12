---
title: "Problems with Sound after Suspend/Hibernate on IBM R52 Laptop with Ubuntu"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by shmi85 on 2007-06-23
Hi everyone --

Basically the problem is that my sound is only working sporadically. It worked right out of the box for mp3s (after I downloaded the codecs, obviously), for downloaded video, for video embedded in websites, system sounds and etc. But then I think after I put it in Hibernate, the sound stopped working. I didn't particularly associate the sound with the sleep features, I thought I had some kind of crappy software soundcard or something (if such a thing exists). So I downloaded ALSA Mixer, according to some documentation on ubuntu.com, and I can play around with the slider controls, which I take to mean that my soundcard is working . . . except that it's not.

So eventually, yesterday, I gave up and went with the Windows Solution and just restarted, which seemed to do the trick. My sound was working perfectly, as ennumerated above. And then last night, I put it into Hibernate mode and today when I started it up again, the sound was dead. I restarted, but this time the restart didn't work at all.

Unfortunately, I can't tell you what soundcard I have since I don't know how to find that out in ubuntu (the equivalent of Device Manager in Windows or something similar).

Thanks for any help anyone can offer -- please remember that I'm pretty new at this and any instructions should be listed out in painful step-by-step detail so I can follow what I need to do :)

~Elisa

---

### Post by twisted_steel on 2007-06-24
I just had this happen to me with an IBM Thinkpad T42.  I tested out hibernate and resume, which worked fine - wireless, video, and everything came back ... except for the sound.  I played with the mixer controls, and everything looks fine on that end.  When I do the sound test in Sound Preferences, I don't heard anything.  In fact, the progress bar that shows that something is playing doesn't even move.  I thought it used to.  I'm still having the problems after a reboot.

---

### Post by twisted_steel on 2007-06-24
It looks like this is a fairly common problem.  I tried the tip on launchpad, which suggested shutting down completely instead of just rebooting.  This cleared it up for me.  I'm going to play around with some of the other suggestions on there.

Launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)

---

### Post by twisted_steel on 2007-06-24
Changing the HIBERNATE_MODE in /etc/default/acpi-support seemed to do the trick.  I played an mp3 before hibernating and opened a web browser.  I hibernated, resumed, and mp3 playback still works.

Open the file for editing:
```
sudo nano /etc/default/acpi-support
```Find the line:
```
# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown
```Comment out the old line and add the HIBERNATE_MODE=platform line:
```
# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
#HIBERNATE_MODE=shutdown
HIBERNATE_MODE=platform
```Save the file (CTRL+O, <enter>, CTRL+X).  The previous is the letter O, not the number 0.  I'm not sure if you have to reboot for changes to take affect, but I did just to be on the safe side.

---

### Post by shmi85 on 2007-06-24
Stellar, editing the hibernate mode also worked for me. Thanks a bunch!

---

### Post by Deep Dish on 2007-06-29
Wow! 
I've been having this sort of problem since Dapper Drake, and that is the only thing I had to do!?!

*sigh*
Regardless, I very much appreciate this find! 

Thanks a million!!!!!!!!!!! :D

---

### Post by ercork on 2007-07-25
Great solution twisted_steel - worked perfectly for me. Thanks!

---

