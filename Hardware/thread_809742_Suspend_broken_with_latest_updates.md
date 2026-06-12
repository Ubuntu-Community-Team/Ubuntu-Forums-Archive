---
title: "Suspend broken with latest updates"
date: 2008-05-27
forum: Hardware
---

### Post by howlsmoving on 2008-05-27
I was begining to be a true believer in Hardy Heron - it fixed every problem I had with any distro.  Wireless worked, printers work, and suspend worked, but with the latest updates, suspend was broken.  I imagine it is the updated kernel and the updated modules that are the problem.  Is this true?  If so, how do I roll back to the previous versions, or fix the problem in the current packages?

Thanks in advance.

Edit: how is it broken?  The screen stays black.  I also just realized that the nvidia drivers were updated to, so maybe that is the problem... any ideas would be appreciated.

---

### Post by Sam Lars on 2008-05-27
Does Ctrl+Alt+Backspace or Ctrl+Alt+F1 work to get you to a login screen, graphical or text-based?
You should try using the nv driver and see if you still have the problem.

---

### Post by howlsmoving on 2008-05-28
Neither of those work.  The screen stays black (the backlight isn't working).  I have to restart the computer by forcing it to turn off... holding down the power button for a few seconds.

---

### Post by Maratonda on 2008-05-29
Have exactly the same problem, same operating system. When I load the old kernel at startup, it works fine. It looks like nobody has an answer to this yet

---

### Post by howlsmoving on 2008-05-29
I hope somebody can look into this.

---

### Post by Sam Lars on 2008-05-29
If there's an issue that needs to be fixed you should look on Launchpad to see if there's already a bug about this and, if there isn't, open a bug report about it.
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)
We'll need more information, such as what video card you're using, what driver you're using for it, and what kernel versions you're using.
As I said, if you're using the "nvidia" driver, try using the "nv" driver instead, or vice versa, to see if the problem goes away.

---

### Post by Maratonda on 2008-05-30
If you're using kernel version 2.6.24-17, having updated from previously working 2.6.24-16, there is this bug report
[https://bugs.launchpad.net/ubuntu/+bug/226279]("https://bugs.launchpad.net/ubuntu/+bug/226279")
which is affecting many people, me included.
Therefore I would not suggest to change video drivers [I have an old ATI, but the same problem], just my opinion though.
At startup, I am able to choose which kernel to load, can you? 
That should be the only solution at the moment, I guess.

---

### Post by pfeels on 2008-05-30
Code:

sudo apt-get install startupmanager

Then go to System > Admin > StartUp-Manager

Change Default OS to > Ubuntu 8.04, kernel 2.6.24-16-generic

And your done

---

### Post by howlsmoving on 2008-06-03
This problem was not fixed with latest round of updates ... kernel 2.6.24-18

---

### Post by Maratonda on 2008-06-06
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279)

It should be in repository hardy-proposed. I haven't tried it myself though.

>  Tim Gardner  wrote on 2008-06-02:  (permalink)

Here is the next attempt to isolate the resume regression. This version has these 2 commits reverted:
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy.git;a=commit;h=4b7c68904bf9ada8c4770ce5927e8ec71769ed92](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy.git;a=commit;h=4b7c68904bf9ada8c4770ce5927e8ec71769ed92)
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy.git;a=commit;h=850c3d6fed840a941727645767e5cf0e70ef59c4](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy.git;a=commit;h=850c3d6fed840a941727645767e5cf0e70ef59c4)

echo "deb [http://ppa.launchpad.net/timg-tpi/ubuntu](http://ppa.launchpad.net/timg-tpi/ubuntu) hardy main" > /tmp/timg-tpi-ppa.list
sudo mv /tmp/timg-tpi-ppa.list /etc/apt/sources.list.d
sudo apt-get install linux-image-2.6.24-19-generic

If you need LUM, LRM, or LBM then install those packages from the same PPA source (amd64 was still building at the time of this note):

sudo apt-get install linux-ubuntu-modules-2.6.24-19-generic linux-restricted-modules-2.6.24-19-generic

Note: The nVidia and fglrx drivers for -19 are also in that PPA.


and some comments

> Tim the -19 kernel (v2) worked perfectly on mine, with both suspend to RAM and suspend to disk.
You're a star.

> So to make it easier for the other noobs below is what you put into Terminal (at least thats what I think Martin was saying)

echo "deb [http://ppa.launchpad.net/timg-tpi/ubuntu](http://ppa.launchpad.net/timg-tpi/ubuntu) hardy main" > /tmp/timg-tpi-ppa.list
sudo mv /tmp/timg-tpi-ppa.list /etc/apt/sources.list.d
sudo apt-get install linux-image-2.6.24-19-generic
sudo apt-get update

