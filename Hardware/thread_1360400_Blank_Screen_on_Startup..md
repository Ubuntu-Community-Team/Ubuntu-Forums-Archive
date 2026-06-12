---
title: "Blank Screen on Startup."
date: 2009-12-20
forum: Hardware
---

### Post by lorddaddy84 on 2009-12-20
Hi, I have a Toshiba Satellite A355-S6935(Core 2 Duo T6400, 4GB SDRAM, ATI Mobility Radeon HD 3650 with 512MB Video RAM.) I have been a long time Ubuntu user, but I just got this laptop and would like to Install 9.10 on it but everytime I try to boot Ubuntu it always hangs on a black/blank screen. Any Ideas for this?

Thanks.

---

### Post by Dawnthorn on 2010-01-25
Someone finally figured out how to get this to work. You need to add "pci=use_crs" to the kernel boot options and that seems to fix it.

---

### Post by Versusnja on 2010-01-27
I do NOT confirm.
I have a Ubuntu 9.10 Server installed on ATOM station, so no graphics expected.
And still - a blank screen.

Even with the following grub.cfg:
> menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        pci=use_crs
        insmod raid
        insmod mdraid
        insmod ext2
        set root=(md0)
        search --no-floppy --fs-uuid --set ace37f9b-c2c4-4425-af6f-04370db9c8df
        linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=ace37f9b-c2c4-4425-af6f-04370db9c8df ro   splash quiet
        initrd  /boot/initrd.img-2.6.31-17-generic
}


---

### Post by lorddaddy84 on 2010-02-07
> **Dawnthorn said:**
> Someone finally figured out how to get this to work. You need to add "pci=use_crs" to the kernel boot options and that seems to fix it.
Seems to work. Gonna test for other issues.

Thanks.

---

### Post by Versusnja on 2010-02-12
But how? Did you add this to /etc/default/grub as 
GRUB_CMDLINE_LINUX="pci=use_crs"?

I just can't figure out to add this to boot options.

---

### Post by ndmp on 2010-02-12
> **lorddaddy84 said:**
> Hi, I have a Toshiba Satellite A355-S6935(Core 2 Duo T6400, 4GB SDRAM, ATI Mobility Radeon HD 3650 with 512MB Video RAM.) I have been a long time Ubuntu user, but I just got this laptop and would like to Install 9.10 on it but everytime I try to boot Ubuntu it always hangs on a black/blank screen. Any Ideas for this?

Thanks.

I had the same with my netbook first time. Luckily I hit "Esc" in frustration and that replaced the blank sceen with the GRUB error report so I was able to track down and fix the problem (in my case, a faulty USB boot drive).

Hope this helps!

---

