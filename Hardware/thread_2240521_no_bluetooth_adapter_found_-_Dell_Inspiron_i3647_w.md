---
title: "no bluetooth adapter found - Dell Inspiron i3647 with Ubuntu 14"
date: 2014-08-20
forum: Hardware
---

### Post by murtaza2 on 2014-08-20
Hi All,

I am some what of a newbie to Ubuntu but can get around with instructions.
 
I installed Ubuntu 14 on my recently purchased  Dell Inspiron i3647 which originally came with windows 8.1. Everything works correct in windows. It has a built in Dell Wireless-N 1705 + Bluetooth 4.0. After installed Ubuntu, during boot I am seeing a bluetooth adapter error that quickly flashes. Once the system boots up no bluetooth adapter is found. I already ran [FONT=Ubuntu Mono]sudo rfkill list[/FONT] but no bluetooth adapter is listed and nothing is soft blocked. Wifi works fine as far as i can tell. 

I have not yet installed the linux-firmware[COLOR=#333333][FONT=UbuntuRegular] and [/FONT][/COLOR]linux-firmware-nonfreepackages but am wondering if there is anything else I need to look at? 

How can I check what the error is that flashes during the boot process? 

Help would be greatly appreciated! 

Ken

---

### Post by murtaza2 on 2014-08-20
BTW I have Ubuntu  64bit installed. I am getting the following error during startup....

10.531718] Bluetooth: Core ver 2.17
[   10.531742] Bluetooth: HCI device and connection manager initialized
[   10.531748] Bluetooth: HCI socket layer initialized
[   10.531749] Bluetooth: L2CAP socket layer initialized
[   10.531752] Bluetooth: SCO socket layer initialized
[   13.773999] Bluetooth: Error in firmware loading err = -110,len = 448, size = 4096
[   13.774029] Bluetooth: Loading patch file failed
[   15.648957] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.648960] Bluetooth: BNEP filters: protocol multicast
[   15.648981] Bluetooth: BNEP socket layer initialized
[   15.658859] Bluetooth: RFCOMM TTY layer initialized
[   15.658868] Bluetooth: RFCOMM socket layer initialized
[   15.658872] Bluetooth: RFCOMM ver 1.11
[  519.874749] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  519.874759] Bluetooth: HIDP socket layer initialized
[  549.002731] input: Bluetooth Wireless Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/bluetooth/hci0/hci0:2/input15
[  549.003070] hid-generic 0005:045E:8502.0004: input,hidraw0: BLUETOOTH HID v1.1b Keyboard [Bluetooth Wireless Keyboard] on 00:15:83:0c:bf:eb

---

### Post by weatherman2 on 2014-08-20
Have you tried installing all the latest Ubuntu updates?  Sometimes these kinds of problems get fixed with updates.

There is a known bug that is similar to what you report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1242079](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1242079)

There is a recent response at the bottom (#57) that claims to have a solution for Ubuntu 14.04.

---

### Post by murtaza2 on 2014-08-20
Thanks I am gonna give this a try....its getting frustrated since this is a brand new machine and I went through all the trouble of installed ubuntu on it. I still have to get the IRC remote working which seems to have issues as well :/

---

### Post by weatherman2 on 2014-08-20
Often the newest machines have the most issues, because the developers have seen the hardware for the least amount of time, if at all.  

On another note: did you have to install an "Additional Driver" for your wireless card?  If not, search your desktop for "Additional Drivers" and see if one is offered for your wireless card (could have automatically been installed in 14.04).  I know a lot of the Broadcom wireless cards have needed an "Additional Driver" to function in Ubuntu.  There may also be optional drivers offered.

---

### Post by murtaza2 on 2014-08-21
Thanks! no additional drivers are found. I tried what posted in #3 by going to that URL and following the directions there. It seemed to work because bluetooth was found and i even used my wireless keyboard for a while but after i rebooted I am again back to the same issue...

here is the error again:

[    8.810823] Bluetooth: Core ver 2.17
[    8.810836] Bluetooth: HCI device and connection manager initialized
[    8.810842] Bluetooth: HCI socket layer initialized
[    8.810843] Bluetooth: L2CAP socket layer initialized
[    8.810846] Bluetooth: SCO socket layer initialized
[   11.414484] Bluetooth: RFCOMM TTY layer initialized
[   11.414494] Bluetooth: RFCOMM socket layer initialized
[   11.414498] Bluetooth: RFCOMM ver 1.11
[   11.665980] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.665983] Bluetooth: BNEP filters: protocol multicast
[   11.665991] Bluetooth: BNEP socket layer initialized
[   11.958737] Bluetooth: Error in firmware loading err = -110,len = 448, size = 1906
[   11.958768] Bluetooth: Loading sysconfig file failed

