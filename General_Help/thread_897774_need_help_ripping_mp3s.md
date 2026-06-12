---
title: "need help ripping mp3s"
date: 2008-08-22
forum: General Help
---

### Post by Dorkenfarber on 2008-08-22
I just bought a sansa mp3 player and can't seem to rip my music as mp3 to put music on it. I tried to follow the instructions on the cdripping wiki but found I didn't need to. I already had the gstreamer plugins. there is already a profile in my sound juicer for mp3s. for some reason it doesn't show up as an option on the list though. ditto for aac(don't really need aac though). how do I get mp3 to show up on the output format list?

---

### Post by aloshbennett on 2008-08-22
I installed gstreamer0.10-plugins-ugly-multiverse and it created an mp3 profile for sound juicer.

These are the profile details:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

---

### Post by silkstone on 2008-08-22
I suggest installing all of the following (if you haven't already!)...

gstreamer0.10-ffmpeg
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-pitfdll

---

### Post by Dorkenfarber on 2008-08-22
thanks it shows up now

---

### Post by Dorkenfarber on 2008-08-22
now the sansa isn't being recognized when I plug it into the usb. also it soesn't seem to be charging. it was fully charged when I plugged it in earlier. I left it plugged in while I went to sleep thinking maybe eventually this computer might notice it but I just woke up and not only is it still not recognized it is down to half a battery. The first time I plugged it in everything worked fine. it  charged and automatically popped up with an icon for it. can any smart people help?

---

### Post by karrank% on 2008-08-22
Which model?

 I have a 2G Clip and you can go into Settings>USB Mode> and choose either MSC (Storage) or MTP (Media player) mode.

 I use MSC mode for plain ol' dragging' & droppin' or in Windoze MTP mode might be better....

Also might want to peek into the Sansa forums,  some good info there....

---

### Post by Dorkenfarber on 2008-08-22
I have the 1G clip. the settings don't seem to do anything. It says it's connected but nothing shows up on my computer. the battery is about dead now from not charging from the usb. maybe it's a defective cable or something I don't know.

---

### Post by silkstone on 2008-08-23
The USB port should deliver 5V whether or not the device is recognised - so it should charge regardless. Assuming you're not plugging it into an unpowered hub, that suggests that either there is a fault in the cable/plugs, or that power is not getting to the USB port. Have you tried different ports?

---

### Post by Dorkenfarber on 2008-08-30
I tried all the ports it didn't work in any of them. So I traded it in for a creative zen stone 2G, and everything works now.

---

