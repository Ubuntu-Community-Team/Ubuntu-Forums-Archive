---
title: "Poor performance from GTX295"
date: 2009-03-23
forum: Hardware
---

### Post by wolfe on 2009-03-23
Hello, in my new build I have an nvidia gtx295.  I am experiencing slower benchmarks than when I had an 8800gt.  I'm using the beta 185 drivers which gave me a little better performance than with the 180, but things are still extremely slow.  Nvidia-settings detects it and shows both cards, but should I really be getting lower numbers than with my 8800gt?

Here is my xorg.conf, its just the default oversimplified ubuntu version

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by wolfe on 2009-03-23
I edited my device section like this and got even worse fps in glxgears

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option "AllowGLXWithComposite" "true
        Option "RenderAccel" "true"
        Option "Coolbits" "1"
        Option "MultiGPU" "true"
EndSection
```

---

