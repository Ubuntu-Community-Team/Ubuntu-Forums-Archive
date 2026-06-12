---
title: "NVidia Compent out to CRT TV"
date: 2016-11-27
forum: Hardware
---

### Post by nekurashikaku on 2016-11-27
Hello all,

Any help would be greatly appreciated. Been trying for a while to get this up and running. My LED TV died on me a while back so hauled out an old Sony CRT ([KV-36FS13]("https://www.cnet.com/products/sony-wega-kv-36fs13/specs/")) to at least have some video playback available in the room that wasn't DVD. The Video Card is an NVidia Quadro FX 580.


xrandr output:
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192DVI-I-1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)

```

Currently no Xorg.conf in /etc/X11 and am running the opensource video drivers for NVidia instead of the proprietary.

[https://lh3.googleusercontent.com/9ZLZNCBF3SeRmo4bKI1qGZQhdZcKjr3sICS0TZ9Wfn1zgeghI2eb2P0UoQztlBIkzDA598R09J0hz4qNGRwAYf8dkDzKCpwJPTQAnYX9g0JqyClAovC8QHNkAzK5zX8BpBVBvoC_t17AYfNUFC1uqrgHiC_GacVMnUWGw0tgyr5qS8w9LaqfLH4CDymhwE9ZbblMtX9BTNxLDivsQrVa7EIdYxUjkcZzz4FBfWwJx-wkEknOohIkqHj5AfAi9r_nG3lSSdAwzuu8g8IeaRRZnpsYRsloNL1MDdeL7Ivu_yyZXLggoY6yh692Vr6N_ncmqfMtUdd7fjJRypwTyGDwEEGCAM3QiLD_lmVkGJfdfX1FWrKSHNghQdYPRWCNx_ROjteVa3V5r_EqxhqMSf2rqRVFYNVEe2CsHWweJ_GrxUITbZNXhIsCvI95qbxGTdVyZBD_KhK1Eg-7aNAMzWbZ1mUlCKTGDHkYEAo2Vl5CRyKOzh9V2vjY7_d3LBBaQCVqaneZPr1Hj_sLPiuTkLmQshfjJXjJtiVLbMaLyFCq4K62YNOHzroJNQljq0T3uuDxuymHW4PmSUEyVHqP4nH6BN_T-sdmbZFwNM2P7x2XRikzvv-7=w501-h890-no](https://lh3.googleusercontent.com/9ZLZNCBF3SeRmo4bKI1qGZQhdZcKjr3sICS0TZ9Wfn1zgeghI2eb2P0UoQztlBIkzDA598R09J0hz4qNGRwAYf8dkDzKCpwJPTQAnYX9g0JqyClAovC8QHNkAzK5zX8BpBVBvoC_t17AYfNUFC1uqrgHiC_GacVMnUWGw0tgyr5qS8w9LaqfLH4CDymhwE9ZbblMtX9BTNxLDivsQrVa7EIdYxUjkcZzz4FBfWwJx-wkEknOohIkqHj5AfAi9r_nG3lSSdAwzuu8g8IeaRRZnpsYRsloNL1MDdeL7Ivu_yyZXLggoY6yh692Vr6N_ncmqfMtUdd7fjJRypwTyGDwEEGCAM3QiLD_lmVkGJfdfX1FWrKSHNghQdYPRWCNx_ROjteVa3V5r_EqxhqMSf2rqRVFYNVEe2CsHWweJ_GrxUITbZNXhIsCvI95qbxGTdVyZBD_KhK1Eg-7aNAMzWbZ1mUlCKTGDHkYEAo2Vl5CRyKOzh9V2vjY7_d3LBBaQCVqaneZPr1Hj_sLPiuTkLmQshfjJXjJtiVLbMaLyFCq4K62YNOHzroJNQljq0T3uuDxuymHW4PmSUEyVHqP4nH6BN_T-sdmbZFwNM2P7x2XRikzvv-7=w501-h890-no)

---

