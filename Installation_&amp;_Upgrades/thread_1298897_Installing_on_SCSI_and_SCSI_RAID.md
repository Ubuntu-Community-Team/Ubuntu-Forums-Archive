---
title: "Installing on SCSI and SCSI RAID"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by m.dr on 2009-10-23
I am trying to install Ubuntu 9.1 Beta (also 9.04 and 8.1) on a system that has 2 SCSI disks on Channel A and Channel B each on an on board Adaptec SCSI controller. The system also has a RAID 5 across 4 SCSI disk on an Adaptec 2110s RAID controller.

The order of the disks in the BIOS is set as:
1. SCSI disk on on board Adaptec Channel A.
2. SCSI disk on on board Adaptec Channel B.
3. Raid Array on Adaptec 2110s PCI.

DVD-ROM drive has first boot order.

The installer sees them (in manual installation screen) in a different order as follows:
1. Raid Array on Adaptec 2110s PCI.
2. SCSI disk on on board Adaptec Channel A.
3. SCSI disk on on board Adaptec Channel B.

And calls them SDA, SDB, SDC respectively.

Although in the automated partitionin choice screen sees them in a slightly different order:
1. SCSI disk on on board Adaptec Channel A.
 2. Raid Array on Adaptec 2110s PCI.
3. SCSI disk on on board Adaptec Channel B.

And calls them SCSI3, SCSI4, SCSI5.

Anyway mount as follows:
Channel A:  /, /var, /usr/local, swap on disk.
Channel B:  /usr, /opt, /tmp, swap.
RAID 5: /home, /space, swap.

In the last screen before install starts I click on Advanced and see the 'Install Boot Loader' is checked and it is **automatically set to hd0**.

After installation and restart I get blank screen.

Again I try in the last screen before install starts I click on Advanced and see the 'Install Boot Loader' is checked and it is **automatically set to hd0**. **I change it to hd1**.

After installation and reboot it starts booting (Ubuntu screen) but starts giving various errors as / cannot be found and such. If you want I can give you the specific errors.

So my questions are:
1.  How do I get the installer to see the drives in the order set in BIOS?
2. Can I use the Alternate installer to fix this - if so using what options?
3. I tried the DVD installer and it does not even start giving various errors.
4. I keep getting an MP-BIOS error when either desktop, alternate, server installer starts. Also with DVD installer but it just crashes after giving some address space collision errors after the MP-BIOS error.

Also each disk as well the network card are on their own IRQ. The SCSI disks on Channel A, B have 11, 9. RAID card has IRQ 5. NIC card has IRQ 7.

Would really like your help on this.

Also having similar issues in a box with 2 SCSI disks and a SATA. I am trying to install the OS on the SCSI and /home, /space swap on SATA. But it sees the SATA as first and SCSI later and cannot boot.

Thanks very much. Would really like to see this hardware detection issue resolved for the 9.1 release if possible for the Desktop and Server installs.

m.dr:confused:

---