---

### Post by weatherman2 on 2014-08-21
It could be you'll need to do those late three lines every time you boot to make it persistent.  I'm not sure of the best way to do this - but one might be to put these lines:

```

[COLOR=#333333][FONT=monospace]cp bt-bcm43142/lib/firmware/BCM43142A0_001.001.011.0028.0036.hcd /lib/firmware/fw-105b_e065.hcd
rmmod btusb
modprobe btusb

```

inside the file /etc/rc.local (which gets run as root or "sudo" each time you boot).

(edit it as "sudo" - e.g. "sudo gedit /etc/rc.local" from a terminal.)

You'll need to put that file bt-bcm43142/lib/firmware/BCM43142A0_001.001.011.0028.0036.hcd somewhere safe so it can be copied each boot.  Perhaps you could put that file in /lib/firmware .  Then modify that first cp command to include the real path of the original firmware file.

There may be a better/easier way to make this change persistent but that's the first thing that comes to mind.[/FONT][/COLOR]

---

### Post by murtaza2 on 2014-08-21
Thanks! I don't think the commands for the custom firmware needs to be rerun each time since the firmware file remains in its location after reboot. I was able to get the bluetooth adapter working once again when i booted with a USB keyboard/mouse plugged in and then enabling the bluetooth keyboard from the bluetooth settings. It didn't enable it by default but the adapter was found. 

I also noticed that when a USB keyboard is not plugged in during boot I see a "**keyboard failure**" error message and the bluetooth adapter is not found after the system boots up. I have to test more to see if this happened because the bluetooth keyboard was off (i don't remember) or if the firmware is not loaded at that time and so the adapter is not enabled.

- Ken

---

### Post by weatherman2 on 2014-08-21
You can get rid of the "keyboard failure" error by entering BIOS Setup (tap F2 when you are powering up the computer) and allow "headless" operation - or "keyboard less" operation.  Something like that.  The downside of bluetooth keyboards is that you generally can't pair them and use them before an operating system loads.

---

### Post by murtaza2 on 2014-08-21
Its F12 for my machine and I didn't see any option for "headless" operation while I was checking to make sure bluetooth is enabled, but i'll double check.

---

### Post by weatherman2 on 2014-08-21
Usually, on a Dell F12 is for the boot menu (which may also have a link to enter BIOS Setup).  On every Dell I've ever worked on, F2 gets you directly into BIOS Setup.

It may not be called "headless" - different manufacturers call it different things.  Most modern computers do have this option.  Look for anything related to the keyboard, report keyboard errors, etc.

---

### Post by murtaza2 on 2014-08-21
Ok thats good to know...that might be why i didnt see that option because I went through it by pressing F12. I'll give that a try! Thanks!

---

### Post by murtaza2 on 2014-08-22
Went into the BIOS and turned off "alert on keyboard errors". Bluetooth adapter is again not being found after restart...looks like its a hit or miss on the bluetooth adapter, its not working consistently. I am starting to think Windows 8.1 might be a better path for now until some of these issues with the never hardware are wrinkled out by Ubuntu. I have already spent 3 long nights trying to figure out the bluetooth and LIRC issues so i can have a working HTPC. Everything works flawlessly in Windows 8.1 and I also read an article on how to setup windows 8.1 so it boot directly into XBMC without all the default processes running. Which is the main reason for going with Ubuntu. 

Thanks for all your help guys! 

- Ken

---

### Post by Gregoire_Cyr on 2014-08-23
> **weatherman2 said:**
> Have you tried installing all the latest Ubuntu updates?  Sometimes these kinds of problems get fixed with updates.

There is a known bug that is similar to what you report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1242079](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1242079)

