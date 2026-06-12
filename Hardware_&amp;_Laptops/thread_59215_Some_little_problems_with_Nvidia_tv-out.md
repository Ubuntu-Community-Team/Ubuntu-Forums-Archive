---
title: "Some little problems with Nvidia tv-out"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by tpls on 2005-08-23
I'm using Ubuntu 5.04 and I have GF 6600 pci-e videocard. My desktop's resolution is 1280x1024 and tv-out is working in Clone-mode almost good.I can see my desktop in the tv screen, but it's cropped in 1024x768-resolution meanwhile the "real" resolution is 1280x1024. For example fullscreen videos size is 1280x1024 but the tv shows only 1024x768 pixels of them. So, is there any chance to "zoom" tv-out output? And I can't use nvtv, becaus it says that I don't have suitable videocard. Hopefully some undestand a little bit, because my english is not very good. Thanks for help in advance.

And here is a clip from my xorg.conf

```
	Option      "TwinView"
	Option      "SecondMonitorHorizSync" "30-50"
	Option      "SecondMonitorVertRefresh" "60"
	Option      "TVStandard" "PAL-G"
	Option      "TVOutFormat" "COMPOSITE"
	Option      "TwinViewOrientation" "Clone"
	Option      "ConnectedMonitor" "CRT, TV"
	Option      "MetaModes" "1280x1024,1024x768; 1024x768,1024x768; 800x600,800x600; 640x480"
```

---

### Post by tristan on 2005-08-23
Try changing:
Option      "MetaModes" "1280x1024,1024x768; 1024x768,1024x768; 800x600,800x600; 640x480"

To:
Option      "MetaModes" "1280x1024,**1280x1024**; 1024x768,1024x768; 800x600,800x600; 640x480"

---

### Post by tpls on 2005-08-23
I edited xorg.conf just like Tristian said but now tv-out doesn't work at all. There is just a blank screen on the tv. Seems that my tv don't support 1280x1024-resolution.

---

### Post by tristan on 2005-08-23
tpls:

Sorry my suggestion didn't help :(

My monitor only goes up to 1024x768 so I set my metamodes 
Option      "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480"
With these I can get a picture on the TV in all modes.


The whole idea of TV out is that it should convert whatever screenmode to something your TV can use (eg 768x576 PAL). It's not trying to send your TV 1280x1024. I think maybe it can't convert 1280x1024 to a TV mode properly. If you hit ctrl-alt-+ to change screen modes, do you see a picture on the TV then?

Sorry again, I'm not an expert at all. Perhaps someone else can help tpls?

---

### Post by tpls on 2005-08-23
[QUOTE=tristan]tpls:

Sorry my suggestion didn't help :(
[/quote]
Iit's ok
> 

My monitor only goes up to 1024x768 so I set my metamodes 
Option      "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480"
With these I can get a picture on the TV in all modes.


The whole idea of TV out is that it should convert whatever screenmode to something your TV can use (eg 768x576 PAL). It's not trying to send your TV 1280x1024. I think maybe it can't convert 1280x1024 to a TV mode properly. If you hit ctrl-alt-+ to change screen modes, do you see a picture on the TV then?

Sorry again, I'm not an expert at all. Perhaps someone else can help tpls?

When I change the the resolution to the 1024x768, the desktop shows on the tv screen and fits perfectly on it. Seems that this is the only way to do it. Btw. I have Acer 19" tft and its optimal resolution is 1280x1024.

---

