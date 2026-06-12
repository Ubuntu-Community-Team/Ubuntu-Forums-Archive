---
title: "Nvidia Quadro NVS 135M driver problems"
date: 2014-10-28
forum: Hardware
---

### Post by carval444 on 2014-10-28
Hi all,

I have some trouble with the Nvidia Quadro NVS 135M drivers.
Ubuntu selected one autocratically one for me: "Using X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau(open source)"
But when I click on the Ubuntu button, the screen goes crazy like a TV test screen([ATTACH=CONFIG]257565[/ATTACH][ATTACH=CONFIG]257566[/ATTACH][ATTACH=CONFIG]257567[/ATTACH])(see top of pictures)
When I saw this problem I decide to chose another driver "Using NVIDIA binary driver-version331.38 from nvidia-331(proprietary,tested).
But when I used That driver, my pc just crashes after a couple of seconds and my screen turns like the top of the pictures but then all over my screen, like this:[ATTACH=CONFIG]257568[/ATTACH]
there are other driver but I dont want to test them all because to get rid of that screen I reinstalled Ubuntu.

any solution?

---

### Post by jdavis2 on 2015-03-27
Ubuntu 14.4 and Kubuntu 14.10 both were randomly crashing for me. I have a D830 laptop with NVS 135M graphics. I am using Xubuntu 14.4 64 bit and it does not randomly crash. However, I do have some driver problems still. I am connected to a JVC tv with a DVI to HDMI cable from the DVI port on a docking station. With the nouveau driver, video seems to be fine but the tv won't use the analog audio input cabled separately to the tv. The nouveau driver is doing something wrong which is telling the tv to expect digital audio over hdmi. When I use the nvidia binary driver, the tv is correctly using the analog audio input, but x.org crashes on nbc.com during commercial breaks in videos.

---

### Post by jdavis2 on 2015-03-31
Update:

It looks like the problem might be lightlocker kicking in while a flash video is playing. I had increased the timeout in power management, but didn't know about lightlocker's separate inactivity timer. I switched back to the nouveau driver and was watching a video when lightlocker interrupted me with the unlock dialog. The computer recovered gracefully with the nouveau driver. I believe the interruption was crashing things when using the nvidia binary driver.

---

