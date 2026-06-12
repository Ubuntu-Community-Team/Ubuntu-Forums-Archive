---
title: "Insert boot media in selected device"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by microfox on 2009-02-27
Hi


After a few attempts to install Ubuntu in the past, I have installed version 8.04 on my PC, proceeded with 338 updates and then updated to version 8.10. This all took an extraordinary amount of time.

I, now, find myself with an error message: "Insert boot media in selected device" every time I have to boot up the computer. I, then, insert the install DVD into the optical drive and then, select the 5th option, (Boot from the first hard drive) before I can finally get access to Ubuntu.

When I first installed Ubuntu, I remember selecting "advanced mode" ans asking for a bootloader. I can also see a Grub in the "boot" folder of my system files but somehow, the system acts as if it doesn't recognize the grub.

Here's what an " fdisk -l" command shows:

/dev/sda1   *           1       30025   241175781   83  Linux
/dev/sda2           30026       30401     3020220    5  Extended
/dev/sda5           30026       30401     3020188+  82  Linux swap / Solaris


Can anyone help me ?

---

### Post by taurus on 2009-02-27
Try installing GRUB to MBR again so you can boot into Ubuntu without inserting a CD/DVD.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by microfox on 2009-02-27
> **taurus said:**
> Try installing GRUB to MBR again so you can boot into Ubuntu without inserting a CD/DVD.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Thanks

Even though the Terminal said the setup was successful, it didn't when I rebooted. Could it be because I don't dual-boot ?

---

