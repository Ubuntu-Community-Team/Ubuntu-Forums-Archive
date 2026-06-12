---
title: "82801G (ICH7 Family) soundcard issues"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by faldor on 2006-10-27
i own a toshiba a105-s4074 laptop with a 82801G (ICH7 Family) soundcard. ive seen several reports of it not working at all in linux but it does work on occasion. 

i was running dapper 6.06 and the sound would work on some reboots but not others. i soon found that when dapper was booting if i unplugged and then replugged the power cord while it was at the boot stage of "loading hardware drivers" the sound would click on just then with an audible pop in the speakers and sound would work full throttle with input and outputs including skype. so i settled on this as a fix until edgy released. i upgraded the day it released and everything went fairly smoothly except no sound. i attempted the same method as last time but i cant tell when its in the stage of loading hardware drivers on boot. so i did some searching for similar problems and found a few cases but no real solutions. one method that worked only once and has not since despite several reboots is to 

```
modprobe -r snd_hda_intel
modprobe snd_hda_intel
```

the first time i attempted the sound clicked on just like it used to and all was working fine. then after i rebooted i tried the same thing and now get an error. (i tried the modprobe commands again as i type this post and it worked, so no error for now)

the card is identified in lspci as:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

i did run into this page [http://archives.free.net.ph/message/20061010.192240.95b0eefd.en.html](http://archives.free.net.ph/message/20061010.192240.95b0eefd.en.html)

which appears to have a patch that could be related to my problem. but being somewhat new to linux i dont know how to apply the kernel patch in ubuntu and, i dont use my modem at all so i dont know if its having problems either.

to recap, as i type this post i have fully functional sound, meaning it does work. but will most likely lose this over a reboot and have to sure way to guarantee it working. after several attempts at finding information regarding this im completely lost as to what the problems is.

---