There is a recent response at the bottom (#57) that claims to have a solution for Ubuntu 14.04.
 Is this the same firmware for dell xps 8700, cause I have the same problem

---

### Post by jeremy31 on 2014-08-23
I would want to see the output of ```
lspci -iA2 net
``` and ```
lsusb
``` before I make any suggestions and ```
lsmod
``` would be helpful

---

### Post by Gregoire_Cyr on 2014-08-23
> **jeremy31 said:**
> I would want to see the output of ```
lspci -iA2 net
``` and ```
lsusb
``` before I make any suggestions and ```
lsmod
``` would be helpful

there it is:


tiness@tiness-XPS-8700:~/Downloads$ lspci -iA2 net
Usage: lspci [<switches>]


Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree


Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers


Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS


Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's


Other options:
-i <file>	Use specified ID database instead of A2
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)


PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file
tiness@tiness-XPS-8700:~/Downloads$ lspci -iA2 net
Usage: lspci [<switches>]


Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree


Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers


Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS


Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's


Other options:
-i <file>	Use specified ID database instead of A2
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)


PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file



tiness@tiness-XPS-8700:~/Downloads$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:0184 Realtek Semiconductor Corp. RTS5182 Card Reader
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 413c:2112 Dell Computer Corp. 
Bus 003 Device 007: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 003 Device 006: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



tiness@tiness-XPS-8700:~/Downloads$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:0184 Realtek Semiconductor Corp. RTS5182 Card Reader
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 413c:2112 Dell Computer Corp. 
Bus 003 Device 007: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 003 Device 006: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tiness@tiness-XPS-8700:~/Downloads$ lsmod
Module                  Size  Used by
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
nls_utf8               12557  1 
udf                    89723  1 
crc_itu_t              12707  1 udf
joydev                 17381  0 
xt_tcpudp              12884  2 
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  3 ip_tables,xt_tcpudp,iptable_filter
rfcomm                 69160  4 
bnep                   19624  2 
nvidia              10540234  60 
nls_iso8859_1          12713  1 
arc4                   12608  2 
x86_pkg_temp_thermal    14205  0 
snd_hda_codec_hdmi     46368  1 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm_intel             143060  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
kvm                   451511  1 kvm_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ath3k                  13318  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
crct10dif_pclmul       14289  0 
btusb                  32412  0 
mei_me                 18627  0 
dcdbas                 14928  0 
drm                   303102  2 nvidia
bluetooth             391136  12 bnep,ath3k,btusb,rfcomm
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
aesni_intel            55624  0 
mei                    82276  1 mei_me
lpc_ich                21080  0 
aes_x86_64             17131  1 aesni_intel
mac_hid                13205  0 
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
video                  19476  0 
ablk_helper            13597  1 aesni_intel
soundcore              12680  1 snd
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              13462  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ses                    17363  0 
enclosure              15368  1 ses
usb_storage            62209  2 
hid_logitech_dj        18581  0 
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  6 hid_generic,usbhid,hid_logitech_dj
ahci                   25819  3 
r8169                  67581  0 
psmouse               106678  0 
libahci                32716  1 ahci
mii                    13934  1 r8169
tiness@tiness-XPS-8700:~/Downloads$

---

### Post by jeremy31 on 2014-08-24
> **Gregoire_Cyr said:**
> there it is:

