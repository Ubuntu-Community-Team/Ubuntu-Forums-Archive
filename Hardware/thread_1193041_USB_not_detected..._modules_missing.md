---
title: "USB not detected... modules missing?"
date: 2009-06-21
forum: Hardware
---

### Post by vegkitty on 2009-06-21
Hey everyone-

I've have a problem for a few weeks that I just can't seem to find the cure to via Google.

I am running Jaunty on a Toshiba Satellite.  Up until a few weeks ago, my usb ports worked fine (I have my printer, an optical mouse, and my MP3 player all hooked up).  Then, for seemingly no reason, they stopped being detected.  Nothing shows up on lsusb, my desktop, nothing.

I did some searching, and I think the problem is that I don't have the modules ehci_hcd, ohci_hcd, or uhci_hcd.  Like, nothing.  When I put in modprobe ehci_hcd (for example... it does the same thing with each), I get:

FATAL: Module ehci_hcd not found.

Am I missing some command I'm supposed to know on how to install modules?  The whole thing seems weird.

Thank you MUCHO.

vegkitty

---

### Post by markmckee601 on 2009-06-21
I had a similar problem with an old version of slackware, try changing _ to - so you would modprobe ehci-hcd

---

### Post by vegkitty on 2009-06-21
> **markmckee601 said:**
> I had a similar problem with an old version of slackware, try changing _ to - so you would modprobe ehci-hcd

hmmm... I tried that and got the same message.  I get the same fatal error, down to the "ehci_hcd" part.  I even tried with a space in between (ehci hcd) and as one word (ehcihcd).  Still nothing.  :(

---

### Post by markmckee601 on 2009-06-22
Have you made any changes recently? e.g. added software, removed software etc..

You can also try locate ehci-hcd.ko or sudo find / -name ehci-hcd.ko

Also what is the output of lsmod | grep usb?

---

### Post by Aacron on 2009-06-22
> **vegkitty said:**
> Hey everyone-

Then, for seemingly no reason, they stopped being detected.  Nothing shows up on lsusb, my desktop, nothing.

vegkitty

Another idea is to check your BIOS to see if anything is out of whack there.

And another thought, are all the USB ports on one side of the lappy?  I had a problem with my VIAO a long time ago where USB went intermittent cause the teeny ribbon that went from the board to the usb ports was shaken loose.  Just a thought.

---

### Post by vegkitty on 2009-06-22
lsmod | grep usb:
>  lsmod | grep usb
usb_storage            99520  0

and for good measure, lsusb
>  lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


and dmesg (it's hella long... sorry)
> [46435.228061] usb 2-3: new low speed USB device using ohci_hcd and address 6
[46435.408065] usb 2-3: device descriptor read/64, error -62
[46435.692052] usb 2-3: device descriptor read/64, error -62
[46435.972055] usb 2-3: new low speed USB device using ohci_hcd and address 7
[46436.152060] usb 2-3: device descriptor read/64, error -62
[46436.436053] usb 2-3: device descriptor read/64, error -62
[46436.716039] usb 2-3: new low speed USB device using ohci_hcd and address 8
[46437.124058] usb 2-3: device not accepting address 8, error -62
[46437.300061] usb 2-3: new low speed USB device using ohci_hcd and address 9
[46437.708049] usb 2-3: device not accepting address 9, error -62
[46437.708125] hub 2-0:1.0: unable to enumerate USB device on port 3


As far as software updates go, I'm constantly changing software on the compy.  I tried clearing out a bunch of programs I'm not using, since I thought the problem had to do with insufficient memory, but, alas, nothing.

And I've tried finagling with my BIOS a bit, but to no avail.  I recently had to get it fixed (the Toshiba problem where the BIOS locks you out for no good reason), so maybe they accidentally snipped a wire or something while they were fixing it?

Thanks for your help, guys.  I may just take the compy to the place that fixed my BIOS and see if there's anything wrong with the physical computer.  I'll keep you updated!

---

### Post by markmckee601 on 2009-06-22
I had that same problem with a usb hub, same error messages.
I just plugged it in and plugged another device that I know that works to verify.

So it is more than likely a hardware problem.

To rule out a software problem you could boot to a live cd/live usb and plug in a device that you know definately works - if you use a wireless keyboard/mouse I would recommend using new batteries.

---

### Post by vegkitty on 2009-06-22
> **markmckee601 said:**
> I had that same problem with a usb hub, same error messages.
I just plugged it in and plugged another device that I know that works to verify.

So it is more than likely a hardware problem.

To rule out a software problem you could boot to a live cd/live usb and plug in a device that you know definately works - if you use a wireless keyboard/mouse I would recommend using new batteries.

I used the trial KDE that's on my boot CD... still didn't work.  That makes me think that there are broken wires or something in the physical computer.  I tried three or four different devices, too (mouse, MP3 player, external HD), none of which were even detected.

Thanks for the advice.  I think I'll go see my friendly neighborhood computer repairman ASAP.

---

