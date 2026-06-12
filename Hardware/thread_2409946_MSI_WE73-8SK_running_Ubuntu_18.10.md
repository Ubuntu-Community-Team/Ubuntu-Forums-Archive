---
title: "MSI WE73-8SK running Ubuntu 18.10"
date: 2019-01-09
forum: Hardware
---

### Post by Stilor on 2019-01-09
Hi,

I am setting up MSI WE73-8SK to dual-boot Windows 10 and KUbuntu 18.10. This post captures some issues I ran into while installing (which, hopefully, would save some time to others); I also have some questions - I'd appreciate if anyone could give me any pointers. Starting with questions:

1. Is it possible to make the modifications to PulseAudio files in /usr/share permanent? The workaround I had to apply (see below), as far as I understand, may get overwritten when a new version of PulseAudio is installed. Or maybe there is a better solution?

2. iwlwifi module occasionally fails to load with:
```

[    6.272255] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0x3, CPU2 Status: 0x240f
[    6.272257] iwlwifi 0000:00:14.3: Failed to start INIT ucode: -110
[    6.284419] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110

```

I have seen it twice out of 20-30 reboots. Not often, but still annoying. I noticed that this issue is reported many times, not just against MSI laptops. "-110" is ETIMEDOUT. Is it related to SecureBoot?

Now some notes on the installation:

1. The installer hangs unless `nomodeset` is added to the command line. Enabling the checkboxes for both "Install 3rd party drivers" and "Enable secure boot" allows the laptop to boot into the newly installed OS. Without "enable secure boot", the machine hangs when logging in to SDM even if proprietary NVidia drivers are installed (unless, again, `nomodeset` is supplied).

2. Enabling "Secure boot" after the initial installation did not work for me: the dialog to enter the new MOK ("machine owner key") did not appear. I saw "update-secureboot-policy" process running and eating CPU time - but it never presented any window in the GUI. 

3. Audio didn't work properly out of the box; the laptop suffers from the same issue as described in [https://wiki.archlinux.org/index.php/MSI_GE63VR#Audio](https://wiki.archlinux.org/index.php/MSI_GE63VR#Audio) - except it is the exact opposite :) On this laptop, the "Headphone" channel controls the volume to both the internal speakers and the headphone jack; therefore the fix is to edit `/usr/share/pulseaudio/alsa-mixer/paths/analog-output-speaker.conf` and replace the "Element Headphone" section with
```

[Element Headphone]                                                                                                                                                      
switch = off
volume = merge

```

I tried playing with `hdajackretask` to make both channels ("Speaker" and "Headphone") controllable separately by PulseAudio but didn't succeed. If anyone knows the recipe - or knows how to make the edits to the `/usr/share/pulseaudio/alsa-mixer/paths/analog-output-speaker.conf` permanent - I'd appreciate the pointers.

---

