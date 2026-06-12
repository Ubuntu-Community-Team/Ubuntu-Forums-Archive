---
title: "module problem with nvidia driver"
date: 2021-01-14
forum: Hardware
---

### Post by townhill on 2021-01-14
I'm using Ubuntu 20.10 and am having a problem with the driver for my nvidia 1050 TI GPU.  I have been using the nvidia 450 driver for some time now without a problem but recently Blender started reporting that there is no GPU available.  Checking  'additional drivers' shows the 450 driver installed but:

running** nvidia-smi** in the terminal gives me

 ```
[FONT=monospace][COLOR=#000000]NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver i[/COLOR]
s installed and running
[/FONT]
```

and running **dkms status **gives me 

```
[FONT=monospace][COLOR=#000000] nvidia, 450.102.04, 5.8.0-36-generic, x86_64: installed (WARNING! Diff between built and installed module!) (WARNING! D[/COLOR]
iff between built and installed module!) (WARNING! Diff between built and installed module!)
[/FONT]
```

I think I need to clean up the module problem but I'm not sure how to do this.  Can someone give me advice on how to fix this?

---

### Post by townhill on 2021-01-14
Today's update seems to have fixed the problem, nvidia-smi now shows the gpu although dkms status still reports built/installed module conflict.

---

