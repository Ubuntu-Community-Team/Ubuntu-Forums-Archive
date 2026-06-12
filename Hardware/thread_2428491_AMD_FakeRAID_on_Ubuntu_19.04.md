---
title: "AMD FakeRAID on Ubuntu 19.04"
date: 2019-10-04
forum: Hardware
---

### Post by drraythe2nd on 2019-10-04
I have been running Ubunu 19.04 for about 3 months now on my ASRock B450M-HDV R4.0 motherboard with a Ryzen 3 1200, and I have been running various versions of ubuntu for the last 2 years before then, and Debian before that, though on different computers. Recently, I was donated two 1TB hard drives. I prompty used mdadm to create a Linux software RAID0 setup for a total of 2TB continuous storage. However, I have decided I want to be able to have this storage accessable from both Windows 10 and Ubuntu. I moved all of my files onto another, much slower 160GB hard drive for storage while I make the transition, and proceeded to switch the SATA mode from RAID to AHCI. Immediatly, neither Ubuntu nor Windows would boot, which I expected. I switched it back over to AHCI and booted into Ubuntu in order to install whatever drivers/kernel modules might be needed. However, **even after an extensive search, ****I could not find a solution to my problem.** My problem is this: I cannot boot into Ubuntu 19.04 when my SATA mode is set RAID. I need drivers/kernel modules that would allow Ubuntu to boot and recognize all connected drives. Here are the details of my setup: I have a Ryzen 3 1200 overclocked to 3.9 GHz at 1.38v running on an ASRock B450M-HDV R4.0 motherboard with one 8GB stick of DDR4-2400 memory. My graphics card is a MSI Areo ITX Radeon RX 560 4GB, for which I have installed zero drivers manually (though this should be irrelevant). Finally, the drives. I have one 240GB Silicon Power SATA 6Gb/s SSD which has both Ubuntu 19.04 and Windows 10 build 1903. Both are allocated approximately 100GB of storage space. There is also some swap space on the SSD (should also be irrelevant). Next I have a SATA 3Gb/s Western Digital 160GB 5400 RPM hard drive which stores the files I will be transferring after this problem is solved. Finally, I have two generic 1TB 5400 RPM SATA 6Gb/s hard drives, one 2.5" drive, and one 3.5" drive. These final two are the drives I want to add together in a RAID0 array. I am connected to the internet over Ethernet and I often get more than 100Mb/s, so downloading large files shouldn't be a problem.

Steps to reproduce:
1. Switch SATA mode in BIOS to RAID (no need to make an array; it will still fail)
2. Try to boot Ubuntu. It will fail at:
        Begin: Loading essential drivers ... done.
        Begin: Running /scripts/init-premount ... done.
        Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
        Begin: Running /scripts/local-premount ...
        [some unrelated text concerning USB mice and keyboards]
        Begin: Waiting for suspend/resume device ... Begin: Running /scripts/local-block ... done.
        done.
        Gave up waiting for suspend/resume device
        done.
        Begin: Waiting for root file system ... Begin: Running /scripts/local-block ... done.
        done.
        Gave up waiting for root file system device. Common problems:
         - Boot args (cat /proc/cmdline)
           - Check rootdelay= (did the system wait long enough?)
         - Missing modules (cat /proc/modules; ls /dev)
        ALERT! UUID=[I'm too lazy to type it out]

Here is /proc/cmdline:
        BOOT_IMAGE=/boot/vmlinuz-5.0.0-31-generic root=UUID=[the same UUID as before] ro

Here is /proc/modules:
        [three concerning USB]
        dm_mirror [more stuff] Live [long hexadecimal]
        dm_region_hash [more stuff] Live [long hexadecimal]
        dm_log [more stuff] Live [long hexadecemal]
        [B]ahci 40960 0 - Live 0xffffffffc0160000
[/B]        [B]libahci 32768 1 ahci, Live 0xffffffffc0154000
[/B]        i2c_piix4 [more stuff] Live [long hexadecimal]
        [two more concerning USB]
        wmi [more stuff] Live [long hexadecimal]
        gpio_amdpt [more stuff] Live [long hexadecimal]
        gpio_generic [more stuff] Live [long hexadecimal]

Here is /dev:
        vga_arbiter rfkill mem null port zero full random urandom kmsg tty console tty[0-63] vcs vcsu vcsa vcs[1-6] vcsu[1-6] vcsa[1-6] snapshot encryptfs fuse gpiochip0 fb0 ptmx ttyS[0-31] ttyprintk hpet hwrng lightnvm loop-control loop[0-7] udmabuf net ppp bus input psaux uinput rtc0 mapper mcelog cpu cpu_dma_latency network_latency network_throughput memory_bandwidth pts core fd stdin stdout stderr char gpiochip1 i2c-[0-3] rtc block hidraw[0-2]

I have already tried:
 - Updating BIOS (I'm on 3.20, which is the latest reccomeneded BIOS for this motherboard)
 - Installing dmraid (did nothing)
 - Adding a script to start dmraid into /script/init-premount
 - Seeing if the Ubuntu live USB could detect any drive [B](It detected none except itself)
[/B] - After all this I went back to AHCI mode and Ubuntu booted normally

If anyone knows a solution to this problem, help would be greatly appreciated.

Thanks in advance,
                Michael

---

