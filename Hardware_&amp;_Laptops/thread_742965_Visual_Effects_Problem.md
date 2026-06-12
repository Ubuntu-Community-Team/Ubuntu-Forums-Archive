---
title: "Visual Effects Problem"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by schibros on 2008-04-02
I am running Ubuntu Gutsy on a Toshiba Satellite 2455-S3001. Everything was working fine untill i changed the **Visula Effcts** from **None** to  **Normal**, which installed the **Nvidia GeForce4 420 Go graphics controller**. After the installation of the card, i was required to restart the system. I restarted and from then on i have been experiencing **graphical corruption**, when the systems loads. It boots fine, but i can not see anything. When i boot from the CD, everything seems to be running fine.

Please i need help on how to **disable the Nvidia GeForce card**, or change bacck the **visual effects to None**. I think it should be done from the recovery mode, since i have corrupt graphics, i cant see my desktop when its loaded. 

Thanks in advance.

---

### Post by luisromangz on 2008-04-02
In the recovery mode or from the live cd (mounting your harddisk), try editing the /etc/xorg.conf file, replacing the "nvidia" driver with "nv".

---

### Post by schibros on 2008-04-02
> **luisromangz said:**
> In the recovery mode or from the live cd (mounting your harddisk), try editing the /etc/xorg.conf file, replacing the "nvidia" driver with "nv".


Thanks,

but what comands do i key in to get it done in the recovery mode?

---

### Post by schibros on 2008-04-02
i was able to resolv the problem.

i used this comand

**sudo apt-get remove --purge nvidia-glx** from the restore mode.

i think this removed the nvidia driver

when i rebooted, ubuntu loaded and said it was running in low graphics mode and asked me if i wanted to configure the graphics card or continue. i choose configure and then selected generic driver and 1024 *768. when Ubuntu came up, i restarted and everything was perfect.

---

