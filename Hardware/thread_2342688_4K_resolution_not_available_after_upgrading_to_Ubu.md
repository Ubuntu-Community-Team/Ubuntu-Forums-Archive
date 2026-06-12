---
title: "4K resolution not available after upgrading to Ubuntu 16.10"
date: 2016-11-09
forum: Hardware
---

### Post by hfujita on 2016-11-09
Hello, I'm using Intel NUC 5i5RYH with Ubuntu Linux, with the Dell P2415Q  monitor. I recently upgraded Ubuntu from 16.04 to 16.10. After upgrade I  can no longer select full 4K resolution (3840x2160). X.org recognizes  up to full HD (1920x1080). If I boot with a kernel that came with 16.04  (linux-image-4.4.0-45-generic), full 4K resolution simply works. Ubuntu  16.10 comes with kernel 4.8 (linux-image-4.8.0-26-generic).

Any  idea on approaching this issue? I'm using HDMI connection to connect  NUC to the monitor. Connection is like this: NUC<->MiniDP-HDMI  adapter<->HDMI cable<->P2415Q

By using xrandr to force resolution settings ([https://wiki.archlinux.org/index.php/Xrandr#Adding_undetected_resolutions]("https://communities.intel.com/external-link.jspa?url=https%3A%2F%2Fwiki.archlinux.org%2Findex.php%2FXrandr%23Adding_undetected_resolutions")  ), I was able to obtain 4k resolution in the 4.8 kernel, but some  flicker on the screen occurred, which was not there in the 4.4 kernel.  Also that settings is temporary; logging out from the session brings me  back to the full-HD login screen. So still some help needed here.


Any suggestion or clarification on my environment is appreciated. Xorg.0.log is attached. Thank you!

(note: this is actually a repost of [https://communities.intel.com/thread/107666](https://communities.intel.com/thread/107666). It was suggested that this forum could be a better place to ask this question.)

---

### Post by mastablasta on 2016-11-10
you could try with newer GPU drivers (x-org edgers or oibaf PPA). 

but before you do, does 16.10 work as it should in live session? if it does, then perhaps something was left over from previous release that is interfering with new system (some configuraiton or something). if oyu have time oyu can also try another distro with kernel 4.8 to see if it is a kernel or Ubuntu issue.

another option 16.04 LTS is supported until 2021 - you can stay on it and if you need any new versions of programs there will probably be PPA's for them.

---

