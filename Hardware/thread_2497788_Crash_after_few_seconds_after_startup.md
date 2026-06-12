---
title: "Crash after few seconds after startup"
date: 2024-05-17
forum: Hardware
---

### Post by mr-blackkrab on 2024-05-17
Hi. I have strange issue with ubuntu 24.04 - when startup (when i already see desktop) after 3-5 seconds ubuntu crash. Monitor become black, OS stop responding (test it via blind terminal commands typing) but CPU cooler still working. So i need to manually shut it down by hold power button.
Problem was starting when i move from discrete graphic card (GTX 1060) to integrated. With discrete was similar problem when i tried to use nvidia drivers.

Hardware:
msi b350 tomahawk arctic white
Ryzen 3 2200G
Kingston A2000 1TB NVMe M.2 SSD
DDR3 RAM 16GB.
-
During solution searching i already update bios to latest version - but it not help. Found, that with "nomodeset" parameter os can run and don't crash.
Also try to install clean 22.04 version. But during installation process, after few seconds after installation begin, i have same behaviour like in main OS.
I may assume, that drivers for amdgpu was loaded, because desktop has 1920x1080 resolution (opposite to 800x600 with nomodeset) during installation process.

---

### Post by currentshaft on 2024-05-17
After the crash, you can press Control-Alt-F1 through F7 to get a non-GUI login prompt to the system. Log in with your username and password, you'll get a terminal prompt, use it to check /var/log for any indications of what is crashing.

---

### Post by mr-blackkrab on 2024-05-18
OS completely freeze when crash, so i can't do anything except reboot system by hold power button. But i can check logs in recovery mode.
Here is syslog when system crash (from moment of startup to crash)
Important! - end of sysloglog look exactly like below, with cutted last message
```

2024-05-18T10:44:45.525834+03:00 MediaCenter systemd-modules-load[316]: Inserted module 'lp'
2024-05-18T10:44:45.525985+03:00 MediaCenter kernel: Linux version 6.8.0-31-generic (buildd@lcy02-amd64-080) (x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-23ubuntu4) 13.2.0, GNU ld (GNU Binutils for Ubuntu) 2.42) #31-Ubuntu SMP PREEMPT_DYNAMIC Sat Apr 20 00:40:06 UTC 2024 (Ubuntu 6.8.0-31.31-generic 6.8.1)
2024-05-18T10:44:45.526051+03:00 MediaCenter kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-6.8.0-31-generic root=UUID=9a122790-ba31-457b-b044-8285a0f6d47a ro quiet splash vt.handoff=7
2024-05-18T10:44:45.526053+03:00 MediaCenter kernel: KERNEL supported cpus:
2024-05-18T10:44:45.526054+03:00 MediaCenter kernel:   Intel GenuineIntel
2024-05-18T10:44:45.526054+03:00 MediaCenter kernel:   AMD AuthenticAMD
2024-05-18T10:44:45.526055+03:00 MediaCenter kernel:   Hygon HygonGenuine
2024-05-18T10:44:45.526029+03:00 MediaCenter systemd-modules-load[316]: Inserted module 'ppdev'
2024-05-18T10:44:45.526056+03:00 MediaCenter kernel:   Centaur CentaurHauls
2024-05-18T10:44:45.526058+03:00 MediaCenter kernel:   zhaoxin   Shanghai  
2024-05-18T10:44:45.526059+03:00 MediaCenter kernel: BIOS-provided physical RAM map:
2024-05-18T10:44:45.526059+03:00 MediaCenter kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009ffff] usable
2024-05-18T10:44:45.526060+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000000000a0000-0x00000000000fffff] reserved
2024-05-18T10:44:45.526060+03:00 MediaCenter kernel: BIOS-e820: [mem 0x0000000000100000-0x0000000009d7ffff] usable
2024-05-18T10:44:45.526061+03:00 MediaCenter kernel: BIOS-e820: [mem 0x0000000009d80000-0x0000000009ffffff] reserved
2024-05-18T10:44:45.526059+03:00 MediaCenter systemd[1]: Mounted snap-bare-5.mount - Mount unit for bare, revision 5.
2024-05-18T10:44:45.526063+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000000a000000-0x000000000a1fffff] usable
2024-05-18T10:44:45.526063+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000000a200000-0x000000000a209fff] ACPI NVS
2024-05-18T10:44:45.526064+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000000a20a000-0x000000000affffff] usable
2024-05-18T10:44:45.526065+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000000b000000-0x000000000b01ffff] reserved
2024-05-18T10:44:45.526063+03:00 MediaCenter systemd[1]: Mounted snap-core22-1380.mount - Mount unit for core22, revision 1380.
2024-05-18T10:44:45.526066+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000000b020000-0x000000005d0f2fff] usable
2024-05-18T10:44:45.526066+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000005d0f3000-0x000000005d1e3fff] reserved
2024-05-18T10:44:45.526067+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000005d1e4000-0x000000005d260fff] ACPI data
2024-05-18T10:44:45.526067+03:00 MediaCenter systemd[1]: Mounted snap-firefox-4173.mount - Mount unit for firefox, revision 4173.
2024-05-18T10:44:45.526070+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000005d261000-0x000000005d768fff] ACPI NVS
2024-05-18T10:44:45.526070+03:00 MediaCenter systemd[1]: Mounted snap-firmware\x2dupdater-127.mount - Mount unit for firmware-updater, revision 127.
2024-05-18T10:44:45.526071+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000005d769000-0x000000005e661fff] reserved
2024-05-18T10:44:45.526072+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000

```

