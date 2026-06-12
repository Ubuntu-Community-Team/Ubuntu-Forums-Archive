---
title: "High pitched whine coming from speakers"
date: 2013-08-05
forum: Hardware
---

### Post by jared2 on 2013-08-05
Hi,

I'm running Ubuntu 13.04 on a Lenovo y410p laptop.  I am dual-booting with Windows 8. 

I'm getting a high pitched whine coming from my speakers when the laptop is running on battery power. Changing the volume makes the speakers pop. Plugging it into the wall supply usually makes it stop.

When I go to System Settings>Sound, it also stops the sound. When I exit Sound settings, the sound resumes after about two seconds, following a loud pop. Turning the speakers off and the mic off each have no effect on the whine.

This problem is non-existent on Windows, and has persisted on Ubuntu from LiveCD, through installation, to the hard drive install.

Any thoughts or help would be appreciated, thank you in advance.

---

### Post by jared2 on 2013-08-07
Update: I got the whine to go away, mostly. I discovered, quite by accident, that changing the backlit keyboard (using the function keys on the keyboard) to either off, or full brightness made the whine go away. The middle brightness setting still causes the whine on battery power.

I also was able to noticed a fainter, more irregular whine come from the speakers when the cpu is under higher load.

Popping is still an issue on battery power. If I had to guess, it's almost like the sound card is shutting down with a pop after a few seconds of no sound output and then popping as it comes back on to play more sound.

I downloaded and installed the latest Alsa PPA and rebooted, but no luck.

---

### Post by jared2 on 2013-08-08
Still having the popping sound from the card. Any ideas I can try?

---

### Post by Yellow Pasque on 2013-08-08
Some notes on hda debugging for the ALSA devs:
> Power-Saving
~~~~~~~~~~~~
The power-saving is a kind of auto-suspend of the device.  When the
device is inactive for a certain time, the device is automatically
turned off to save the power.  The time to go down is specified via
`power_save` module option, and this option can be changed dynamically
via sysfs.

The power-saving won't work when the analog loopback is enabled on
some codecs.  Make sure that you mute all unneeded signal routes when
you want the power-saving.

The power-saving feature might cause audible click noises at each
power-down/up depending on the device.  Some of them might be
solvable, but some are hard, I'm afraid.  Some distros such as
openSUSE enables the power-saving feature automatically when the power
cable is unplugged.  [B]Thus, if you hear noises, suspect first the
power-saving. [/B] See /sys/module/snd_hda_intel/parameters/power_save to
check the current value.  If it's non-zero, the feature is turned on.


Notes on Power-Saving Mode
==========================

AC97 and HD-audio drivers have the automatic power-saving mode.
This feature is enabled via Kconfig CONFIG_SND_AC97_POWER_SAVE
and CONFIG_SND_HDA_POWER_SAVE options, respectively.

With the automatic power-saving, the driver turns off the codec power
appropriately when no operation is required.  When no applications use
the device and/or no analog loopback is set, the power disablement is
done fully or partially.  It'll save a certain power consumption, thus
good for laptops (even for desktops).

The time-out for automatic power-off can be specified via power_save
module option of snd-ac97-codec and snd-hda-intel modules.  Specify
the time-out value in seconds.  0 means to disable the automatic
power-saving.  The default value of timeout is given via
CONFIG_SND_AC97_POWER_SAVE_DEFAULT and
CONFIG_SND_HDA_POWER_SAVE_DEFAULT Kconfig options.  Setting this to 1
(the minimum value) isn't recommended because many applications try to
reopen the device frequently.  10 would be a good choice for normal
operations.

The power_save option is exported as writable.  This means you can
adjust the value via sysfs on the fly.  For example, to turn on the
automatic power-save mode with 10 seconds, write to
/sys/modules/snd_ac97_codec/parameters/power_save (usually as root):

	# echo 10 > /sys/modules/snd_ac97_codec/parameters/power_save


Note that you might hear click noise/pop when changing the power
state.  Also, it often takes certain time to wake up from the
power-down to the active state.  These are often hardly to fix, so
don't report extra bug reports unless you have a fix patch ;-)

For HD-audio interface, there is another module option,
power_save_controller.  This enables/disables the power-save mode of
the controller side.  Setting this on may reduce a bit more power
consumption, but might result in longer wake-up time and click noise.
Try to turn it off when you experience such a thing too often.


---

### Post by swordsmith on 2013-09-25
@Jared,

I'm getting the exact same problem too, and there doesn't seem to be any good solution.
I'm dual booting ArchLinux and Win 8. When I first installed Arch, there was only slight popping sound when I change the volume, and during booting on/off. Today the constant whine would start as soon as X11 is started, add on battery. After plugging the power, changing the volumn in alsamixer would stop the whine.

Have you found a fix to this? Having a new laptop is kinda stupid when it has to be plugged in all the time...

---

### Post by swordsmith on 2013-09-25
Oh, I forgot to mention that, if you do "modprobe snd_hda_intel" or blacklist "snd_hda_intel" in modprobe.d/modprobe.conf, the sound goes away, but you also don't have any sound anymore...

---

### Post by swordsmith on 2013-09-25
Oh, I forgot to mention that, if you do "modprobe snd_hda_intel" or blacklist "snd_hda_intel" in modprobe.d/modprobe.conf, the sound goes away, but you also don't have any sound anymore...

---

### Post by swordsmith on 2013-09-25
Alright, I finally found a solution!
Indeed, this problem is due to the "power_save" option of the snd_hda_intel module. However, I was really confused because I've tried to set "option snd-hda-intel power_save=0" in all permutations of {/etc/modprobe.d/snd-hda-intel.conf, /etc/modprobe.d/modprobe.conf, /etc/modprobe.d/local.conf}, yet every time I reboot, the BEEPING would start and the power_save value would become 1, even though it was 0 before starting X.

Turns out it was the pm-utils' fault, as shown in this post ([http://www.foxswap.com/computers-and-technology/ubuntu-12-04-clicking-sound-from-speakers/](http://www.foxswap.com/computers-and-technology/ubuntu-12-04-clicking-sound-from-speakers/))
Whew!

---

### Post by swordsmith on 2013-09-25
Alright, I finally found a solution!
Indeed, this problem is due to the "power_save" option of the snd_hda_intel module. However, I was really confused because I've tried to set "option snd-hda-intel power_save=0" in all permutations of {/etc/modprobe.d/snd-hda-intel.conf, /etc/modprobe.d/modprobe.conf, /etc/modprobe.d/local.conf}, yet every time I reboot, the BEEPING would start and the power_save value would become 1, even though it was 0 before starting X.

Turns out it was the pm-utils' fault, as shown in this post ([http://www.foxswap.com/computers-and-technology/ubuntu-12-04-clicking-sound-from-speakers/](http://www.foxswap.com/computers-and-technology/ubuntu-12-04-clicking-sound-from-speakers/))
Whew!

---

