---
title: "Fingerprint reader problems"
date: 2012-01-22
forum: Hardware
---

### Post by Lockheed on 2012-01-22
I have been trying to set my fingerprint reader to support xscreensaver, sudo etc.
I tried all 3 solutions:
- ThinkFinger (doesn't support my hardware)
- fprint (there's something wrong with it, too)
- fingerprint-gui

I got the furthers with the last one. The issue I am stuck on now is, that it does not seem to have access to USB device, even though I added my user to the appropriate group.

Although scanning my finger on 'su' command works fine:
```
$ su
Password: fp:debug [fp_init] 
fp:debug [register_driver] registered driver upekts
fp:debug [register_driver] registered driver upeke2
fp:debug [register_driver] registered driver aes4000
fp:debug [register_driver] registered driver aes2501
fp:debug [register_driver] registered driver uru4000
fp:debug [register_driver] registered driver vcom5s
fp:debug [register_driver] registered driver upeksonly
fp:debug [register_driver] registered driver aes1610
fp:debug [register_driver] registered driver vfs101
fp:debug [find_supporting_driver] driver upeksonly supports USB device 147e:2016
fp:debug [find_supporting_driver] selected driver upeksonly supports USB device 147e:2016

Fingerprint Login 1.02
Authenticating root
Swipe your finger or type your password:
OK
fp:debug [fp_exit] 

[root@panzor juha]# 

```

for some reason it doesn't for sudo, nor for the xscreensaver:
```
fp:debug [fp_init] 
fp:debug [register_driver] registered driver upekts
fp:debug [register_driver] registered driver upeke2
fp:debug [register_driver] registered driver aes4000
fp:debug [register_driver] registered driver aes2501
fp:debug [register_driver] registered driver uru4000
fp:debug [register_driver] registered driver vcom5s
fp:debug [register_driver] registered driver upeksonly
fp:debug [register_driver] registered driver aes1610
fp:debug [register_driver] registered driver vfs101
fp:debug [find_supporting_driver] driver upeksonly supports USB device 147e:2016
fp:debug [find_supporting_driver] selected driver upeksonly supports USB device 147e:2016
fp:debug [fp_exit]
```
And nothing happens. After ~1 minute, it times out never getting to the "Fingerprint Login 1.02" stage.

I would relaly appreciate some help with it, because after long, long search I am fairly certain, there is no online resources that could help with that, and that includes fingerprint-gui documentation.

---