and here kern.log

```
2024-05-18T10:44:45.525985+03:00 MediaCenter kernel: Linux version 6.8.0-31-generic (buildd@lcy02-amd64-080) (x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-23ubuntu4) 13.2.0, GNU ld (GNU Binutils for Ubuntu) 2.42) #31-Ubuntu SMP PREEMPT_DYNAMIC Sat Apr 20 00:40:06 UTC 2024 (Ubuntu 6.8.0-31.31-generic 6.8.1)
2024-05-18T10:44:45.526051+03:00 MediaCenter kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-6.8.0-31-generic root=UUID=9a122790-ba31-457b-b044-8285a0f6d47a ro quiet splash vt.handoff=7
2024-05-18T10:44:45.526053+03:00 MediaCenter kernel: KERNEL supported cpus:
2024-05-18T10:44:45.526054+03:00 MediaCenter kernel:   Intel GenuineIntel
2024-05-18T10:44:45.526054+03:00 MediaCenter kernel:   AMD AuthenticAMD
2024-05-18T10:44:45.526055+03:00 MediaCenter kernel:   Hygon HygonGenuine
2024-05-18T10:44:45.526056+03:00 MediaCenter kernel:   Centaur CentaurHauls
2024-05-18T10:44:45.526058+03:00 MediaCenter kernel:   zhaoxin   Shanghai  
2024-05-18T10:44:45.526059+03:00 MediaCenter kernel: BIOS-provided physical RAM map:
2024-05-18T10:44:45.526059+03:00 MediaCenter kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009ffff] usable
2024-05-18T10:44:45.526060+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000000000a0000-0x00000000000fffff] reserved
2024-05-18T10:44:45.526060+03:00 MediaCenter kernel: BIOS-e820: [mem 0x0000000000100000-0x0000000009d7ffff] usable
2024-05-18T10:44:45.526061+03:00 MediaCenter kernel: BIOS-e820: [mem 0x0000000009d80000-0x0000000009ffffff] reserved
2024-05-18T10:44:45.526063+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000000a000000-0x000000000a1fffff] usable
2024-05-18T10:44:45.526063+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000000a200000-0x000000000a209fff] ACPI NVS
2024-05-18T10:44:45.526064+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000000a20a000-0x000000000affffff] usable
2024-05-18T10:44:45.526065+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000000b000000-0x000000000b01ffff] reserved
2024-05-18T10:44:45.526066+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000000b020000-0x000000005d0f2fff] usable
2024-05-18T10:44:45.526066+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000005d0f3000-0x000000005d1e3fff] reserved
2024-05-18T10:44:45.526067+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000005d1e4000-0x000000005d260fff] ACPI data
2024-05-18T10:44:45.526070+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000005d261000-0x000000005d768fff] ACPI NVS
2024-05-18T10:44:45.526071+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000005d769000-0x000000005e661fff] reserved
2024-05-18T10:44:45.526072+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000005e662000-0x000000005effffff] usable
2024-05-18T10:44:45.526073+03:00 MediaCenter kernel: BIOS-e820: [mem 0x000000005f000000-0x00000000dfffffff] reserved
2024-05-18T10:44:45.526074+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
2024-05-18T10:44:45.526074+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000000fd100000-0x00000000fdffffff] reserved
2024-05-18T10:44:45.526076+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000000fea00000-0x00000000fea0ffff] reserved
2024-05-18T10:44:45.526077+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000000feb80000-0x00000000fec01fff] reserved
2024-05-18T10:44:45.526078+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
2024-05-18T10:44:45.526079+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000000fec30000-0x00000000fec30fff] reserved
2024-05-18T10:44:45.526079+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
2024-05-18T10:44:45.526080+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000000fed40000-0x00000000fed44fff] reserved
2024-05-18T10:44:45.526081+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
2024-05-18T10:44:45.526082+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000000fedc2000-0x00000000fedcffff] reserved
2024-05-18T10:44:45.526083+03:00 MediaCenter kernel: BIOS-e820: [mem 0x00000000
```

