---
title: "eee intermittent audio"
date: 2009-04-09
forum: Hardware
---

### Post by kainalu on 2009-04-09
Ive been having intermittent audio with Ubuntu 8.10 on my EEE 901 with the eee-lean kernel and eee-control. I am posting my modules here that are loaded when the audio is working and im hoping someone can tell me which is the audio module or help me solve the problem.

thanks!
kainalu


lsmod:

Module                  Size  Used by
nls_iso8859_1           4096  1 
nls_cp437               5760  1 
vfat                   11136  1 
fat                    49056  1 vfat
i915                   30208  2 
drm                    78120  3 i915
cpufreq_stats           5252  0 
i2c_dev                 6792  2 
i2c_i801                9488  1 
i2c_core               23956  2 i2c_dev,i2c_i801
usb_storage            73408  1 
uvcvideo               54792  0 
pcspkr                  2688  0 
libusual               19220  1 usb_storage
psmouse                45336  0 
rt2860sta             546008  1 
intel_agp              25788  1 
agpgart                34120  3 drm,intel_agp
eeepc_laptop           10132  0 
rfkill                  8728  2 eeepc_laptop
sd_mod                 34200  6 
sg                     31540  0 
ehci_hcd               35340  0 
uhci_hcd               22928  0 
usbcore               141296  6 usb_storage,uvcvideo,libusual,ehci_hcd,uhci_hcd
vesafb                  5892  1

---

