---
title: "[SOLVED] Upgrading PCIe network adapter"
date: 2013-06-02
forum: Hardware
---

### Post by scbingham on 2013-06-02
Hello Forum

Mods, I wasn't sure where this fits, Networking & Wireless or Hardware, move as you see fit.

I have an Advent 5301 laptop running Ubuntu 12.04LTS 64. It comes with a Realtek RTL8187B PCIe adapter.

I installed an Atheros ar5B95 PCIe adapter (with a mounting plate as it's a half length card), as it has the capability to used as an Access Point.

Usually I turn on the wireless adapter by Fn + F10. This failed to work for the ar5b95.

I typed dmesg & got the following:

122.650702] atkbd serio0: Unknown key released (translated set 2, code 0xad on isa0060/serio0).
[  122.650709] atkbd serio0: Use 'setkeycodes e02d <keycode>' to make it known.

Also, quite soon afterwards my wired connection went off line.

I'm thinking there's a hardware issue. There's no mention of wireless adapter in the bios, so nothing to change there. After much searching I've found nothing to help.

So, am I niave in thinking PCIe adapters are interchangeable or have I missed something?

If I can get the hardware issue sorted, I'm sure I'll have s/w issues to play with.

Any help & advice is most welcome.

---

### Post by Elfy on 2013-06-10
*Thread moved to **Hardware**.*

---

### Post by varunendra on 2013-06-10
> **scbingham said:**
> Usually I turn on the wireless adapter by Fn + F10. This failed to work for the ar5b95.
....
There's no mention of wireless adapter in the bios, so nothing to change there.
Does it show up in lspci?
```
lspci -nn
```

If not, make sure the card is plugged in correctly, then do a BIOS reset. It must appear in lspci, as well as in BIOS settings as far as I know.

---

### Post by scbingham on 2013-06-10
Thanks for responding Varun! I'll put the card in again tomorrow (it's not with me at the moment), try as you advised & report back.

Even with the original card in (which works fine), there is no mention of the ethernet card at all in the BIOS.

---

### Post by varunendra on 2013-06-10
> **scbingham said:**
> Even with the original card in (which works fine), there is no mention of the ethernet card at all in the BIOS.

Ethernet means wired connection interface, while this card is a wireless one. Also, it is expected to show up in BIOS with some options to enable/disable it, but some OEMs 'may' choose to omit that setting, it is not mandatory. Although so far I know of no such model whose BIOS doesn't provide an option to enable/disable wireless if it exists, but there are thousands of OEMs/Models and my experience is very small.

Still, in order for a device to work, it needs to be 'seen' by the OS first. And in order for an OS to 'see' a device, the BIOS must detect it first, then pass that info to the OS.

So... if even lspci doesn't show it, just reset the BIOS, assuming the card itself is functional and is supported by the bus to which you have attached it.

---

### Post by scbingham on 2013-06-10
Output of lspci -nn with the original Realtek wireless adapter:

00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 671MX [1039:0671]
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge) [1039:0003]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] [1039:0968] (rev 01)
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 IDE Controller [1039:5513] (rev 01)
00:03.0 USB controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.3 USB controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
00:05.0 IDE interface [0101]: Silicon Integrated Systems [SiS] SATA Controller / IDE mode [1039:1183] (rev 03)
00:0f.0 Audio device [0403]: Silicon Integrated Systems [SiS] Azalia Audio Controller [1039:7502]
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)

As you can see, there's no mention of the wireless card. Also there's no mention of it in the BIOS.
After the laptop has booted, the wireless card can be turned on & off by pressing Fn + F10. There is no difference to the lspci output whether it is on or off.

Unfortunately I can not install the Atheros card until tomorrow. Is there any other output which may be of use in the mean time?

---

### Post by varunendra on 2013-06-10
> **scbingham said:**
> As you can see, there's no mention of the wireless card. Also there's no mention of it in the BIOS.
After the laptop has booted, the wireless card can be turned on & off by pressing Fn + F10. There is no difference to the lspci output whether it is on or off.
Hmm.. doesn't make sense. I'm wondering it the so called PCIe card is somehow using a USB bus. Please also check-
```
lsusb
```