> Thanks Martin. :-)
Resume from suspend to ram is working back using -19 you have summited in hardy-proposed.
Tested on HP Compaq nc2400 with last BIOS from HP.

---

### Post by Paul Weaver on 2008-06-09
[I]Quote:
So to make it easier for the other noobs below is what you put into Terminal (at least thats what I think Martin was saying)

echo "deb [http://ppa.launchpad.net/timg-tpi/ubuntu](http://ppa.launchpad.net/timg-tpi/ubuntu) hardy main" > /tmp/timg-tpi-ppa.list
sudo mv /tmp/timg-tpi-ppa.list /etc/apt/sources.list.d
sudo apt-get install linux-image-2.6.24-19-generic
sudo apt-get update [/I]

You should update before the install
I had to append the line to my sources.list file -- sources.list.d didn't seem to be recognised. 

The fix worked brilliantly for me -- like the poster above my NC2400 suspends and resumes now, which is great. On top of that, it seems to be more stable than before I upgraded to hardy (I occasionally had suspend/resume issues then), resume feels "snappier", thanks!

---

### Post by Paul Weaver on 2008-06-11
Unfortunatly it's not all roses on my nc2400. Sleep works, and works well, however a couple of times wireless (iwl3945) hasn't returned after sleep. I think this is after an extended period of sleep (a few hours), rather than 20 minutes, but either way.

rmmodding iwl3945, iwlwifi_mac80211 and cfg80211 and re modprobing didn't help. dmesg reported that the RF kill switch was off, when it wasn't. Turning it off and back on didn't help.

It seems the nic goes into a deep sleep and doesn't recover, shown from this snippet of dmesg
[  566.057603] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[  566.134658] iwl3945: Radio Frequency Kill Switch is On:
[  566.134665] Kill switch must be turned off for wireless networking to work.
[  566.141865] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[  566.151904] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[  566.171864] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[  566.199436] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[  566.219415] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[  578.170956] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[  578.220662] iwl3945: MAC is in deep sleep!
[  578.220807] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[  578.280439] iwl3945: MAC is in deep sleep!
[  578.280524] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[  578.340155] iwl3945: MAC is in deep sleep!
[  578.449917] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC

