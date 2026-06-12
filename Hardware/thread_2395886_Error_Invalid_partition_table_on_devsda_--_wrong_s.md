---
title: "Error: Invalid partition table on /dev/sda -- wrong signature f69."
date: 2018-07-08
forum: Hardware
---

### Post by archimedes1981 on 2018-07-08
I am upgrading my Dell N5030 CPU RAM and HDD>SSD in one go.
All seems to be working only that the System is only booting half way.
I cloned my HDD to an SSD using dd. It gave me a number of errors while cloning and it seemed to try lower speeds every time until it finally managed to clone the whole 120Gb.
It seemed to be having trouble somewhere along the extended partition where my /home folder is. I was not sure if my HDD was on ATA or AHCI setting, so when I tried booting the first time with my SSD I first left everything as is (ATA) then tried AHCI. 
It seems to be getting stock at th same place and gives me an option for maintenence "system ctl default" or "journalctl -xp" or "systemctl reboot" etc.
I had 16.04 on it and I don't want to lose my /Home folder (partition).
I'm now trying to install 18.04 through live USB.
installed gpart but it doesn't seem to fix anything. Gparted is giving Error: Invalid partition table on /dev/sda -- wrong signature f69.
Do I need to clone it again? I would have to take it apart again.
thanks

---

### Post by archimedes1981 on 2018-07-08
So Gpart lets me open the /home folder and there's 3 users. one of which I now remember for some reason got corrupted. I don't recall what happened with that user but the I can only navigate till the first folders (Desktop, Documents etc). Don't need that user at all but through gparted I can't delete it or anything. The users I require are visible and probably healthy. Can I repair the partition?

---

### Post by archimedes1981 on 2018-07-08
I installed testdisk but not sure what i'm doing.

---

### Post by Yellow Pasque on 2018-07-08
> **archimedes1981 said:**
> I installed testdisk but not sure what i'm doing.

Can you give any output from it? For example, can you analyze the disk in question and give the output?

---

