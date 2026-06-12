---
title: "fglrx graphic driver problem"
date: 2016-07-30
forum: Hardware
---

### Post by rob141 on 2016-07-30
Hello everyone, i have had Ubuntu 15.10 for a while even when 16.04 was out, i did not update at first.

I have decide to go for it today and now everything seem to be working but 

- my ati fglrx driver does not work ok. i do have images ok but its not the ati drivers because i cant even watch a video or anything.

- my HDMI audio does not work either. I have no sound at all

maybe this may help you help me:

 lspci -nn | grep HDMI
02:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series] [1002:aa60]
 lspci -nn | grep VGA
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M] [1002:68c1]

thank you very much in advance

---

### Post by Yellow Pasque on 2016-07-30
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/#fglrx)

Make sure everything from fglrx is purged (including any custom /etc/X11/xorg.conf file). The open source radeon driver should work well. Installing mesa-vdpau-drivers and mesa-va-drivers should help with video. If you're still having problems after doing that, post your /var/log/Xorg.0.log  (use [ code ] [ /code ] tags).

---

### Post by rob141 on 2016-08-01
Thank you very much Temujin, its working now. 

Audio and video is perfect.

Thanks again ;)

---

