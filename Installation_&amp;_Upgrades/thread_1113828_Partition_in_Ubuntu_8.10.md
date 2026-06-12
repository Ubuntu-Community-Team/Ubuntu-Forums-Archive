---
title: "Partition in Ubuntu 8.10"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by Naz_Farooq on 2009-04-02
[FONT="Arial"][SIZE="3"]Hi All,
I have my laptop 2Gig with 1.45 G ram and 80 GB HDD. I want to install WindowsXP and Ubuntu 8.10 both OS. What is the best way to do a partition of 80 GB HDD. My friend has done earlier on my laptop 3 partitions i.e., 20 (for WnidowsXP) - 40 (FAT32) - 16 (for Ubuntu). 3.5 GB is left for ubuntu support ram. Is it suitable?
Can any one give me the commands for making partitions in a good way. Means what are the commands for making partitions as I have mentioned above. If some one is thinking it a stupid question, please don't think so because I am new in Linux..[/SIZE][/FONT]
:):)

---

### Post by miklcct on 2009-04-07
install gparted from the repository, then use it to do everything about partitioning

---

### Post by Naz_Farooq on 2009-04-08
> **miklcct said:**
> install gparted from the repository, then use it to do everything about partitioning

But what are the commands?

---

### Post by Mike.lifeguard on 2009-04-08
> **Naz_Farooq said:**
> But what are the commands?

Gparted has a GUI. I think it's actually just a frontend for parted - so in terminal you can do 'sudo parted' then 'help' to see commands.

---

