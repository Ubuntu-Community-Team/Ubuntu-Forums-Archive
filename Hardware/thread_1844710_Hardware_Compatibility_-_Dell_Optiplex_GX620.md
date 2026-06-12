---
title: "Hardware Compatibility - Dell Optiplex GX620"
date: 2011-09-15
forum: Hardware
---

### Post by Sponge34 on 2011-09-15
Hi,

Not a question, more a 'results of empirical experiment'...

HTC Desire, Dell Optiplex G620, Ubuntu 11.04 Unity + Gnome

The above combination does not mount the Desire if any of the following are true:
1. You use the Front USB Ports
2. You use a Rear USB port for a Cherry keyboard (RS14100 USB/FPR)with a USB Hub and you then plug the phone into the hub.

I suspect that it is to do with the USB power because if you connect the phone to the rear port directly it mounts fine.

Err, now I feel a little puzzled because having plugged the thing in on the rear and successfully mounted it, using the front ports now seems to work as expected.

Interestingly if you use the same phone in the front ports on a Dell Precision 380, Ubuntu 11.04 + Xfce everything behaves as you would expect.

On the GX620 Ubuntu 10.10 + Gnome both the failing port combinations worked.

/me heads down to the shops for a long micro USB cable

S.

dmesg tail for when it fails on the GX620 (Keyboard Hub)
[FONT="Courier New"][1200560.921104] usb 4-2.1: new full speed USB device using uhci_hcd and address 13
[1200561.023096] usb 4-2.1: not running at top speed; connect to a high speed hub
[1200561.051284] usb 4-2.1: rejected 1 configuration due to insufficient available bus power
[1200561.051291] usb 4-2.1: no configuration chosen from 1 choice
[/FONT]


dmesg tail for when it works on the GX620

[FONT="Courier New"][1199663.220020] usb 1-5: new high speed USB device using ehci_hcd and address 4
[1199663.366614] scsi5 : usb-storage 1-5:1.0
[1199664.367168] scsi 5:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[1199664.368468] sd 5:0:0:0: Attached scsi generic sg1 type 0
[1199664.375515] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[1199693.012816] sd 5:0:0:0: [sdb] 7698432 512-byte logical blocks: (3.94 GB/3.67 GiB)
[1199693.017046] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[1199693.025778] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[1199693.186722]  sdb: sdb1
[1199736.039651] sdb: detected capacity change from 3941597184 to 0
[1199745.199561] usb 1-5: USB disconnect, address 4[/FONT]

---

### Post by dougalkerr on 2011-09-15
So, what's the outcome/your conclusions?

I use a GX620 at work dual booted with Win7 (coz I have to) and Ubuntu Ultimate Edition 2.9 at the moment, waiting for UE 3.0 to come out and stop hearts.
The problems you found with the front ports might lead me to think that is the reason for certain things failing to be connected properly in Win7 too.

I wish manufacturers would properly test things before they say they have a working product, tuh!!!
Anyways, hopefully changing to a new Dell 790 before long. that will be interesting with Compiz Fusion and all the eye candy I can throw at it.
Now if I can only get the mouse gestures to work so that I have a more Android or Apple like feel about the whole thing...

---

