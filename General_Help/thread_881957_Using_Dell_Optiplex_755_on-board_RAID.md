---
title: "Using Dell Optiplex 755 on-board RAID"
date: 2008-08-06
forum: General Help
---

### Post by CyberCowboy on 2008-08-06
I have an Optiplex 755 which has a basic on-board RAID system.  I'm using 2 160 GB SATA's and have already created a RAID 1 configuration.

Do I need any special drivers while doing the install? 

 I went through the install already and was still able to see both drives.  I set all of my partitons on one of the drives and continued the setup.  During the following reboot it paused on the RAID screen in bios and the HD light was on steady.  All this happened last night and I went to bed before it proceeded but would like to know if when I get home from work I will have a working RAID set up or I wasted a night.

---

### Post by fjgaude on 2008-08-06
Working raid, likely not. Sounds like you will have to use something like **dmraid**, but I don't know enough about your system to say for sure.

Let us know what happens when you get home.

---

### Post by CyberCowboy on 2008-08-06
> **fjgaude said:**
> Working raid, likely not. Sounds like you will have to use something like **dmraid**, but I don't know enough about your system to say for sure.

Let us know what happens when you get home.

Thanks for the quick response Fjuade, since I'm fairly new to RAID building process is there a guide that is recommended for this setup?  Making matters slightly more difficult (possibly) is that I'm doing a server install on this box so I can't use the few guides I've had that suggest adding packages to the live CD when it's running before doing the install.

Alternately is there anyway to add the DMRAID AFTER the install on one of the drives and just have it start the raid after (essentially the same thing as rebuilding the raid after replacing a failed drive?)

---

### Post by fjgaude on 2008-08-07
I would think you could install dmraid on a server:

```
sudo apt-get install dmraid
```

Learn how dmraid works and then put the array in your /etc/fstab file... and then all should be okay.

Let us know if you have any troubles. Do a google on dmraid to find help.

---

