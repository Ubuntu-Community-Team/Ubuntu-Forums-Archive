---
title: "How to set up RAID 1 on Ubuntu Jaunty with ASUS P5Q Motherboard"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by BorisPlankton on 2009-05-27
Hello,
I am posting this as I have a new Hard Drive and am looking to set up
RAID 1 with Jaunty.

My setup is:
CPU: Intel® Core™2 Quad Q8200 Quad Core 4x2.33GHz 4MB Cache
Motherboard: ASUS P5Q Pro (Gb LAN 8-ch HD Audio Crossfire)
Graphics Card: MSI ATI Radeon HD2600XT 512MB 2DVI/HDCP PCI-Express
O/S Linux Ubuntu 9.04
RAM: OCZ Platinum 2x2 GB DDR2 RAM 1066MHz

Hard Drive 2 x WD-5001AA* Western Digital Caviar Black 500GB 32Mb

I have installed Ubuntu Jaunty already and all is fine. I have read the Motherboard manual and figure I can do the BIOS bit:
'Configure SATA as item in BIOS to RAID' exit BIOS then I set the Intel Matrix Storage Manager to RAID 1 with the drives installed.

I then re-install Jaunty and all will work? From what I have seen and read I am not confident that this is going to be as easy as that. But I give you this to shoot at. Can anyone see any issues/problems I am going to face?

In particular, do I need to install alternative Jaunty?
And, if so, how easy is this to install?

---

### Post by ronparent on 2009-05-27
Since youplan to use a fakeraid configuration, you should follow the guide here as best you can:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Basically your raid bios configures your raid1. Installing and activating your raid should initiate the mirroring of the first drive on the second. I am unclear what is necessary to automatically activate the raid on boot and would welcome any explite input on this.

The raid1 is relatively easy because you can boot directly to the 1st drive and activate the raid once booted. First you have to install dmraid - in a terminal enter** apt-get install dmraid -y**. Once the output indicates the install is successful you can enter **dmraid -ay**. This will activate the raid and populate /dev/mapper with the symbolic link entries you use to mount individual partitions (the entries ending in numbers, 1, 2, etc are the mountable partitions). In 8.04 installing dmraid was enought for the raid partitions to be automatically activated on all boots subsequent to its installation. I have had to manually activate and mount the raid partitions since upgrading to 9.04. I don't know what the explicite answer to that is yet. Good luck. You should in any case be able to work normally with your raid as long as you activate it after booting.

---

### Post by BorisPlankton on 2009-05-28
Thanks. I do not fully understand which might mean I should not attempt this.
The 'FakeRaidHowto says'The most common reason for using fakeRAID is in a dual-boot environment, where both Linux and Windows must be able to read and write to the same RAID partitions.' If I am not concerned about this does this mean I should use Ubuntu's Softraid capability . And, if so, what steps do I take here?

If the fakeRAID route suggested is the one to take when do I set the BIOS to RAID 1.
As I have Ubunutu installed I assume I can proceed through Terminal as things stand.
I did not understand the point about activating the raid on boot. Would we not expect it to just work after this set up - Oh I see you hare having to activate and mount manually after booting. How simple is this?

Does the fact that I am asking these questions mean that I should stop now!

---

### Post by ronparent on 2009-05-28
If you do not need to dual boot with windows the mddam software raid is a good approach. You will have to read some guides for using it. Also, if you have already activated the MB raid in bios, you will have to deactivate it and probably erase the fakeraid meta data from your drives. Yes it would be much simpler to use the drives independently. As long as you use a good backup strategy the risk to you data is minimal.

---

