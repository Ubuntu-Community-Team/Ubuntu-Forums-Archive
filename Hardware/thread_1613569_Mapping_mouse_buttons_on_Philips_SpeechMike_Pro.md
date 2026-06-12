---
title: "Mapping mouse buttons on Philips SpeechMike Pro"
date: 2010-11-04
forum: Hardware
---

### Post by KFwLsKvVAs on 2010-11-04
Hello,

I am trying to get a Philips SpeechMike Pro to work on my ubuntu 10.10 machine.  The mouse, right click and left click work automagically, but there are buttons near the bottom of the device (F1 - F4) that do not, along with 6 buttons on the top (EOL/**P, RECORD, INS/OVR, F.RWD, PLAY/STOP, and F.FWD) that also do not work.  What I would like to do is be able to map each of the buttons how I want, and I tried using "btnx" to detect it but it responds with "error: could not find any event handlers" and then repeats "warning: no valid pipes from pid: 3849" many many times.  

Is there a way to get btnx to detect all of the buttoms, or a different way to map them?

Separately, and I'm not holding my breath, but is there a way to make the record function of the speechmike work as an audio line-in?

Thanks for any help.

---

### Post by KFwLsKvVAs on 2010-11-04
also, here is a picture if it's any help.  

[http://www.pcaspeech.com/onlinestore/usrimage/0speechmike5276.jpg](http://www.pcaspeech.com/onlinestore/usrimage/0speechmike5276.jpg)

---

### Post by KFwLsKvVAs on 2010-11-09
bump?

I've tried using xev to bring up the white box to figure out what the extra buttons on the speechmike thing show up as, but none of the extra buttons (f1 - f4, reverse play/pause, forward, record, and 2 other buttons on the top that I don't know what they're intended for) record any sort of button event in xev.  Is there some sort of config. file to edit to make these buttons active or something?  What about getting the mic to work with the record button?

---

### Post by simohell on 2012-05-17
> **murderape said:**
> What I would like to do is be able to map each of the buttons how I want, and I tried using "btnx" to detect it but it responds with "error: could not find any event handlers" and then repeats "warning: no valid pipes from pid: 3849" many many times.  


Since I found this on google and had a similar result:
Try to run the command with sudo.

```
sudo btnx-config
```

---

