---
title: "intel HD 3000 cpu internal gpu series maybe newers RC6 mode video tearing"
date: 2013-01-17
forum: Hardware
---

### Post by xfcewithmutter on 2013-01-17
i'm acer 5755g user. im using last v1.21 bios. processor is i5-2430m includes hd 3000 gpu.

i tried manjaro, fedora, fubuntu, debian, ubuntu.

i tried all possible ubuntu mainline kernel archives 3.5, 3.6, 3.7, 3.8 drm includes drm intel next drm and others....

if rc6 mode enabled compiz, kwin, mutter all of them giving this tearing.

when rc6 mode totaly disabled all of them good.

results same as me: 

i915_enable_rc6=1
[http://www.youtube.com/watch?v=jK3L-n5_OX0](http://www.youtube.com/watch?v=jK3L-n5_OX0)

i915_enable_rc6=0
[http://www.youtube.com/watch?v=mVTPTSHjCqQ](http://www.youtube.com/watch?v=mVTPTSHjCqQ)

when im using mutter. i can add /etc/environment file with it:
"CLUTTER_PAINT=disable-clipped-redraws:disable-culling" this is fix problem but not work on archlinux/manjaro

not work on kwin and best result is i915_enable_rc6=0 and without "CLUTTER_PAINT=disable-clipped-redraws:disable-culling"

a lot of laptop-notbook using intel processor and from sandybridge their new optimus switching is different. first gpu is intel gpu.

edit:

i starting with system last 3.7.3 kernel. 

no tearing but. power consumption is high. look line rc6 mode disabled.

but

command:dmesg|fgrep -i "rc6"  

[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.4.26-030426-generic root=UUID=44014c58-cd71-4151-b0bc-4dddda8cf7a3 ro crashkernel=384M-2G:64M,2G-:128M acpi_backlight=vendor i915.i915_enable_rc6=7
[ [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.4.26-030426-generic root=UUID=44014c58-cd71-4151-b0bc-4dddda8cf7a3 ro crashkernel=384M-2G:64M,2G-:128M acpi_backlight=vendor i915.i915_enable_rc6=7
[ [   25.699034] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp on

when this situation if i try shutdown system last message is drm i915 "bla bla bla" gpu hung.... 


when is stardet with last 3.4.26 kernel  

power consumtion low ( look like rc6 activated ) and i can see video tearing 




if i start system with battery without power plug alvays rc6 activated and video tearing enabled. im thinking kernel cant control rc6 mode....

---

