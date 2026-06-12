---
title: "PS Eye camera microphone doesn't work after computer is restarted/woken from sleep"
date: 2020-12-02
forum: Hardware
---

### Post by aggserp4 on 2020-12-02
[COLOR=#D7DADC][COLOR=#000000][FONT=arial]I  am trying to use an old PlayStation Eye camera I've got on my computer,  as it's becoming more and more necessary to have a webcam now due to  social distancing and all that. From what I read online, the webcam is  supposed to be plug-and-play on Linux, and that was the impression I got  when first plugging it in, as both the video and audio from it worked  perfectly.
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Upon restarting my  computer however, I stumbled upon the fact that the microphone, for  whatever reason, doesn't work. It's not that the computer isn't  detecting it; it shows up on the list of connected microphones, and I  can adjust its volume, but there is no audio from it at all. The video  input from the webcam also works perfectly.
[/FONT][/COLOR]
[FONT=arial][COLOR=#000000]Upon  searching online, I found plenty of people of having problems with the  audio from this webcam, and one solution which worked for a user was [/COLOR][[COLOR=#000000]this[/COLOR]]("https://renatocunha.com/2012/04/playstation-eye-audio-linux/")[COLOR=#000000],  which, as far as I can understand, instructs PulseAudio to manually  load the module for the webcam. I tried the same solution as the one  posted on the linked blog (with the exception of using a different  number for the device since I have more audio devices on my system), but  all that accomplished was making the camera show up twice in the list  of audio inputs in GNOME Settings, with neither of them producing any  output.[/COLOR][/FONT]
[COLOR=#000000][FONT=arial]
One strange thing that I  noticed about this camera is that it doesn't seem to ever turn off for  as long as power is supplied to the computer. So the microphone on it  only seems to work once for every time it's turned on; if the computer  is powered off and then on again it won't work on the second boot, but  if I turn the power supply off and then on again as the computer is  turned off it will work on the next boot.[/FONT][/COLOR][COLOR=#000000][FONT=arial] 

I'm  not really certain what to do about this, I don't even know if this  problem is related to Linux or related to the hardware of my computer or  the camera itself. Does anyone here have any ideas?
[/FONT][/COLOR]

[/COLOR]

---

### Post by bcschmerker on 2020-12-09
I've experience with the SONY® PlayStation® Eye™, a USB camera with two optical focal-length settings and a 640x480 CCD.  I never attempted to use the onboard microphones, which don't show up in ALSA on my system.  Ye've probably encountered the hardware limitations of the camera itself, as the CCD settings cannot be adjusted in Video4LinUX.

---

### Post by aggserp4 on 2020-12-14
Thanks for the reply. Can you elaborate on what you mean by "CCD settings"?

---

### Post by bcschmerker on 2020-12-14
SONY® had OmniVision Technologies Inc. manufacture a 640x480px CCD "USB Camera-B4.09.24.1" (USB ID 1415:2000) for the PlayStation® Eye&#8482;, which (judging from sudo lsusb -d 1415:2000 -v) was apparently subcontracted to Nam Tai E&E Products Limited for assembly.  The Eye is fixed-focus at two focal lengths.  Exposure and white balance are automatic.  Webcamoid has available video formats as GRBG, RGB3, BGR3, YU12, and YV12 (YUYV renders an unusable image); available resolutions as 320x240px (top left) and 640x480px; and available FPS as 30, 37, 50, 60, 75, 100, 125, 150, and 187.

IdeasOnBoard.org does not list this camera in the [Supported Devices list at Page /uvc](http://www.ideasonboard.org/uvc/#Supported%20devices); the Eye is, at best, partially compatible.

---

