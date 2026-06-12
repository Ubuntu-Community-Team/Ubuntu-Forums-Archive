---
title: "&quot;sudo make&quot; Problem when trying to install driver on laptop"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by simpsonsfreak on 2007-12-06
Hi everyone,
I'm completely new to this compiling thing. I am following the instructions to configure the audio card to work with an Acer Aspire 4310 ([http://ubuntuforums.org/showthread.php?t=542264](http://ubuntuforums.org/showthread.php?t=542264)) and I'm stuck.  Here are the instructions:

> 2. Realtek 268 Intel HDA Chipset ALSA Patch:
(shamelessly copied from user venky80 from [https://bugs.launchpad.net/ubuntu/+s...22/+bug/116326](https://bugs.launchpad.net/ubuntu/+s...22/+bug/116326))
1)Download alsa-drivers, alsa-firware, alsa-lib, alsa-util version 1.0.14 from ALSA.org and extract it into a directory named ALSA in desktop or your home
2) Replace patch_realtek.c and hda_proc.c in the ~ALSA/alsa-driver-1.0.14/alsa-kernel/pci/hda with the new files from [http://launchpadlibrarian.net/855257...arch_files.zip](http://launchpadlibrarian.net/855257...arch_files.zip)
3) Then do sudo ./configure sudo make and sudo make install in the following folders according to the order specified (order is important) ALSA lib , ALSA utils ALSA firmware and lastly ALSA drivers.
hopefully you will see no errors.
4) restart


Everything has been fine until I type "sudo make" for ALSA drivers (the last one). This is the error I get:

/home/hayden/Desktop/ALSA/alsa-driver-1.0.15/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function &#8216;alc662_mux_enum_put&#8217;:
/home/hayden/Desktop/ALSA/alsa-driver-1.0.15/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:10546: error: &#8216;struct hda_codec&#8217; has no member named &#8216;in_resume&#8217;
make[4]: *** [/home/hayden/Desktop/ALSA/alsa-driver-1.0.15/pci/hda/patch_realtek.o] Error 1
make[3]: *** [/home/hayden/Desktop/ALSA/alsa-driver-1.0.15/pci/hda] Error 2
make[2]: *** [/home/hayden/Desktop/ALSA/alsa-driver-1.0.15/pci] Error 2
make[1]: *** [_module_/home/hayden/Desktop/ALSA/alsa-driver-1.0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2


I have no idea what this error is... can someone please help me figure out how to get this working?

All help is much appreciated :)

edit: BTW, Instead of using the 1.0.14 ALSA packages, i used the 1.0.15 packages.

---

### Post by daviddehoog on 2007-12-06
Hi simpsonsfreak

It sounds as though the alsa-util version 1.0.15 code isn't as complete as the alsa-util version 1.0.14 code. The error that make returned indicates that there are errors in the code that need to be fixed.

I'd suggest that you download the alsa-util version 1.0.14 package, and have another go. All should be well.

Cheers
David

---

### Post by Yellow Pasque on 2007-12-06
> It sounds as though the alsa-util version 1.0.15 code isn't as complete as the alsa-util version 1.0.14 code. The error that make returned indicates that there are errors in the code that need to be fixed.

I'd suggest that you download the alsa-util version 1.0.14 package, and have another go. All should be well.

I'm going to disagree. The error is in the patch code, not the ALSA code.
```
**patch_realtek.c:10546: error**: &#8216;struct hda_codec&#8217; has no member named &#8216;in_resume&#8217;
```

---

