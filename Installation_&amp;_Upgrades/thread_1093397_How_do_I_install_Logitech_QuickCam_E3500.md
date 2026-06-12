---
title: "How do I install Logitech QuickCam E3500?"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by MrPatton84 on 2009-03-11
Hi everybody, 

How do I install this webcam on my Ubuntu laptop? The cd installation setup will obviously not run because it's an exe. file.

Do I need to download the driver instead?

Thanks in advance, 

Chris

---

### Post by thtrgremlin on 2009-03-11
As far as I know, you can just plug it in and it will work. You just need software. I would recommend using cheese to get started. 

[http://projects.gnome.org/cheese/](http://projects.gnome.org/cheese/)

```
sudo apt-get install cheese
```

---

### Post by MrPatton84 on 2009-03-11
Thanks a lot! I just plugged it in and opened up Skype and it worked :D

Only problem though, the playback flickers really badly. Any idea why this might be? I've noticed a similar problem when trying to watch videos in anything other than VLC. 

Thanks again,

Chris

---

### Post by SwapSpace on 2009-04-11
Hi all!

It worked perfectly for me too. Until now. Yesterday I did an upgrade using apt and got a new kernel image and modules, 2.6.24-23-generic. The camera just don work anymore. Skype just gives me an black screen (where the video stream is supposed to be shown) and other video capture programs just throws an "Couldn't open unit 'v4:/dev/video0': wrong argument" message. (message translated. I'm using a Swedish version)

Sys logs says nothing bad:
```
Apr 11 16:17:37 ubunt kernel: [  152.143114] usb 5-4: new high speed USB device using ehci_hcd and address 4
Apr 11 16:17:37 ubunt kernel: [  152.381023] usb 5-4: configuration #1 chosen from 1 choice
Apr 11 16:17:37 ubunt kernel: [  152.689515] Linux video capture interface: v2.00
Apr 11 16:17:37 ubunt kernel: [  152.764666] usbcore: registered new interface driver snd-usb-audio
Apr 11 16:17:37 ubunt kernel: [  152.769274] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a4)
Apr 11 16:17:37 ubunt kernel: [  152.783621] usbcore: registered new interface driver uvcvideo
Apr 11 16:17:37 ubunt kernel: [  152.783630] USB Video Class driver (v0.1.0)
```

I'm using Ubuntu 8.04 Hardy.

Any ideas?

Btw, I have tried to unplug an replug the camera. It did not do any good. I have even tried to restart the computer with the camera unpluged. No difference.


Thank you all for any help!

//Jens

---

### Post by SwapSpace on 2009-04-11
Sorry. Last message was not all true. I digged a litte bit more in my syslogs and I found a lot of these:

*Apr 11 20:13:19 ubunt kernel: [14278.597923] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).*

I found this reported bug on this item: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293409](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293409)

But the bug was reported using kernel 2.6.27 and I am using 2.6.24. I also noticed that the bugreport was dated 4th och November 2008. It should have been fixed by now right?

Any one having the same problem? Any one having any solution?

Best regards
Jens

---

### Post by jwandc3 on 2009-07-11
I bought one today in Shanghai for Ubuntu 8.04. It worked immediately on Ekiga, and after a couple of restarts, it goes great on Skype. I installed the drivers thru Wine but not sure if that's why it works. Anyway, it does. Very satisfied.

---

### Post by aj_the_first on 2009-07-27
> **SwapSpace said:**
> Sorry. Last message was not all true. I digged a litte bit more in my syslogs and I found a lot of these:
 
*Apr 11 20:13:19 ubunt kernel: [14278.597923] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).*
 
I found this reported bug on this item: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293409](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293409)
 
But the bug was reported using kernel 2.6.27 and I am using 2.6.24. I also noticed that the bugreport was dated 4th och November 2008. It should have been fixed by now right?
 
Any one having the same problem? Any one having any solution?
 
Best regards
Jens
 
 
I am having the exact same problem.  It worked perfectly in Intrepid (kernel 2.6.27), worked perfectly in Jaunty (kernel 2.6.28), but it doesn't work at all, no matter which driver I download and install, in Hardy (kernel 2.6.24)  
I have no idea why, but I really need it to work.  either that or I really need to upgrade to Intrepid again (can't use Jaunty because of video driver issues)
 
Can anyone help?

---

### Post by g00fy11 on 2009-11-09
hi,
how this webcam on ubuntu 9.10?

---

