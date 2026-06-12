---
title: "uvcvideo fails to query dell inspiron 1520's webcam on Kubuntu 8.04"
date: 2008-10-01
forum: Hardware
---

### Post by sl33p3r on 2008-10-01
Hello all,

I have a Dell Inspiron 1520 with an integrated webcam:
```
# lsusb
Bus 007 Device 005: ID 05a9:2640 OmniVision Technologies, Inc.
```

I am using the uvcvideo driver, which fails to load on system start or modprobe, with this log:
```
Oct  1 13:13:19 sanitarium-laptop kernel: [ 2743.053045] Linux video capture interface: v2.00
Oct  1 13:13:19 sanitarium-laptop kernel: [ 2743.060661] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
Oct  1 13:13:19 sanitarium-laptop kernel: [ 2743.063266] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
Oct  1 13:13:19 sanitarium-laptop kernel: [ 2743.066520] usbcore: registered new interface driver uvcvideo
Oct  1 13:13:19 sanitarium-laptop kernel: [ 2743.066534] USB Video Class driver (v0.1.0)

```

The lsmod command tells me that:
```
# lsmod | grep video
uvcvideo               58116  0
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
video                  19856  0
output                  4736  1 video
usbcore               146028  6 uvcvideo,hci_usb,usbhid,ehci_hcd,uhci_hcd
```

The dist is Ubuntu 8.04, upgraded from 7.10, and I switched to KDE on the way. The webcam used to work, but I can't pinpoint the exact time when the driver started to fail loading.
The kernel version is 2.6.24-19-generic.

Anyone had this issue or knows how to solve it?
I tried googling for the "Failed to query..." message but didn't find anything.
I also searched the forums but didn't find any relevant topic, if this issue was addressed before, please kindly point me in the right direction. :)

Thank you.

---

### Post by Rangua on 2008-10-04
i'm having a similar problem with the integrated camera on the hp tx2510us.. it's weird, because when i try to use the camera on windows, the software crashes and later i can't shut down the computer properly... 
anyways, here the dmesg
>  [14158.469229] uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -110 (exp. 26).
[14163.813182] uvcvideo: Failed to query (135) UVC control 9 (unit 3) : -110 (exp. 2).
[14164.133150] uvcvideo: Failed to query (135) UVC control 2 (unit 3) : -110 (exp. 2).
[14164.453154] uvcvideo: Failed to query (135) UVC control 7 (unit 3) : -110 (exp. 2).
[14164.773157] uvcvideo: Failed to query (135) UVC control 3 (unit 3) : -110 (exp. 2).
[14165.093150] uvcvideo: Failed to query (135) UVC control 6 (unit 3) : -110 (exp. 2).

The camera works sometimes, but in general it doesn't... pherhaps if i could somehow disable the camera and then enable it again (simulating a shut down), it would be a temporary solution to the problem... so i tried the following, it said:
>   
rangua@metacafe:/dev$ modprobe -r uvcvideo
FATAL: Module uvcvideo is in use.



PS: could it be a hardware problem?

---

### Post by skolnick on 2008-11-09
i have exactly the same issue with the integrated webcam on my dell vostro 1400 laptop. I use Fedora 9, but I guess if any of us find a solution for this, it will apply to any distro.

Regards.

---

### Post by denizenx on 2008-11-13
lol the funny thing is I have the same probs with generic V4L access. BUT KOPETE WORKS

---

