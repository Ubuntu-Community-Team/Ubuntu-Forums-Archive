---
title: "AMD Radeon HD 5450 Graphics Card"
date: 2010-03-27
forum: Hardware
---

### Post by MasterMIKE on 2010-03-27
For some reason I cannot get this card too work on Ubuntu 9.10. I removed the proprietary driver and installed the open source driver, but I'm not sure what to do from there. Would someone mind helping me out. Kinda annoyed with the 1280x1024 resolution.

Note : I'm using the 64-bit installation

---

### Post by khelben1979 on 2010-03-27
Have you tried Catalyst 10.3 with that graphics card? Get it [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English").

---

### Post by MasterMIKE on 2010-03-27
Not sure if I have lol and thanks. I'll give it a shot and get back to you if its worked. Fingers crossed :)

Edit: Ah it worked and the driver is now installed and working. However there is now another problem. Whenever I try too play a video the screen would flash black before playback begins. Is there a reason for this?

---

### Post by khelben1979 on 2010-03-28
It could be a problem with your video codecs. What application are you using to play videos? And what video format is being used?

---

### Post by MasterMIKE on 2010-03-29
I've tried using Totem movie player Gnome-Mplayer and VLC. I have tried too play xvid AVI's, x264 MKV's and MP4's,

I'm using the codecs that Totem told me too use at promt after clicking search. I'd assume these are the GStreamer ones.

---

### Post by khelben1979 on 2010-03-29
Newer versions of VLC have codecs inbuilt directly in the player and so I'm wondering what version are you using right now?

Mplayer codecs [here]("http://www.mplayerhq.hu/design7/dload.html#binary_codecs") if you're interested. The source archive contains a readme file which explains how it's gonna get installed.

---

### Post by MasterMIKE on 2010-03-29
I'm using VLC version 1.0.2. Thanks for the MPlayer codecs, I'll install those now :)

EDIT: Ok Totem is now not flashing black since I installed the restricted extras, but all other players including VLC and MPlayer still flash black.

---

### Post by khelben1979 on 2010-03-30
Yes, okay! Maybe you need [Medibuntu]("https://help.ubuntu.com/community/Medibuntu")?

Also, in case you would be interested in the source code of VLC, you can access it on [this page]("http://www.videolan.org/vlc/download-sources.html"). I'm not sure it helps, but if you're curious you can try.

Are you able to watch DVDs flicker free over there?

---

### Post by MasterMIKE on 2010-03-31
Right I've installed Medibuntu 64bit codecs and libdvdcss2. I then tried out DVD playback and found that all video players cause flickering 'cept Totem.

I also compiled the latest VLC which for some reason can't even start playback of DVD's. It can however still play normal videos, but it still causes the screen to flicker :(

---

### Post by derrick1985 on 2010-09-04
Hi,

I was wondering if this was still an issue for you?

---

