---
title: "No display output after installing driver"
date: 2020-10-06
forum: Hardware
---

### Post by alessandro-tocci on 2020-10-06
Hi,

I am running Kubuntu Groovy on my desktop and have been for 2 months now.
Some days ago I was trying to use with this computer the docking station  I use with my work laptop, so that I could be able to easily switch  between the work laptop and personal desktop.

I installed the docking station driver (it's a Dell D6000) and upon  rebooting, the screen went black as if it was receiving *no signal at  all*. Shortly afterwards, the message (from the monitor's firmware)  "Input signal out of range. Change settings 10 1440x900 - 60 Hz"  appeared.

I tried installing the proprietary video driver (I have an Nvidia  Geforce 8800 GT) to no avail. I tried uninstalling and reinstalling the  Nouveau-firmware package and the Nvidia driver (nvidia-340), but  nothing.
I tried deleting .local/share/kscreen and all its content, but that didn't help.

When running xrandr I get:
```
 sudo xrandr
Can't open display

```

when manually running startx, if I have the nvidia driver installed I  get to open a desktop session, that has a res of 640x400 and it's  hence unusable and resolution cannot be modified;
if I run startx using Nouveau - which I have happily used since forever -  I don't even get to open a video session and the screen goes pitch  black right away.

Any ideas about how I might get out of this dead end? I'm really stuck at this point...

Thanks a lot for any help.
Ale

---

### Post by TheFu on 2020-10-08
Groovy isn't released. The Development Release sub-forum is for yet to-be-released stuff, yes?
[https://www.omgubuntu.co.uk/2020/05/ubuntu-20-10-release-features](https://www.omgubuntu.co.uk/2020/05/ubuntu-20-10-release-features) says we have to wait a few more weeks.

---

### Post by alessandro-tocci on 2020-10-12
Hi theFu, thanks for your reply.

I'm aware that this is a development version and there's a dedicated sub-forum for that, but when I checked the guidelines it said the purpose of that part is "the development of the upcoming version" where I didn't feel my case belongs. Apologies if I'm wrong, I was feeling more like the "hello, I messed up with my 10-years-old hardware and now I'm stuck" case with an easy solution.
However, the display is now working without any further intervention - will mark this as resolved. Thank you

---

