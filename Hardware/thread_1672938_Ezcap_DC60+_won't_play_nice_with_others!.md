---
title: "Ezcap DC60+ won't play nice with others!"
date: 2011-01-21
forum: Hardware
---

### Post by SteveDee on 2011-01-21
Having successfully married up a composite video camera to "motion" via an Ezcap, I rushed out and bought a second device so I could monitor the action in 2 bird nesting boxes.

Unfortunately the 2 Ezcaps don't want to work at the same time, on the same computer. Whichever starts up firsts, runs OK. But the second one produces an error:-
> 
v4l2: ioctl queue buffer failed: No space left on device


This seems to be a shortcoming in the EM28xx driver, so I've tried experimenting with a couple of variables.

According to this: [http://www.kernel.org/doc/Documentation/video4linux/CARDLIST.em28xx](http://www.kernel.org/doc/Documentation/video4linux/CARDLIST.em28xx)
..there are 77 possible card settings.

As my device is a eb1a:2861 I've tried "CARD=1".

I've also read that "alt=3" is supposed to fix this kind of problem (I think this increases the buffer size). But while this does allow video capture from both devices at the same time, the video has a lot of horizontal instability (its unusable!).

So the best I can come up with is to load the driver like this:-
```

sudo modprobe EM28xx card=1 alt=4

```
...which results in a slight horizontal random noise pattern (like short horizontal lines) on both video streams.

I'm not sure that trying the other 76 card settings with the 8 possible "alt" settings is a practical proposition, so if anyone has a better answer to this problem, or can explain what the "alt" options are for, please let me know!

---

### Post by rmt1947 on 2011-01-21
The symptom "first EasyCAP works, second doesn't" usually indicates inadequate USB bandwidth in the computer, in other words a hardware limitation, so I guess the answer is to get the em28xx driver to reduce the framerate somehow.  If this approach fails another solution is available at modest cost - see posts #3, #8 and #10 at:

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3901200](http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3901200)

Mike

---

### Post by SteveDee on 2011-01-22
Hi Mike, thanks for your input.

I may have to fall back on the suggestion of a 2nd USB interface card, but for the moment I want to stick with the old Compaq Evo that I'm using, which does not support expansion. As this system will be running continuously from the end of February 'till the beginning of July, the Evo is a good choice as the input power is typically just 30watts, and this computer is super reliable when running Lubuntu.

 This system will happily display video from 2 standard USB webcams via 2 instances of mPlayer. So I'm hoping that the 'bandwidth' issue with the EzCaps is something that I can either fix or at least improve upon.

I'd like to get a better idea how the EzCap system works, and I think you may be able to help.

Here are a few points which puzzle me, and maybe you can comment on:-
 - I am surprised that the EM28xx list I refer to in my previous post does not have a "eb1a:2861" reference listed against an "eMPIA Technology, Inc, EM2861" entry. If this list can be relied upon, then my card setting should be "1", but this setting does not support "audio". (so far I have checked 46 card options, and 12 support audio).
 - I'm using audio support as an indication that a card setting may, or may not, be the correct one. However, its possible that none of these settings are "correct" and that a better video compromise might be reached by using a "mute" card option.
 - If Markus Rechberger (the driver king) is an eMpia employee, why isn't the eMpia product/driver relationship better defined?
 - How does the Ezcap/driver/application plumbing work when it comes to bandwidth? Examples:-
 - - When you change the bitrate in the application, are you controlling the data transfer between Ezcap and driver, or just using less data from the driver?
 - - I understand that the Ezcap has a basic PAL resolution of 720 x 576, so does reducing the application resolution actually reduce USB data flow, or does it remain unaffected?
 - - I've seen tables concerning the "alternate" option like this:-
> 
Alternate setting 0, max size= 0
Alternate setting 1, max size= 0
Alternate setting 2, max size= 1448
Alternate setting 3, max size= 2048
Alternate setting 4, max size= 2304
Alternate setting 5, max size= 2580
Alternate setting 6, max size= 2892
Alternate setting 7, max size= 3072

...they are not always the same, so I suspect they relate to specific hardware, but basically I don't know what they are.

 - - They do look like buffers, and since I get a better result using 3 or 4, I assume they are within the Ezcap. However, this does not explain why 5-7 are worse than 4 on my device. So I'd still like to know what they are and (if they are in the Ezcap) how I can check what is available on my device.

