---
title: "Fiio e10k headphone amp"
date: 2016-10-08
forum: Hardware
---

### Post by killnine2 on 2016-10-08
Hello, Ubuntu 16.04 doesn't recognize my Fiio e10k amp. i've rebooted while it was plugged in and it doesn't recognize it, it should be plug and play but I just can't enable it?

---

### Post by Bucky Ball on 2016-10-09
Welcome. You are going to need to give a lot more information than that. How does the thing connect to your machine? What doesn't recognise it? How are you adjudicating this? What have you done so far to try and fix? What exactly is the situation? 

'It doesn't work' will get you little support. Best to try and give as much information as possible (the release and flavour of Ubuntu you are using and some idea of your computer is always a good start ... :))

---

### Post by killnine2 on 2016-10-09
It plugs in through USB. It basically is a headphone amp, you then plug in the headphones into the headphone jack in the amp. 

I have tried to mess with the sound settings. But no avail. What do I have to do exactly?

---

### Post by Bucky Ball on 2016-10-09
Which sound settings? Pulse Audio Volume Control? If not, get some music going and launch PAVControl. Go to the 'output' tab and you should see the audio stream level meter bouncing up and down. Above that there is a drop down list box. Is the Fiio in there? Check also in 'Playback'. If it is in the drop-down list it might be a matter of experimentation.

Please open a terminal and paste this in:

```
lsusb
```

Hit enter. Post the output of that command between [code] tags (see the link in my signature at the bottom of this post for how).

---

### Post by killnine2 on 2016-10-09
> **Bucky Ball said:**
> Which sound settings? Pulse Audio Volume Control? If not, get some music going and launch PAVControl. Go to the 'output' tab and you should see the audio stream level meter bouncing up and down. Above that there is a drop down list box. Is the Fiio in there? Check also in 'Playback'. If it is in the drop-down list it might be a matter of experimentation.

Please open a terminal and paste this in:

```
lsusb
```

Hit enter. Post the output of that command between ```
 tags (see the link in my signature at the bottom of this post for how).

I went to pavcontrol and clicked on the output tab but fiio is not there. There is no stream meter bouncing up and down, that only happens on the Input devices (front microphone)

   [code]killnine@Earth:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 005: ID 413c:2010 Dell Computer Corp. Keyboard
Bus 001 Device 003: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by Bucky Ball on 2016-10-09
Is that output with the device plugged in and on? If not, please provide again (and I will request again, *between code tags*). Thanks.

---

### Post by killnine2 on 2016-10-09
Yes its plugged in, and on.

---

### Post by Bucky Ball on 2016-10-09
Well, the odd thing is I see no sign of it in your output. Please check the USB cable, swap if necessary. This device is known to work fine with other equipment? Very strange ...

With it in and on, try this one:

```
sudo lshw -C sound
```

Post the output here between code tags.

---

### Post by Yellow Pasque on 2016-10-10
If the device doesn't show up in lsusb, I would suggest plugging the device in and then checking the end of dmesg:
```
dmesg | tail -n 20
```

---

