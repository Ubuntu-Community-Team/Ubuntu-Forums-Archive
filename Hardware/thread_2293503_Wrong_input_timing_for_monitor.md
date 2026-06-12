---
title: "Wrong input timing for monitor"
date: 2015-09-05
forum: Hardware
---

### Post by zkab on 2015-09-05
I have a standard Ubuntu server installation of 14.04.3 LTS and the server is attached to our LAN but also to a KVM switch (Aten 8-ports ACS1208A) via its console port.
Sometimes after a reboot I receive following error message on the KVM switch console and then it is locked - only server power off/on helps.

"The current input timing is not supported by the monitor display.
Please change your input timing to 1920x1080@60 Hz or any other monitor listed timing as per the monitor specifications."

But according to manual the Preset Display Modes for Dell U2212HM are:

VESA, 720 x 400 31.5 70.0 28.3 -/+
VESA, 640 x 480 31.5 60.0 25.2 -/-
VESA, 640 x 480 37.5 75.0 31.5 -/-
VESA, 800 x 600 37.9 60.3 40.0 +/+
VESA, 800 x 600 46.9 75.0 49.5 +/+

VESA, 1024 x 768 48.4 60.0 65.0 -/-
VESA, 1024 x 768 60.0 75.0 78.8 +/+
VESA, 1152 x 864 67.5 75.0 108.0 +/+
VESA, 1280 x 1024 64.0 60.0 108.0 +/+
VESA, 1280 x 1024 80.0 75.0 135.0 +/+
VESA, 1600 x 1200 75.0 60.0 162.0 +/+
VESA, 1920 x 1080 67.5 60.0 148.5 +/+

How can that be fixed ?

---

