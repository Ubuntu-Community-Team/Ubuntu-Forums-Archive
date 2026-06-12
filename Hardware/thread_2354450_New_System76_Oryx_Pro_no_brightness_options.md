---
title: "New System76 Oryx Pro no brightness options"
date: 2017-03-02
forum: Hardware
---

### Post by Jacob-Gates on 2017-03-02
Hey everyone, I have been using Ubuntu for a few years now and I have learned just about everything by either me really wanting to know what's going on or by breaking something and having to fix it. That being said I know some parts of linux very well and others not so well. 

I just got in my new System76 Oryx and I installed Ubuntu Gnome on it, overwriting the original OS System76 had installed. Everything is working great except for the brightness options. I first noticed that the function keys for the brightness wouldn't even react. No pop up or change in the screen's brightness. However every single other function works, such as volume. So I went to the power settings and there is no brightness options in there either. So I think there is an issue with the hardware being recognized correctly or maybe I have the wrong driver. I did follow System76's directions on reinstalling which includes installing their drivers package and the nvidia driver package. Obviously it is working enough, but I would like to get it fully working.

What I have done so far is changing the settings in the grub to:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""
```

I also saw to try this so I did:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

I updated grub and rebooted after both changes and there was no change.

In some posts I have seen people requesting the following command so I will provide it now just in case it's useful to anyone:

```
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.8.0-39-generic root=UUID=fb68a9a6-accf-4ee0-9b1d-d7447c89e7a9 ro acpi_backlight=vendor quiet splash vt.handoff=7
```

As for the build it is a System76 Oryx pro 
Processor: Intel® Core™ i7-7700HQ CPU @ 2.80GHz × 8 
Graphics: GeForce GTX 1060/PCIe/SSE2
OS: Ubuntu 16.04.2 LTS 64-bit
Desktop Environment: Gnome3

If there is anything else I can provide just ask and any help is appreciated.

---

