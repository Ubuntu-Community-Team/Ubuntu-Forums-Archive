---
title: "usb bus problems with new kernels"
date: 2021-11-29
forum: Hardware
---

### Post by maxmonz2 on 2021-11-29
Hi,

I have a Lenovo Thinkpad T580 notebook connected to an i-Tec docking station via usb-c cable. All USB peripherals (mouse, keyboard, etc.) and 2 monitors (HDMI) are connected to the docking station.
The driver that allows everything to work is the DisplayLink.
Up to version 5.4.0.89 of the kernel everything worked without problems.
With version 5.4.0.90 and the latest 5.4.0.91 a strange situation occurs. Occasionally the monitors darken and even the mouse does not respond. From in-depth analysis it seems that there is a problem on the USB bus for which the devices are disconnected for a few seconds until everything starts working again.
It is definitely a problem related to the new kernels because everything was fine with the previous ones.
Anyone have an idea and can help me?
Thanks

---

### Post by #&amp;thj^% on 2021-11-29
I would also include the return of: (Just add it to your original post)
```
inxi --admin --verbosity=7 --filter --no-host --width
```
Might get more people interested. More Info is a good thing.;)
```
Device-1: 2-6.1:5 info: DisplayLink UOEOS Laptop Dock
  type: Audio,Communication,CDC-Data driver: cdc_ncm,snd-usb-audio
  interfaces: 7 rev: 2.1 speed: 480 Mb/s power: 500mA chip-ID: 17e9:4307

```
And I don't have the "displaylink" driver installed.
```
Kernel: 5.14.21-hardened1-1-hardened x86_64 bits: 64 compiler: gcc v: 11.1.0

```
I'll confess I don't use any Display connections on it. (No Need for myself)

---

### Post by #&amp;thj^% on 2021-12-01
Please consider adding "Displaylink" to your Title.
have'nt heard back from you, but I'll share some links to help anyone interested.

