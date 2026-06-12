---
title: "FAIL: Orinoco / Hermes (Buffalo brand) PCMCIA NIC under Ubuntu 9.10"
date: 2009-11-03
forum: Hardware
---

### Post by bluechristian on 2009-11-03
Prologue: I love Ubuntu, and am ultra-impressed w/ all of those who create and upkeep Ubuntu. Kudos.

The Problem: My Orinoco (Buffalo brand) card worked under 9.02 and previous versions of Ubuntu. I upgraded to 9.2. Two kernels are installed by default, apparently, one (the *.28* kernel) works but disables my sound card and laptop synaptic touch pad. (I use it right now w/ an external USB mouse, but this isn't acceptable.) 

I want the newer (*.32 ?) kernel (and its successors, as they appear!) to work... and it does w/ sound card and touch pad. It does not, however, power up the Orinoco card. Here are some output lines I garnered which may help:

lshw returned this from each kernel (older kernel -- card works -- first):[INDENT]  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:3c:3b:ea
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 6.16 ip=192.168.11.100 multicast=yes wireless=IEEE 802.11b
jon@jon-laptop:~$ 
[/INDENT]---
AND THIS IS FROM THE LATER (NEWER) KERNEL (only took the bit re eth1 -- the orinoco) -- the card is present but fails to fully configure:[INDENT]  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:3c:3b:ea
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
[/INDENT]Note the fail on the last line to configure the device in the second kernel above.

Portion of dmesg file (focusing on the newer kernel now) showing ultimate failure of orinoco card to load:[INDENT][   52.444907] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[   52.680284] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   52.684513] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   52.686190] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   52.687711] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   52.690142] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   52.691888] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   52.788195] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[   53.126424] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   53.240887] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   53.304493] ALI 5451 0000:00:06.0: enabling device (0005 -> 0007)
[   53.305398] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
[   53.305412] PCI: setting IRQ 5 as level-triggered
[   53.305431] ALI 5451 0000:00:06.0: PCI INT A -> Link[LNK7] -> GSI 5 (level, low) -> IRQ 5
[   53.381944] eth1: Hardware identity 0001:0002:0004:0002
[   53.382087] eth1: Station identity  001f:0001:0006:0010
[   53.382101] eth1: Firmware determined as Lucent/Agere 6.16
[   53.385881] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
[   53.484288] eth1: Attempting to download firmware agere_sta_fw.bin
[   53.484336] hermes_dld: AUX enable returned 0
[   53.486077] hermes_dld: AUX disable returned 0
[   53.486087] hermes_dld: Actual PDA length 998, Max allowed 1000
[   53.486097] eth1: Read PDA returned 0
[   53.486115] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
[   53.509296] eth1: Cannot find firmware agere_sta_fw.bin
[   53.509414] eth1: Hardware identity 0001:0002:0004:0002
[   53.509554] eth1: Station identity  001f:0001:0006:0010
[   53.509568] eth1: Firmware determined as Lucent/Agere 6.16
[   53.509578] eth1: Ad-hoc demo mode supported
[   53.509587] eth1: IEEE standard IBSS ad-hoc mode supported
[   53.509596] eth1: WEP supported, 104-bit key
[   53.509726] eth1: MAC address 00:02:2d:3c:3b:ea
[   53.509869] eth1: Station name "HERMES I"
[   53.510591] eth1: ready
[   53.513174] eth1: orinoco_cs at 0.0, irq 3, io 0x0100-0x013f
[   55.521428] type=1505 audit(1257105983.026:12): operation="profile_replace" pid=717 name=/usr/share/gdm/guest-session/Xsession
[   56.156958] type=1505 audit(1257105983.662:13): operation="profile_replace" pid=718 name=/sbin/dhclient3
[   56.157779] type=1505 audit(1257105983.662:14): operation="profile_replace" pid=718 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   56.158144] type=1505 audit(1257105983.662:15): operation="profile_replace" pid=718 name=/usr/lib/connman/scripts/dhclient-script
[   56.184180] AC'97 1 does not respond - RESET
[   56.208152] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   56.208195] ali mixer 1 creating error.
[   63.638650] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   63.713512] eth0: DSPCFG accepted after 0 usec.
[   63.713750] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   64.389810] eth1: New link status: Disconnected (0002)
[   64.660179] hermes @ 00010100: Timeout waiting for command 0x0002 completion.
[   64.660179] eth1: Unable to disable port while reconfiguring card
[   64.660179] eth1: Resetting instead...
[   65.262286] eth1: Attempting to download firmware agere_sta_fw.bin
[   65.262341] hermes_dld: AUX enable returned 0
[   65.264203] hermes_dld: AUX disable returned 0
[   65.264213] hermes_dld: Actual PDA length 998, Max allowed 1000
[   65.264225] eth1: Read PDA returned 0
[   65.264246] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
[   65.284006] eth1: Cannot find firmware agere_sta_fw.bin
[   65.284305] eth1: orinoco_reset: Error -2 re-initializing firmware
[   65.284415] eth1: Device has been disabled!
[/INDENT]I greatly appreciate any help which can be offered to rectifiy this.

