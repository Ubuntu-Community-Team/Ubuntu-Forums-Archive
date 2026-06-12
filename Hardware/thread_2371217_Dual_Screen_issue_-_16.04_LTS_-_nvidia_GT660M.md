---
title: "Dual Screen issue - 16.04 LTS - nvidia GT660M"
date: 2017-09-12
forum: Hardware
---

### Post by nebu-06 on 2017-09-12
Hello,

I am experiencing an issue with the dual screen feature on Unbuntu 16.04 LTS install on an iMAC late 2012 equipped with an Nvidia GT660m. My second display is properly detected but when I am trying to enable it, I get the error "Could not set the configuration for CRTC 635" followed by the message "GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gsd_2drr_2derror_2dquark.Code2: could not set the configuration for CRTC 635" as you can see in the screeshots below. But the catch is that this configuration works if I reboot, and the activation also works randomly from the same display settings. But as this screen is switched by a KVM, and that each time I switch this screen on the other computer, Ubuntu considers the screen as detached, when I switch again the screen on Ubuntu, most of the time I get this error.






[ATTACH=CONFIG]276700[/ATTACH]
[ATTACH=CONFIG]276701[/ATTACH]

I tried updating the driver. As far as I can tell from the "Additional drivers" settings, I have the latest nvidia driver from the "graphics-drivers" ppa.

[IMG]https://drive.google.com/file/d/0BxcfWsB0TgiEbGpyYlhNTmZOZ00/view?usp=sharing[/IMG]

[ATTACH=CONFIG]276702[/ATTACH]

But I am not sure that I am actually using the latest driver...

```
$ dpkg --get-selections | grep nvidia
nvidia-381                    deinstall
nvidia-384                    install
nvidia-opencl-icd-381                deinstall
nvidia-opencl-icd-384                install
nvidia-prime                    install
nvidia-settings                    install

```

Any help/suggestions is welcome. Keep in mind I am considering myself as a beginner on Ubuntu :-)

---

