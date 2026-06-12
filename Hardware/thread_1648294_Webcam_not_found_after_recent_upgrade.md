---
title: "Webcam not found after recent upgrade"
date: 2010-12-18
forum: Hardware
---

### Post by sber0903 on 2010-12-18
Hello.

I  run Ubuntu on a Sylvania G Netbook, and haven't been using it since the spring.  When I started using it again recently, of course there were upgrades available after the hiatus, so I gladly upgraded.

After doing so, I attempted a video chat on Skype (my primary use for this netbook) with fail of the video part.  This c0mputer c0mes with a built in webcam, so there is no way for me to unplug the USB.

I would say I am a beginner level user, but after searching through the forums for sometime, I believe it might be a driver issue,  but I do not know how to go about fixing this problem.  I tried a few other things that I saw with typing c0mmands into the Terminal, but I generally don't know what I am looking at/for.
Thank you!

Also, while I am here, I might as well ask about another problem I have had since I got this c0mputer off of Ebay.  I have installed the Flash plugin, but still can't watch video.  Sometimes with Youtube I get audio, but not always.  Is there something special for Linux/Ubuntu in regards to Flash that I am missing?  I downloaded the version re***mended for Ubuntu, but it just doesn't work correctly.

I also can't get Pandora to work.  It begins loading, and then freezes a quarter of the way through, and says 'Done' at the bottom of the Mozilla Firefox window.

---

### Post by sber0903 on 2010-12-19
Results of running "lsusb" in Terminal:

user@netbook:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 002: ID 18e8:6229 Q*** RT2573
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Results of running "lsmod | grep video":

user@netbook:~$ lsmod | grep video
video                  17375  1 i915
output                  1871  1 video

---

### Post by IcarusR on 2010-12-19
Looks like webcam is not listed in lsusb & not recognised by ubuntu.

Is there any mention of it in the log files ?

---

### Post by sber0903 on 2010-12-19
I'm sorry, how do I find the log files?  Pretty fresh to Ubuntu here.  Thank you for your patience though.

All I know is that the integrated webcam worked before I updated Ubuntu.  I can find nowhere on the internet any information about this webcam.  
Is there a way to jump back to before I updated the computer?

---

### Post by IcarusR on 2010-12-19
> how do I find the log files?

System > Administration > Log File Viewer

Install cheese run from terminal, what errors do you get ?

---

### Post by sber0903 on 2010-12-19
"No device  found" in Cheese.  Same in Skype.  Fn+Esc has no results.

There is no "Log File Viewer" to be found in Administration

---

