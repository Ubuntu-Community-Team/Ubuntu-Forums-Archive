---
title: "Lenovo Z575 Resolution Problems"
date: 2012-01-23
forum: Hardware
---

### Post by abramdemski on 2012-01-23
Hi,

I had a previous thread in the installation forum:

[http://ubuntuforums.org/showthread.php?t=1913816](http://ubuntuforums.org/showthread.php?t=1913816)

My current situation is: I have installed ubuntu 10.04 (just a wubi install until I get everything figured out), but the resolution is incorrect. The screen is 1366x768, but the monitor preferences only lists a 1024x768 option. I tried to add 1366x768 using the instructions here:

[https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

This successfully adds to the list of resolutions, but 1366 becomes 1368 (the cvt and gtf utilities don't like the number 1366), and when I try to change to the new resolution in monitor preferences, I get the error "The selected configuration for displays could not be applied: could not set the configuration for CRTC 262".

I found a similar situation here, which went unresolved:

[http://superuser.com/questions/139073/how-to-add-higher-video-resolution-in-ubuntu-10-04-unr-on-eee1101ha](http://superuser.com/questions/139073/how-to-add-higher-video-resolution-in-ubuntu-10-04-unr-on-eee1101ha)

---

### Post by gdea73 on 2012-03-13
yikes that sounds rather annoying... did you ever find a solution? I'm getting this model of laptop in the mail very soon and I'm going to use Ubuntu; provided the screen displays properly :P

Although did you even have Catalyst installed when you were reporting this problem? (see wiki.cchtml.com for the correct method of installing and configuring AMD/ATi drivers).

edit: never mind, I see you were the author of the other (similar) thread. Nevertheless if you're still active on the forums sometime I'd appreciate if we can try to work through this together, when I get my shiny new Z575 in the mail.

edit2: papibe, as soon as I get my laptop and install Ubuntu on it I will jump in and help troubleshoot as well, if abramdemski isn't checking the thread.

---

### Post by papibe on 2012-03-13
Hi abramdemski.

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Since it may be a little log, I'd recommend pasting it here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and posting the link to it.

Regards.

---

