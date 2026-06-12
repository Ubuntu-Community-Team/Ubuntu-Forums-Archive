---
title: "MSI GT683DX log messages constant usb error"
date: 2011-12-13
forum: Hardware
---

### Post by MediocreGopher on 2011-12-13
Just got a new laptop, installed Ubuntu 10.04 LTS on it. Everything seems to work ok, except for these three things:

In /var/log/messages the following gets logged a few times a second:
Dec 11 14:08:19 TheBoss kernel: [   93.553339] usb 2-1.7: reset full speed USB device using ehci_hcd and address 4

I've googled around for this problem, so far the only thing that seemed like it might apply was a post saying that CONFIG_USB_EHCI_TT_NEWSCHED needed to be enabled in the kernel. However this was an in archlinux post, so I figured it probably didn't apply. The following was in my .config for my kernel:

CONFIG_USB_EHCI_TT_NEWSCHED=y

For fun I compiled the kernel with that turned off; resulted in kernel panic, so I guess that's not the way to go.

Does anyone have any ideas of where to go with this?

---

