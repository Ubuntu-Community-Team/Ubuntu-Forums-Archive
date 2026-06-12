---
title: "usb 3.0 stopped working"
date: 2016-01-02
forum: Hardware
---

### Post by dmtparker on 2016-01-02
I have an Intel NUC i5 with 4 usb 3.0 ports mounted on the motherboard. It was working just fine with Ubuntu Studio 14.04 until just recently. After an update about a week ago, my computer stopped recognizing 3.0 devices. It works just fine with 2.0 devices in any of the 4 ports. When I plug in a 3.0 device, it powers up, but does not get recognized (hdd not mounted, no entry added to /dev). I originally blamed the new kernel (3.13.0-74-lowlatency), but that is not the case as I have tried dropping back to kernel 3.13.0-70 and the problem persists.
So now the question: What happened to 3.0 support?
Here is what I have for info so far:

```
mark@mark-desktop:~$ lsmod | grep xhci
mark@mark-desktop:~$ 
```

i.e., no output. so the module is not loaded??

```
mark@mark-desktop:~$ dmesg | grep xhci
[    0.601388] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.601392] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.707506] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.707522] xhci_hcd 0000:00:14.0: irq 56 for MSI/MSI-X
[    0.707605] usb usb2: Manufacturer: Linux 3.13.0-70-lowlatency xhci_hcd
[    0.709566] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.709569] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.709603] usb usb3: Manufacturer: Linux 3.13.0-70-lowlatency xhci_hcd
[    1.917604] usb 2-1: new full-speed USB device number 2 using xhci_hcd
[    2.189563] usb 2-7: new full-speed USB device number 4 using xhci_hcd
mark@mark-desktop:~$ 
```

but dmesg finds 3.0 devices

```

mark@mark-desktop:~$ sudo modprobe xhci_hcd
[sudo] password for mark: 
mark@mark-desktop:~$ lsmod | grep xhci
mark@mark-desktop:~$ 

```
modprobe did not complain when asked to load xhci_hcd, but it didn't load it either. And 3.0 devices still don't work.
Hopefully somebody can help me find and restore 3.0 support as nearly all my data is on a 3.0 1TB hdd.
Thanks in advance.

---

### Post by weatherman2 on 2016-01-02
Try to boot a live USB of Ubuntu and check for USB 3.0 functionality there.  if it still doesn't work, then you've probably got a hardware issue of some sort.

---

### Post by dmtparker on 2016-01-02
OK, this makes no sense to me, but perhaps it will to someone else. I went into the Intel Visual Bios and unchecked the UEFI option (there is no UEFI device anyway). F-10 to save and exit, boot into Ubuntu and now my usb 3.0 devices work normally. Just for the fun of it, I rebooted again. This time they are NOT working. Reboot again, this time entering Setup again. Change absolutely nothing, but exit with F-10 and the usb 3.0 devices work again! I have done this enough times to verify that it is not a fluke - If I enter Setup, exit and save, the resulting boot will recognize the 3.0 devices. If I just reboot without entering setup, the resulting boot will not recognize them?????

---

### Post by weatherman2 on 2016-01-02
In theory, restarting is supposed to give you the same hardware state as a cold boot, but in practice it may not.  Your hardware might be in an unstable state at restart that causes the USB 3.0 problems, but a cold shut down (or something done in BIOS setup) clears it.

What I would do is compare dmesg settings related to USB in the two cases, one where USB 3.0 works and the other where it doesn't.  Any difference in the messages might give you a hint to the problem.  Then it might be only a matter of setting something in Grub at boot time or something to clear out the problem reliably at each boot.

You might also look for a BIOS update, if one is available from Intel, that could fix this problem.

---

### Post by dmtparker on 2016-01-02
dmesg not working:
```
[B]mark@mark-desktop:~$ dmesg | grep xhci
[    0.602075] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.602079] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.739440] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.739456] xhci_hcd 0000:00:14.0: irq 56 for MSI/MSI-X
[    0.739539] usb usb2: Manufacturer: Linux 3.13.0-74-lowlatency xhci_hcd
[    0.741473] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.741476] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.741510] usb usb3: Manufacturer: Linux 3.13.0-74-lowlatency xhci_hcd
[    1.949333] usb 2-1: new full-speed USB device number 2 using xhci_hcd
[    2.119258] usb 2-7: new full-speed USB device number 3 using xhci_hcd
mark@mark-desktop:~$ [/B]
```

dmesg with usb 3.0 working:
```
mark@mark-desktop:~$ dmesg | grep xhci
[    0.598753] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.598757] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.599822] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.599838] xhci_hcd 0000:00:14.0: irq 56 for MSI/MSI-X
[    0.599924] usb usb2: Manufacturer: Linux 3.13.0-74-lowlatency xhci_hcd
[    0.601878] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.601881] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.601916] usb usb3: Manufacturer: Linux 3.13.0-74-lowlatency xhci_hcd
[    1.804047] usb 2-1: new full-speed USB device number 2 using xhci_hcd
[    2.075865] usb 2-7: new full-speed USB device number 4 using xhci_hcd
[    2.294927] usb 3-3: new SuperSpeed USB device number 2 using xhci_hcd
[   30.558560] usb 3-2: new SuperSpeed USB device number 3 using xhci_hcd

```
So, it is different, but I don't know why.
The NUC has no battery, so what would a 'cold' boot be as opposed to turning off (I have the power button set to 'Shutdown'.) and then back on?

---

### Post by weatherman2 on 2016-01-02
Going into BIOS could clear some state of something in the hardware.  Just a guess.  I have seen things like that before.  Oh my laptop, when I cold power on, the Grub boot menu can't be read - the text is skewed (like an old TV out of adjustment).  it still boots fine.  But if I restart, the Grub menu is perfectly readable.  Probably something similar but in my case doesn't cause a real problem.

The only difference I see is that the two USB 3 devices aren't set up in the second case.  Sounds like you need a finer level of debugging - not sure how to do that.  Sometimes /var/log/syslog or other log files might have more information.  You probably aren't the only one with NUC USB problems in Linux.  Try some creative web searches.  There's also an Intel support board, and you could post your problem there as well.

---

### Post by dmtparker on 2016-01-02
> **weatherman2 said:**
> 
You might also look for a BIOS update, if one is available from Intel, that could fix this problem.

RIGHT! The Intel website is ridiculously Windows-centric, but I finally found the latest Bios for my NUC, downloaded and installed it and at least for 3 boots in a row, the problem is SOLVED.
I will mark thread as such and re post if it recurs.

---

