---
title: "[SOLVED] No Backlight after Suspend - Intrepid"
date: 2008-11-23
forum: Hardware
---

### Post by funkydan2 on 2008-11-23
Hi,

I've just installed Intrepid on my Sony VAIO VGN-T37GP and I'm having trouble when waking up from suspend.

The symptoms are that when I wake up the machine from suspend, the backlight isn't turned on to the LCD screen.  Everything is working - it's just that the screen is super dark, and pressing the brightness control keys makes barely any difference (resuming from Hibernate works perfectly).

It seems to me to be very similar to [this bug]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/292256"), but the suggestions there of fiddling with 'vbetool post' didn't bring the backlight up.

I'm happy for any suggestions of what to try.

Hardware:
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
Kernel:
Linux vaio-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

Thanks,

Daniel

---

### Post by funkydan2 on 2008-11-24
I've been playing around, and it seems that running the /etc/acpi/sleep.sh script works as expected!  The machine sleeps and then upon resume the screen works well (but it doesn't ask for a password).  However either closing the lid (gnome-power-manager is set to suspend at this case) or selecting 'suspend' from the 'Shutdown the computer' dialog (comes up after pressing the power button) still causes the no backlight problem.

So is there a way to change the scripts called by the gnome tools?

---

### Post by lwhitmore on 2008-12-01
Hi - I have the same problem... I'm using Intrepid on a Sony VGN-B3VP - if anyone has any advice, would be very grateful.

Cheers

Luke

---

### Post by khaije1 on 2008-12-02
same problem here, it's particularly annoying because it worked like a (good) dream in hardy.

I as well have a sony laptop pcg-r505, weird eh?


Linux callisto 2.6.27-10-generic #1 SMP Fri Nov 21 12:00:22 UTC 2008 i686 GNU/Linux
\00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]

lshal | grep system.hardware 
  system.hardware.primary_video.product = 13687  (0x3577)  (int)
  system.hardware.primary_video.vendor = 32902  (0x8086)  (int)
  system.hardware.product = 'PCG-R505GCK(UC)'  (string)
  system.hardware.serial = 'xxxxxxxx-xxxxxxx'  (string)
  system.hardware.uuid = 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx'  (string)
  system.hardware.vendor = 'Sony Corporation'  (string)
  system.hardware.version = 'R3246791'  (string)

---

### Post by funkydan2 on 2008-12-03
Has any tried just running /etc/acpi/sleep.sh?  Or having a look at the [launchpad bug](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/292256) which seems to be similar to see if there's anything there that helps?

I still haven't got any further :(

---

### Post by khaije1 on 2008-12-04
/etc/acpi/sleep.sh didn't work for me. same skit.

i tried all three pm backends: kernel, uswsusp, tuxonice. 

Tuxonice/suspend2 didn't work for me at all, i think perhaps it didn't install properly. In the case of kernel and uswsusp they were very much the same results except that uswsusp is slower, that is to say hbernate/resume works and suspend/resume fails.

I'm tried using different variations of the pm quirks found [here]("http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-explain.html") but have yet to notice a positive difference as a result.

