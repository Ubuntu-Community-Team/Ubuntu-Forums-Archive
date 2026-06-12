---
title: "How does Ubuntu make video drivers work?"
date: 2009-05-18
forum: Hardware
---

### Post by JackH79 on 2009-05-18
Hi there.

After having fiddled around with some others distros alongside Jaunty I realised something curious:
My graphics card (friggin ATI Radeon HD 2300, which is not supported by ATI's own drivers) works fine under 9.04 out-of-the-box. I can watch full screen videos without stuttering (well, as long as they are not HD) and can run compiz with all effects, no drama. "Real" 3d stuff doesn't work but is not really needed. My xorg.conf file looks like this:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Now my question:
This doesn't work in any of the other distros I've tried so far. I always had to fiddle around with radeon/radeonhd drivers and the xorg.conf to get my machine working. So, what is the difference in Ubuntu? I'm suspecting some kernel configuration.
Does anybody know? Or does anybody know where I could find out more?

Any help or pointing in the right direction would be much appreciated. Thanks.

---

