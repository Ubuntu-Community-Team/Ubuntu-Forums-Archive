---
title: "Skype sound settings for Inspiron &amp; Intrepid"
date: 2008-12-20
forum: Hardware
---

### Post by paragkalra on 2008-12-20
I am using Intrepid on Inspiron 1525. Sound on system is working and also microphones are working. I am being able to capture and play the sound using "Sound Recorder"

Also I came across this post:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

While attempting to un-install pulse audio I was greeted with following message:
> 
The following packages will be REMOVED:
  linux-headers-2.6.27-7{u} linux-headers-2.6.27-7-generic{u} pulseaudio 
0 packages upgraded, 0 newly installed, 3 to remove and 24 not upgraded.
Need to get 0B of archives. After unpacking 53.3MB will be freed.

I don't want to do so as my VMware server depends on "linux-headers"

Any other solution or does someone know skype sound settings for Inspiron 1525 n Series

---

### Post by hardyn on 2008-12-20
start skype and change the sound settings to pulse, not oss or alsa; you will not have to remove anything.

Although with 8.10 starting the camera causes skype to crash; i have not figured that out yet, but i have not given it much time either.

---

### Post by paragkalra on 2008-12-20
I first connected the microphone, then I changed "Sound In", "Sound Out" & "Ringing" to "pulse", applied the settings and tried making a test call but no success. It displays the same: "Problem with Audio Playback"

Did I miss something? :confused:

---

### Post by hardyn on 2008-12-20
? that is all i had to do.

vmware im sure can be reconfigured for ALSA; so removing pulse might not be the end of the world.

---

### Post by paragkalra on 2008-12-27
Today I found that my skype test call (echo123) is working. I can hear everything very clearly but recording being done is of very low intensity. I have to speak really loud to hear back my voice in the skype test call.

I think the problem is due to capture level.

As u can see in the attached screenshot "capture" level becomes low moment skype test call starts. And moment skype terminates it shoots up to the highest level. Could this be an issue ?

---

