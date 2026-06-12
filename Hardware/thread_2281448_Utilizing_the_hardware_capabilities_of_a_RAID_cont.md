---
title: "Utilizing the hardware capabilities of a RAID controller"
date: 2015-06-07
forum: Hardware
---

### Post by Will_Moonen on 2015-06-07
For some basic development purpose I'm using a Win2k3. I'm considering a move to Ubuntu with Samba as the main workload for this server is file sharing. I have a couple of questions which should be read as “exploring limitations and options” as I have not yet installed Ubuntu.

 The server is based on a system board with the ancient NF4 chipset, an AMD Opteron dual core CPU and 4 gig of memory.
It is equiped with a Dell Perc 5i controller in a RAID-5 config which is holding a one logical, NTFS formatted volume of 4 TB. I have a backup ready of this content. The system is started via a separate, 150 Gig / 10k WD drive.
For the moment, in an attempt balancing performance and resource usage, my preference would be staying away from any type of software RAID and only utilize the hardware RAID-5 capabilities of this Dell controller.

While the controller is in the supported hardware list, I cannot find documentation describing how to make this happen.
I have also searched several fora in an attempt finding somebody who was able to get this going. Most fora topics are about problems with booting from a volume served by this controller.

Apparently I'm overlooking something? What would be the recommended approach (besides using replacing the hardware)?

 
Thank you – Will

---

### Post by SeijiSensei on 2015-06-07
I know that RedHat and CentOS will detect that RAID card automatically during installation and install the appropriate driver.  I think Debian/Ubuntu will do so as well.  The easiest way to test is to boot from an installation CD and use the trial option.  When it's installed the RAID array will appear as a single device to Linux like /dev/sda.

---

### Post by Will_Moonen on 2015-06-09
> **SeijiSensei said:**
> The easiest way to test is to boot from an installation CD and use the trial option.  When it's installed the RAID array will appear as a single device to Linux like /dev/sda.

Sounds like a plan - thank you! :-)

---

