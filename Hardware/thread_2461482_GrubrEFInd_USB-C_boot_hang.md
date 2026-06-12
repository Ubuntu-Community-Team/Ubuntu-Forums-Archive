---
title: "Grub/rEFInd USB-C boot hang"
date: 2021-05-01
forum: Hardware
---

### Post by jonbonney on 2021-05-01
I have an HP Envy x360 that dual boots to Unbuntu 20.04.2  and Windows 10. When I purchased the laptop it came with an HP USB-C docking station and Windows pre-installed.  After installing Ubuntu with Grub as the default boot loader, and using the HP docking station, the system would hang at the grub menu. I tried various combinations of plugging and unplugging devices from the docking station, including the docking station alone with no devices.  All with the same results.  Figuring it might be the HP docking station, I purchased an Anker docking station that also provided power over USB-C. Same results. 
The only way I can boot the laptop is by unplugging the USB cable before grub loads. 
To date I've tried rEFInd with the same results, 2 different docking stations, and disabling the ability to boot from USB within the BIOS.  I also have 2 of these laptops, one with Ubuntu and one still with the default pre-installed Windows image still loaded.  The untouched machine boots just fine with both docking stations and all hardware attached. 
Looking for ideas.

---

### Post by oldfred on 2021-05-01
Is Ubuntu on internal drive or on external where you are using Docking station for connection?

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

HP is one of the worst at dual booting. You typically have to update UEFI, and reset boot order from within UEFI as it does not remember changes in boot order from efibootmgr which grub also uses to set Ubuntu as first in boot order. Some try old legacy/BIOS/CSM install, but then always have to boot from UEFI one time boot menu as UEFI & BIOS are not compatible & once you start booting, you cannot switch boot modes. Or can not use grub for dual boot.
And Windows typically with all systems does updates, turning fast start up back on. And many Windows systems also up date UEFI resetting to defaults which you then have to redo to get Ubuntu working again.

---

### Post by jonbonney on 2021-05-01
Thanks Oldfred - I have Ubuntu installed on the internal drive. No external drives are attached to this laptop.
Not sure what further information you're requesting.  I'd be happy to provide it.  Maybe my post was a bit rambling too, I just wanted to provide as much information and context initially as possible.  To summarize briefly, my issue is that with Ubuntu installed, I cannot boot at all with a USB-C device plugged in, notably the two different docking stations.  As long as I unplug while powering on, or restarting the laptop, I can boot into either OS just fine.

---

### Post by oldfred on 2021-05-01
Does grub menu come up, so issue is after grub?
I might try removing quiet splash to see boot process or check logs after incorrect boot.

Or do you not even get a grub menu when USB-C plugged in?
Then I would make sure you have latest UEFI from HP and maybe drivers for docking stations.
I saw one user with a Dell station that had to update its firmware, to get dock to work.

---

### Post by jonbonney on 2021-05-01
Both Grub and rEFInd will initially load, but freeze with plugged in. Unplugged, both boot loaders operate fine and will dump you into the OS selected.  So the issue is pre-handoff to the OS. it's like the boot loader is scanning for something or trying to load something and hangs. Only a hard power off, unplug USB and power on will work. 
I did the usual firmware updates from HP, modified BIOS settings to disable USB boot in case that was the problem.

---

### Post by oldfred on 2021-05-01
Then remove quiet splash and see where it stops. It unusually is not last command posted but several further up on screen.
Or check log files for errors from previous boot.

Errors/Warnings:
sudo journalctl -b -p err
sudo egrep -i 'warn|error' /var/log/*g

---

### Post by tea for one on 2021-05-01
I wonder if this is an issue with the power needed to fire up the laptop and the docking station?

In your original post, the [COLOR="#0000FF"]untouched machine with Windows [/COLOR] boots OK with the docking station attached.

This leads me to think that the factory tweaked the software/hardware to allow the laptop to boot together with the docking station which, you say, came with the purchase.

Just an observation, no concrete experience with these docking stations.

---

### Post by jonbonney on 2021-05-01
Hm. Power issue. That could be something I possibly test using an external power supply (non USB). With both plugged in, there should be ample power supplied. I'll try that too.

---

### Post by jonbonney on 2021-05-01
> **oldfred said:**
> Then remove quiet splash and see where it stops. It unusually is not last command posted but several further up on screen.
Or check log files for errors from previous boot.

Errors/Warnings:
sudo journalctl -b -p err
sudo egrep -i 'warn|error' /var/log/*g

Are Grub/rEFInd errors captured there? I thought those were only OS error related.

---

### Post by oldfred on 2021-05-01
I am not sure there currently is anyway to capture grub errors.
But if you get grub menu, then grub is working.

---

### Post by jonbonney on 2021-05-02
> **oldfred said:**
> I am not sure there currently is anyway to capture grub errors.
But if you get grub menu, then grub is working.

Well, power wasn't the issue. But with Grub freezing and no way to see related errors, I might just be out of luck.

---

