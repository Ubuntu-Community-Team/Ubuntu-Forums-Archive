---
title: "Dual boot F11/U9.04 live CD issues"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by KeepItFunky on 2009-08-14
I've got Fedora 11 installed, would like to add Ubuntu 9.04, but when I go to boot up with the live CD, I get a series of errors.

```

[ 0.536002] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[17.368028] ata1.00: revalidation failed (errno=-5)
[27.532028] ata1.00: revalidation failed (errno=-5)

```

The weird thing is that before I ever put Fedora on this machine, I had installed K/Ubuntu 8.10 from a Live CD w/out any of the errors as printed above.

Trying to resolve them I turned up the suggestion to select **F6** -> **noapic**.. for more info see [http://ubuntuforums.org/showthread.php?t=1224789]("http://ubuntuforums.org/showthread.php?t=1224789")

With this I was able to fully boot from the CD, but when I got to the installation dialogue's partition options, it says that there is no OS (nor any existing partitions) on the HDD. Which isn't true, as I am able to boot right up into Fedora after I quit the install.

Averatec 6200 series laptop
AMD Athlon 1800Mhz
2Gb RAM
Fedora 11

---

### Post by SoftwareExplorer on 2009-08-15
Does it show the partitions if you go to System-> Admistration->Partition Editor?

---

### Post by KeepItFunky on 2009-08-15
> **SoftwareExplorer said:**
> Does it show the partitions if you go to System-> Admistration->Partition Editor?

Yeah...
/dev/sda1    ext3     200.00 Mb - boot
/dev/sda2    lvm2      55.69 Gb - lvm

Why would it be recognized here & not in the Install dialogue?

---

### Post by SoftwareExplorer on 2009-08-15
Looks like your disk is set up with logical volume management. Inside of the lvm2 partition there can be multiple other partitions. I'm guessing the liveCD installer doesn't know how to handle it. I know the alternate installer CD can set up (and therefore probably manipulate) lvm, but I've never done it myself. Hopefully someone who knows more about this will see your thread and help because its something I've never tried.

---

