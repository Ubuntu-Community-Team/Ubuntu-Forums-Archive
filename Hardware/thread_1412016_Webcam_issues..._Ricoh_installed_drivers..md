---
title: "Webcam issues... Ricoh installed drivers."
date: 2010-02-20
forum: Hardware
---

### Post by janthonywj on 2010-02-20
Alright... I know there are plenty of other threads out there about the webcam issues with Ricoh. I felt I could start a new one, as I have read as many as I can find trying to fix this problem. 

I'm running Ubuntu Karmic (64-bit), Kernel 2.6.31-20, on a Sony FZ laptop. lsusb output is attached... Notice the detected hardware. Then, after following some other threads (mainly [http://ubuntuforums.org/showthread.php?t=1266384](http://ubuntuforums.org/showthread.php?t=1266384) ) I installed new firmware and drivers. You can see the difference in drivers in the other attachment. 

The goal here is to get skype to work. I attached the options menu for skype. It is now detecting the video device as the UVC Camera... weird since I ran the following commands after building the drivers.

sudo modprobe r5u870
sudo modprobe -r uvcvideo

Probably important to not that skype didn't have any device available in the options before I started installing new drivers. So I thought I was making progress. After I noticed that skype was detecting the UVC camera, I decided to try:

sudo modprobe uvcvideo
sudo modprobe -r r5u870

Still the same result though. I'm not an experienced Linux user FYI... 

Can anyone help me figure out this last part? :confused:

---

### Post by IcarusR on 2010-02-20
If you are trying to get your system to use r5u870 module & not uvcvideo module I believe you need to remove uvcvideo then load r5u870 the finally start skype.

So run these commands in this order...
```
sudo modprobe -r uvcvideo
sudo modprobe r5u870
skype
```

If this works then you need to blacklist uvcvideo

---

### Post by janthonywj on 2010-02-20
I tried switching the order... What you say makes sense... but still no go. Infact, now I don't see any cam under skype options. I doubt this has anything to do with what I just did. As I haven't received much response, I've been playing with it, trying to re-install different drivers I find online and such... I just don't have the skills to figure it out. 

CHALLENGE SOMEONE. I know there have to be a substantial amount of people out there with the same problem, un-addressed just because the cam is not of high priority. This is a very common built in webcam and microphone in laptops.

---

