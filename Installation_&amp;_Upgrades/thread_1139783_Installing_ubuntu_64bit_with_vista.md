---
title: "Installing ubuntu 64bit with vista"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by lawrencep93 on 2009-04-27
i7 920@2.8GHz,Nvidia 285GTX , 6GB 1333MHz G-skill ram, Asus P6T Deluxe, seagate 1TB HDD, WD 1TB HDD, WD 1TB external HDD, Twin Samsung 2233SW LCD, 850W CM PSU, Thermaltake Full Armor+, Sony sata DVD/CD burner.
thats my computer
i have made an 80GB partition on the internal WD, but the only thing is I have never installed ubuntu and vista at the same time, and I really do not want to loose vista as it will be impossible to re-activate, any help or instructions?

---

### Post by Mark Phelps on 2009-04-27
So, do you already have Vista installed? Or are you looking for advice on alternatives for installing both Vista and Ubuntu?

---

### Post by lawrencep93 on 2009-04-28
I have vista installed on my primary 1TB HDD, have made a 80GB partition on my secondary 1TB HDD, and I do not want to loose vista. Also I have a netgear WIFI card that needs drivers any ideas?

---

### Post by lisati on 2009-04-28
It can be done. I have Visa Home Premium (32-bit) and Ubuntu Intrepid (8.10, 64-bit) happily co-existing in a dual-boot situation on one of my laptops.

The approach I took went something like this:[LIST=1]
[*]Make a backup of the VIsta recovery partition using the "Toshiba Create Recovery Disk(s)" tool that was preinstalled on my laptop
[*]Defragment Vista's main partition within Vista
[*]Make a backup of the important data I had inside Vista
[*]Using the partitioner "gParted" on the Ubuntu "Live CD" (it's under System->Administration->Partition manager), shrink the Vista partition, freeing up enough space to hold Ubuntu (Vista didn't want to do this for me with its own partition manager, probably because it was using the partitioner)
[*]Close gParted
[*]Start the installer, telling it when it asked me to use the largest continuous free space
[*]Reboot into Vista to make sure it still works (a "chkdsk" followed by a system restart is normal)
[*]Restart the laptop, and boot into Ubuntu
[*]Check for and apply updates (System->Administration->Update manager)
[/LIST]

Since you have already set aside an 80GB partition, you can probably skip the "Shrink the Vista partition" step above, and point the installer's partitioner at the partition you've already assigned for the task.

The part of the installation process that needs the most care is the partitioning stage: be careful to read the choices the installer gives you carefully before you commit to any changes.

---

