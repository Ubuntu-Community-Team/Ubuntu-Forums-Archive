---
title: "Sound hardware"
date: 2008-07-25
forum: Hardware
---

### Post by ipadoug on 2008-07-25
Please, someone help me!

My notebook from HP was working well with the older versions of ubuntu. But the 8.04 one have the exact problem:

"The sound hardware have a strange sound, or like a radio bad sintonized, that with this i can´t listen to music or see some dvd videos. So, i´d like to uninstall the file of the hardware or reconfig it again to get it with a norma function. I remember that the older versions of ubuntu had the sound configured perfectly."

Thanks to the one that had the heart to help me!

Please, forgive my mistakes in english!!!!!!!!!!!!!

---

### Post by evets25 on 2008-07-25
If anyone is going to be able to help you, they'll need to know a few details, such as:

- What kind of laptop, exactly? (For instance, mine is a Lenovo Ideapad Y510. Yours would be an HP whatever whatever,)
- What kind of sound card do you have? (run lspci from a commandline, and give us the output.)
- What kernel version are you running? (run "uname -r" from commandline, and give us the output.)

Otherwise, we can't do anything besides give you tips for "sound cards in general." :) Your problem could be almost anything.

---

### Post by ipadoug on 2008-07-25
OK. I can´t do it now but later i will give you the information you need to help me. Thank You!

---

### Post by ipadoug on 2008-07-26
My laptop have the listed especifications:

- HP Pavilion dv6220
- Processador AMD Mobile Sempron 3500+ e cache L2 de 512 KB (1,8 GHz)
- SDRAM DDR2 512 MB (1 Dimm)
- nvidia GeForce Go 6150

My sound card, with the "lspci", show me this information:

"00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)

00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)"

My Kernel version show me this: 2.6.24-19-generic

I pray for this help you help me!!!

---

### Post by ipadoug on 2008-09-08
Now my sound is OK! Know how? I just dactivated my microphone sound, using the volume control. I did that with all drivers instaled on the laptop. NIVIA, ALSA, .... So, if anybody has the same problem, do this that it can help a lot!

Good day for everybody!

---

### Post by nr4g3d on 2008-09-08
Thanks ipadoug! I have an Acer 5920g and was trying to troubleshoot my audio. Disabling the microphone device did the trick :)

---

