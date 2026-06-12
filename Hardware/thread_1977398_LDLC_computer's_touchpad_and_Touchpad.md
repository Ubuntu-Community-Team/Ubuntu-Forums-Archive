---
title: "LDLC computer's touchpad and Touchpad"
date: 2012-05-10
forum: Hardware
---

### Post by lorap1 on 2012-05-10
Hello, 
I have an ultra-portable computer LDLC Mercury NB3-BBN, purchased in late 2011. 
Impossible to recognize the touchpad as 10.04. 
I've scoured the documentation on the touchpad and installed gpointing  unresponsive, but gsynaptics. 
However, he always asks "Could not initialize gsynaptics. 
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use gsynaptics ". 
But I did everything according to the doc. Same  sign as / etc / default / grub option "i8042.nopnp" on the requested  row like this: GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash i8042.nopnp" 
Is what I did right?
I have an ultraportable, I've installed ubuntu netbook but 10.04 Lucid. The touchpad does not work. I followed the thread, I put the result of the following tests:

user @ user-laptop: ~ $ aptitude show xserver-xorg-input-synaptics | grep Version
Version: 1.2.2-1ubuntu4
user @ user-laptop: ~ $ egrep-i 'synaptic | alps | ETPS' / proc / bus / input / devices
user @ user-laptop: ~ $ lspci
00:00.0 Host bridge: Intel Corporation DMI N10 Family Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Integrated Graphics Controller Family N10 (rev 02)
00:02.1 Display controller: Intel Corporation Integrated Graphics Controller Family N10 (rev 02)
00:1 b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1 c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1 c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1 d.0 USB Controller: Intel Corporation USB UHCI Controller N10/ICH7 Family # 1 (rev 02)
00:1 d.1 USB Controller: Intel Corporation USB UHCI N10/ICH 7 Family Controller # 2 (rev 02)
00:1 d.2 USB Controller: Intel Corporation USB UHCI N10/ICH 7 Family Controller # 3 (rev 02)
00:1 d.3 USB Controller: Intel Corporation USB UHCI N10/ICH 7 Family Controller # 4 (rev 02)
00:1 d.7 USB Controller: Intel Corporation USB2 EHCI N10/ICH 7 Family Controller (rev 02)
00:1 E.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1 F.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1 f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1 f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc.. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
user @ user-laptop: ~ $ xinput-list
&#9121; Virtual core pointer id = 2 [master point (3)]
&#9116; &#8627; Virtual core pointer XTEST id = 4 [Slavic point (2)]
&#9116; &#8627; 2way 2.4GHz RF Mouse Receiver id = 10 [slave pointer (2)]
&#9116; &#8627; PS / 2 Generic Mouse id = 12 [slave pointer (2)]
&#9116; &#8627; Macintosh mouse button emulation id = 13 [slave pointer (2)]
Virtual core keyboard &#9123; id = 3 [master keyboard (2)]
    &#8627; Virtual core keyboard XTEST id = 5 [slave keyboard (3)]
    &#8627; Power Button id = 6 [slave keyboard (3)]
    &#8627; Video Bus id = 7 [slave keyboard (3)]
    &#8627; Power Button id = 8 [slave keyboard (3)]
    &#8627; Sleep Button id = 9 [slave keyboard (3)]
    &#8627; AT Translated Set 2 keyboard id = 11 [slave keyboard (3)]
user @ user-laptop: ~ $

So I did not have the possibility to change  kernel though mine is updated.
Can you help me? I changed the file / usr/lib/X11/xorg.conf.d/10-synaptics.conf. Here as I have changed:

Section "InputClass"
    Identifier "touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/ dev / input / event *"
    Driver "synaptics"
        Option "SHMConfig" "true"
EndSection

Section "InputClass"
    Identify "Dell Inspiron Embedded buttons quirks"
    MatchTag "inspiron_1011 | inspiron_1012"
    MatchDevicePath "/ dev / input / event *"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "90"
    Option "AreaBottomEdge" "4100"
EndSection

Section "InputClass"
    Identify "Dell Inspiron quirks"
    MatchTag "inspiron_1120"
    MatchDevicePath "/ dev / input / event *"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "250"
EndSection

Section "InputClass"
    Identifier "HP Mininote quirks"
    MatchTag "mininote_1000"
    MatchDevicePath "/ dev / input / event *"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "20"
EndSection

Is what I did right?
I doubt that we should change the touchpad in the bios. Indeed, I had a full Windows 7 who was operating the touch pad on the machine.
Can you help me?
Obviously, the "Touchpad" I installed does not work: it gives me:

Could not initialize gsynaptics.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use gsynaptics

Solutions?

---

