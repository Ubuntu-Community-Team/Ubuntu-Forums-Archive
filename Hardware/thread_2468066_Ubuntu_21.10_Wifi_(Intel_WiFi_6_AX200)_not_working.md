---
title: "Ubuntu 21.10 Wifi (Intel WiFi 6 AX200) not working."
date: 2021-10-17
forum: Hardware
---

### Post by dayned892 on 2021-10-17
Hello, I'm using 21.10 (actually a beta from a few weeks ago, but it's been updated) and I cant get my wireless card working. Its an intel AX200. I believe that this should be supported on kernel 5.1+. My system can see it, for example 

```
lshw -C network
<ethernet device>
  *-network 
       description: Network controller 
       product: Wi-Fi 6 AX200 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       version: 1a 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list 
       configuration: driver=iwlwifi latency=0 
       resources: irq:24 memory:fc600000-fc603fff
```

And I can see it gets the firmware here:
```
dmesg | grep iwl
[    4.658835] iwlwifi 0000:04:00.0: enabling device (0000 -> 0002) 
[    4.666305] iwlwifi 0000:04:00.0: api flags index 2 larger than supported by driver 
[    4.666317] iwlwifi 0000:04:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 89.3.35.37 
[    4.666523] iwlwifi 0000:04:00.0: loaded firmware version 63.c04f3485.0 cc-a0-63.ucode op_mode iwlmvm 
[    4.826950] iwlwifi 0000:04:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
```

Any advice is appreciated, as my home internet runs at 1-2mbps on a good day, so I usually use a 5g hotspot to get a faster speed, but that requires wifi obviously.

When I open the wifi settings (which I have to search for, it doesn't exist when I open settings) it tells me that no wireless adapter has been detected.

---

### Post by dayned892 on 2021-10-17
To anyone finding this in the future, my issue was having fast-boot enabled in my windows partition. Turning this off fixed my problem.

---

### Post by johnfoss on 2022-01-26
Hey, I am running Kernel 5.13.0-27-generic with  Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340

I also had a lot of problems although windows fast-boot is turned off.

First of all, wifi disconnects a few time per day and firmware crashes with:
```
kernel: iwlwifi 0000:01:00.0: Microcode SW error detected. Restarting 0x0.
kernel: iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
kernel: iwlwifi 0000:01:00.0: Status: 0x00000040, count: 6
kernel: iwlwifi 0000:01:00.0: Loaded firmware version: 63.c04f3485.0 cc-a0-63.ucode....
```

Second when this firmware is loaded other wifi clients get reduced net speed, or even get kicked out.
Sometimes my router avm 7530 AX even crashed and I had to switch router wifi off and on again.


WORKAROUND:
last but not least I just renamed firmware, so older version gets loaded:
```
sudo mv /lib/firmware/iwlwifi-cc-a0-62.ucode /lib/firmware/iwlwifi-cc-a0-62.ucode.orig
sudo mv /lib/firmware/iwlwifi-cc-a0-63.ucode /lib/firmware/iwlwifi-cc-a0-63.ucode.orig

```

now on firmware version 59.601f3a66.0 cc-a0-59.ucode everything is fine again:
```
sudo dmesg | grep iwlwifi
[    7.628554] iwlwifi 0000:01:00.0: enabling device (0000 -> 0002)
[    7.656957] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-cc-a0-63.ucode failed with error -2
[    7.670199] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-cc-a0-62.ucode failed with error -2
[    7.670334] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-cc-a0-61.ucode failed with error -2
[    7.670461] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-cc-a0-60.ucode failed with error -2
[    7.673647] iwlwifi 0000:01:00.0: api flags index 2 larger than supported by driver
[    7.673663] iwlwifi 0000:01:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 89.3.35.22
[    7.673894] iwlwifi 0000:01:00.0: loaded firmware version 59.601f3a66.0 cc-a0-59.ucode op_mode iwlmvm
[    7.792215] iwlwifi 0000:01:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[    8.024612] iwlwifi 0000:01:00.0: base HW address: a8:7e:ea:35:2c:99
[    8.042705] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[   11.774193] iwlwifi 0000:01:00.0: Got NSS = 3 - trimming to 2
```

---

### Post by simonsaysthis on 2022-02-02
I want to confirm that indeed something is broken on 21.10 for Intel AX200 Wifi cards. I can use Kernel 5.13.0.28 fine on 20.04 with good speeds and stability. Using the same Kernel with 21.10 will result in no Wifi connection on some restarts, or dropped connections during a desktop session.

None of the iwconfig options have resolved the issue.

Also, there are no other operating systems on my machine, secure boot is disabled and fast boot is also disabled.

---

