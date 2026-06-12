---
title: "Diskless System Won't Boot - Broadcom Dfirmware problem"
date: 2009-09-07
forum: Hardware
---

### Post by akester on 2009-09-07
I am setting up a PXE boot environment to tinker with, and have run into some issues.

I have set everything up acoording to [this article]("https://help.ubuntu.com/community/DisklessUbuntuHowto").  --I did have to use some different software.  I am using pfsense for the DHCP Server and Freenas as the NFS server. however I followed the steps of PXE linux and mirroring a working HDD.

I have copied a working Ubuntu 8.04 installation to the NFS root and it is being read by Ubuntu during its boot.

However when I try to boot over the network, The bootup will stop with the error "b43-phy0 ERROR: Firmware File 'b43/ucode5.fw' not found or load failed."
Then it says to go download the latest firmware.

I checked the NFS directory in the /lib/firmware and overwrote the exsisting files.  I then ran chmod on them using SSH on freenas and reboot the client system, but it returns the same error.

The system will not contimue to boot, about every 5 minutes it will redisplay the error messages.

The network installation is an exact copy of the local instalation on the computer and the local copy works fine.  The wireless card can connect and everything.

I am stumped at this point.  I have found many articles but they require that you go into the console of the client wich obviously is not an option.

The system is a compaq persario v5000 laptop.

Thanks

---