```

tiness@tiness-XPS-8700:~/Downloads$ lspci -iA2 net
Usage: lspci [<switches>]


Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree


Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers


Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS


Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's


Other options:
-i <file>    Use specified ID database instead of A2
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)


PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
tiness@tiness-XPS-8700:~/Downloads$ lspci -iA2 net
Usage: lspci [<switches>]


Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree


Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers


Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS


Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's


Other options:
-i <file>    Use specified ID database instead of A2
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)


PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file



tiness@tiness-XPS-8700:~/Downloads$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:0184 Realtek Semiconductor Corp. RTS5182 Card Reader
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 413c:2112 Dell Computer Corp. 
Bus 003 Device 007: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 003 Device 006: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



tiness@tiness-XPS-8700:~/Downloads$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:0184 Realtek Semiconductor Corp. RTS5182 Card Reader
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 413c:2112 Dell Computer Corp. 
Bus 003 Device 007: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 003 Device 006: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tiness@tiness-XPS-8700:~/Downloads$ lsmod
Module                  Size  Used by
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
nls_utf8               12557  1 
udf                    89723  1 
crc_itu_t              12707  1 udf
joydev                 17381  0 
xt_tcpudp              12884  2 
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  3 ip_tables,xt_tcpudp,iptable_filter
rfcomm                 69160  4 
bnep                   19624  2 
nvidia              10540234  60 
nls_iso8859_1          12713  1 
arc4                   12608  2 
x86_pkg_temp_thermal    14205  0 
snd_hda_codec_hdmi     46368  1 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm_intel             143060  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
kvm                   451511  1 kvm_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ath3k                  13318  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
crct10dif_pclmul       14289  0 
btusb                  32412  0 
mei_me                 18627  0 
dcdbas                 14928  0 
drm                   303102  2 nvidia
bluetooth             391136  12 bnep,ath3k,btusb,rfcomm
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
aesni_intel            55624  0 
mei                    82276  1 mei_me
lpc_ich                21080  0 
aes_x86_64             17131  1 aesni_intel
mac_hid                13205  0 
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
video                  19476  0 
ablk_helper            13597  1 aesni_intel
soundcore              12680  1 snd
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              13462  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ses                    17363  0 
enclosure              15368  1 ses
usb_storage            62209  2 
hid_logitech_dj        18581  0 
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  6 hid_generic,usbhid,hid_logitech_dj
ahci                   25819  3 
r8169                  67581  0 
psmouse               106678  0 
libahci                32716  1 ahci
mii                    13934  1 r8169
tiness@tiness-XPS-8700:~/Downloads$
```

