---
title: "ath9k doesn't recover from suspend on 16.04"
date: 2016-05-02
forum: Hardware
---

### Post by richard-a-blum on 2016-05-02
I just upgraded my Acer Aspire v5 from 14.04 to 16.04, and I've noticed that sometimes the wireless interface doesn't properly recover when I wake the laptop from suspend.  The symptoms are that the network is not connected, and the list of available networks in Network Manager is missing all my networks, and most of my neighbors'.  I am able to recover w/
[FONT=courier new]sudo rmmod ath9k
sudo modprobe ath9k
[FONT=arial]

This is the listing from lspci:
[/FONT][/FONT]04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)

And the logs of the wakeup from dmesg:
[ 7287.884812] ACPI: Low-level resume complete
[ 7287.884881] ACPI : EC: EC started
[ 7287.884882] PM: Restoring platform NVS memory
[ 7287.885305] Enabling non-boot CPUs ...
[ 7287.904876] x86: Booting SMP configuration:
[ 7287.904878] smpboot: Booting Node 0 Processor 1 APIC 0x2
[ 7287.907890]  cache: parent cpu1 should not be sleeping
[ 7287.908144] CPU1 is up
[ 7287.910649] ACPI: Waking up from system sleep state S3
[ 7287.928697] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
[ 7287.928877] ehci-pci 0000:00:1a.0: System wakeup disabled by ACPI
[ 7287.929566] PM: noirq resume of devices complete after 16.267 msecs
[ 7287.929955] PM: early resume of devices complete after 0.334 msecs
[ 7287.941856] ath: phy0: ASPM enabled: 0x42
[ 7287.941877] tg3 0000:04:00.0: System wakeup disabled by ACPI
[ 7287.945178] sd 0:0:0:0: [sda] Starting disk
[ 7288.172568] usb 1-1.3: reset high-speed USB device number 4 using ehci-pci
[ 7288.172843] rtc_cmos 00:03: System wakeup disabled by ACPI
[ 7288.264562] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 7288.289848] ata1.00: configured for UDMA/133
[ 7288.336514] usb 1-1.1: reset full-speed USB device number 13 using ehci-pci
[ 7288.430465] usb 1-1.1: device firmware changed
[ 7288.430857] PM: resume of devices complete after 500.929 msecs
[ 7288.431284] PM: Finishing wakeup.
[ 7288.431287] Restarting tasks ... 
[ 7288.436375] usb 1-1.1: USB disconnect, device number 13
[ 7288.443218] done.
[ 7288.512462] usb 1-1.1: new full-speed USB device number 14 using ehci-pci
[ 7288.606982] usb 1-1.1: string descriptor 0 read error: -22
[ 7288.606999] usb 1-1.1: New USB device found, idVendor=0489, idProduct=e04e
[ 7288.607005] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3[ 7288.950071] IPv6: ADDRCONF(NETDEV_UP): enp4s0f0: link is not ready
[ 7288.659448] usb 1-1.1: USB disconnect, device number 14
[ 7288.936631] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 7288.948738] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 7288.950071] IPv6: ADDRCONF(NETDEV_UP): enp4s0f0: link is not ready
[ 7289.136462] usb 1-1.1: new full-speed USB device number 15 using ehci-pci
[ 7289.136540] IPv6: ADDRCONF(NETDEV_UP): enp4s0f0: link is not ready
[ 7289.193152] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 7289.230819] usb 1-1.1: string descriptor 0 read error: -22
[ 7289.230838] usb 1-1.1: New USB device found, idVendor=0489, idProduct=e04e
[ 7289.230845] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 7288.659448] usb 1-1.1: USB disconnect, device number 14
[ 7288.936631] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 7288.948738] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 7288.950071] IPv6: ADDRCONF(NETDEV_UP): enp4s0f0: link is not ready

Any suggestions?

---

### Post by richard-a-blum on 2016-05-13
So, I have been digging into this and I think the problem actually lies with network-manager.  Restarting network-manager without unloading and reloading ath9k is enough to get the wifi back.  For now, I've switched to wicd, which seems to work.  I've noticed that wicd takes several seconds after logging back in to find the wifi again, while network-manager would either find it immediately or not at all.  That makes me wonder if there's some race condition that network-manager is getting into.  I'd rather use network-manager if possible, so is there a way to automatically restart network manager after resuming my session?

---

### Post by weatherman2 on 2016-05-13
You could automatically either restart Network Manager or remove/reload the module after resume - as you are now doing manually.

How to do this may have changed by 16.04 (which I've not really used yet), but in older versions, you could add commands in the file /etc/pm/sleep.d/20_custom .

---

### Post by richard-a-blum on 2016-05-28
Thanks weatherman2.  I figured out that the new systemd location for scripts that run on resume is actually /lib/systemd/system-sleep.  The workaround of putting a script in that directory to run service network-manager restart seems to be working.

---

### Post by kurt18947 on 2016-05-28
I'm seeing a similar intermittent problem with Ubuntu Gnome 16.04 and an Intel 620x wifi adapter. Restarting network manager fixes the problem so yeah, network manager and resume aren't always behaving properly, it seems.

---

### Post by roger_1960 on 2016-05-29
That may well be this known bug [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1439771](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1439771)

---