This would seem to be a widespread regression. 
similar thread: [#1]("http://ubuntuforums.org/showthread.php?t=770147") [#2]("http://ubuntuforums.org/showthread.php?t=580001") 

meh.

---

### Post by khaije1 on 2008-12-05
not sure if this is already clear but suspend still works great using the hardy kernel. Because i did a dist-upgrade from hardy -> intrepid i still have 2.6.24-21-generic (hardy's last kernel) selectable.

When i loaded 2.6.24-21-generic and attempt suspend it works like a charm. To me this just confirms that it's not a user-space utility problem, or probably even a config issue. It's likely that this problem is due to a kernel regression.

The next thing I may try is switching the pm backend to use the uswsusp from debian's sid. Ha, or maybe i'll just use the hardy kernel. My impression so far is intrepid is among the worst ubuntu releases yet. The hardy series was probably the strongest.

---

### Post by funkydan2 on 2008-12-08
I've noticed that my system (Vaio VGN-T37GP) is also quite 'laggy' when it comes to doing ACPI-type things.  For example changing the brightness using the Fn+F5/6 combination often takes a while to come into effect, and it normally takes a few seconds between plugging/unplugging the power, and Gnome Power Manager recognising this change in status.  

On my Dell Vostro 1500 Laptop, this is almost instantaneous (though it is also a much faster laptop).

I wonder if these things are related.

---

### Post by owend on 2008-12-10
> **funkydan2 said:**
> Hi,

I've just installed Intrepid on my Sony VAIO VGN-T37GP and I'm having trouble when waking up from suspend.

The symptoms are that when I wake up the machine from suspend, the backlight isn't turned on to the LCD screen.  Everything is working - it's just that the screen is super dark, and pressing the brightness control keys makes barely any difference (resuming from Hibernate works perfectly).

It seems to me to be very similar to [this bug]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/292256"), but the suggestions there of fiddling with 'vbetool post' didn't bring the backlight up.

I'm happy for any suggestions of what to try.

Hardware:
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
Kernel:
Linux vaio-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

Thanks,

Daniel
Hi, it may not be relevant, but under Hardy (Acer laptop, AMD processor), I had no suspend (or more accurately no resume). I finally got suspend working by going to /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux and changing the QUIRKS line to QUIRKS="--quirk-s3-bios --quirk-s3-mode --quirk-dpms-suspend --quirk-dpms-on --quirk-vbestate-restore --quirk-vbemode-restore --quirk-vga-mode3 --quirk-vbe-post --quirk-reset-brightness" (ie enabling all quirks except --quirk-radeon-off).

it works, but I don't know why, or which bit was critical: it ain't bust so I'm not trying to fix it!

---

### Post by funkydan2 on 2008-12-10
owend - you are a champion!

This is what I did.

I had a look at /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux and worked out that with my graphics card some quirks were already being enabled, but not all. Thus to the 'non NEW_INTEL, nVidia, ATI' section of the script, I enabled the S3_BIOS, S3_MODE, and DPMS_SUSPEND quirks, so that my hal-systempower-suspend-linux script now looks like this:
```

#!/bin/sh

alarm_not_supported() {
	echo org.freedesktop.Hal.Device.SystemPowerManagement.AlarmNotSupported >&2
	echo Waking the system up is not supported >&2
	exit 1
}

unsupported() {
	echo org.freedesktop.Hal.Device.SystemPowerManagement.NotSupported >&2
	echo No suspend method found >&2
	exit 1
}

read seconds_to_sleep

# on some video drivers we must ignore video quirks, since they break
# on them; this particularly affects Intel >= 915G and the proprietary
# nvidia and fglrx drivers.
if [ -d /sys/module/i915 ]; then
    # the i915 kmod also drives the i830 and i855 chips nowadays, but they
    # still need quirks on at least Linux 2.6.24.
    PRODID=`hal-get-property --udi $HAL_PROP_INFO_UDI --key system.hardware.primary_video.product`
    if [ "$PRODID" != 13696 ] && [ "$PRODID" != 13698 ] && \
        [ "$PRODID" != 13687 ]; then
        NEW_INTEL=1
    fi
fi

if [ "$NEW_INTEL" ] || [ -d /sys/module/nvidia ] || [ -d /sys/module/fglrx ];
then
    HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_BIOS=false
    HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_MODE=false
    HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_SUSPEND=false
    HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_ON=false
    HAL_PROP_POWER_MANAGEMENT_QUIRK_VBESTATE_RESTORE=false
    HAL_PROP_POWER_MANAGEMENT_QUIRK_VBEMODE_RESTORE=false
    HAL_PROP_POWER_MANAGEMENT_QUIRK_VGA_MODE_3=false
    HAL_PROP_POWER_MANAGEMENT_QUIRK_VBE_POST=false
    HAL_PROP_POWER_MANAGEMENT_QUIRK_RADEON_OFF=false
    HAL_PROP_POWER_MANAGEMENT_QUIRK_RESET_BRIGHTNESS=false
# if we do not have any explicit quirks in the hal FDIs, enable a few by
# default which work around kernel problems and are necessary with most older
# video drivers
elif ! env | grep -q HAL_PROP_POWER_MANAGEMENT_QUIRK; then
    HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_BIOS=true #added by DS
    HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_MODE=true #added by DS
    HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_SUSPEND=true #was false
    HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_ON=true
    HAL_PROP_POWER_MANAGEMENT_QUIRK_VBESTATE_RESTORE=true
    HAL_PROP_POWER_MANAGEMENT_QUIRK_VBEMODE_RESTORE=true
    HAL_PROP_POWER_MANAGEMENT_QUIRK_VGA_MODE_3=true
    HAL_PROP_POWER_MANAGEMENT_QUIRK_VBE_POST=true
    HAL_PROP_POWER_MANAGEMENT_QUIRK_RESET_BRIGHTNESS=true
fi

# Make a suitable command line argument so that the tools can do the correct
# quirks for video resume.
# Passing the quirks to the tool allows the tool to not depend on HAL for data.
QUIRKS=""
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_BIOS" = "true" ] && QUIRKS="$QUIRKS --quirk-s3-bios"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_MODE" = "true" ] && QUIRKS="$QUIRKS --quirk-s3-mode"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_SUSPEND" = "true" ] && QUIRKS="$QUIRKS --quirk-dpms-suspend"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_ON" = "true" ] && QUIRKS="$QUIRKS --quirk-dpms-on"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VBESTATE_RESTORE" = "true" ] && QUIRKS="$QUIRKS --quirk-vbestate-restore"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VBEMODE_RESTORE" = "true" ] && QUIRKS="$QUIRKS --quirk-vbemode-restore"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VGA_MODE_3" = "true" ] && QUIRKS="$QUIRKS --quirk-vga-mode3"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VBE_POST" = "true" ] && QUIRKS="$QUIRKS --quirk-vbe-post"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_RADEON_OFF" = "true" ] && QUIRKS="$QUIRKS --quirk-radeon-off"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_RESET_BRIGHTNESS" = "true" ] && QUIRKS="$QUIRKS --quirk-reset-brightness"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_NONE" = "true" ] && QUIRKS="$QUIRKS --quirk-none"

# Urh. Do any BIOSen handle this correctly?
if [ $seconds_to_sleep != "0" ] ; then
	alarm_not_supported
fi

# We only support pm-utils
if [ -x "/usr/sbin/pm-suspend" ] ; then
	/usr/sbin/pm-suspend $QUIRKS
	RET=$?
else
	# TODO: add support
	unsupported
fi

# Refresh devices as a resume can do funny things
for type in button battery ac_adapter
do
	devices=`hal-find-by-capability --capability $type`
	for device in $devices
	do
		dbus-send --system --print-reply --dest=org.freedesktop.Hal \
			  $device org.freedesktop.Hal.Device.Rescan
	done
done

exit $RET

```

(In the middle there are three lines that I've changed.)

I'll probably fiddle with this a little more over the next few days to see which of the quirks was the one that was needed, but for now, I'm just stocked that I've got suspend working!

---

### Post by funkydan2 on 2008-12-10
Actually, all I need to do is to change
```

HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_SUSPEND=false

```
to
```

HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_SUSPEND=true

```
(line 46 of /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux).

++kudos to owend

---

### Post by funkydan2 on 2008-12-11
Nope, actually all three must be needed, because after a reboot suspend didn't work with only the DPMS_SUSPEND quirk turned on.

(I read somewhere that some of these switches are 'sticky', that can sometimes fool you when debugging because you think that you aren't using a particular command, but it's still in effect.)

---

### Post by lwhitmore on 2008-12-12
Hey - thanks

Adding the three lines

```

HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_BIOS=true
HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_MODE=true
HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_SUSPEND=true

```

after the following (found at line 49)

```

elif ! env | grep -q HAL_PROP_POWER_MANAGEMENT_QUIRK; then

```

worked for me too.

I'm using a Sony VGN-B3VP laptop with Intrepid.

---

### Post by funkydan2 on 2008-12-13
I've reported this as a bug in launchpad, with the hope that it may get fixed in a later release. You may like to subscribe or help out there as well:

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/307126](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/307126)

---

### Post by lwhitmore on 2009-02-22
This problem has started up again on my laptop.  I think that it may have been installation of some updates, which reintroduced the problem.

Has anyone else got the same problem?

---

### Post by wirehead2501 on 2009-03-04
ARGH.  Yes, it is happening to me again now, too.  I originally had the problem after upgrade to Intrepid, fixed as per this post.  Just installed some updates last night that have broken it again.  My first thought was that this file had been overwritten, but I just checked, and it still has the changes in it.  >_<  Anyone got any other bright ideas?

*Edited to add: I'm on a VAIO VGN-T140P.

*Edited again, a bit later: I found Synaptic->File->History and got the list of stuff I updated last night.  Looks like the most likely culprit was hal-info.  I will keep digging and update here as I figure stuff out.

last update: hal-info (20081124-0ubuntu1~intrepid) to 20090128-0ubuntu1~intrepid2

last update before that (working) was: hal-info (20081001-0ubuntu1~hardy1) to 20081124-0ubuntu1~hardy

*Edit: Yep, okay, I downgraded the package in Synaptic and, voila, I get my LCD back after suspend again.

For those who don't know how to do it, go into Synaptic and search for the hal-info package.  Go to Package->Force Version and select the version prior to the one that's currently installed.  Apply to downgrade it.  Then to keep Synaptic from wanting to automatically upgrade it again, Package->Lock Version.

If anyone comes up with the REAL solution to this (e.g. where you still get to upgrade hal-info), I'd definitely be interested in hearing it.  Meanwhile, hope this helps someone else.

*Final edit of the evening, I promise: Just reported the bug here: [https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/336521](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/336521)

---

### Post by scradock on 2009-04-15
I've been chasing similar problems on a different machine, and found the same solution (editing the .../hal-system-power-suspend-linux file). Then the update happened and I lost the fix, like you did.

So I snooped around a bit and found that the HAL information is now used directly out of the HAL database, not from the file we edited. I've restored correct functioning on my machine by using the hal-set-property command - see "man hal-set-property" - to address specific power-management.quirks. For the dpms-suspend quirk it would go like this:

sudo hal-set-property --udi '/org/freedesktop/Hal/devices/computer' --key "power_management.quirk.dpms_suspend" --bool "true"

to set it to true, and correspondingly --bool "false" to set it to false.

I really don't know why the developers are making these changes, without any notification that I can see. The business of setting the correct quirks is getting more and more arcane and complicated, and users are apparently not supposed to trouble with it - leave it to HAL. Well, HAL doesn't know what my machine needs, apparently - or yours. In my case I set all quirks to false, and it works fine!

---

### Post by ssri on 2009-05-22
I disliked using vbetool to turn off my laptop's backlight.  I noticed that I started to have the problem when xrandr automatically initiated after kubuntu detected my tv signal through a connected svideo cable.  Disabling xrandr from the post below solved the problem.  Now dpms and powerdevil both work.

[http://ubuntuforums.org/showthread.php?t=1137576](http://ubuntuforums.org/showthread.php?t=1137576)

---

### Post by James Keating on 2009-06-10
My laptop is an NEC VersaPro VY15F, with an Intel 82852/855GM graphics device. Hibernate worked, but not suspend. 

Before Karmic (9.10), my solution was to edit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux and change the quirks line to:
QUIRKS="--quirk-s3-bios --quirk-s3-mode --quirk-dpms-on --quirk-vbe-post --quirk-vbestate-restore" 
(This needed to be redone after each update, since the file got overwritten.)

Now that file has no effect. Instead, I must add two boot parameters and delete references to the quirks in a file that removes them instead of letting them take effect.

The first time I suspend, resume works for a moment and then goes into hibernation. After coming out of hibernation, resume works from the second time on. This may be peculiar to my machine.

Make backups of all files you change. All changes must be made as root.

My new method:

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

