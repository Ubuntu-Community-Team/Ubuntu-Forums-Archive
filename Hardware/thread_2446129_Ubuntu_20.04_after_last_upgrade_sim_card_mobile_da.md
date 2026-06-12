---
title: "Ubuntu 20.04 after last upgrade sim card mobile data not working anymore"
date: 2020-06-25
forum: Hardware
---

### Post by moromete on 2020-06-25
Hello,

"Mobile broadband disabled" and if i try to connect "Mobile broadband unavailable"

Last resort -> mmcli:
```

 #/snap/bin/modem-manager.mmcli -m 0
  --------------------------
  General  |      dbus path: /org/freedesktop/ModemManager1/Modem/0
           |      device id: ec57507202c8b9a8c27b95656559fae5c807386c
  --------------------------
  Hardware |   manufacturer: FIBOCOM
           |          model: L831-EAU
           |       revision: L831_V2E.0C.00.10
           |   h/w revision: L831-EAU-00 v1.0.0
           |      supported: gsm-umts, lte
           |        current: gsm-umts, lte
           |   equipment id: 862727033144507
  --------------------------
  System   |         device: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-4
           |        drivers: cdc_mbim
           |         plugin: Fibocom
           |   primary port: cdc-wdm1
           |          ports: wwan0 (net), cdc-wdm1 (mbim)
  --------------------------
  Status   | unlock retries: sim-pin (3)
           |          state: disabled
           |    power state: on
           | signal quality: 74% (cached)
  --------------------------
  Modes    |      supported: allowed: 3g, 4g; preferred: none
           |        current: allowed: 3g, 4g; preferred: none
  --------------------------
  IP       |      supported: ipv4, ipv6, ipv4v6
  --------------------------
  3GPP     |           imei: 862727033144507
           |   registration: idle
  --------------------------
  SIM      |      dbus path: /org/freedesktop/ModemManager1/SIM/0

Enabled with
#nmcli r wwan on
Add connection
#nmcli c add type gsm ifname cdc-wdm1 con-name digi apn internet
Up connection
# nmcli connection
NAME                 UUID                                  TYPE  DEVICE 
Digi.Net Mobil Home  1f3e12f2-589c-4487-8aa1-99ef82f554c9  gsm   --     
# nmcli connection up uuid 1f3e12f2-589c-4487-8aa1-99ef82f554c9
# journalctl -xe NM_CONNECTION=1f3e12f2-589c-4487-8aa1-99ef82f554c9 + NM_DEVICE=cdc-wdm1 uuid 1f3e12f2-589c-4487-8aa1-99ef82f554c
Activation: starting connection 'digi' (cad7aeed-6495-42e4-a9d4-9f0dfb729238)
397] device (cdc-wdm1): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
745] device (cdc-wdm1): state change: prepare -> failed (reason 'gsm-registration-timeout', sys-iface-state: 'managed')
816] device (cdc-wdm1): Activation: failed for connection 'digi'

```

With external ZTE modem. same "Mobile broadband disabled"
 
```

#dmesg
[   53.143269] usb 1-2.2: New USB device found, idVendor=19d2, idProduct=2000, bcdDevice= 0.00
[   53.143286] usb 1-2.2: New USB device strings: Mfr=3, Product=2, SerialNumber=4
[   53.143298] usb 1-2.2: Product: ZTE WCDMA Technologies MSM
[   53.143309] usb 1-2.2: Manufacturer: ZTE,Incorporated
[   53.143318] usb 1-2.2: SerialNumber: MF1900RDSD010000
[  

```
```

# nmcli d
DEVICE          TYPE      STATE         CONNECTION      
wlp1s0          wifi      connected     PrimariaHD-FREE 
p2p-dev-wlp1s0  wifi-p2p  disconnected  --              
cdc-wdm2        gsm       unavailable   --              
lo              loopback  unmanaged     --    
```

```
# inxi -Fx
System:    Host: romeo-atom Kernel: 5.7.0-999-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Gnome 3.36.2 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Detachable System: LENOVO product: 80XF v: Lenovo MIIX 320-10ICR serial: P202ZBH1 
           Mobo: LENOVO model: LNVNB161216 v: SDK0J91196WIN serial: P202ZBH1 UEFI: LENOVO v: 5HCN39WW date: 05/11/2018 
Battery:   ID-1: BAPM charge: 21.0 Wh condition: 33.3/33.3 Wh (100%) model: Bitland AXP288 status: Discharging 
CPU:       Topology: Quad Core model: Intel Atom x5-Z8350 bits: 64 type: MCP arch: Airmont rev: 4 L2 cache: 1024 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 11520 
           Speed: 480 MHz min/max: 480/1920 MHz Core speeds (MHz): 1: 480 2: 480 3: 1811 4: 1753 
Graphics:  Device-1: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics vendor: Lenovo driver: i915 
           v: kernel bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 800x1280~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics (CHV) v: 4.6 Mesa 20.0.4 direct render: Yes 
Audio:     Device-1: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit vendor: Lenovo 
           driver: intel_atomisp2_pm v: kernel bus ID: 00:03.0 
           Sound Server: ALSA v: k5.7.0-999-generic 
Network:   Device-1: Intel Wireless 3165 driver: iwlwifi v: kernel port: 1000 bus ID: 01:00.0 
           IF: wlp1s0 state: up mac: 7c:2a:31:ea:cd:42 
           IF-ID-1: wwan0 state: down mac: b2:f0:cc:30:ff:46 
Drives:    Local Storage: total: 177.49 GiB used: 65.40 GiB (36.8%) 
           ID-1: /dev/mmcblk0 model: DF4064 size: 58.24 GiB 
           ID-2: /dev/mmcblk2 model: ED4QT size: 119.25 GiB 
Partition: ID-1: / size: 56.58 GiB used: 32.72 GiB (57.8%) fs: ext4 dev: /dev/mmcblk0p2 
Sensors:   System Temperatures: cpu: 42.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 255 Uptime: 7m Memory: 3.71 GiB used: 1.18 GiB (31.9%) Init: systemd Compilers: gcc: 9.3.0 Shell: bash 
           v: 5.0.16 inxi: 3.0.38
```

---

### Post by manelvf on 2021-05-21
Hi,

I have the same problem, but coming from a 20.04 fresh install, and using the embedded modem of a Lenovo Thinkpad. Is it possible that another process is using the device? Network manager doesn't give many clues.

---

### Post by moromete on 2021-05-22
Hi, 

Sorry i leave Ubuntu, to many windows in kernel.

---

