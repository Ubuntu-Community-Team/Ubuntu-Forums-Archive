---
title: "byt-rt5640 byt-rt5640: ASoC: CPU DAI baytrail-pcm-audio not registered - No Sound"
date: 2014-11-28
forum: Hardware
---

### Post by ronniepinsky on 2014-11-28
Edit:  Problem solved.  Apparently this was caused by a firmware mismatch or insufficient firmware files in /lib/firmware/intel . To be sure you are using the correct firmware, uninstall linux-firmware,  and be sure there is nothing remaining in /lib/firmware/intel.  Finally  copy the contents of the chromium repo (click tgz to download) to  /lib/firmware/intel.  You should see an audio device on next boot.

-----------

I am testing an Intel Bay Trail Tablet running Kernel 3.16.2 from the Ubuntu mainline PPA with linux-firmware installed and up to date.  I need this kernel or newer for working wireless.  I see this error in dmesg and sound is not working:

```
[URL="http://ubuntuforums.org/showthread.php?t=2254631"]
sst-acpi: cannot load firmware intel/fw_sst_0f28.bin-i2s_master[/URL]

```

The file that ships with ubuntu in the linux-firmware package is named "fw_sst_0f28.bin-48kHz_i2s_master" instead.  This is also the name of the file in the official linux firmware git tree: [http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/tree/intel/fw_sst_0f28.bin-48kHz_i2s_master](http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/tree/intel/fw_sst_0f28.bin-48kHz_i2s_master) .  This is another one with the original naming I found referenced on this forum: [https://chromium.googlesource.com/chromiumos/third_party/linux-firmware/+/refs/heads/stabilize-5339.B/intel/](https://chromium.googlesource.com/chromiumos/third_party/linux-firmware/+/refs/heads/stabilize-5339.B/intel/) .

I can either rename the original, rename the official, or use the Google version but they all result in the same error on the next boot.  Several instances of:

```

byt-rt5640 byt-rt5640: ASoC: CPU DAI baytrail-pcm-audio not registered

```

and also:

```

baytrail-pcm-audio baytrail-pcm-audio: ipc: error DSP boot timeout

```

This post on xda developers talks a little about what I am trying to do: [http://forum.xda-developers.com/showpost.php?p=56208354&postcount=370](http://forum.xda-developers.com/showpost.php?p=56208354&postcount=370)

Where can I go from here?

---

