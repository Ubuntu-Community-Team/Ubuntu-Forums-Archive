---
title: "Unable to use properly two external monitors on Dell lnspiron laptop running 15.04"
date: 2015-04-26
forum: Hardware
---

### Post by gorg3 on 2015-04-26
Hi, 

I have a Dell 5110 laptop with Ubuntu 15.04 installed which has two video cards: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller and NVIDIA Corporation GF108M [GeForce GT 525M]. I have installed NVIDIA's 346.59 proprietary driver. My goal is to use two external monitors which are 24 (via HDMI) and 17 (via VGA) inches. The problem is that the NVIDIA X Server  Settings can only detect the 24 inches monitor (connected via HDMI) but is not able to detect the other one (and the built in monitor as well). In addition from System Settings --> Displays I can see that my Ubuntu system detects both of them. When I use each of them separately (not having the other one connected) everything works fine. However, when I try to use both of them simultaneously several problems occur such as messages like "The selected configuration for displays could not be applied" or bad resolution etc. Do you have any suggestions on how to make NVIDIA X Server Settings detect both of them in the first place and make the whole setup with my two external monitors function properly? Thanks in advance.

---

### Post by TheFu on 2015-04-27
I'm guessing here - don't know if this will work.

Can you disable the intel GPU someway - perhaps unload the kernel module or blacklist the driver?  If so, then the nvidia GPU might drive both outputs?
**lsmod |grep vid** might show the driver.
```
lsmod |grep vid
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  4 uvcvideo,gspca_main,videobuf2_core,gspca_zc3xx
video                  18903  1 i915

```
So, on my machine, it would be the **i915** driver to blacklist. Thinking about this more, I don't think it will let me rmmod it on a running system. My example doesn't show 2 GPUs, sorry. This machine only has 1 and none of the other machines here currently booted have 2 GPUs.
[B]
Be extremely careful doing this.[/B]  Make certain you have **openssh-server** setup and working so you can get in over a network connection and de-blacklist the module first if there isn't any screen displayed.  It could be bad - really bad.  Alternatively be very comfortable booting off a liveCD, mounting the partition with /etc/ and removing the blacklisted line that way. Either method will work - it would be best to have preparations for this BEFORE it is needed.  If you don't - you could end up with a laptop that doesn't show a display at all again.

---

