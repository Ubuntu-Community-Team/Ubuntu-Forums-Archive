---
title: "No Sound after install"
date: 2022-06-20
forum: Hardware
---

### Post by Cushie on 2022-06-20
I have a sound problem and wonder if there is a possible fix? I have seen several leads but nothing solved.
I have installed a new Huawei Matebook with an up to date 22.04 dual boot, all installed well but have no speaker or mike input/output. 
   Intel Core i5 11th Generation, 
   iRis XE graphics 
   Intel Tiger Lake  Smart Sound, 
but nothing smart or working. 
Output Device in settings  is "Dummy Output" , Microphone is all blank.
Under 'hardinfo' no speaker or microphone is listed under Input devices .
           Kernel Modules of interest ? :-
             soundwire_intel	Intel Soundwire Link Driver
             soundwire_generic_allocation	SoundWire Generic Bandwidth Allocation
            snd_soc_acpi	ALSA SoC ACPI module
            PCI Devices   Multimedia audio controller	Intel Corporation Tiger Lake-LP Smart  
              Sound Technology Audio Controller (rev 20)
            soundwire_bus	SoundWire bus
            snd_soc_core	ALSA SoC Core
            snd_compress	ALSA Compressed offload framework
What can I do to connect or switch ton hese devices? i would appreciate any help.

---

### Post by gdesilva on 2022-06-21
Worth checking out the solution here on Archlinux forum [https://bbs.archlinux.org/viewtopic.php?id=260139](https://bbs.archlinux.org/viewtopic.php?id=260139)

---

### Post by mIk3_08 on 2022-06-21
> **Cushie said:**
> I have a sound problem and wonder if there is a possible fix? I have seen several leads but nothing solved.
I have installed a new Huawei Matebook with an up to date 22.04 dual boot, all installed well but have no speaker or mike input/output. 
   Intel Core i5 11th Generation, 
   iRis XE graphics 
   Intel Tiger Lake  Smart Sound, 
but nothing smart or working. 
Output Device in settings  is "Dummy Output" , Microphone is all blank.
Under 'hardinfo' no speaker or microphone is listed under Input devices .
           Kernel Modules of interest ? :-
             soundwire_intel    Intel Soundwire Link Driver
             soundwire_generic_allocation    SoundWire Generic Bandwidth Allocation
            snd_soc_acpi    ALSA SoC ACPI module
            PCI Devices   Multimedia audio controller    Intel Corporation Tiger Lake-LP Smart  
              Sound Technology Audio Controller (rev 20)
            soundwire_bus    SoundWire bus
            snd_soc_core    ALSA SoC Core
            snd_compress    ALSA Compressed offload framework
What can I do to connect or switch ton hese devices? i would appreciate any help.
Its better to run this command below so the community know the exact and complete info of your system and post the information or pastebin link in this thread. Regards and cheers.```
https://github.com/UbuntuForums/system-info
```

---