---

### Post by MAFoElffen on 2024-05-18
Please run the UbuntuForums 'system-info' Script in my signature line to show us what you have and what drivers it is using. Please post the URL of where it uploads to. (There is a sticky on that script in this section.)

To try booting. at the grub2 menu, press the <E> key to enter the edit mode > go to the line that starts with "linux", and alternately replace the words "quiet splash" with "nomodeset" or "3"...

---

### Post by mr-blackkrab on 2024-05-19
Here is result of system-info
[https://paste.ubuntu.com/p/dzVp6hSSvy/](https://paste.ubuntu.com/p/dzVp6hSSvy/)

---

### Post by MAFoElffen on 2024-05-19
Your video driver is not loading:
```

---------- Video Details from 'lshw':

  *-display UNCLAIMED
       description: VGA compatible controller
       product: Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:38:00.0
       version: c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
       configuration: latency=0
       resources: 
           memory:e0000000-efffffff 
           memory:f0000000-f01fffff 
           ioport:e000(size=256) 
           memory:fe500000-fe57ffff
  *-graphics
       product: simpledrmdrmfb
       physical id: 1
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=1024,768

```
Then AMD iGPU in your CPU is going Unclaimed. I don't see your nVidia GTX 1650... Did you have it pulled during that report?

---

### Post by mr-blackkrab on 2024-05-20
1060 is not connected. I want to use my PC only with integrated graphic card.
Not loaded amd drivers - i think reason is "nomodeset" parameter. Without this parameter OS crash after few seconds

---

### Post by MAFoElffen on 2024-05-20
Try this... At the Grub2 Menu > Edit > boot line... Instead of using "nomodeset"... add this:
```

radeon.si_support=0 amdgpu.si_support=1 radeon.cik_support=0 amdgpu.cik_support=1

```
Tell me if that works...

---

### Post by Crafty Kisses on 2024-05-22
Look at the system logs around the time of the crash for any suspicious entries. Check: ```
/var/log/syslog
``` Secondarily use the following command: ```
journalctl 
``` 

Then check:

```
sudo tail -n 100 /var/log/syslog
sudo journalctl -xe
```

I'd also rerun: 

```
dmesg | less
tail -n 100 /var/log/kern.log
```

It does seem like this is a video driver issue though.

---

### Post by mr-blackkrab on 2024-05-26
Thanks all for the help. While searching for solutions, I realized what the problem was. I had bad CPU cooling, so when using the iGPU, the CPU would overheat almost instantly and shut down the PC. After replacing the cooling system with a new one, the problem is solved.

---

