---
title: "Help needed with write protection"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by DawieS on 2009-07-08
Hi guys,

This is my first post, I upgraded from Windows XP to Ubuntu 9.04 last week. First of all, I must say that I was pleasantly surprised!! Thanks to all the wonderful people out there for their great work!!!):P

The installation on my daughter's PC went without a glitch. However on my PC, I have the following minor issues:
- I have an old web-cam (Canyon CNR - WCAM43). From what I have read on various forums and groups, the best solution is to buy a Linux compatible web-cam, instead of wasting a lot of time, only to end up with a half-working old web-cam.
- I have a flat-bed scanner connected. From what I have read, it should be fairly easy to get it working 100%.
- The on-board sound (Gigabyte S-Series GA-MA69G-S3H) does not work. With XP I had to disable the front panel jack detection in the driver interface before it worked (probably a bug on the motherboard). I have searched the various forums and found a lot of good advice on how to achieve the same. So far I have done the following:
      - The boot configuration was adjusted to allow for sound de-bugging. Various de-bugging and information files were created.
      - When using Alsamixer, the headphone slider is stuck at 0% and will not go up, although it is green and not muted.
      - I now need to write the value "hp_detect = yes" into the following file:
/sys/class/sound/hwC0D3/hints
I tried 'sudo gedit' but it is unable to open the file. I tried another editor Kate, which opens the file but is unable to save, even with a different name. Kate however reports that the file location is the following:
/sys/devices/pci0000:00/0000:00:14.2/sound/card0/hwC0D3/hints

Wherever the file is, it seems that I do not have authorisation to write in that directory. I am now somewhat confused and stuck. If someone can point me in the right direction, it would be much appreciated !!
[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by earthpigg on 2009-07-08
i have seen others that, for their computer, 8.04 works fine on whereas 9.04 does not. this is *not* the way things *should* be, but nothing is perfect. try tossing an 8.04 live cd in, see how that works.

> - I now need to write the value "hp_detect = yes" into the following file:
/sys/class/sound/hwC0D3/hints

i google searched that file, and the only result i got was *this* thread.... where did you get that information from?

---

### Post by DawieS on 2009-07-10
Thanks for the reply.

I have booted up from the Ubuntu 9.04 Live CD and found that the /sys folder on the hard drive is empty. All folders and files in it only exists while Ubuntu is alive (probably for security reasons). 

I then had another look at the instructions in the Readme files that I have followed. It seems that I have skipped the second last step (having to to with the permission settings of the configuration files).

[i google searched that file, and the only result i got was *this* thread.... where did you get that information from?[/quote]

I have downloaded the following driver tar file from Realtek (the vendor of the on-board sound card) and uncompressed it. It contains the same sound drivers installed by Ubuntu 9.04 but also contains a number of Reame files:

LinuxPkg_5.12.tar.bz2

 The file-naming convention used in the instructions is slightly different from those Ubuntu use. I thus had to hunt for files with the file browser to verify success. I will compile a how-to for new users like me with the same problem.

More sound-related info at:  [http://www.alsa-project.org](http://www.alsa-project.org)

---