Oh well, I messed up the first command, it should have been ```
lspci | grep -iA2 net
```
But that doesn't really matter, the rest shows what is needed, you have an Atheros Bluetooth chipset ```
Bus 003 Device 007: ID 0cf3:3004 Atheros Communications, Inc
``` with all the correct modules loaded, now lets see if the firmware files are on the system ```
ls /lib/firmware/ar3k
```

---

### Post by Gregoire_Cyr on 2014-08-24
> **jeremy31 said:**
> Oh well, I messed up the first command, it should have been ```
lspci | grep -iA2 net
```
But that doesn't really matter, the rest shows what is needed, you have an Atheros Bluetooth chipset ```
Bus 003 Device 007: ID 0cf3:3004 Atheros Communications, Inc
``` with all the correct modules loaded, now lets see if the firmware files are on the system ```
ls /lib/firmware/ar3k
```



Im getting this:

tiness@tiness-XPS-8700:~$ bus 003 Device 007: ID 0cf3:3004 Atheros Communications, Inc                                                                                                                                                                                         
DEBUG: Log opened                                                                                                                                                                                                                                                              
ERROR: Usage:                                                                                                                                                                                                                                                                  
ERROR: bus [-d module]... [-m module]...[-f conf_file]                                                                                                                                                                                                                         
tiness@tiness-XPS-8700:~$ ls /lib/firmware/ar3k                                                                                                                                                                                                                                
AthrBT_0x01020001.dfu  AthrBT_0x01020201.dfu  AthrBT_0x31010000.dfu  ramps_0x01020001_26.dfu  ramps_0x01020200_40.dfu  ramps_0x01020201_40.dfu  ramps_0x31010000_40.dfu                                                                                                        
AthrBT_0x01020200.dfu  AthrBT_0x11020000.dfu  AthrBT_0x41020000.dfu  ramps_0x01020200_26.dfu  ramps_0x01020201_26.dfu  ramps_0x11020000_40.dfu  ramps_0x41020000_40.dfu                                                                                                        
tiness@tiness-XPS-8700:~$

---

### Post by jeremy31 on 2014-08-24
So it looks like the correct firmware is there, any error in dmesg ```
dmesg | grep "usb 3-7"
```

---

### Post by Gregoire_Cyr on 2014-08-24
> **jeremy31 said:**
> So it looks like the correct firmware is there, any error in dmesg ```
dmesg | grep "usb 3-7"
```


tiness@tiness-XPS-8700:~$ dmesg | grep "usb 3-7"
[    1.762632] usb 3-7: new high-speed USB device number 4 using xhci_hcd
[    1.788220] usb 3-7: New USB device found, idVendor=0bda, idProduct=0184
[    1.788223] usb 3-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.788224] usb 3-7: Product: USB2.0-CRW
[    1.788225] usb 3-7: Manufacturer: Generic
[    1.788225] usb 3-7: SerialNumber: 20100818841300000
tiness@tiness-XPS-8700:~$

---

### Post by jeremy31 on 2014-08-24
Ok, that isn't the correct device try ```
dmesg | grep "usb 3-8"
```

---

### Post by Gregoire_Cyr on 2014-08-24
> **jeremy31 said:**
> Ok, that isn't the correct device try ```
dmesg | grep "usb 3-8"
```


Its giving me nothing...

---

### Post by jeremy31 on 2014-08-24
```
dmesg | grep -i atheros
```
```
sudo dpkg --get-selections | grep -i blue
```
```
cat /sys/class/dmi/id
```

---

### Post by Gregoire_Cyr on 2014-08-24
> **jeremy31 said:**
> ```
dmesg | grep -i atheros
```
```
sudo dpkg --get-selections | grep -i blue
```
```
cat /sys/class/dmi/id
```


tiness@tiness-XPS-8700:~$ dmesg | grep -i atheros
[    2.160529] usb 3-13: Manufacturer: Atheros Communications
[    9.019471] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90006180000, irq=19
tiness@tiness-XPS-8700:~$ sudo dpkg --get-selections | grep -i blue
[sudo] password for tiness: 
bluedevil                                       install
blueman                                         install
bluetooth                                       install
bluewho                                         install
bluez                                           install
bluez-alsa:amd64                                install
bluez-cups                                      install
bluez-gstreamer                                 install
bluez-hcidump                                   install
bluez-tools                                     install
gir1.2-gnomebluetooth-1.0                       install
gnome-bluetooth                                 install
indicator-bluetooth                             install
libbluedevil1:amd64                             install
libbluetooth3:amd64                             install
libgnome-bluetooth11                            install
pulseaudio-module-bluetooth                     install
python-bluez                                    install
tiness@tiness-XPS-8700:~$ cat /sys/class/dmi/id
cat: /sys/class/dmi/id: Is a directory
tiness@tiness-XPS-8700:~$

---

### Post by jeremy31 on 2014-08-24
Not my day ```
cat /sys/class/dmi/id/modalias
```

Same wifi card as mine
```
dmesg | grep "usb 3-13"
```
```
rfkill list
```

---

### Post by Gregoire_Cyr on 2014-08-24
> **jeremy31 said:**
> Not my day ```
cat /sys/class/dmi/id/modalias
```

Same wifi card as mine
```
dmesg | grep "usb 3-13"
```
```
rfkill list
```

BTW thank you very much for your time:p


tiness@tiness-XPS-8700:~$ cat /sys/class/dmi/id/modalias
dmi:bvnDellInc.:bvrA08:bd04/16/2014:svnDellInc.:pnXPS8700:pvr:rvnDellInc.:rn0KWVT8:rvrA03:cvnDellInc.:ct3:cvr:
tiness@tiness-XPS-8700:~$ dmesg | grep "usb 3-13"
[    2.142528] usb 3-13: new full-speed USB device number 6 using xhci_hcd
[    2.160524] usb 3-13: New USB device found, idVendor=0cf3, idProduct=3004
[    2.160527] usb 3-13: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.160528] usb 3-13: Product: Bluetooth USB Host Controller
[    2.160529] usb 3-13: Manufacturer: Atheros Communications
[    2.160530] usb 3-13: SerialNumber: Alaska Day 2006
tiness@tiness-XPS-8700:~$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
tiness@tiness-XPS-8700:~$

---

### Post by jeremy31 on 2014-08-24
Are you dual booted with Windows?  If you are, see if bluetooth is working there because something strange is going on

---

### Post by Gregoire_Cyr on 2014-08-24
> **jeremy31 said:**
> Are you dual booted with Windows?  If you are, see if bluetooth is working there because something strange is going on



Thats the thing.... I wiped it from the hard drive as it was pre-installed, but i tried bluetooth on windows before wiping it and it was working well.
So I guess that I would need to reinstall windows as dual boot and upgrade the drivers in order to get it working.... if so, I will wait till it really bugs me out, cuz right now its not really a deal breaker for me, i'll live survive without it;)

Thank you again! Your time and advices are really appreciated

---

### Post by jeremy31 on 2014-08-24
> **Gregoire_Cyr said:**
> Thats the thing.... I wiped it from the hard drive as it was pre-installed, but i tried bluetooth on windows before wiping it and it was working well.
So I guess that I would need to reinstall windows as dual boot and upgrade the drivers in order to get it working.... if so, I will wait till it really bugs me out, cuz right now its not really a deal breaker for me, i'll live survive without it;)

Thank you again! Your time and advices are really appreciated

It wouldn't be a driver update in windows but I wonder if a change in the grub parameter might help and it can't hurt. ```
sudo gedit /etc/default/grub
``` now find the line > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Change this line to be ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
``` save and exit gedit then ```
sudo update-grub
``` and reboot
It may or not help but I doubt it will cause problems.

