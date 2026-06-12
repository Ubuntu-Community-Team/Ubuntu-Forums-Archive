---
title: "No sound after upgrading from 18.04 LTS to 20.04 LTS"
date: 2020-05-04
forum: Hardware
---

### Post by sla-sz on 2020-05-04
I didn&#8217;t wait for the stable version of Ubuntu 20.04 LTS and upgraded my 18.04 LTS version using this command
```

[SIZE=1]update-manager -c -d
[/SIZE]
```
I was aware I was doing an upgrade to developer version, anyway I decided to upgrade my OS.
The upgrade had ended, I didn&#8217;t notice any crucial things during the process.
The new system has one failure, there is no sound after booting, the only option for sound setting is a &#8220;dummy output&#8221;.
A temporary solution for this exists, I just need to execute this command: (I&#8217;ve found it in [https://bugs.launchpad.net/ubuntu/+source/linux-oem-osp1/+bug/1864061/comments/58](https://bugs.launchpad.net/ubuntu/+source/linux-oem-osp1/+bug/1864061/comments/58))
```

[SIZE=1]pulseaudio -k && sudo alsa force-reload
[/SIZE]
```
After executing this command the sound is working for a whole session.
My question is:
Is there any stable solution for my problem or should I wait for the stable version of 20.04 which supposedly will be released in July this year?

(5.4.0-29-generic, x86_64, Dell n5040)
```

[SIZE=1]    ... :~$ lspci -vvv | grep -A8 Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Dell 5 Series/3400 Series Chipset High Definition Audio
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 31
    Region 0: Memory at fbf00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel[/SIZE]

```
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

While executing the command:
```

[SIZE=1]pulseaudio -k && sudo alsa force-reload
[/SIZE]
```
I noticed that one process that was to be restarted was blocked by ```

timidity

```.
Then I decided to uninstall ```
timidity
``` and ```
timidity-daemon
```.
Sound in speakers of my laptop appeared immediately after uninstalling the two apps.
Sound works also after a reboot.
However speaker testing doesn't work for me.

---

