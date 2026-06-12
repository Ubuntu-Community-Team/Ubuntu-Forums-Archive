---
title: "Audio does not work neither in feisty nor edgy"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by kitts_82 on 2007-04-21
I just bought a new Laptop (HP tx1003), installed feisty and discovered that sound does not work. I have read a lot of recent posts relating to this but all deal with regression. I tried edgy and sound does not work over there either.

The funny thing is the feisty thinks that sound is working. From software point of view everything works, Amarok plays but there is no audio output. The only sound i have heard is the system beep when using konsole.

The laptop has a light for the mute and it glows in red (blue means its working). Here are some relevant information:

```

$ dmesg | grep codec
[   20.936000] hda_codec: Unknown model for ALC660VD/ALC861VD, trying auto-probe from BIOS...
$ sudo lspci -v | grep -i -A 5 audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at d7000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xd7000000 irq 21
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).

```

Does anyone have a solution for this? This is what alsamixer report:

```
Card: HDA NVidia                                                                                                                            &#9474;
&#9474; Chip: Realtek ALC861-VD                                                                                                                     &#9474;
&#9474; View: [Playback] Capture  All                                                                                                               &#9474;
&#9474; Item: PCM [dB gain=-51.00, -51.00]
```

---

### Post by kitts_82 on 2007-04-23
Ok... Not the solution i would like but at least sound is now working. I installed the OSS 4.0 deb.

Sound works it is not a nice experience.. kmix does not work.. festival does not play sound.. At least amarok works. So  i can play some music while I research further! :-D

---

### Post by anil_chin on 2007-11-17
hi can you tell me the solution to the problem, i have a Gateway 4530gz, which is similar to most gateway 4000 series laptops. I am unable to listen to sound in it

---

