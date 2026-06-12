---
title: "Cannot get a USB external disk working in 8.10"
date: 2008-11-02
forum: General Help
---

### Post by unixer on 2008-11-02
Hi,

I have a Western Digital external USB HD.  I can't get it working under Intrepid Ibex.

In the log message, I have the following:
Nov  2 10:37:16 strontium kernel: [  392.300028] usb 1-1: new high speed USB device using ehci_hcd and address 2
Nov  2 10:37:16 strontium kernel: [  392.448725] usb 1-1: configuration #1 chosen from 1 choice
Nov  2 10:37:17 strontium kernel: [  392.891492] usb 1-1: USB disconnect, address 2
Nov  2 10:37:18 strontium kernel: [  393.732032] usb 1-1: new high speed USB device using ehci_hcd and address 3
Nov  2 10:37:18 strontium kernel: [  393.882013] usb 1-1: configuration #1 chosen from 1 choice
Nov  2 10:37:18 strontium kernel: [  394.323848] usb 1-1: USB disconnect, address 3
Nov  2 10:37:19 strontium kernel: [  395.164023] usb 1-1: new high speed USB device using ehci_hcd and address 4
Nov  2 10:37:19 strontium kernel: [  395.313250] usb 1-1: configuration #1 chosen from 1 choice
Nov  2 10:37:20 strontium kernel: [  395.757331] usb 1-1: USB disconnect, address 4
Nov  2 10:37:20 strontium kernel: [  396.600030] usb 1-1: new high speed USB device using ehci_hcd and address 5
Nov  2 10:37:21 strontium kernel: [  396.748686] usb 1-1: configuration #1 chosen from 1 choice
Nov  2 10:37:21 strontium kernel: [  397.190688] usb 1-1: USB disconnect, address 5
Nov  2 10:37:22 strontium kernel: [  398.032028] usb 1-1: new high speed USB device using ehci_hcd and address 6
Nov  2 10:37:22 strontium kernel: [  398.181326] usb 1-1: configuration #1 chosen from 1 choice
Nov  2 10:37:22 strontium kernel: [  398.623796] usb 1-1: USB disconnect, address 6


I can use a USB stick without problem.  My mouse is also USB and it works just fine.

Also, I have two laptops, one with Gutsy and one with Hardy and my WD HD works fine with those.

An idea what can be the problem?  Or a way to diagnose the problem?

Thanks,
Bernard

---

