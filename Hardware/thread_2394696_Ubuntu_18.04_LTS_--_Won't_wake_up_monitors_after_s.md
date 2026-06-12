---
title: "Ubuntu 18.04 LTS -- Won't wake up monitors after sleep"
date: 2018-06-20
forum: Hardware
---

### Post by mc88 on 2018-06-20
Been developing on Linux Mint 18.3 for several years, but decided to port over to Ubuntu 18.04 LTS for various development reasons. Everything is working great, but... I'm having a hard time waking up the monitors from sleep. My desktop enters and maintains sleep without any issues, but when coming out of sleep, the monitors won't turn on. I tried unplugging and re-plugging the monitors in, no dice, still no signal. The only way to get a signal is to hard reboot.

Am I missing something? Linux Mint didn't have any sleep issues.

```
System:    Kernel: 4.15.0-23-generic x86_64 bits: 64 gcc: 7.3.0 Desktop: Gnome 3.28.1 (Gtk 3.22.30)
           Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop System: ASUS product: All Series serial: N/A
           Mobo: ASUSTeK model: X99-PRO/USB 3.1 v: Rev 1.xx serial: N/A
           UEFI: American Megatrends v: 3701 date: 03/31/2017
CPU:       10 core Intel Core i7-6950X (-MT-MCP-) arch: Broadwell rev.1 cache: 25600 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 59969
           clock speeds: max: 4000 MHz 1: 1200 MHz 2: 1200 MHz 3: 1199 MHz 4: 1200 MHz 5: 1350 MHz 6: 1200 MHz
           7: 1204 MHz 8: 1290 MHz 9: 1199 MHz 10: 1199 MHz 11: 1201 MHz 12: 1199 MHz 13: 1199 MHz 14: 1201 MHz
           15: 1423 MHz 16: 1201 MHz 17: 1199 MHz 18: 1282 MHz 19: 1200 MHz 20: 1200 MHz
Graphics:  Card: NVIDIA GM200 [GeForce GTX TITAN X] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.6 ) driver: nvidia Resolution: 2560x1440@165.00hz, 2560x1440@74.97hz
           OpenGL: renderer: GeForce GTX TITAN X/PCIe/SSE2 version: 4.6.0 NVIDIA 390.48 Direct Render: Yes
Audio:     Card-1 Intel C610/X99 series HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GM200 High Definition Audio driver: snd_hda_intel bus-ID: 01:00.1
           Card-3 XMOS driver: USB Audio usb-ID: 003-007
           Sound: Advanced Linux Sound Architecture v: k4.15.0-23-generic
Network:   Card-1: Intel Ethernet Connection (2) I218-V driver: e1000e v: 3.2.6-k port: f000 bus-ID: 00:19.0
           IF: eno1 state: up speed: 1000 Mbps duplex: full mac: 30:5a:3a:57:90:46
           Card-2: Broadcom Limited BCM4352 802.11ac Wireless Network Adapter driver: wl bus-ID: 05:00.0
           IF: wlp5s0 state: down mac: 40:e2:30:c0:4d:c2
Drives:    HDD Total Size: 3024.6GB (0.9% used)
           ID-1: /dev/nvme0n1 model: Samsung_SSD_950_PRO_512GB size: 512.1GB
           ID-2: /dev/nvme1n1 model: Samsung_SSD_960_PRO_1TB size: 1024.2GB
           ID-3: /dev/sda model: ST2000DX001 size: 2000.4GB temp: 33C
           ID-4: /dev/sdb model: Samsung_SSD_850 size: 256.1GB temp: 0C
           ID-5: /dev/sdc model: SAMSUNG_SSD_830 size: 256.1GB temp: 0C
Partition: ID-1: / size: 234G used: 25G (12%) fs: ext4 dev: /dev/sdb2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.0C mobo: N/A gpu: 0.0:39C
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 388 Uptime: 4:06 Memory: 2626.6/32075.5MB Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 

```

---

### Post by caseyfw2 on 2019-01-28
I had this issue and resolved it by updating to the latest mainline kernel (4.20) from the Ubuntu published one (4.15) using the Ubuntu Kernel Update Utility (aka Ukuu).


At first I thought it might be a display driver problem, so I downgraded to nvidia-390, but it persisted. Completely disappeared after updating to 4.20 kernel though.

---

### Post by markackerman8@gmail.com on 2019-01-30
THis is just a guess so bare with me if it is not what you're looking for ....

Problems SOLVED! I
&#8728; Hibernate/Suspend - NVHDA Sound does not repopulate
• However, if I manually disable the audio output output "sudo tee /proc/acpi/nvhda <<< OFF" I'm then able to get it to sleep. I then have to turn it on again on resume with "sudo tee /proc/acpi/nvhda <<< ON
```
$ sudo tee /proc/acpi/nvhda <<< OFF 
```         (before Hibernation/Suspend or Sleep)
```
$ sudo tee /proc/acpi/nvhda <<< ON 
```           (After Resume)

• SOLVED! I

Always trying to help, Mark

---

