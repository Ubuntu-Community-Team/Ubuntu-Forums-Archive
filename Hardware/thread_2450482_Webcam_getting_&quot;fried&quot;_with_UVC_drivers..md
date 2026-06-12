---
title: "Webcam getting &quot;fried&quot; with UVC drivers. How to avoid?"
date: 2020-09-14
forum: Hardware
---

### Post by musicant on 2020-09-14
I've got a new Thinkpad T14s (Intel), running Ubuntu 20.04 with mainline kernel 5.8.8. (The laptop is so new, the drivers in the LTS kernel aren't all there yet, so I grabbed something more recent.) I spent the last 24 hours trying to solve a problem I had with the built-in webcam. I had spent a little time tweaking its settings in OBS Studio (which sits on top of the typical UVC drivers), and after making a change or two the quality of the webcam got MUCH worse. Blurry, black specks, etc. Usable, but lousy. So, I hunkered down and did some reading, and learned about guvcview and v4l2, both of which let me look at and tweak the settings. Nothing I could do could come close at fixing the webcam. I could make it brighter, dimmer, change color, make some resolution changes, and for the most part I could make it _worse_, but I couldn't get it to the level I knew it should be at. Reboots wouldn't fix it: the change was clearly persistent in the webcam.

Finally, I rebooted to the emergency Windows partition I had. Windows Camera app looked terrible. Skype looked terrible. I found a forum out there suggesting resetting video settings in Skype. Tried it; didn't work. In a moment of inspiration hours later, I started up Panopto, which is a video capture app that my workplace provides. BAM! It restored the camera settings to something that looked great. Holy moly, thank goodness. But when I looked at all the sliders and switches (brightness, auto exposure, etc, you name it), it was all really close to defaults, and certainly nothing dramatically different from what I tried. I was seriously beginning to doubt myself that it had ever looked better.

So, I rebooted to Linux again, and started up Cheese. Looked fine at first, but then I started tweaking to change resolutions, and BAM, the camera went out again and got much worse in quality. Reboot to Windows, start Panopto, go to record a video, and again camera looks good. Stuck around for a Linux reboot, and even looks good now in OBS Studio, so long as I am VERY CAREFUL not to change settings.

So, I've got a bunch of questions, some vary basic, some less so. I'd love answers to all of them, but I'll settle for an answer to whatever people can help with.

1. WTF is actually going on here? Is this a bug in the camera firmware?

2. Whether it's a camera bug, a UVC driver bug, or otherwise, is there somewhere useful I can file this as a bug report? If so: where, and what information should I provide that would be useful? I'm guessing that a general email to Lenovo customer support isn't going to do it.

3. I literally lost a bunch of sleep over this: until I discovered the Panopto hack, I was convinced I'd fried my webcam. Changing settings in guvcview wouldn't fix it: I could put in the precise same settings that had been there when I first booted back to Linux before I fried it again, and it wouldn't help. I would love to find a way to lock down my webcam so software can't change its settings and do this. Is there any way I can do that, i.e. lock the camera so the UVC drivers can't fry it? I've seen some websites that say the changes you make with a UVC tool aren't persistent to reboots, but they clearly are to this setup. They even persist across OS updates. I assume there must be some kind of flash in the camera storing that?

4. WTF is Panopto doing that nothing else will? I tried resetting my webcam to defaults using guvcview, but it set the sliders and knobs to default values, but the image still looked terrible. Ditto in Windows with Skype. Panopto is magic. Is there some other tool or mechanism I could have used to get the webcam to reset to factory defaults, preferably from within Ubuntu?

Many thanks for the help. I'd love to understand more deeply what's going on here, and I haven't been successful at finding solid explanations of what sort of changes can be made to the webcam from the Windows side beyond what the UVC drivers are presumably doing in Ubuntu.

---

### Post by crip720 on 2020-09-14
Think it is more to do with it being very new hardware.  Linux and Windows settings do not cross over.  You had to get the newest kernel for the laptop, imagine that windows is not up to date on it either.  Lenovo would be the best place for answers, if they want to help.  Could also just be a buggy/defective webcam.

---

