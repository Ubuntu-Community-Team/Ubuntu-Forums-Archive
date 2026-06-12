---
title: "USB wireless mouse- half way there! - Interlink RemotePoint"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by NigO on 2007-04-01
Hello,

I'm trying to get an Interlink RemotePoint Global Presenter wireless mouse / presentation controller to work with ubuntu (currently using dapper).  It seems to get to a point where it _should_ work according to all the USB guides I can find, but it doesn't.  I've tested it with Windows XP and it works fine, no drivers are supplied or required.

Can anyone point me in the right direction- ie how to debug what is happening!

Normally ls -l /dev/input shows:
```
crw-rw---- 1 root root 13,  64 Feb 15 19:28 event0
crw-rw---- 1 root root 13,  66 Jan 15 15:50 event2
crw-rw---- 1 root root 13,  67 Feb 15 19:28 event3
crw-rw---- 1 root root 13,  63 Jan 15 15:50 mice
crw-rw---- 1 root root 13,  32 Feb 15 19:28 mouse0
crw-rw---- 1 root root 13, 128 Feb 15 19:28 ts0

```
Once I plug in the USB receiver, dmesg | tail gives me:
```
[23714702.032000] usb 3-1: new low speed USB device using ohci_hcd and address 8
[23714702.316000] input: Interlink Electronics USB 2.4GHz RF Receiver as /class/input/input13
[23714702.316000] input: USB HID v1.10 Mouse [Interlink Electronics USB 2.4GHz RF Receiver] on usb-0000:00:0a.1-1
[23714702.344000] input: Interlink Electronics USB 2.4GHz RF Receiver as /class/input/input14
[23714702.344000] input: USB HID v1.00 Keyboard [Interlink Electronics USB 2.4GHz RF Receiver] on usb-0000:00:0a.1-1
```
and ls -l /dev/input shows:
```
crw-rw---- 1 root root 13,  64 Feb 15 19:28 event0
crw-rw---- 1 root root 13,  65 Apr  1 08:12 event1
crw-rw---- 1 root root 13,  66 Jan 15 15:50 event2
crw-rw---- 1 root root 13,  67 Feb 15 19:28 event3
crw-rw---- 1 root root 13,  68 Apr  1 08:12 event4
crw-rw---- 1 root root 13,  63 Jan 15 15:50 mice
crw-rw---- 1 root root 13,  32 Feb 15 19:28 mouse0
crw-rw---- 1 root root 13,  34 Apr  1 08:12 mouse2
crw-rw---- 1 root root 13, 128 Feb 15 19:28 ts0
crw-rw---- 1 root root 13, 129 Apr  1 08:12 ts1
```

From what I've read, the mouse and keyboard buttons should now work, and cat should show activity when the mouse joystick is moved or keys pressed.  I've tried to 'cat /dev/input/event1' and similarly for each of the new devices, but all are completely silent.

What should I try next?  All the USB howto's seem to go from the above to 'everything now works correctly' :(

I've been working at this for a couple of weeks, and would really appreciate some help!

Nigel

---

### Post by NigO on 2007-04-04
> **NigO said:**
> 
I'm trying to get an Interlink RemotePoint Global Presenter wireless mouse / presentation controller to work with ubuntu (currently using dapper).  It seems to get to a point where it _should_ work according to all the USB guides I can find, but it doesn't.  I've tested it with Windows XP and it works fine, no drivers are supplied or required.

Tested with Feisty 7.04 Beta, and the mouse and keyboard events are now active.  I've not tried it in X yet [installing on a 450MHz with 64MB RAM is not fast!], but it looks good so far.

I would still like to be able to use it in dapper, as we are standardising on it for long term support, so if anyone could advise what the difference might be in the USB / HID drivers, I could try to backport them.

Nigel

---

### Post by NigO on 2007-04-04
> **NigO said:**
> Tested with Feisty 7.04 Beta, and the mouse and keyboard events are now active.  I've not tried it in X yet [installing on a 450MHz with 64MB RAM is not fast!], but it looks good so far.

I would still like to be able to use it in dapper, as we are standardising on it for long term support, so if anyone could advise what the difference might be in the USB / HID drivers, I could try to backport them.


Now thoroughly tested with OpenOffice impress, all buttons and functions work correctly- next & previous slide, blank screen, left and right mouse buttons and mouse move wih joystick.:) 

One word of warning though, Interlink expressed no interest at all in supporting Linux and were not able to help beyond "it's a composite USB device, we can't say any more", so if using another of their products and/or another linux distro, proceed with caution to avoid disappointment!

Hope the above one-person discussion is useful to others!

Nigel

---

