---
title: "Sony Vaio VGN-FZ -Almost Working-"
date: 2009-03-05
forum: Hardware
---

### Post by Avatharian on 2009-03-05
Been using Ubuntu on my Vaio VGN-FZ280E for a couple of weeks now, and everything works out of the box except the camera. there are also a couple of other things that aren't quite up to snuff as i will detail here:

[LIST=1]
[*]The Backlight: My backlight control does nothing. I have absolutely no control over the backlight, it's just always at 100%. Not a huge problem, but it would be nice to be able to dim the backlight when i go onto battery power. I'm using the restricted nVidia driver version 177, if that helps.

[*]The Volume Control: For some reason, the entirety of my volume control seems to exist only in the latter 60% of the bar when I change the volume. As in, my volume is effectively muted when the bar is filled to about 60% and then goes all the way to full volume once I fill the last 40%. I'm thinking that it is just some configuration with ALSA, but I'm not really sure how to do that.

[*]As Mentioned previously, The Camera. As far as i can tell, Ubuntu isn't detecting it at all. When I run hardinfo, it doesn't appear anywhere, either in PCI or USB. I'm running a dual-boot configuration with Windows XP, and windows can see and use it just fine, although it detects it as a USB camera. It's a Motion Eye camera built into the monitor. 
[/LIST]
Help would be greatly appreciated with these issues. If anyone needs to know the output from some configuration file or command, let me know.

really nice Laptop Specs list at [http://www.docs.sony.com/reflib/docget.asp?manualid=102339&template_id=1&region_id=1&DL=']("http://www.docs.sony.com/reflib/docget.asp?manualid=102339&template_id=1&region_id=1&DL='") (PDF)

---

### Post by Avatharian on 2009-03-07
Bump..
I found something about the Motion Eye cam, but it apparently doesn't work with the current kernel

---

### Post by jordanribera on 2009-03-11
I also have a Vaio VGN-FZ (FZ410E). I've run into basically all the same issues but I've also noticed that the headphone jack on the side doesn't do much of anything.

(also: I'm thinking of trying to upgrade to 8.10 to get the newest kernel so I can try out that webcam fix. However, both of my brothers also have vaios (different models) and they have not been able to run 8.10. If I get it working I will let you know)

---

### Post by HoneyGutClusters on 2012-09-13
I know this post is ancient, but I'll toss in the answer for posterity.

If you're not seeing the camera in lspci, then it's probably a "non-WDM" model. You should see a kernel module loaded called "uvcvideo." This module is supposed to be the webcam driver module, but it doesn't have the microcode to manage the camera.

Check dmesg for any info reported by the uvcvideo module

```
dmesg | grep uvc
```

This should provide you with the ID of the camera (it was 05ca:183b in my case.)

You will find instructions and information regarding compiling the microcode loader for uvcvideo here:

[https://bitbucket.org/ahixon/r5u87x/](https://bitbucket.org/ahixon/r5u87x/)

Look at the "Quick Start" section of the site for the terminal commands to build this module.

IAdditional information can be found at:
[http://www.arakhne.org/ricoh/index.html](http://www.arakhne.org/ricoh/index.html)

---

### Post by Toz on 2012-09-13
Alot has changed in three years. Thanks for sharing, but it would be a better idea to start a new thread. 
Thread closed.

---

