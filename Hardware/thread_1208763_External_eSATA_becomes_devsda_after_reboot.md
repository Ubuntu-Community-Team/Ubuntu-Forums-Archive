---
title: "External eSATA becomes /dev/sda after reboot"
date: 2009-07-09
forum: Hardware
---

### Post by kirkunit on 2009-07-09
Hello all,
I've run in to a little problem I hope you can help a semi-noob like myself with. (Been away from *nix-systems for a long time)

Running Ubuntu 9.04
I recently bought an eSATA dock for 3.5" hard drives, and found that if I plug in a drive while ubuntu's running, it gets assigned /dev/sde, after my internal drives. But when I reboot, it becomes /dev/sda, pushing the other drives down a step, which seems to wreak havoc with the mounting table, creating ghost mounts, duplicates, wrong label, whathaveya. 

I would assume this is because the eSATA controller on the motherboard takes priority over the regular (different) SATA controller.
Is there a way to force certain disks to become /dev/sda, b, etc so that my internal drives stay on the same id? Or another workaround I haven't thought of?
Thanks!

Best regards,
Björn Flink

---

### Post by vikkikanhaua on 2009-07-09
there might be some option in ur bios which lets u select the hard drive order by which the HDDs r selected for booting....
hope that helps

---

### Post by kirkunit on 2009-07-09
Thanks, but I looked there too. It's last in the list of available hard drives for boot priority. I'm guessing the eSATA controller just lies ahead of the SATA one in the PCIe bus or something.

---

### Post by kirkunit on 2009-07-09
Oh! I now discovered the wonder of identifying disks by UUID instead of /dev/sd*. That works fine!

---

