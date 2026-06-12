---
title: "HP Mini 210-1000 Bluetooth blues"
date: 2010-04-23
forum: Hardware
---

### Post by Sisophon2001 on 2010-04-23
Hi,

I am trying to get a HP Mini 210-1000 to work with bluetooth without any success.I have read many posts with similar problems but none that I found report the same results from diagnostic programs.

In System Information (accessed on start-up by pressing Esc Key followed by F1) I am told I have

Bluetooth FCC ID : QDS-BRCM1044

When Ubuntu (UNR 9.10) starts the bluetooth icon displayed in the status bar but is greyed out, and a mouse over says 

Bluetooth : Disabled

Right clicking on the icon says

Bluetooth: On 

but I can see from trying to use it that nothing works.

When I try

```
garvan@hp-mini:~$ hciconfig
hci0:	Type: USB
	BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
	DOWN 
	RX bytes:0 acl:0 sco:0 events:0 errors:0
	TX bytes:0 acl:0 sco:0 commands:1 errors:1

garvan@hp-mini:~$
```

I get some errors that I do not understand.

Any ideas of what I might try next? Anybody with the same hardware running UNR?

As far as I know it was working (blue Icon anyway) before I installed the restricted Broadcom 802.11 Linux STA wireless driverfor. The wireless is more important than bluetooth if I must make a choice.

Thanks for any help

Garvan

---

### Post by Sisophon2001 on 2010-04-26
No reply, and I am still stuck. I know posts get lost in the forest here, so I will try one more time by bumping the message.

Garvan

---

### Post by P4man on 2010-04-26
If you can confirm  bluetooth works again when you disable the broadcom driver, then it would certainly warrant filing a bug report.

If it still doesnt work without the wifi driver, can you provide the output of

```
lsusb
```

and

```
lspci
```


BTW, it actually looks as if bluetooth is turned off. Does your laptop have a hardware button for bluetooth? Or is it a combined one for bluetooth and wifi? Can you toggle it, does it change anything?

---

### Post by FloorK on 2010-04-26
Same problem, hp mini 210
trying to connect to a bluetooth headset, to no avail
hope the below helps.

lsusb
Bus 001 Device 002: ID 5986:0182 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 03f0:2a1d Hewlett-Packard 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lspci
00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by P4man on 2010-04-26
Hmm same is reported here:
[http://getsatisfaction.com/jolicloud/topics/hp_mini_210_mostly_works](http://getsatisfaction.com/jolicloud/topics/hp_mini_210_mostly_works)

Broadcom driver seems to kill bluetooth. Id open a bug report on launchpad.

---

### Post by Sisophon2001 on 2010-04-27
> **P4man said:**
> If you can confirm  bluetooth works again when you disable the broadcom driver, then it would certainly warrant filing a bug report.

If it still doesnt work without the wifi driver, can you provide the output of ...<snip>

I uninstalled the broadcom driver and now bluetooth works perfectly.I can connect to and browse all the files on my mobile phone. The hardware key to switch bluetooth on and off also works. But I have no wireless.

In general I would prefer wireless to be working so I will reinstall the broadcom driver.

You talk about filing a bug report, but this is a restricted driver so I think the Ubuntu developers will do nothing. It may be better to report the bug to broadcom who wrote the driver. I would guess from the BRCM in the id of my Buletooth device that it is also a broadcom product?

Thanks for the help.

Garvan

---

### Post by P4man on 2010-04-27
The driver for the wifi might be restricted, but that doesnt necessarily mean its actually the drivers fault or cant be worked around. Even if canonical cant solve this, they would be well placed to contact broadcom about this. Id still open a bug report (if for no other reason that also others can find out about the issue and possibly post workarounds). Also the same driver I think works fine on other laptops and maybe even other distro's, so Id file a bug report.

Anyway, as a workaround, have you tried using ndiswrapper to load windows drivers?

---

### Post by Sisophon2001 on 2010-04-27
When filing a bug report I found that the same bug was reported for a different model HP in December (Bug # 499445) and message #48 to #51 on that page says that a newly released driver fixes the problem. Instillation instructions look complicated, so I will wait until after updating to 10.04 before trying them.

Thanks for all the help.

Garvan


EDIT:
After updating to UNR 10.04 I found that the problem has been fixed in the latest release.

---

### Post by FloorK on 2010-05-10
Hi Sisophon, did you go for the B43 or STA driver?
The STA is the proprietary one, the other is about reading firmware.
My guess is the STA. but it'd be nice for people with similar problems to know :)
Cheers,
Floor

EDIT: STA driver is working like a charm!

---

### Post by Sisophon2001 on 2010-05-29
> **FloorK said:**
> Hi Sisophon, did you go for the B43 or STA driver?
The STA is the proprietary one, the other is about reading firmware.
My guess is the STA. but it'd be nice for people with similar problems to know :)
Cheers,
Floor

EDIT: STA driver is working like a charm!

I also used the STA driver.

Garvan

---

