---
title: "Hardware Acceleration Intel HD2000"
date: 2022-07-03
forum: Hardware
---

### Post by allen2 on 2022-07-03
I have an old Core 2 Duo laptop that runs Intel HD 2000 graphics.  It can play youtube videos in Windows 10 and Chrome OS Flex (which gives me hope for Ubuntu).  It seems that hardware acceleration is not enabled / supported in Ubuntu by default in either Google Chrome or Firefox.  Hardware acceleration is enabled in their preference settings.  Is there a way to get hardware acceleration working with HD 2000 graphics in Ubuntu?

---

### Post by Yellow Pasque on 2022-07-03
What does this command return?
```
vainfo
```

---

### Post by mikewhatever on 2022-07-03
I wouldn't expect a lot of hardware decoding from an HD2000 (2011). It is old and won't get any newer.
Youtube uses a lot of AV1 and VP9, and both codecs were introduced after 2011. HD2000 can probably decode AVC aka H.264.
Hardware decoding of AV1 by Intel started with Xe Graphics quite recently, so..., adjust your expectations accordingly.

---

### Post by Yellow Pasque on 2022-07-04
> **mikewhatever said:**
> Youtube uses a lot of VC1 and VP9, and both codecs were introduced after 2011.

I think you mean AV1. VC1 is much older ([https://en.wikipedia.org/wiki/VC-1](https://en.wikipedia.org/wiki/VC-1))

> HD2000 can probably decode AVC aka H.264.

If it can, then h264ify might be a solution: [https://addons.mozilla.org/en-US/firefox/addon/h264ify/](https://addons.mozilla.org/en-US/firefox/addon/h264ify/)

---

### Post by mikewhatever on 2022-07-04
> **Yellow Pasque said:**
> I think you mean AV1. VC1 is much older ([https://en.wikipedia.org/wiki/VC-1](https://en.wikipedia.org/wiki/VC-1))



If it can, then h264ify might be a solution: [https://addons.mozilla.org/en-US/firefox/addon/h264ify/](https://addons.mozilla.org/en-US/firefox/addon/h264ify/)

Yes, thank you, AV1 it is. Also, h264ity has not been updated since 2019, and it did not seem to do anything when tested.

---

### Post by Yellow Pasque on 2022-07-04
> **mikewhatever said:**
> Yes, thank you, AV1 it is. Also, h264ity has not been updated since 2019, and it did not seem to do anything when tested.

:\ How did you test it? Can you give the vainfo?
```
vainfo
```

---

### Post by mikewhatever on 2022-07-04
Installed it, restarted FF, looked at "Stats for nurds" on youtube. It was always AV1.
> ~$ vainfo
libva info: VA-API version 1.7.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/r600_drv_video.so
libva info: Found init function __vaDriverInit_1_7
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.7 (libva 2.6.0)
vainfo: Driver version: Mesa Gallium driver 21.2.6 for AMD RS880 (DRM 2.50.0 / 5.13.0-52-generic, LLVM 12.0.0)
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileNone                   :	VAEntrypointVideoProc


The hardware is about as old as the OP's - Radeon HD 4225/4250.

---

### Post by Yellow Pasque on 2022-07-04
I see. That's a good test system.
Have you tried toggling "media.av1.enabled" in FF's about:config?

---

### Post by mikewhatever on 2022-07-04
No, I have not, and that actually did something interesting - VP9.  I've then also toggled "media.ffvpx.enabled", and now it is AVC1, but the CPU is still at 50%, which doesn't look like accelerated decoding.

---

### Post by Yellow Pasque on 2022-07-04
You may have to try a couple more hacks: [https://ubuntuhandbook.org/index.php/2021/08/enable-hardware-video-acceleration-va-api-for-firefox-in-ubuntu-20-04-18-04-higher/](https://ubuntuhandbook.org/index.php/2021/08/enable-hardware-video-acceleration-va-api-for-firefox-in-ubuntu-20-04-18-04-higher/)

---

### Post by mikewhatever on 2022-07-05
Yes, I've seen that before, but accelerated playback doesn't work with Radeon HD 4225/4250. Not sure why, ...could be too old.
That said, I've successfully tested it on another machine with Intel's HD2000. Had to do the following:
 > - install the h264ing extention
 - media.ffmpeg.vaapi.enabled    true
 - media.av1.enabled    false
 - media.ffvpx.enabled    false

There was no need for anything else.

---

### Post by mIk3_08 on 2022-07-08
> **allen2 said:**
> I have an old Core 2 Duo laptop that runs Intel HD 2000 graphics.  It can play youtube videos in Windows 10 and Chrome OS Flex (which gives me hope for Ubuntu).  It seems that hardware acceleration is not enabled / supported in Ubuntu by default in either Google Chrome or Firefox.  Hardware acceleration is enabled in their preference settings.  Is there a way to get hardware acceleration working with HD 2000 graphics in Ubuntu?
Please run the script below and post the information or pastebin link in this thread. Regards and cheers.
```
https://github.com/UbuntuForums/system-info
```

---

