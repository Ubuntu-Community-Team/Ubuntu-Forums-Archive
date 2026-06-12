---
title: "Problem with Intel integrated graphics after upgrade to 16.04 (blank screen)"
date: 2016-04-27
forum: Hardware
---

### Post by Kari_Salmela on 2016-04-27
Hello all,

I upgraded one desktop pc system to 16.04 and after first reboot screen went totally blank (permanently) at the point where KMS does the mode setting for higher resolution vga, and the system booted otherwise normally. I was able to remotely change boot parameters to "nomodeset" and after that I did get video, but obviously all the hardware acceleration features of Intel graphics were gone (and I need them). Without nomodeset it will stay blank no matter what I tried. Tv display is connected with motherboard HDMI (1920x1080) if that's of interest here.

Some specs:

CPU: model name      : Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz stepping        : 9
kernel: vmlinuz-4.4.0-21-generic (x86_64)
Motherboard: Asus P8Z77 
X.Org X Server 1.18.3
xserver-xorg-video-intel                             2:2.99.917+git20160325-1ubuntu1


In Xorg.0.log there are errors stating /dev/dri/card0 is not found, so I figure the problem lies with that kernel driver initialization module is unsuccessful (even though lsmod shows that i915 driver is loaded) and therefore there are no suitable devices for Xorg server to write to for mode setting etc.

If I boot with kernel 4.2.0-35-generic, the drivers work just fine without nomodeset. 

Has anyone seen something like this? Do you have any ideas how to make this work? I noticed that some people are seeing similar symptoms with Core i5 3470K and kernel 4.4 but I cannot say if those were otherwise related to this.

I'd rather not have custom kernel and/or proprietary display driver installed for simplicity, but that's not out of the question if nothing else works. 

Best regards,

Kari

---

### Post by roler2 on 2016-04-27
[COLOR=#000000]"even though lsmod shows that i915 driver is loaded"[/COLOR]

Please read all the posts applicable to the i915 Driver and 16.04 and the Kernel upgrades. There are several. Even those who are experiencing tearing, poor Graphics, poor Font Rendering, etc. it is all more than likely the same basic issue. Until the Kernel issue is fixed, if it ever will be, there will continue to be Graphics problems, especially with the Intel Bay Trail Drivers,, such as the i915.

If your need is immediate, reinstall basic 14.04 with the default 3.13 Kernel, not the Kernel upgrades, such as with 14.04.2 and subsequent. At this moment, it is the only Kernel that will work effectively (and does quite well) with the i915.

---

### Post by QLee on 2016-04-28
> **Kari_Salmela said:**
> Hello all,

I upgraded one desktop pc system to 16.04 and after first reboot screen went totally blank (permanently) at the point where KMS does the mode setting for higher resolution vga, and the system booted otherwise normally. I was able to remotely change boot parameters to "nomodeset" and after that I did get video, but obviously all the hardware acceleration features of Intel graphics were gone (and I need them). Without nomodeset it will stay blank no matter what I tried. Tv display is connected with motherboard HDMI (1920x1080) if that's of interest here.

Some specs:

CPU: model name      : Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz stepping        : 9
kernel: vmlinuz-4.4.0-21-generic (x86_64)
Motherboard: Asus P8Z77 
X.Org X Server 1.18.3
xserver-xorg-video-intel                             2:2.99.917+git20160325-1ubuntu1



Has anyone seen something like this? Do you have any ideas how to make this work? I noticed that some people are seeing similar symptoms with Core i5 3470K and kernel 4.4 but I cannot say if those were otherwise related to this.

Kari

Kari, can you mention where you saw that about Core i5 3470K and kernel 4.4, I can't find it?

You do not have a "Bay Trail" processor.

The i915 driver is not a "Bay Trail" driver, it is the opensource driver for Intel video.

Don't be confused about that.

The i915 driver needs KMS, so no wonder you're not satisfied with the "nomodeset" parameter.

I have an installation of 16.04 running the i915 driver.

 You show X.Org X Server 1.18.3 do you mean that to represent xserver-xorg?

On my system:
```
QLee@Atlas-Ubu16:~$ apt-cache policy xserver-xorg
xserver-xorg:
  Installed: 1:7.7+13ubuntu3
  Candidate: 1:7.7+13ubuntu3
  Version table:
 *** 1:7.7+13ubuntu3 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
```

Are you sure the upgrade finished correctly, at this early stage of the release cycle sometimes the upgrade path for some things doesn't work correctly yet. Maybe you could boot to recovery mode and make sure everything is upgraded and your package manager is not showing errors.

---

### Post by roler2 on 2016-04-28
Current i915 driver is [COLOR=#333333][FONT=Ubuntu]2:2.99.917+git20151015.6861391f-0ubuntu0sarvatt.

Another very good Forum Member posted a temporary fix which will at least get a Desktop. The i915 has to be installed manually within Recovery Mode. It still does not work very well with the 16.04 Kernel. OS Updating issues, some freezes, etc. With the temporary fix in place, the OS can be utilized as a secondary OS, but not as a primary. If Lubuntu would incorporate the Default 3.13 Series Kernel until a permanent fix is released, then everything would work very well.[/FONT][/COLOR]

---

