---
title: "audio cards not listed without starting cheese webcam program"
date: 2015-05-26
forum: Hardware
---

### Post by dass-arvind on 2015-05-26
Hi Guys

I have come up with a strange thing. I have a commodity hardware which does recording. Issue is, 
sysadmin@rrd-recorder1:~$ aplay -laplay: device_list:268: no soundcards found...
sysadmin@rrd-recorder1:~$ arecord -larecord: device_list:268: no soundcards found...

Now , I will start cheese manually from desktop and close it.

Here is the new output:

sysadmin@rrd-recorder1:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev3 Analog [ALC662 rev3 Analog]  Subdevices: 1/1  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC662 rev3 Alt Analog [ALC662 rev3 Alt Analog]  Subdevices: 1/1  Subdevice #0: subdevice #0
card 1: C525 [HD Webcam C525], device 0: USB Audio [USB Audio]  Subdevices: 1/1  Subdevice #0: subdevice #0

Can anyone help me out ? Looks like starting cheese program triggers something

):P:lolflag:

---

### Post by dino99 on 2015-05-26
logs might help you know about the warnings/errors; possibly that hardware is missing a driver

---

### Post by dass-arvind on 2015-05-26
Okay, just curious, if it is missing driver, why it starts displaying results after I start/close cheese ! :popcorn:

---

