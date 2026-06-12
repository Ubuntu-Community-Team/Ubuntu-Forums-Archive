---
title: "No sound from headphone jack"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by X40nick on 2007-12-23
Hi,

I can't get any sound through my headphones, I was trying to watch a video and I can hear it with the speakers but not the headphones?

I don't know what should card I have? How can I check?

Sorry, I am quite new to this whole Linux OS thing so keep the advice simple! 

Thank you.

Nick.

---

### Post by eggdeng on 2007-12-23
```
aplay -l
```
(that's a lowercase L, not a 1) will tell you what card you have.

---

### Post by X40nick on 2007-12-24
nick@nick-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nick@nick-laptop:~$ 


That was the response? What do I do know to get the sound playing from my headphones please?

Thank you.

Nick.

---

### Post by eggdeng on 2007-12-24
You will find some tips to get it working quickly at
[http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")
For a more exhaustive approach, try
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by ugm6hr on 2007-12-24
> **X40nick said:**
> I can't get any sound through my headphones, I was trying to watch a video and I can hear it with the speakers but not the headphones?


In that case - the problem is probably not your sound card.  You probably just need to turn the "headphone" volume up - Ubuntu (alsa sound controller) has separate volume controls for each "channel", and Ubuntu often defaults some of them to muted.

In Terminal:
```
alsamixer
```

The arrow keys move between channels and increase / decrease volumes.  **Importantly**, "M" button mutes and unmutes (there will be an "MM" or "OO" indicator near the bottom of each bar.  The tab key swaps between output channels (i.e. speakers) and input channels (i.e. mics etc).

Just unmute all the output channels and maximise all the volumes to see if it works.  From there, a bit of experimentation will let you know which is which.  You can also edit the Ubuntu main sound control to control a different channel if you wish.  Otherwise there is a GUI for alsamixer in Synaptic.

---

### Post by Aurora@FleetBuzz on 2008-01-02
Thanks, **ugm6hr**!  I didn't see this thread until today, but I had started one yesterday here:
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4053931](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4053931)

I can get sound from the headphones, but only when it's also coming out of the speakers.  When I turn down the volume of the speakers, the sound dies in the headphones.  

Any ideas on how to get the two operating independently?

---

