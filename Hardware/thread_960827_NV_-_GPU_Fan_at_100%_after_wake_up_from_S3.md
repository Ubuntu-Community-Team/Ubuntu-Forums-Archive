---
title: "NV - GPU Fan at 100% after wake up from S3"
date: 2008-10-27
forum: Hardware
---

### Post by unsen on 2008-10-27
Problem: after wakeup from S3 the GPU fan is spinning at full speed all the time.

after rebooting, the gpu-fan is working at normal speed again, meaning temperature-controlled. btw, the CPU-fan is working temperature-controlled all the time and after a wakeup from S3 too. 

the same problem i've had under WXP, but it was solved after a MAINBOARD bios-update! but with ubuntu-linux, i'm still having this issue.

i have a twin-view system. the S3 mode i got to work only by deactivating the "sync to vblank" in NVIDIA X Server Settings, nothing more.

i didnt have to change the often mentioned settings in acpi-support: SAVE_VBE_STATE and POST VIDEO. though i tried several configurations turning off or on some of these to fix the wakeup problem. 

right now it looks like:

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true
# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true
# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true
# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

System: ASUS M2N-SLI Deluxe - X2-4600EE / MSI NX7900GS-T2D512E-OC (Bios 5.71.22.42.08 ) / driver: nvidia restricted, ubuntu hardy

---

