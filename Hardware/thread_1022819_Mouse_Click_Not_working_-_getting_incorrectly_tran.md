---
title: "Mouse Click Not working - getting incorrectly translated as motion"
date: 2008-12-27
forum: Hardware
---

### Post by smaniam on 2008-12-27
Hi I have a USB tablet (which is not directly supported on Linux) which is correctly detected as mouse and performs correctly as a mouse on Mandriva and earlier versions of Ubuntu.

But in the 8.14, my mouse clicks are getting translated as motion instead of Clicks. I have checked this using xev and "xinput test"

I have played around with xinput, xmodmap but the results are the same.

My Xlog shows that:
(II) config/hal: Adding input device Ntk
(**) Ntk: always reports core events
(**) Ntk: Device: "/dev/input/event6"
(II) Ntk: Found x and y relative axes
(II) Ntk: Found x and y absolute axes
(II) Ntk: Found absolute touchpad
(II) Ntk: Found 2 mouse buttons
(II) Ntk: Configuring as mouse
(II) XINPUT: Adding extended input device "Ntk" (type: MOUSE)
(**) Ntk: YAxisMapping: buttons 4 and 5
(**) Ntk: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

I would like to know if:
1. Is there a better way to identify and configure the buttons correctly?
2. Do we have to tweak usbhid/evdev?

Thanks
smaniam

---

