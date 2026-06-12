---
title: "Modprobe to cure one second delay"
date: 2022-11-08
forum: Hardware
---

### Post by triplemaya on 2022-11-08
I was suggested to run a modprobe script to cure my one second delay issue. When attached to an external monitor there is a one second delay before it registers mouse clicks or keyboard.

This is the script:
```

sudo su -
modprobe drm_kms_helper
echo 0 > /sys/module/drm_kms_helper/parameters/poll
echo "drm_kms_helper" >> /etc/modprobe.d/local.conf
echo "drm_kms_helper" >> /etc/modules-load.d/local.conf
echo "options drm_kms_helper poll=0" >> /etc/modprobe.d/local.conf
update-initramfs -u

```

It does not work. I was told by an expert that "I think that instruction must have been in error as that doesn't match the syntax for that config file (see [https://manpages.ubuntu.com/manpages/trusty/man5/modprobe.d.5.html](https://manpages.ubuntu.com/manpages/trusty/man5/modprobe.d.5.html) ). So remove that line and re-run update-initramfs -u"

I did this but no better result. I would love to get this to work. The only alternative is to sell the laptop and get one that does not use this graphics card!

Old thread is here:

[HTML]https://ubuntuforums.org/showthread.php?t=2478871[/HTML]

---

