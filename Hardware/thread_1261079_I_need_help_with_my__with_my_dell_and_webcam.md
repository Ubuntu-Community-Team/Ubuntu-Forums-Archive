---
title: "I need help with my  with my dell and webcam"
date: 2009-09-08
forum: Hardware
---

### Post by staylor29a11 on 2009-09-08
I have a dell inspiron b130 and i need to find a way to get drivers for a sabrent usb camera with mic. it works well on winxp but i hate windows xp because it's slow, buggy and too many crashes.  when i type into terminal, i get 1c4f:3000 and no name for my cam i've got camerarama, cheese and other softwares, i tried to test with skype but no results. any advice? Newbie to ubuntu:KS:confused::(

---

### Post by bobpaul on 2009-09-26
I think I have the same camera (does yours have 3 LEDs on either side of the lens?). It was unbranded when I bought 2 from ebay. Claimed to be supported on XP but not Vista or Linux. It worked on Vista x64 in Skype (but not Gizmo for some reason). Shows as 1C4F:3000 in lsusb without a name. Shows as "USB Web Camera /dev/video0" in Skype and cheese (gizmo on linux doesn't do video :'[ ) but nothing happens when I choose test. Anyone gotten this working?

**Edit**
dmesg shows the following after plugging in the camera: ```
[910473.416099] usb 3-1: new full speed USB device using ohci_hcd and address 4
[910473.629146] usb 3-1: configuration #1 chosen from 1 choice
[910473.630712] uvcvideo: Found UVC 1.00 device USB Web Camera (1c4f:3000)
[910473.644698] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[910473.664080] input: USB Web Camera as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input16

```

---

### Post by bobpaul on 2009-09-27
Oh. Hmm. Might just be a skype problem (hopefully just with the test part, but nobody is online to try for real). I found [This post]("http://lists.berlios.de/pipermail/linux-uvc-devel/2008-May/003527.html") and run luvcview from the term. A window showing the video appeared. Camera working, skype maybe not working.

**Edit** I upgraded to the current Karmic Alpha and the camera works Cheese as well as aMSN. It still doesn't appear to work in Skype, but I believe that to be a graphics driver related issue (using the ati driver and an Xpress 200 chip) as I can't even view other people's videos in Skype. My advice, wait for 9.10's at the end of October.

---

