---
title: "Twin view error"
date: 2010-11-19
forum: Hardware
---

### Post by Sempfinger on 2010-11-19
Hello Everyone,

I run Ubuntu 10.04 with up to date package of nvidia-current (i.e. nvidia-glx-185, the proprietary driver). I have a dell vostro 1400 with a NVidia 8400 GM graphics card. The display resolution is 1280x800. Additionally, I have a Samsung SyncMaster 940 BF external 19" Monitor with 1280x1024 resolution connected via VGA.

At the moment, I use the samsung as an external monitor. Today I wanted to try out TwinView in the System -> Administration -> NVIDIA X Server Settings

I selected TwinView and pressed apply. A notification window pops up and tells me to save to x config file and restart x server. When I press "Apply what is possible", I get the following error message:

```
Failed to set MetaMode (1) 'CRT-0: nvidia-auto-select @1280x1024 +1280+0, DFP-0: nvidia-auto-select @1280x800 +0+0' (Mode 2560x1024, id: 50) on X screen 0
```

It seems that nvidia-auto-select cannot set a "common" resolution for both? Truth is: I have no Idea.

Any hints or advice?

Thanks in advance

Edit: obviously 'save to x config file and restart x server' as in 'save to x config file and restart x server' did it.

---

