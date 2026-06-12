---
title: "Lenova Ideapad Y530 sound configuration"
date: 2009-09-05
forum: Hardware
---

### Post by gibxam on 2009-09-05
Hello fellow ubunters, I'm trying to configure my soundcard and am having trouble this is the link to my chipset/information [http://www.alsa-project.org/db/?f=d7b21c0d8c7772b958a9983bd29ce132b704c241](http://www.alsa-project.org/db/?f=d7b21c0d8c7772b958a9983bd29ce132b704c241) I have gotten up to finding my module in the ALSA-Configuration.txt but now I cannot find my soundcards codec, perhaps I need to upgrade to a more recent or more stable driver? Please help, thank you.

---

### Post by gibxam on 2009-09-05
Just an update I have tried upgrading my drivers to:

Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Sep  4 2009 for kernel 2.6.28-15-generic (SMP).

while building the new drivers I recieved the following warning:

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

I'm going to go back to the troubleshooting page and see if my codec is present in the new driver. Thank you for any help.

---

### Post by santhinen on 2009-11-13
Hi,
I am using Lenovo Y530 and installed Ubuntu 9.10 on the day it was released. As you know there is problem with the sound, i.e the subwoofer does not work. For ubuntu 9.04 I followed Wyths method and installed new alsa package and it worked well. I tried the same with Ubuntu 9.10 and at the end of the installation and reboot, no sound cards are detected. I looked for solution in the forum but nothing worked. I tried changing the alsa package versions. First tried package with version number ending in 21, then 20 and 19... the problem persists... Did anyone else have this problem??
Please let me the know the solution for it. Thank you..

---

### Post by wroom on 2010-01-21
> **santhinen said:**
> Hi,
I am using Lenovo Y530 and installed Ubuntu 9.10 on the day it was released. As you know there is problem with the sound, i.e the subwoofer does not work. For ubuntu 9.04 I followed Wyths method and installed new alsa package and it worked well. I tried the same with Ubuntu 9.10 and at the end of the installation and reboot, no sound cards are detected. I looked for solution in the forum but nothing worked. I tried changing the alsa package versions. First tried package with version number ending in 21, then 20 and 19... the problem persists... Did anyone else have this problem??
Please let me the know the solution for it. Thank you..

This is quite strange fact about 9.04.

My wife got Y530 with disabled subwoofer and microphone. Here is a simple investigation.

First of all: 
```
#lspci -v | grep -i audio

00:1b.0 Audio device: Intel Corporation 82801I (**ICH9 **Family) HD Audio Controller (rev 03)
Subsystem: Lenovo Device 3a0d
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at a3d00000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel
```

And here is a link to [alsa wiki]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel").

As you could see - there is no support for intel ICH9 (HD audio ) chipsets.

---

### Post by wroom on 2010-01-21
Otherwise - the source code is written to support ICH9 chips.

We could see it in alsa-kernel/pci/hda/hda_intel.c file for alsa-1.0.22
```

MODULE_SUPPORTED_DEVICE("{{Intel, ICH6},"
			 "{Intel, ICH6M},"
			 "{Intel, ICH7},"
			 "{Intel, ESB2},"
			 "{Intel, ICH8},"
			 **"{Intel, ICH9},"**
			 "{Intel, ICH10},"
			 "{Intel, PCH},"
			 "{Intel, SCH},"
			 "{ATI, SB450},"
			 "{ATI, SB600},"
			 "{ATI, RS600},"
			 "{ATI, RS690},"
			 "{ATI, RS780},"
			 "{ATI, R600},"
			 "{ATI, RV630},"
			 "{ATI, RV610},"
			 "{ATI, RV670},"
			 "{ATI, RV635},"
			 "{ATI, RV620},"
			 "{ATI, RV770},"
			 "{VIA, VT8251},"
			 "{VIA, VT8237A},"
			 "{SiS, SIS966},"
			 "{ULI, M5461}}");
MODULE_DESCRIPTION("Intel HDA driver");

```

---

### Post by wroom on 2010-01-21
> **wroom said:**
> Otherwise - the source code is written to support ICH9 chips.

We could see it in alsa-kernel/pci/hda/hda_intel.c file for alsa-1.0.22
```

MODULE_SUPPORTED_DEVICE("{{Intel, ICH6},"
			 "{Intel, ICH6M},"
			 "{Intel, ICH7},"
			 "{Intel, ESB2},"
			 "{Intel, ICH8},"
			 **"{Intel, ICH9},"**
			 "{Intel, ICH10},"
			 "{Intel, PCH},"
			 "{Intel, SCH},"
			 "{ATI, SB450},"
			 "{ATI, SB600},"
			 "{ATI, RS600},"
			 "{ATI, RS690},"
			 "{ATI, RS780},"
			 "{ATI, R600},"
			 "{ATI, RV630},"
			 "{ATI, RV610},"
			 "{ATI, RV670},"
			 "{ATI, RV635},"
			 "{ATI, RV620},"
			 "{ATI, RV770},"
			 "{VIA, VT8251},"
			 "{VIA, VT8237A},"
			 "{SiS, SIS966},"
			 "{ULI, M5461}}");
MODULE_DESCRIPTION("Intel HDA driver");

```

of course there is a problem in hda_codec.c !

I will perform some tests with modified hda_codec.c from alsa1.0.22 to be sure at 100%. (when i get home ).

---

