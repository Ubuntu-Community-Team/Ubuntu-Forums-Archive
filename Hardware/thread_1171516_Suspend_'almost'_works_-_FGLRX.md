---
title: "Suspend 'almost' works - FGLRX?"
date: 2009-05-27
forum: Hardware
---

### Post by sam_uk on 2009-05-27
Hi All

I have a [https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6325](https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6325)

It has a Xpress 200m graphics card. I use Intrepid as Jaunty does not support the FGLRX driver which makes my graphics card work OK.

Suspend 'almost works' I can suspend, and resume, however following a resume it seems the backlight is on about half power and the screen is very dim. Is there a way to fix this please?

user@laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.8304 Release


Is there a log file somewhere I can provide?

---

### Post by sam_uk on 2009-05-29
<bump> anyone?

---

### Post by Duckter on 2009-05-29
Try going to System -> Preferences -> Session and then unchecking the Bluetooth Manager.  After a reset this should hopefully solve the problem (unless you use Bluetooth).

Not entirely sure the exact reasons why but it worked for me and my Radeon.

---

### Post by sam_uk on 2009-06-01
Thanks for the suggestion, afraid it did not work for me :(

Anyone have any other ideas?

---

### Post by James Keating on 2009-06-10
Before Karmic (9.10), I edited /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux and changed the quirks line to:
QUIRKS="--quirk-s3-bios --quirk-s3-mode --quirk-dpms-on --quirk-vbe-post --quirk-vbestate-restore" 
(This needed to be redone after each update, since the file got overwritten.)

Now that file has no effect. Instead, I must add two boot parameters and delete references to the quirks in a file that removes them instead of letting them take effect.

The first time I suspend, resume works for a moment and then goes into hibernation. After coming out of hibernation, resume works from the second time on. This may be peculiar to my machine (an NEC VersaPro VY15F with an Intel 82852/855GM Integrated Graphics Device).

Make backups of all files you change. All changes must be made as root.

My method:

1. In /boot/grub/menu.lst
add i915.modeset=0 nomodeset to the defoptions line. This disables the new kernel mode-setting (KMS):
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash i915.modeset=0 nomodeset

If menu.lst doesn't exist, your installation uses a new GRUB method.
If so, edit /etc/defaults/grub
and add i915.modeset=0 nomodeset:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0 nomodeset"

1b) Save and run the command update-grub.

2. In /usr/lib/pm-utils/sleep.d/98smart-kernel-video
delete all references to the quirks you need.
In my case, two quirks are in the section remove_all_video_quirks: 
     --quirk-s3-bios  --quirk-s3-mode
and three are in the section have_smart_intel: 
     --quirk-dpms-on --quirk-vbe-post --quirk-vbestate-restore

3) Save and reboot.

To find the quirks you need, look at the manpage for pm-suspend, and run pm-suspend followed by quirk options. Try combining everything that looks likely, then removing some. Be thorough and patient. Make notes, because you may be rebooting a lot until something works. 

If no combination works, try installing uswsusp and running s2ram, or try TuxOnIce, though I had no luck with either.

##########

Update for Lucid:

Under Lucid, the instructions above do not work -- with those kernel parameters, I boot into a black screen.
i915.modeset needs to be on in order to boot.

1. In /boot/grub/menu.lst
add i915.modeset=1 to the defoptions line. This enables the new kernel mode-setting (KMS):
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash i915.modeset=0 

If menu.lst doesn't exist, your installation uses a new GRUB method.
If so, edit /etc/defaults/grub
and add i915.modeset=0 nomodeset:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"

2) Save and run the command update-grub.

3) Save and reboot.

Formerly, after suspending the machine for the first time after each boot, it would recover for a moment and then go into hibernation. After booting out of hibernation, suspend worked find. Now, after suspending for the first time, the machine recovers for a moment and then suspends. After resuming, subsequent suspends work fine. 

I had video trouble with Lucid (apps hanging, system failure on viewing video), which I have solved by installing the newest Ubunu kernel (details are in a different thread).

---

### Post by timosha on 2009-12-03
> **James Keating said:**
> 
My method:


If menu.lst doesn't exist, your installation uses a new GRUB method.
If so, edit /etc/defaults/grub
and add i915.modeset=0 nomodeset:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0 nomodeset"

1b) Save and run the command update-grub.

2. In /usr/lib/pm-utils/sleep.d/98smart-kernel-video
delete all references to the quirks you need.
In my case, two quirks are in the section remove_all_video_quirks: 
     --quirk-s3-bios  --quirk-s3-mode
and three are in the section have_smart_intel: 
     --quirk-dpms-on --quirk-vbe-post --quirk-vbestate-restore

3) Save and reboot.

.

This works on my Thinkpad R51 with Intel 855GM  and Karmic. Thank you very much

---