**EDIT:**
Oh, and also -
```
sudo lshw -C network
```

---

### Post by scbingham on 2013-06-10
lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bb4:0ff9 High Tech Computer Corp. Desire / Desire HD / Hero (Charge Mode)
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 002: ID 0425:0001 Motorola Semiconductors HK, Ltd 
Bus 001 Device 006: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter

If I switch the adapter off, it disappears from the list.

---

### Post by varunendra on 2013-06-10
> **scbingham said:**
> lsusb:
Bus 001 Device 006: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter

If I switch the adapter off, it disappears from the list.
Like I suspected, nothing surprising.

In the same way your other card should also appear in lsusb. I believe this is the very reason why your BIOS does not show any wireless settings - it is not using the pci bus at all !

Try it when you get the card tomorrow.

---

### Post by scbingham on 2013-06-10
sudo lshw -C network:  (I've omitted the bits about the wired adapter.
 *-network
       description: Wireless interface
       physical id: 4
       bus info: usb@1:1
       logical name: wlan0
       serial: 00:16:44:ad:9c:ff
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.2.0-45-generic firmware=N/A ip=192.168.1.68 link=yes multicast=yes wireless=IEEE 802.11bg

If I switch it off, it doesn't appear in the output.

So, tomorrow when I get hold of the card & fit it, how will I be able to switch it on? In my original post there is an error listed in dmesg when I press Fn + F10

---

### Post by varunendra on 2013-06-10
> **scbingham said:**
> So, tomorrow when I get hold of the card & fit it, how will I be able to switch it on? In my original post there is an error listed in dmesg when I press Fn + F10
I believe resetting the BIOS with the card seated properly should make it work.

The reason I suspect this is that probably the BIOS has remembered the pin configuration of the current card, thus sending on/off signals according to the current one while they should be different for the atheros one. Resetting BIOS should 'force' it to probe all the attached devices again and configure them as suitable.

In any case, trying is better than guessing ;)

---

### Post by scbingham on 2013-06-10
Makes sense. When I get into the thing (bit of a nightmare) I'll look for a reset switch or maybe just pull the clock battery & see what occurs.
In the mean time, thanks for your assistance so far. :D

---

### Post by varunendra on 2013-06-10
> **scbingham said:**
> Makes sense. When I get into the thing (bit of a nightmare) I'll look for a reset switch or maybe just pull the clock battery & see what occurs.
In the mean time, thanks for your assistance so far. :D

You're welcome!
I hope we succeed in the last.

*(oh, 5:35 in the morning.... guess it's time to sleep now :P)*

---

### Post by scbingham on 2013-06-11
Atheros card installed. I removed the motherboard battery for 15+ mins.
Reassembled, powered up & straight into Ubuntu, as if nothing had ever happened.
Tried Fn + F10. Nothing, except the following from dmesg:

61.751965] atkbd serio0: Unknown key released (translated set 2, code 0xad on isa0060/serio0).
[   61.751971] atkbd serio0: Use 'setkeycodes e02d <keycode>' to make it known.

So, I'm back at square one. :(

---

### Post by varunendra on 2013-06-12
Sorry it took me so long to reply. But I couldn't find any matching cases anywhere to be able to suggest anything.

If even BIOS (and lsusb) doesn't show it up, maybe the best thing to do first would be to contact the vendor asking whether such transition is possible or not on this machine. And if yes, then what are the compatibility aspects to look for.

We can try a few more things, but I doubt it would be of any use if the card itself turns out to be incompatible.

---

### Post by scbingham on 2013-06-12
These machines were made specifically for a high street retailer, Currys/Dixons, who are no longer trading on the high street.
I have read else where that in some circumstances machines such as these often have the BIOSs configured so upgrades, except memory or disks, are not possible. This is to make it easier for in store staff to support them.

Looks as though I have one of these :(, so no point in flogging a dead horse.

Thanks anyway for all your efforts. I'll mark this as solved.

---

