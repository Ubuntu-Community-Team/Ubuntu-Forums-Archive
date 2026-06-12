---
title: "External hdd failure"
date: 2009-06-23
forum: Hardware
---

### Post by Michlis on 2009-06-23
I have problems with external hdd connected using USB<->IDE adapter. It was formatted into 2 partitions (FAT+EXT3) for both Linux and Windows backup purposes. When copying some pictures on Windows file transfer has stopped in the middle and after some time I had to kill it (LED on hdd enclosure didn't indicate any activity). Since then, the hdd is not recognized at all neither under Windows nor Linux (lsusb shows nothing new after plugging the hdd). I am afraid the hdd is gone, since there is no sound on power-up, as it used to be a bit noisy before.

Is there anything I can do to check/repaid/recover the hdd?

What format for USB hdd partitions do you recommend to use both under Linux and Windows to avoid such problems in future?

---

### Post by rob2uk on 2009-06-23
You may find that it's only the drive controller in the enclosure that's gone wrong, rather than the actual drive - The enclosure I use shows up as one device using lsusb/Windows Device Manager, the drive itself shows up as another.

Try to borrow another enclosure from someone and drop your drive into that,

[EDIT] Same goes for the USB -> IDE adapter, if you mean one of these: 

[IMG]http://www.lakewoodconferences.com/direct/dbimage/50280447/USB_to_IDE_Adapter.jpg[/IMG]

---