This problem is strange because the Bluetooth is in dmesg and lsmod and even the proper modules are loaded yet rfkill doesn't have it listed

I have had good luck with the IOgear bluetooth USB dongles in Ubuntu but they are older models GBU221 and GBU421

---

### Post by Gregoire_Cyr on 2014-08-24
> **jeremy31 said:**
> It wouldn't be a driver update in windows but I wonder if a change in the grub parameter might help and it can't hurt. ```
sudo gedit /etc/default/grub
``` now find the line 
Change this line to be ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
``` save and exit gedit then ```
sudo update-grub
``` and reboot
It may or not help but I doubt it will cause problems.

This problem is strange because the Bluetooth is in dmesg and lsmod and even the proper modules are loaded yet rfkill doesn't have it listed

I have had good luck with the IOgear bluetooth USB dongles in Ubuntu but they are older models GBU221 and GBU421


Just to be sure before doing this, I get the line GRUB_CMDLINE_LINUX_DEFAULT="spalsh quiet"  instead of "quiet splash"   is it ok...

---

### Post by jeremy31 on 2014-08-25
> **Gregoire_Cyr said:**
> Just to be sure before doing this, I get the line GRUB_CMDLINE_LINUX_DEFAULT="spalsh quiet"  instead of "quiet splash"   is it ok...

As long as it is splash quiet and not spalsh quiet like you typed it, it should be fine

---

### Post by Gregoire_Cyr on 2014-08-25
> **jeremy31 said:**
> As long as it is splash quiet and not spalsh quiet like you typed it, it should be fine

Lol. As soon as I finish work, I'll try it and give you news...

---

### Post by Gregoire_Cyr on 2014-08-25
Unfortunately, bluetooth is not working after that trick:(  But as I said, I'm ok with it, I just wanted to try to fix it...at least:)

---

