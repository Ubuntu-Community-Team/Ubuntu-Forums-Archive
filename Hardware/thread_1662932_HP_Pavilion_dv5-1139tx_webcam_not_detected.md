---
title: "HP Pavilion dv5-1139tx webcam not detected"
date: 2011-01-08
forum: Hardware
---

### Post by AlexRiri on 2011-01-08
Hey, I've had this problem for a while. I've got an inbuilt webcam on my HP Pavilion dv5-1139tx but whenever I try to use it, it just won't detect.
When I use CyberLink Youcam I get a message saying "No video device detected. Please plug a video device into your computer. If you are using a an integrated camera please make sure that it is turned on."
I've also tried Quickplay but I just get a green screen for that, and for Skype it's a black screen.
I've checked for driver updates but it says it's up to date, and there are no drivers available for download on the HP site.
Does anyone have any suggestions?
Thanks

---

### Post by friv_livs on 2011-01-09
See if "cheese" from the repos detects it.

If not, see if it shows up in terminal with ```
sudo lshw
```.

Also try ```
lsusb
``` in terminal.

---

### Post by gnomepm on 2011-01-16
I have the same problem, but a little different.It was working fine before and now it's not working.This happend to my fingerprint reader too.Any clues?

---

### Post by friv_livs on 2011-01-16
See what kernel driver is being used for the webcam and fingerprint reader, then:

```
sudo modprobe "driver"
```

replacing "driver" with your device's kernel driver.

then shutdown, and restart using your power button.

I sometimes have to do this with my wifi card.

---

### Post by friv_livs on 2011-01-16
Didn't realize first reply went through.

---