```

[    0.355087] Back to C!
[    0.355603] Enabling non-boot CPUs ...
[    0.355709] CPU0 attaching NULL sched-domain.
[    0.364995] SMP alternatives: switching to SMP code
[    0.366621] Booting processor 1/1 eip 3000
[    0.376929] Initializing CPU#1
[    0.456808] Calibrating delay using timer specific routine.. 2394.24 BogoMIPS (lpj=4788480)
[    0.456817] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000 00000000
[    0.456825] monitor/mwait feature present.
[    0.456830] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.456833] CPU: L2 cache: 2048K
[    0.456836] CPU: Physical Processor ID: 0
[    0.456838] CPU: Processor Core ID: 1
[    0.456840] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00042940 0000c1a9 00000000 00000000 00000000
[    0.457533] CPU1: Intel(R) Core(TM) Duo CPU      U2500  @ 1.20GHz stepping 0c
[    0.457596] CPU0 attaching sched-domain:
[    0.457600]  domain 0: span 03
[    0.457602]   groups: 01 02
[    0.457606] CPU1 attaching sched-domain:
[    0.457609]  domain 0: span 03
[    0.457611]   groups: 02 01
[    0.458091] CPU1 is up
[    0.461576] Switched to high resolution mode on CPU 1
[    0.493111] APIC error on CPU0: 00(40)
[    0.493114] APIC error on CPU1: 00(40)
[    1.538525] PM: Writing back config space on device 0000:00:02.0 at offset f (was 100, writing 10a)
[    1.538537] PM: Writing back config space on device 0000:00:02.0 at offset 7 (was 0, writing f0480000)
[    1.538543] PM: Writing back config space on device 0000:00:02.0 at offset 6 (was 8, writing e0000008)
[    1.538549] PM: Writing back config space on device 0000:00:02.0 at offset 5 (was 1, writing 2001)
[    1.556287] PM: Writing back config space on device 0000:00:02.1 at offset 4 (was 0, writing f0500000)
[    1.556297] PM: Writing back config space on device 0000:00:02.1 at offset 1 (was 900000, writing 900007)
[    1.572282] PM: Writing back config space on device 0000:00:1b.0 at offset f (was 100, writing 105)
[    1.572307] PM: Writing back config space on device 0000:00:1b.0 at offset 3 (was 0, writing 10)
[    1.572316] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100000, writing 100002)
[    1.572346] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 19
[    1.572356] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[    1.572387] PM: Writing back config space on device 0000:00:1c.0 at offset f (was 100, writing 4010b)
[    1.572402] PM: Writing back config space on device 0000:00:1c.0 at offset 9 (was 10001, writing 1fff1)
[    1.572410] PM: Writing back config space on device 0000:00:1c.0 at offset 8 (was 0, writing 40004000)
[    1.572417] PM: Writing back config space on device 0000:00:1c.0 at offset 7 (was 20000000, writing 200000f0)
[    1.572429] PM: Writing back config space on device 0000:00:1c.0 at offset 3 (was 810000, writing 810010)
[    1.572438] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100000, writing 100407)
[    1.572485] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.572497] PCI: Enabling device 0000:00:1d.0 (0000 -> 0001)
[    1.572502] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 18
[    1.572511] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    1.572519] PM: Writing back config space on device 0000:00:1d.0 at offset f (was 100, writing 10a)
[    1.572535] PM: Writing back config space on device 0000:00:1d.0 at offset 8 (was 1, writing 2021)
[    1.572581] usb usb1: root hub lost power or was reset
[    1.572618] PCI: Enabling device 0000:00:1d.1 (0000 -> 0001)
[    1.572622] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 16
[    1.572631] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    1.572639] PM: Writing back config space on device 0000:00:1d.1 at offset f (was 200, writing 20b)
[    1.572656] PM: Writing back config space on device 0000:00:1d.1 at offset 8 (was 1, writing 2041)
[    1.572699] usb usb2: root hub lost power or was reset
[    1.572732] PCI: Enabling device 0000:00:1d.2 (0000 -> 0001)
[    1.572736] ACPI: PCI Interrupt 0000:00:1d.2[B] -> GSI 22 (level, low) -> IRQ 16
[    1.572745] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    1.572753] PM: Writing back config space on device 0000:00:1d.2 at offset f (was 200, writing 20b)
[    1.572770] PM: Writing back config space on device 0000:00:1d.2 at offset 8 (was 1, writing 2061)
[    1.572813] usb usb3: root hub lost power or was reset
[    1.572834] PCI: Enabling device 0000:00:1d.3 (0000 -> 0001)
[    1.572839] ACPI: PCI Interrupt 0000:00:1d.3[B] -> GSI 22 (level, low) -> IRQ 16
[    1.572848] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    1.572856] PM: Writing back config space on device 0000:00:1d.3 at offset f (was 200, writing 20b)
[    1.572873] PM: Writing back config space on device 0000:00:1d.3 at offset 8 (was 1, writing 2081)
[    1.572916] usb usb4: root hub lost power or was reset
[    1.588255] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[    1.588260] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 18
[    1.588269] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    1.588285] PM: Writing back config space on device 0000:00:1d.7 at offset f (was 100, writing 10a)
[    1.588309] PM: Writing back config space on device 0000:00:1d.7 at offset 4 (was 0, writing f0584000)
[    1.588371] PM: Writing back config space on device 0000:00:1e.0 at offset 9 (was 10001, writing 1fff1)
[    1.588378] PM: Writing back config space on device 0000:00:1e.0 at offset 8 (was 0, writing f030f010)
[    1.588395] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100007, writing 100107)
[    1.588420] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    1.588482] PM: Writing back config space on device 0000:00:1f.1 at offset f (was 100, writing 105)
[    1.588498] PM: Writing back config space on device 0000:00:1f.1 at offset 8 (was c01, writing 20a1)
[    1.588515] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2800005, writing 2880005)
[    1.588529] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 20 (level, low) -> IRQ 19
[    1.588536] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    1.588555] Coming out of suspend...
[    1.588636] ata2: port disabled. ignoring.
[    1.590136] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (000000005) is beyond end of object [20070126]
[    1.590147] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.C1F3] (Node f7c4da98), AE_AML_PACKAGE_LIMIT
[    1.590205] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.C002.C0DA.C2F3._STM] (Node f7c50690), AE_AML_PACKAGE_LIMIT
[    1.590265] ata1: ACPI set timing mode failed (status=0x300d)
[    1.591156] ata1.01: _GTF unexpected object type 0x1
[    1.604269] PCI: Enabling device 0000:08:00.0 (0000 -> 0002)
[    1.604323] PM: Writing back config space on device 0000:08:00.0 at offset f (was 100, writing 10b)
[    1.604393] PM: Writing back config space on device 0000:08:00.0 at offset 4 (was 0, writing 40000000)
[    1.604407] PM: Writing back config space on device 0000:08:00.0 at offset 3 (was 0, writing 10)
[    1.604428] PM: Writing back config space on device 0000:08:00.0 at offset 1 (was 100002, writing 100406)
[    1.624473] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.634486] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.686032] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.696017] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.705985] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.716026] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.726038] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.736050] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.746063] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.756055] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.766081] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.776089] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.796133] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.806208] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.816215] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.817162] PM: Writing back config space on device 0000:02:00.0 at offset c (was 0, writing f7cf0000)
[    1.817187] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 4010)
[    1.817197] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 2b00000, writing 2b00002)
[    1.817240] PM: Writing back config space on device 0000:02:09.0 at offset f (was 34001ff, writing 5c0010b)
[    1.817248] PM: Writing back config space on device 0000:02:09.0 at offset e (was 0, writing 18fc)
[    1.817256] PM: Writing back config space on device 0000:02:09.0 at offset d (was 0, writing 1800)
[    1.817263] PM: Writing back config space on device 0000:02:09.0 at offset c (was 0, writing 14fc)
[    1.817271] PM: Writing back config space on device 0000:02:09.0 at offset b (was 0, writing 1400)
[    1.817278] PM: Writing back config space on device 0000:02:09.0 at offset a (was 0, writing 4bfff000)
[    1.817286] PM: Writing back config space on device 0000:02:09.0 at offset 9 (was 0, writing 48000000)
[    1.817294] PM: Writing back config space on device 0000:02:09.0 at offset 8 (was 0, writing 47fff000)
[    1.817302] PM: Writing back config space on device 0000:02:09.0 at offset 7 (was 0, writing 44000000)
[    1.817310] PM: Writing back config space on device 0000:02:09.0 at offset 6 (was 0, writing b0060302)
[    1.817320] PM: Writing back config space on device 0000:02:09.0 at offset 4 (was 0, writing f0110000)
[    1.817328] PM: Writing back config space on device 0000:02:09.0 at offset 3 (was 820000, writing 82a820)
[    1.817337] PM: Writing back config space on device 0000:02:09.0 at offset 1 (was 2100000, writing 2100007)
[    1.833147] PM: Writing back config space on device 0000:02:09.1 at offset f (was 4030200, writing 403020b)
[    1.833183] PM: Writing back config space on device 0000:02:09.1 at offset 5 (was 0, writing f0114000)
[    1.833208] PM: Writing back config space on device 0000:02:09.1 at offset 4 (was 0, writing f0111000)
[    1.833216] PM: Writing back config space on device 0000:02:09.1 at offset 3 (was 800000, writing 804010)
[    1.833228] PM: Writing back config space on device 0000:02:09.1 at offset 1 (was 2100000, writing 2100006)
[    1.867676] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.877660] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.882869] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[f0111000-f01117ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.882916] PM: Writing back config space on device 0000:02:09.4 at offset f (was 2ff, writing 20b)
[    1.882941] PM: Writing back config space on device 0000:02:09.4 at offset 5 (was 0, writing f0119000)
[    1.882949] PM: Writing back config space on device 0000:02:09.4 at offset 4 (was 0, writing f0118000)
[    1.882960] PM: Writing back config space on device 0000:02:09.4 at offset 1 (was 2100000, writing 2100002)
[    1.882998] tpm_inf_pnp 00:02: activation failed
[    1.887861] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.897900] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.907911] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.917921] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.927933] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.937929] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.947944] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.957969] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.988053] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    1.998078] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    2.008295] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    2.022541] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    2.032591] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    2.052540] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    2.072490] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    2.099977] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    2.608245] ata1.00: ACPI cmd ef/03:01:00:00:00:a0 filtered out
[    2.608249] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    2.624160] ata1.00: configured for UDMA/100
[    2.796198] ata1.01: configured for MWDMA2
[    2.796262] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    2.796294] sd 0:0:0:0: [sda] Write Protect is off
[    2.796298] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.796342] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.796385] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    2.796406] sd 0:0:0:0: [sda] Write Protect is off
[    2.796410] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.796451] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.963566] sd 0:0:0:0: [sda] Starting disk
[    2.991581] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 22
[    2.993154] PM: Finishing wakeup.
[    2.993156] Restarting tasks ... <6>usb 1-1: USB disconnect, address 8
[    3.017248] done.
[    3.372405] usb 2-1: USB disconnect, address 6
[    3.612253] usb 2-1: new full speed USB device using uhci_hcd and address 7
[    3.640445] tg3.c:v3.86 (November 9, 2007)
[    3.640482] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 20
[    3.692061] eth0: Tigon3 [partno(BCM95788A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:1b:24:31:d6:08
[    3.692075] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
[    3.692079] eth0: dma_rwctrl[763f0000] dma_mask[32-bit]
[    3.796295] usb 2-1: configuration #1 chosen from 1 choice
[    4.044077] usb 5-7: USB disconnect, address 14
[    4.044084] usb 5-7.3: USB disconnect, address 15
[    4.330903] usb 1-1: new full speed USB device using uhci_hcd and address 9
[    4.506956] usb 1-1: configuration #1 chosen from 1 choice


```

---