Thank you.

---

### Post by bluechristian on 2009-11-03
Ack! NOT 9.2... I wrote that, but meant 9.10 is the new upgrade installation of Ubuntu. Sorry.

---

### Post by bluechristian on 2009-11-03
And re hardware:

I'm running a Compaq Presario 2545 (Pentium 4) laptop. It had an internal Broadcom wireless NIC, which didn't work in Linux and which I physically removed from the laptop. (So there's no hardware conflict occurring on that front.) It also has an internal (wired) NIC, which has never conflicted and which I strongly doubt has anything to do with the current issue.

Will give any additional info upon request. I consider myself fairly sophisticated re Ubuntu and Linux, but admit I've never compiled a kernel... :)

---

### Post by bluechristian on 2009-12-03
Heh... I guess I'm talking to myself here... but an update.

My Compaq laptop failed. Long story. Wont' tell it.

Pulled my 60g hard drive with Ubuntu 9.1 on it from Compaq 2510us and stuck it into a Dell Latitude C610 (1.2 ghz Pentium M (III) CPU, 756 megs memory).

Booted into it expecting a mess due to hardware changes. It came up FLAWLESSLY -- which I did not expect at all!

*EXCEPT*!!!!

The same network card issues still exist with my Buffalo Orinoco / Hermes card.

However, I can now get the card to work... but how is not good.

Initially, the card's power light and second light, the connectivity light, both go green. But after a few seconds of activity, the connectivity light goes dark. 

The card is designated as eth1 -- but iwconfig shows it as not being defined a wireless card.

After repeatedly unplugging and replugging the card, iwconfig will suddenly show it being there. But the second I use wicd to look at what networks are available (I replaced the original gnome / ubuntu network manager w/ wicd a while back when trying to diagnose this same issue), the card's connectivity light goes out again and wicd reports there are no networks to see. Checking iwconfig again reveals that eth1 is no longer listed as a wireless card.

After again replugging the card, I end up manuall inputting the info via terminal session:

sudo iwconfig essid mynetwork key hexnumber 

And here's where I have some hope... because after I do this, and type in iwconfig, I get the proper information back. Everything says it is up and running.

HOWEVER I am not yet truly connected. I can't get on line. So I click the wicd icon on my task bar. It shows networks, but the second I click on one, BOOM! THE NIC's LIGHT GOES OUT AGAIN. Sheesh.

This is repeated over and over... and at some point, suddenly, the card and wicd see each other. I am able to click the network I want and it instantly connects.

But no ryhme or reason here, folks. Help? I keep thinking there's some sort of conflict between two different files, programs, or some such both wanting control of the card. Maybe even two drivers? I checked the blacklist and all that, nothing there to see.

I spend up to 15 minutes getting connected every time I reboot my machine. 

Again ANY help appreciated.

---

