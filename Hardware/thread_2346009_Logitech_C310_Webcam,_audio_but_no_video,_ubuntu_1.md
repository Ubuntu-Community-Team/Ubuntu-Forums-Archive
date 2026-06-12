---
title: "Logitech C310 Webcam, audio but no video, ubuntu 16.04"
date: 2016-12-10
forum: Hardware
---

### Post by kingrpg2 on 2016-12-10
I have had a Logitech C310 webcam for a while now.  Back when I had 14.04, audio and video worked fine.  Then at some point, the video stopped working but the audio input continued to work.  Later I decided to do a fresh 16.04 install on the same machine and the video still does not work.  I have spent some time searching through support threads for this webcam, but none seem to provide a working solution for me.

To elaborate on what I mean concerning the video, when I test the video in Cheese or Skype, a completely black display is shown.  With guvcview, no image is also shown, but the Guvcview window crashes instead.  However, the LED on the camera does light up.  Typing lsusb shows the webcam is indeed plugged in:
> 
Bus 003 Device 005: ID 046d:081b Logitech, Inc. Webcam C310

Furthermore, when I go to the audio settings, the webcam is recognised as a microphone input device and the microphone works normally.

When I load guvcview in the terminal, the following message continually appears as it tries to capture video:

> 
V4L2_CORE: Could not grab image (select timeout): Directory not empty

This is preceded by the following preamble:

> GUVCVIEW: version 2.0.2
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
ALSA lib pcm_dmix.c:1029:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm_route.c:867:(find_matching_chmap) Found no matching channel map
ALSA lib pcm_dmix.c:1029:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock


Any help would be appreciated, thanks.

---

