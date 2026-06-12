---
title: "1 audio jack out of 3 not working on laptop"
date: 2016-10-14
forum: Hardware
---

### Post by ramikhatib on 2016-10-14
I have Windows 10 + Ubuntu 16.04 installed on my laptop. The audio chip installed is realtek ALC898.  The laptop has 3 audio jacks on the right side. By default from furthest to closest:

 
[LIST]
[*]Line-out
[*]Microphone
[*]Headphone
[/LIST]


All 3 work normally on Windows 10. The first 2 are working normally in Ubuntu. The last one is not detected at all.

I installed alsa-tools-gui and opened hdajackretask. This is how the pins are by default.



[IMG]http://i.imgur.com/ApxnfRc.png[/IMG]

Pin 17 for the 1st jack and pin 18 for 2nd jack. I ticked unconnected pins. After testing, I found out that pin 1b is the 3rd jack. I ticked Override on pin 1b and chose Headphones. Now Ubuntu detects the jack when I plug earphone in or out switching between Headphones and Speakers.

The only issue is that there is NO sound coming out of the jack. I tried messing around with Advanced override, set model=auto, and install boot override. No sound comes out of the jack. Only thing working is that I managed to let Ubuntu detect it.

---