There are probably other commands and options (I think I've seen something like "i2c_scan") so any info on these would be helpful also.

Thanks once again, Steve

---

### Post by rmt1947 on 2011-01-22
Hi Steve,

> - - When you change the bitrate in the application, are you controlling the data transfer between Ezcap and driver, or just using less data from the driver?
- - I understand that the Ezcap has a basic PAL resolution of 720 x 576, so does reducing the application resolution actually reduce USB data flow, or does it remain unaffected?


This is the crux of the matter.  In my driver (for EasyCAP DC60 with USB ID 05e1:0408 ) I cannot reduce the quantity of data conveyed over USB because I don't know how to set the registers of the STK1160 chip in order to achieve this - there is no datasheet available.  But (as far as I know) reverse engineering was not needed for the em28xx driver used by your EzCAP DC60+ (USB ID eb1a:2861), so it's possible that if mplayer (say) sends the right instructions requesting a lower framerate the em28xx driver will respond by setting some registers in the em2861 chip which reduce that bitrate over USB.  I don't know whether this actually the case because I (still) have not looked at the em28xx source code.

You might consider raising your questions with the kernel programmers who maintain the em28xx driver.  They live on the mailing list at

[http://www.mail-archive.com/linux-media@vger.kernel.org/maillist.html](http://www.mail-archive.com/linux-media@vger.kernel.org/maillist.html)

It's mostly programmer chat, but you'll see that there is an occasional question from an end-user.  If you do get an answer (which may be brusque) it will be definitive.  A less bruising alternative might be the list at

[http://dir.gmane.org/gmane.linux.usb.user](http://dir.gmane.org/gmane.linux.usb.user)

I don't read these lists myself so I cannot judge how useful they would be in getting information on the em28xx driver, but they might be a better bet than the Ubuntu forums.

Mike

---

### Post by SteveDee on 2011-01-23
Hi Mike,

I've decided to give up on this one, and I'll either use these devices with individual USB controllers or on separate computers.

But here are a few final comments & observations:-

 - Changes to the application bitrate and resolution do not seem to make any difference, although the images from mPlayer are better (more stable) than with Motion.

 - Although I can run both of my _USB_ cameras together, I suspect this is because one is old & maybe a USB 1 device, so perhaps it needs less bandwidth. Whereas the 2 Ezcaps with composite video cameras require too much bandwidth.

 - There are problems with the EM28xx drivers. When inserting the Ezcap the system auto selects "card=1" (as per the list referenced above) but this cannot be correct, because its one of the options that does not support sound. (I have reported this to: [email]linux-media@vger.kernel.org[/email] ...but I'm not holding my breath!)
 
 - Although using "sudo em28xx card=<n>" forces the driver to use card <n>, when you have 2 (Ezcap) devices, the second one reverts to the autodetected value (i.e. card=1). I could not see a way to overcome this.

 - This article reflects on the "bad blood" surrounding the development & implementation of the Linux em28xx driver: [http://lwn.net/Articles/306601/](http://lwn.net/Articles/306601/)

Once again, thanks for you input.

Steve

---

### Post by beh on 2012-03-16
> **SteveDee said:**
> Hi Mike,

I've decided to give up on this one, and I'll either use these devices with individual USB controllers or on separate computers.

But here are a few final comments & observations:-

 - Changes to the application bitrate and resolution do not seem to make any difference, although the images from mPlayer are better (more stable) than with Motion.

 - Although I can run both of my _USB_ cameras together, I suspect this is because one is old & maybe a USB 1 device, so perhaps it needs less bandwidth. Whereas the 2 Ezcaps with composite video cameras require too much bandwidth.

 - There are problems with the EM28xx drivers. When inserting the Ezcap the system auto selects "card=1" (as per the list referenced above) but this cannot be correct, because its one of the options that does not support sound. (I have reported this to: [email]linux-media@vger.kernel.org[/email] ...but I'm not holding my breath!)
 
 - Although using "sudo em28xx card=<n>" forces the driver to use card <n>, when you have 2 (Ezcap) devices, the second one reverts to the autodetected value (i.e. card=1). I could not see a way to overcome this.

 - This article reflects on the "bad blood" surrounding the development & implementation of the Linux em28xx driver: [http://lwn.net/Articles/306601/](http://lwn.net/Articles/306601/)

Once again, thanks for you input.

Steve

This may not apply to you any longer, but hopefully this will help someone else out in the future. If you need to specify multiple cards to the driver you can do so with commas in between (e.g. modprobe em28xx card=10,20 ).

---