[https://displaylink.org/forum/showthread.php?t=67372](https://displaylink.org/forum/showthread.php?t=67372)

Tested and working on my end with [s]Arch "5.15.5-hardened1-1-hardened"[/s] and Ubuntu "5.11"
After you have Downloaded *all* mentioned from the link provided.
```

cd /home/me/Downloads

chmod +x displaylink-driver-5.4.1-55.174.run
```
Now we use:
```

./displaylink-driver-5.4.1-55.174.run --noexec --keep
```

followed by:
```

tar xf evdi-1.7.0.tar.gz

pushd evdi-1.7.0

patch -p1 < ../228.patch

popd

```
And:
```

rm displaylink-driver-5.4.1-55.174/evdi.tar.gz

pushd evdi-1.7.0
```
and more:
```
tar cf evdi.tar.gz *

cp evdi.tar.gz ../displaylink-driver-5.4.1-55.174/

popd
```
We're getting close now:
```
cd displaylink-driver-5.4.1-55.174/

sudo ./displaylink-installer.sh install
```
Now some basic configs:
```
sudoedit /etc/X11/xorg.conf.d/20-evdi.conf

```
I added to that new file:
```

Section "OutputClass"
	Identifier "DisplayLink"
	MatchDriver "evdi"
	Driver "modesetting"
	Option "AccelMethod" "none"
EndSection

```
On Arch I had to enable:
```
sudo  modprobe udl
```
I can't remember if I did for Ubuntu though. (It was a late night for me) 



```
xrandr --current
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 340mm x 190mm
   1920x1080     60.00*+
   1680x1050     59.88  
   1400x1050     59.98  
   1600x900      60.00    59.95    59.82  
   1280x1024     60.02  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1368x768      60.00    59.88    59.85  
   1280x800      59.81    59.91  
   1280x720      59.86    60.00    59.74  
   1024x768      60.00  
   1024x576      60.00    59.90    59.82  
   960x540       60.00    59.63    59.82  
   800x600       60.32    56.25  
   864x486       60.00    59.92    59.57  
   640x480       59.94  
   720x405       59.51    60.00    58.99  
   640x360       59.84    59.32    60.00  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 1210mm x 680mm
   1920x1080     60.00*   50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
[B][COLOR="#FF0000"]HDMI2 disconnected (normal left inverted right x axis y axis)
VGA1 disconnected (normal left inverted right x axis y axis)[/COLOR][/B]
VIRTUAL1 disconnected (normal left inverted right x axis y axis)


```
Not very user friendly, sorry best I could do here.:(
You may also at first see a "greenish screen", normal from what I hear.
My method went as follows.

---

### Post by maxmonz2 on 2021-12-02
Hi and thanks for your reply.

I'm going to try the patch as explained in the link as soon as I can.
Meanwhile here's the return from inxi command.

```
inxi --admin --verbosity=7 --filter --no-host --width 100

System:    Kernel: 5.4.0-91-generic x86_64 bits: 64 compiler: gcc v: 9.3.0            parameters: BOOT_IMAGE=/boot/vmlinuz-5.4.0-91-generic 
           root=UUID=7bcd4fee-49b8-4085-a340-4bc93b69c1b1 ro 
           Desktop: Gnome 3.36.9 wm: gnome-shell dm: GDM3 3.36.3 
           Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:   Type: Laptop System: LENOVO product: 20L9CTO1WW v: ThinkPad T580 serial: <filter> 
           Chassis: type: 10 serial: <filter> 
           Mobo: LENOVO model: 20L9CTO1WW serial: <filter> UEFI: LENOVO v: N27ET43W (1.29 ) 
           date: 08/13/2021 
Battery:   ID-1: BAT0 charge: 24.9 Wh condition: 31.9/31.9 Wh (100%) volts: 15.6/15.2 
           model: LGC 01AV493 type: Li-poly serial: <filter> status: Unknown cycles: 40 
           ID-2: BAT1 charge: 18.7 Wh condition: 23.5/24.0 Wh (98%) volts: 12.0/11.5 
           model: SMP 01AV452 type: Li-poly serial: <filter> status: Unknown cycles: 10 
           Device-1: hidpp_battery_0 model: Logitech MX Keys Wireless Keyboard serial: <filter> 
           charge: 55% (should be ignored) rechargeable: yes status: Discharging 
Memory:    RAM: total: 15.38 GiB used: 1.38 GiB (9.0%) 
           RAM Report: permissions: Unable to run dmidecode. Root privileges required. 
CPU:       Topology: Quad Core model: Intel Core i7-8550U bits: 64 type: MT MCP arch: Kaby Lake 
           family: 6 model-id: 8E (142) stepping: A (10) microcode: EA L2 cache: 8192 KiB 
           bogomips: 31999 
           Speed: 772 MHz min/max: 400/1800 MHz Core speeds (MHz): 1: 700 2: 700 3: 700 4: 700 
           5: 700 6: 700 7: 701 8: 700 
           Flags: 3dnowprefetch abm acpi adx aes aperfmperf apic arat arch_perfmon art avx avx2 
           bmi1 bmi2 bts clflush clflushopt cmov constant_tsc cpuid cpuid_fault cx16 cx8 de ds_cpl 
           dtes64 dtherm dts epb ept ept_ad erms est f16c flexpriority flush_l1d fma fpu fsgsbase 
           fxsr ht hwp hwp_act_window hwp_epp hwp_notify ibpb ibrs ida intel_pt invpcid 
           invpcid_single lahf_lm lm mca mce md_clear mmx monitor movbe mpx msr mtrr nonstop_tsc 
           nopl nx pae pat pbe pcid pclmulqdq pdcm pdpe1gb pebs pge pln pni popcnt pse pse36 pti 
           pts rdrand rdseed rdtscp rep_good sdbg sep smap smep ss ssbd sse sse2 sse4_1 sse4_2 
           ssse3 stibp syscall tm tm2 tpr_shadow tsc tsc_adjust tsc_deadline_timer vme vmx vnmi 
           vpid x2apic xgetbv1 xsave xsavec xsaveopt xsaves xtopology xtpr 
           Vulnerabilities: Type: itlb_multihit status: KVM: Split huge pages 
           Type: l1tf mitigation: PTE Inversion; VMX: conditional cache flushes, SMT vulnerable 
           Type: mds mitigation: Clear CPU buffers; SMT vulnerable 
           Type: meltdown mitigation: PTI 
           Type: spec_store_bypass 
           mitigation: Speculative Store Bypass disabled via prctl and seccomp 
           Type: spectre_v1 mitigation: usercopy/swapgs barriers and __user pointer sanitization 
           Type: spectre_v2 mitigation: Full generic retpoline, IBPB: conditional, IBRS_FW, STIBP: 
           conditional, RSB filling 
           Type: srbds mitigation: Microcode 
           Type: tsx_async_abort status: Not affected 
Graphics:  Device-1: Intel UHD Graphics 620 vendor: Lenovo driver: i915 v: kernel bus ID: 00:02.0 
           chip ID: 8086:5917 
           Display: x11 server: X.Org 1.20.11 driver: i915 compositor: gnome-shell 
           resolution: 1920x1080~60Hz, 1920x1080~60Hz, 1920x1080~60Hz 
           OpenGL: renderer: Mesa Intel UHD Graphics 620 (KBL GT2) v: 4.6 Mesa 21.0.3 
           direct render: Yes 
Audio:     Device-1: Intel Sunrise Point-LP HD Audio vendor: Lenovo driver: snd_hda_intel 
           v: kernel bus ID: 00:1f.3 chip ID: 8086:9d71 
           Device-2: DisplayLink type: USB driver: cdc_ncm,snd-usb-audio,usbfs bus ID: 2-4.1:4 
           chip ID: 17e9:6000 serial: <filter> 
           Device-3: GN Netcom type: USB driver: jabra,snd-usb-audio,usbhid bus ID: 1-4.4.2.3:14 
           chip ID: 0b0e:245e serial: <filter> 
           Sound Server: ALSA v: k5.4.0-91-generic 
Network:   Device-1: Intel Ethernet I219-V vendor: Lenovo driver: e1000e v: 3.2.6-k port: efa0 
           bus ID: 00:1f.6 chip ID: 8086:15d8 
           IF: enp0s31f6 state: down mac: <filter> 
           Device-2: Intel Wireless 8265 / 8275 driver: iwlwifi v: kernel port: efa0 
           bus ID: 04:00.0 chip ID: 8086:24fd 
           IF: wlp4s0 state: down mac: <filter> 
           IF-ID-1: docker0 state: down mac: <filter> 
           IP v4: <filter> scope: global broadcast: <filter> 
           IF-ID-2: enx806d970c8d49 state: up speed: N/A duplex: N/A mac: <filter> 
           IP v4: <filter> type: noprefixroute scope: global broadcast: <filter> 
           IP v6: <filter> type: noprefixroute scope: link 
           WAN IP: <filter> 
Drives:    Local Storage: total: 238.47 GiB used: 164.23 GiB (68.9%) 
           SMART Message: Unable to run smartctl. Root privileges required. 
           ID-1: /dev/nvme0n1 vendor: LITE-ON model: CA3-8D256 size: 238.47 GiB block size: 
           physical: 512 B logical: 512 B speed: 31.6 Gb/s lanes: 4 serial: <filter> rev: 24879 
           scheme: GPT 
           Message: No Optical or Floppy data was found. 
RAID:      Message: No RAID data was found. 
Partition: ID-1: / raw size: 115.88 GiB size: 113.94 GiB (98.32%) used: 102.27 GiB (89.8%) 
           fs: ext4 dev: /dev/nvme0n1p2 label: N/A uuid: 7bcd4fee-49b8-4085-a340-4bc93b69c1b1 
           ID-2: /boot/efi raw size: 258.0 MiB size: 254.0 MiB (98.46%) used: 14.3 MiB (5.6%) 
           fs: vfat dev: /dev/nvme0n1p1 label: N/A uuid: D796-0FA0 
           ID-3: /home raw size: 122.34 GiB size: 119.42 GiB (97.61%) used: 61.95 GiB (51.9%) 
           fs: ext4 dev: /dev/nvme0n1p3 label: N/A uuid: 519384a4-bad2-47c9-9946-6af4223a8a49 
           ID-4: /home/<filter>/NAZGhoul/Data raw size: N/A size: 296.64 GiB used: 2.87 GiB (1.0%) 
           fs: cifs remote: //192.168.1.52/Data label: N/A uuid: N/A 
           ID-5: /home/<filter>/NAZGhoul/Documents raw size: N/A size: 79.31 GiB 
           used: 50.84 GiB (64.1%) fs: cifs remote: //192.168.1.52/homes/massimo label: N/A 
           uuid: N/A 
           ID-6: /home/<filter>/NAZGhoul/Music raw size: N/A size: 495.06 GiB 
           used: 173.84 GiB (35.1%) fs: cifs remote: //192.168.1.52/Music label: N/A uuid: N/A 
           ID-7: /home/<filter>/NAZGhoul/Photos raw size: N/A size: 296.64 GiB 
           used: 45.54 GiB (15.4%) fs: cifs remote: //192.168.1.52/Photos label: N/A uuid: N/A 
           ID-8: /home/<filter>/NAZGhoul/Video raw size: N/A size: 1.49 TiB 
           used: 548.37 GiB (36.0%) fs: cifs remote: //192.168.1.52/Video label: N/A uuid: N/A 
           ID-9: /home/<filter>/raspy1 raw size: N/A size: 29.16 GiB used: 16.74 GiB (57.4%) 
           fs: fuse.sshfs remote: pi@192.168.1.40:/home/pi label: N/A uuid: N/A 
           ID-10: /snap/audacity/922 raw size: 185.3 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop0 label: N/A uuid: N/A 
           ID-11: /snap/bare/5 raw size: 4 KiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop1 label: N/A uuid: N/A 
           ID-12: /snap/cherrytree/40 raw size: 68.3 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop2 label: N/A uuid: N/A 
           ID-13: /snap/core/11993 raw size: 99.4 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop3 label: N/A uuid: N/A 
           ID-14: /snap/core18/2253 raw size: 55.5 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop4 label: N/A uuid: N/A 
           ID-15: /snap/core20/1242 raw size: 61.8 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop5 label: N/A uuid: N/A 
           ID-16: /snap/gnome-3-28-1804/161 raw size: 164.8 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop6 label: N/A uuid: N/A 
           ID-17: /snap/gnome-3-34-1804/72 raw size: 219.0 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop8 label: N/A uuid: N/A 
           ID-18: /snap/gnome-3-34-1804/77 raw size: 219.0 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop7 label: N/A uuid: N/A 
           ID-19: /snap/gnome-3-38-2004/76 raw size: 242.3 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop13 label: N/A uuid: N/A 
           ID-20: /snap/gnome-3-38-2004/87 raw size: 247.9 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop15 label: N/A uuid: N/A 
           ID-21: /snap/gnome-system-monitor/174 raw size: 2.5 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop18 label: N/A uuid: N/A 
           ID-22: /snap/gtk-common-themes/1519 raw size: 65.2 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop14 label: N/A uuid: N/A 
           ID-23: /snap/gtk2-common-themes/13 raw size: 140 KiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop10 label: N/A uuid: N/A 
           ID-24: /snap/postman/133 raw size: 175.4 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop16 label: N/A uuid: N/A 
           ID-25: /snap/slack/48 raw size: 129.4 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop17 label: N/A uuid: N/A 
           ID-26: /snap/snap-store/547 raw size: 51.0 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop12 label: N/A uuid: N/A 
           ID-27: /snap/snap-store/558 raw size: 54.2 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop9 label: N/A uuid: N/A 
           ID-28: /snap/sublime-text/110 raw size: 64.7 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop11 label: N/A uuid: N/A 
Unmounted: Message: No unmounted partitions found. 
USB:       Hub: 1-0:1 info: Full speed (or root) Hub ports: 12 rev: 2.0 speed: 480 Mb/s 
           chip ID: 1d6b:0002 
           Hub: 1-4:2 info: Genesys Logic 4-port hub ports: 4 rev: 2.1 speed: 480 Mb/s 
           chip ID: 05e3:0610 
           Hub: 1-4.2:4 info: VIA Labs ports: 4 rev: 2.1 speed: 480 Mb/s chip ID: 2109:2210 
           Device-1: 1-4.2.3:8 info: Good Way & GWC type: HID driver: hid-generic,usbhid 
           interfaces: 1 rev: 2.0 speed: 12 Mb/s chip ID: 065f:f60f serial: <filter> 
           Hub: 1-4.4:7 info: Genesys Logic 4-port hub ports: 4 rev: 2.1 speed: 480 Mb/s 
           chip ID: 05e3:0610 
           Hub: 1-4.4.1:9 info: VIA Labs ports: 4 rev: 2.1 speed: 480 Mb/s chip ID: 2109:2817 
           Hub: 1-4.4.1.3:13 info: VIA Labs ports: 4 rev: 2.1 speed: 480 Mb/s chip ID: 2109:2817 
           Hub: 1-4.4.1.4:15 info: VIA Labs USB2.1 Hub ports: 4 rev: 2.1 speed: 480 Mb/s 
           chip ID: 2109:2817 
           Hub: 1-4.4.2:10 info: Genesys Logic 4-port hub ports: 4 rev: 2.1 speed: 480 Mb/s 
           chip ID: 05e3:0610 
           Device-2: 1-4.4.2.1:12 info: Trust type: Mouse driver: hid-generic,usbhid interfaces: 1 
           rev: 1.1 speed: 12 Mb/s chip ID: 145f:02e5 
           Device-3: 1-4.4.2.3:14 info: GN Netcom type: Audio,HID 
           driver: jabra,snd-usb-audio,usbhid interfaces: 4 rev: 2.0 speed: 12 Mb/s 
           chip ID: 0b0e:245e serial: <filter> 
           Device-4: 1-4.4.2.4:16 info: Logitech Unifying Receiver type: Keyboard,Mouse,HID 
           driver: logitech-djreceiver,usbhid interfaces: 3 rev: 2.0 speed: 12 Mb/s 
           chip ID: 046d:c52b 
           Device-5: 1-4.4.4:11 info: Alcor Micro AU9540 Smartcard Reader type: Smart Card 
           driver: N/A interfaces: 1 rev: 2.0 speed: 12 Mb/s chip ID: 058f:9540 
           Device-6: 1-7:3 info: Intel type: Bluetooth driver: btusb interfaces: 2 rev: 2.0 
           speed: 12 Mb/s chip ID: 8087:0a2b 
           Device-7: 1-8:5 info: IMC Networks Integrated Camera type: Video driver: uvcvideo 
           interfaces: 2 rev: 2.0 speed: 480 Mb/s chip ID: 13d3:56a6 serial: <filter> 
           Device-8: 1-9:6 info: Synaptics type: <vendor specific> driver: N/A interfaces: 1 
           rev: 2.0 speed: 12 Mb/s chip ID: 06cb:009a serial: <filter> 
           Hub: 2-0:1 info: Full speed (or root) Hub ports: 6 rev: 3.0 speed: 5 Gb/s 
           chip ID: 1d6b:0003 
           Device-9: 2-3:2 info: Realtek USB3.0-CRW type: Mass Storage driver: usb-storage 
           interfaces: 1 rev: 3.0 speed: 5 Gb/s chip ID: 0bda:0316 serial: <filter> 
           Hub: 2-4:3 info: Genesys Logic USB3.1 Hub ports: 4 rev: 3.2 speed: 5 Gb/s 
           chip ID: 05e3:0620 
           Device-10: 2-4.1:4 info: DisplayLink type: <vendor specific> 
           driver: cdc_ncm,snd-usb-audio,usbfs interfaces: 7 rev: 3.2 speed: 5 Gb/s 
           chip ID: 17e9:6000 serial: <filter> 
           Hub: 2-4.2:5 info: VIA Labs ports: 1 rev: 3.0 speed: 5 Gb/s chip ID: 2109:0210 
           Hub: 2-4.4:6 info: Genesys Logic USB3.1 Hub ports: 4 rev: 3.2 speed: 5 Gb/s 
           chip ID: 05e3:0620 
           Hub: 2-4.4.1:7 info: VIA Labs ports: 4 rev: 3.1 speed: 5 Gb/s chip ID: 2109:0817 
           Hub: 2-4.4.1.3:9 info: VIA Labs USB3.0-CRW ports: 4 rev: 3.1 speed: 5 Gb/s 
           chip ID: 2109:0817 
           Hub: 2-4.4.1.4:10 info: VIA Labs USB3.1 Hub ports: 4 rev: 3.1 speed: 5 Gb/s 
           chip ID: 2109:0817 
           Hub: 2-4.4.2:8 info: Genesys Logic Hub ports: 4 rev: 3.1 speed: 5 Gb/s 
           chip ID: 05e3:0612 
           Hub: 3-0:1 info: Full speed (or root) Hub ports: 2 rev: 2.0 speed: 480 Mb/s 
           chip ID: 1d6b:0002 
           Hub: 3-1:2 info: Genesys Logic 4-port hub ports: 4 rev: 2.1 speed: 480 Mb/s 
           chip ID: 05e3:0610 
           Device-11: 3-1.1:3 info: Genesys Logic microSD Card Reader type: Mass Storage 
           driver: usb-storage interfaces: 1 rev: 2.0 speed: 480 Mb/s chip ID: 05e3:0751 
           Hub: 4-0:1 info: Full speed (or root) Hub ports: 2 rev: 3.1 speed: 10 Gb/s 
           chip ID: 1d6b:0003 
           Hub: 4-1:2 info: Genesys Logic USB3.1 Hub ports: 4 rev: 3.1 speed: 5 Gb/s 
           chip ID: 05e3:0626 
Sensors:   System Temperatures: cpu: 44.0 C mobo: N/A 
           Fan Speeds (RPM): cpu: 2521 
Info:      Processes: 331 Uptime: 1m Init: systemd v: 245 runlevel: 5 Compilers: gcc: 9.3.0 
           alt: 8/9 Shell: bash v: 5.0.17 running in: gnome-terminal inxi: 3.0.38 
```

---

### Post by #&amp;thj^% on 2021-12-06
Mine was on a Thinkpad T540p with Intel/Nvidia 470.
I need to amend my other post, no longer works for Arch 5.15.
Let me know how you end up.

---

### Post by maxmonz2 on 2021-12-30
I decided to not preceed with the patch because the problem described is different.
For me DisplayLink works but has random  usb cut off.
By the way it's also referred to an older version.

---

### Post by maxmonz2 on 2022-01-28
Am I the only one experiencing this problems?
Nobody has any idea or suggestion?
It's very frustrating.
Who can help me? What can I do? Should I work forever with the old kernel or throwing the docking station away?

---

### Post by maxmonz2 on 2022-02-17
Evidently I was the only one with this problem and nobody cares but now  it's been solved.
The support gave me a patch for device's firmware.

---

