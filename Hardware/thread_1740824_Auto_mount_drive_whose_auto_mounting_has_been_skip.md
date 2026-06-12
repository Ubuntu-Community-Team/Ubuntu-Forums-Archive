---
title: "Auto mount drive whose auto mounting has been skipped"
date: 2011-04-27
forum: Hardware
---

### Post by aepsil0n on 2011-04-27
Hey all,

I have a technical question about the following little problem: as many users may do I use an USB hard drive in Ubuntu 10.10. I have configured it within /etc/fstab to auto mount while my system boots. So far, no problem.

Now, when my drive is off it won't mount on start-up but the mounting process is skipped &#8211; either automatically or by pressing S when prompted to do so. In this case *is it possible to configure it, so that it will mount automatically when I switch it on after booting without root access?*

As of now this fails due to the missing root access. I can do it manually, of course, but on the long term this is somewhat nasty.

It does boot automatically when it is not in /etc/fstab. So I figure this has something to do with access rights of whatsoever but I'm not sure what I would have to do. Can anyone give me a hint on that?

---

### Post by dabl on 2011-04-27
The whole "value proposition" behind the USB system is "hot pluggable".  USB devices are not presumed to be connected at boot time, and may appear on any of the USB connectors on the platform, at any time, and may be removed independently of system shutdown.  For these reasons, the only use case where mounting a USB hard drive at boot, via /etc/fstab makes sense (at least to me), is when it is intended to be a "permanent" fixture on the system, i.e. when you never intend to unplug it and use it elsewhere.

So, if you will plug it in when you need it, leave it connected as long as you wish, and USING "SAFELY REMOVE", you can disconnect it whenever you wish.  Just skip the /etc/fstab editing.

---

