---
title: "Projector and Laptop monitor with xrandr"
date: 2010-02-05
forum: Hardware
---

### Post by bo01 on 2010-02-05
Hi,
I have Debian stable on a laptop and all I want to do is to have a clone on a projector. I have succeeded to do this on any other CRT monitor, but I can't do this with the projector. 

The output of the xrandr -q gives the VGA1 connected. So, its not hardware's problem.

Any ideas?

Thx in advance!

---

### Post by chewearn on 2010-02-05
What exactly does "xrandr -q" say?

I suspect it's actually is a hardware problem.  Projectors are notorious for giving wrong EDID info or no info at all.  Sometimes, there is a VGA hardware switch in between the laptop and projector that is causing trouble.

---

### Post by bo01 on 2010-02-05
The xrandr -q say that the VGA1 device is connected. I cannot post the exact output, because the projector is in work. 

But I don't think its a hardware issue, because in windows the projector works fine.

---

### Post by chewearn on 2010-02-06
> **bo01 said:**
> The xrandr -q say that the VGA1 device is connected. I cannot post the exact output, because the projector is in work. 

I am sure "xrandr -q" says more than that; for instance, it should also say what resolutions are supported.  That would help for the next command, e.g. "xrandr --output VGA1 --mode 1024x768"

> But I don't think its a hardware issue, because in windows the projector works fine.

Unfortunately, Xorg is more fussy about auto-detection.  Windows usually do a better job handling unusual situation.  That my personal experience/opinion.

---

### Post by bo01 on 2010-02-06
Yes, it gives the resolution supported and then I run the command with the --mode argument, but nothing happens. And no error message too.

Anything else??? :(

---

### Post by chewearn on 2010-02-06
What graphics hardware do you have?

I re-read your first post, you mentioned you have Debian stable?  I'm not sure if my experience with Ubuntu will fully apply.

EDIT:
Instead of xrandr on-the-fly configuration, you might have to revert back to manual xorg.conf editing for this to work.

---

### Post by bo01 on 2010-02-06
I have an Nvidia one. The configuration file are almost the same between Debian-Ubuntu. I don't know what to add in the xorg.conf.

The strange thing is that, as I mentioned, with any other CRT monitor the xrandr work fine.

---

### Post by chewearn on 2010-02-06
Are you running proprietary nvidia driver, or open source "nv"?  If it's proprietary, the proper way to set this up is using nvidia-settings.

```
nvidia-settings
```

Or (if you need to write to xorg.conf)
```
gksudo nvidia-settings
```

---

