---
title: "display + mouse issues"
date: 2011-11-24
forum: Hardware
---

### Post by rollyah on 2011-11-24
Dear all,
i have ubuntu 11.04 64bit installed on an hp pavilion g7

i'm facing the following issues:

1. On screen saver lock, all notifications are shown on screen
ie: thunderbird,pidgin,tweetdeck notifications are shown even though the screensaver is on and locked.

2. at times, the mouse' left click stops working, though the touchpad works normally. whenever i use the touchpad the mouse(Usb connected) works again.

3. when i minimize a page, and open another it's not rendering properly. in other wrods lets say i had tweetdeck and firefox opened on top. if i minimize firefox,the firefox page still shows and parts of tweetdeck appears only when i hover my mouse over them. the solution to that is to show desktop and then maximizing one of the windows.

note that all was working on 10.4 on the same device.

Relevant info:
lspci -v #only vga related info shown

01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company Device 1672
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at a0000000 (64-bit, prefetchable) [size=256M]
        Memory at c2600000 (64-bit, non-prefetchable) [size=128K]
        I/O ports at 4000 [size=256]
        Expansion ROM at c2620000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Legacy Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Capabilities: [150] Advanced Error Reporting
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx, radeon

dpkg --get-selections | grep ati

xserver-xorg-video-ati                          install

---

