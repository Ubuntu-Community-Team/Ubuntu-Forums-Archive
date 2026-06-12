---
title: "Logitech C920 no video in messenger (zoom, signal)"
date: 2022-02-26
forum: Hardware
---

### Post by a4c8 on 2022-02-26
When I use zoom or signal calls no video is displayed.

There seems to be an issue with dmesg:

```
dmesg | tail
[11853.270445] audit: type=1400 audit(1645891941.486:163): apparmor="DENIED" operation="mknod" profile="snap.zoom-client.zoom-client" name="/dev/shm/aomshm.93dc.0" pid=37852 comm="vda_thread" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
[11860.007512] usb 3-4: restoring control 00000000-0000-0000-0000-000000000001/1/2
[11860.007518] usb 3-4: restoring control 00000000-0000-0000-0000-000000000001/3/4
[11860.007521] usb 3-4: restoring control 00000000-0000-0000-0000-000000000001/17/8
[11860.007760] usb 3-4: restoring control 00000000-0000-0000-0000-000000000101/4/8
[11860.007764] usb 3-4: restoring control 00000000-0000-0000-0000-000000000101/6/10
[11860.007767] usb 3-4: restoring control 00000000-0000-0000-0000-000000000101/9/4
[11860.008776] usb 3-4: Failed to query (SET_CUR) UVC control 10 on unit 3: -32 (exp. 2).
[11860.117924] audit: type=1400 audit(1645891948.334:164): apparmor="DENIED" operation="mknod" profile="snap.zoom-client.zoom-client" name="/dev/shm/aomshm.93dc.0" pid=37852 comm="vda_thread" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
[12091.850863] perf: interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 79750

```

Although it's detected correctly.

```
lsusb
...
Bus 003 Device 004: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
...

```

I tried fixing it as explained [here]("https://www.christitus.com/logitech-c920-linux-driver/")

```
v4l2-ctl --list-devices
Video Capture 4 (usb-0000:00:14.0-4):
    /dev/video0
    /dev/video1

```

Normally it should be detected as logitech C920 and not Video Capture 4?

```
v4l2-ctl -d /dev/video0 --list-ctrls
                     brightness 0x00980900 (int)    : min=0 max=255 step=1 default=128 value=128
                       contrast 0x00980901 (int)    : min=0 max=255 step=1 default=128 value=128
                     saturation 0x00980902 (int)    : min=0 max=255 step=1 default=128 value=128
 white_balance_temperature_auto 0x0098090c (bool)   : default=1 value=1
                           gain 0x00980913 (int)    : min=0 max=255 step=1 default=0 value=0
           power_line_frequency 0x00980918 (menu)   : min=0 max=2 default=2 value=2
      white_balance_temperature 0x0098091a (int)    : min=2000 max=6500 step=1 default=4000 value=2200 flags=inactive
                      sharpness 0x0098091b (int)    : min=0 max=255 step=1 default=128 value=195
         backlight_compensation 0x0098091c (int)    : min=0 max=1 step=1 default=0 value=0
                  exposure_auto 0x009a0901 (menu)   : min=0 max=3 default=3 value=1
              exposure_absolute 0x009a0902 (int)    : min=3 max=2047 step=1 default=250 value=125
         exposure_auto_priority 0x009a0903 (bool)   : default=0 value=1
                   pan_absolute 0x009a0908 (int)    : min=-36000 max=36000 step=3600 default=0 value=0
                  tilt_absolute 0x009a0909 (int)    : min=-36000 max=36000 step=3600 default=0 value=0
                 focus_absolute 0x009a090a (int)    : min=0 max=250 step=5 default=0 value=0
                     focus_auto 0x009a090c (bool)   : default=1 value=0
                  zoom_absolute 0x009a090d (int)    : min=100 max=500 step=1 default=100 value=100

```

But still no video.

I then installed guvcview and after tweaking amplification I got a clear video. Unfortunately I don't know how to persist it. And there seems to be an issue with dmesg?

---

### Post by TheFu on 2022-02-26
Can you use a non-snap package for each?
I don't have any issues with my C920 and Jitsi, but I won't/don't use Zoom or Telegram.

---

### Post by him610 on 2022-02-26
Does it work with cheese?

---

### Post by a4c8 on 2022-02-26
> **TheFu said:**
> Can you use a non-snap package for each?
I don't have any issues with my C920 and Jitsi, but I won't/don't use Zoom or Telegram.
I also tried teams in browser (chrome) without success.

> **him610 said:**
> Does it work with cheese?
Yes, it does.

---

