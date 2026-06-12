---
title: "HP Pavilion DV6000 infrared red remote"
date: 2009-06-08
forum: Hardware
---

### Post by kiddykoff on 2009-06-08
A while ago i brought the infrared remote control to the laptop i am now using, HP pavilion 6815nr.

I tried system>preferences>keyboard shortcuts and adding custom shortcuts, but some of the button presses are unrecognized.

Some of the keys are already binded to the keyboard like the left arrow, but others are not.

Can someone tell me how to bind these buttons? I figure I'll be able to take it from there

Thanks in advance

---

### Post by kiddykoff on 2009-06-08
The keys that didn't work were quickplay, dvd, and a windows button. my fastfoward and rewind are binded to ctrl-f and ctrl-b, respectively. How do i change this?

and also

bump

---

### Post by djodjoman on 2009-06-08
I never got those to work, but never tried either cause i never felt the necessity to use them, but sure it would be nice to bind them to a shortcut ... it seems like windows buttons, i don't know ... I have quick play and DVD button on my laptop and they do nothing on Ubuntu... the other keys, so as the other remote keys work fine.

---

### Post by esdi on 2012-04-11
Hello, 

I was going to start a thread with the exact same question so,  since this one was not solved... here goes.

On Oneiric and Precise beta2, I am able to check that the remote generates key codes for most buttons using the command:

```
sudo evtest /dev/input/event4
```I do not have lirc installed at the moment because I want to pinpoint the cause of the remote buttons not generating events.

This remote (that comes with my Pavilion DV6575CA) is somehow interpreted as a keyboard by ubuntu.  I have found no trace of infrared hardware mentioned in lspnp, lsusb, lspci, and all the other commands I have tried.

When running evtest, if I press a button on the remote, the same code shows up if I press the same button on the keyboard. For example the Play/Pause button of the remote generates this:

```
Event: time 1334159335.906876, type 4 (EV_MSC), code 4 (MSC_SCAN), value a2
Event: time 1334159335.906887, type 1 (EV_KEY), code 164 (KEY_PLAYPAUSE), value 1
Event: time 1334159335.906891, -------------- SYN_REPORT ------------
Event: time 1334159335.914339, type 4 (EV_MSC), code 4 (MSC_SCAN), value a2
Event: time 1334159335.914345, type 1 (EV_KEY), code 164 (KEY_PLAYPAUSE), value 0
Event: time 1334159335.914347, -------------- SYN_REPORT ------------

```The Play/Pause button of the keyboard also:
```
Event: time 1334159340.374885, type 4 (EV_MSC), code 4 (MSC_SCAN), value a2
Event: time 1334159340.374895, type 1 (EV_KEY), code 164 (KEY_PLAYPAUSE), value 1
Event: time 1334159340.374899, -------------- SYN_REPORT ------------
Event: time 1334159340.445856, type 4 (EV_MSC), code 4 (MSC_SCAN), value a2
Event: time 1334159340.445865, type 1 (EV_KEY), code 164 (KEY_PLAYPAUSE), value 0
Event: time 1334159340.445867, -------------- SYN_REPORT ------------

```Unfortunately for the quick play, dvd and windows button of the remote, there is nothing displayed by evtest.

The same buttons on the keyboard / button bar of the laptop generates this:
```
Event: time 1334159632.782640, type 4 (EV_MSC), code 4 (MSC_SCAN), value 88
Event: time 1334159632.782647, type 1 (EV_KEY), code 226 (KEY_MEDIA), value 1
Event: time 1334159632.782648, -------------- SYN_REPORT ------------
Event: time 1334159632.792839, type 4 (EV_MSC), code 4 (MSC_SCAN), value 88
Event: time 1334159632.792845, type 1 (EV_KEY), code 226 (KEY_MEDIA), value 0
Event: time 1334159632.792847, -------------- SYN_REPORT ------------
Event: time 1334159633.525445, type 4 (EV_MSC), code 4 (MSC_SCAN), value 8e
Event: time 1334159633.525451, type 1 (EV_KEY), code 389 (KEY_DVD), value 1
Event: time 1334159633.525454, -------------- SYN_REPORT ------------
Event: time 1334159633.535142, type 4 (EV_MSC), code 4 (MSC_SCAN), value 8e
Event: time 1334159633.535146, type 1 (EV_KEY), code 389 (KEY_DVD), value 0
Event: time 1334159633.535148, -------------- SYN_REPORT ------------
Event: time 1334159635.891856, type 4 (EV_MSC), code 4 (MSC_SCAN), value db
Event: time 1334159635.891864, type 1 (EV_KEY), code 125 (KEY_LEFTMETA), value 1
Event: time 1334159635.891867, -------------- SYN_REPORT ------------
Event: time 1334159636.001259, type 4 (EV_MSC), code 4 (MSC_SCAN), value db
Event: time 1334159636.001267, type 1 (EV_KEY), code 125 (KEY_LEFTMETA), value 0
Event: time 1334159636.001269, -------------- SYN_REPORT ------------

```How can I investigate how the events are generated?
Can someone point me in the right direction?

Thanks

---

