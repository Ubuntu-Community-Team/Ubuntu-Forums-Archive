---
title: "Questions about nvidia and i2c_nvidia_drm"
date: 2024-07-23
forum: Hardware
---

### Post by kingpenguin on 2024-07-23
I am using Ubuntu 24.04 with the kernel 6.8.0-38-generic. After installing the nvidia driver 535 I am seeing two issues. 
[LIST=1]
[*][drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00002700] Failed to grab modeset ownership
[*]UBSAN: array-index-out-of-bounds in build/nvidia/535.183.01/build/nvidia-uvm/uvm_mmu.c:569:17
[/LIST]

I am almost positive that #2 is a known ongoing bug talked about here [https://forums.developer.nvidia.com/t/ubsan-array-index-out-of-bounds-complaints-in-newer-kernels/271705](https://forums.developer.nvidia.com/t/ubsan-array-index-out-of-bounds-complaints-in-newer-kernels/271705) and will be fixed in later versions of the driver. Also someone from nvidia has already commented on that saying it is a harmless issue and the code related was here [https://github.com/NVIDIA/open-gpu-kernel-modules/blob/main/kernel-open/nvidia-uvm/uvm_pmm_gpu.c#L224](https://github.com/NVIDIA/open-gpu-kernel-modules/blob/main/kernel-open/nvidia-uvm/uvm_pmm_gpu.c#L224). 

The 1st issue is more what I had questions on. I found here [https://answers.launchpad.net/ubuntu/+question/706349](https://answers.launchpad.net/ubuntu/+question/706349) that you should be able to do the following below.
```
[COLOR=#000000][FONT=&quot]echo "blacklist i2c_nvidia_gpu" > /etc/modprobe.[/FONT][/COLOR][COLOR=#000000][FONT=&quot]d/blacklist_[/FONT][/COLOR][COLOR=#000000][FONT=&quot]i2c-nvidia-[/FONT][/COLOR][COLOR=#000000][FONT=&quot]gpu.conf && [/FONT][/COLOR][COLOR=#000000][FONT=&quot]sudo update-initramfs -u[/FONT][/COLOR]
```

I was reading here [https://www.kernel.org/doc/html/latest/i2c/busses/i2c-nvidia-gpu.html](https://www.kernel.org/doc/html/latest/i2c/busses/i2c-nvidia-gpu.html) that is has to do with Type-c, but I was a little unsure if that means usb type c or something else. I do not see any usb c ports on my 4070TI, so if it is I assume it is safe to blacklist. My major question is does anyone see an issue doing this on an ubuntu 24.04 desktop machine that the only real things I do is wine gaming and browsing the web?

Thank you in advance for everything! I really hope I posted this in the right location.

---

### Post by #&amp;thj^% on 2024-07-23
Have you tried with adding a kernel parameter "fbdev=1 " In "/etc/default/grub" first.

---

### Post by kingpenguin on 2024-07-23
No I have not. Can you explain a bit more about what this will do and how you are expecting it to solve the issue? I am not looking for any guarantees but just trying to understand what this is really doing.
The only thing that I am pretty sure of is that is for frame buffer support. I thought most applications just use the x11 or wayland protocols to do this. Also I was under the understanding that fb is more for terminal output not the gui ( I might be completely wrong here )

---

### Post by #&amp;thj^% on 2024-07-23
modesetting of course, Straight from nVidia:
> The issue here is that any application opening one of the /dev/dri/card* device files automatically attempts to get DRI &#8220;master&#8221; permission. In the NVIDIA driver model, that tries to get &#8220;modeset ownership&#8221; on the corresponding GPU. If another driver component already has modeset ownership, then getting &#8220;master&#8221; fails and prints this message.

This happens even if the application doesn&#8217;t want or need DRI master.
Their suggestion is:
> You can avoid the problem by loading nvidia-drm with the[COLOR="#FF0000"] fbdev=1[/COLOR] parameter. But like I mentioned in my earlier reply, this message is usually harmless and expected. You can just ignore it if you&#8217;re not having any functional problems regarding applications using DRM just for rendering.
I'm told that the newer drivers have a fix already:
```
 nvidia-smi|grep NVIDIA
| NVIDIA-SMI 555.52.04              Driver Version: 555.52.04      CUDA Version: 12.5     |
|   0  NVIDIA GeForce RTX 3050 ...    Off |   00000000:01:00.0 Off |                  N/A |

```
```
sudo dmesg|grep NVIDIA 
[   11.140505] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  555.52.04  Tue Jun  4 13:54:58 UTC 2024
[   11.156093] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  555.52.04  Tue Jun  4 13:21:08 UTC 2024

```]

---

### Post by kingpenguin on 2024-07-23
That would be amazing. If that is the case I might just wait for that, I am not really experiencing an issue per say but just wanted to start cleaning up the errors in the logs.

---

### Post by #&amp;thj^% on 2024-07-23
Sounds like a wise choice.

---

### Post by kingpenguin on 2024-07-23
Now that I am off work it does seem that there is a nvidia-driver-555 in apt. Is this something that you would say is stable for gaming use?

---

### Post by #&amp;thj^% on 2024-07-23
> **kingpenguin said:**
> Now that I am off work it does seem that there is a nvidia-driver-555 in apt. Is this something that you would say is stable for gaming use?

Are you running the "ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/" as a source?

I'm not much of gamer so nothing helpful there. But I do now find it stable as always "YMMV" :)
Note my installed Driver:
```
apt policy nvidia-driver-555 nvidia-dkms-555
nvidia-driver-555:
  Installed: 555.52.04-0ubuntu0~gpu24.10.1
  Candidate: 555.52.04-0ubuntu0~gpu24.10.1
  Version table:
 *** 555.52.04-0ubuntu0~gpu24.10.1 500
       [COLOR="#FF0000"] 500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu oracular/main amd64 Packages[/COLOR]
        100 /var/lib/dpkg/status
nvidia-dkms-555:
  Installed: 555.52.04-0ubuntu0~gpu24.10.1
  Candidate: 555.52.04-0ubuntu0~gpu24.10.1
  Version table:
 *** 555.52.04-0ubuntu0~gpu24.10.1 500
        [COLOR="#FF0000"]500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu oracular/main amd64 Packages[/COLOR]-Driver
        100 /var/lib/dpkg/status

```

I just spent a couple of days helping someone fix their install using Ubuntu-Drivers.
I don't use it, I just prefer cli.
Please remove and purge the old driver before installing the new driver.

---

