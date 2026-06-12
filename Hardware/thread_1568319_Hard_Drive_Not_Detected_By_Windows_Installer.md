---
title: "Hard Drive Not Detected By Windows Installer"
date: 2010-09-05
forum: Hardware
---

### Post by Lexess on 2010-09-05
I recently changed my hard drive to a dynamic drive by mistake because I wanted to have more partitions. That was a pain to deal with because windows wouldn't boot anymore. I used the Ubuntu live cd and fully reformatted the drive. I installed Ubuntu on one partition and have the other partitions set as NTSF.

I also deleted my recovery partition by mistake. I get an error of "NTLDR is missing" If I try to use an external hdd for installation. Windows XP installation doesn't recognize that there are any hard drives.

Ubuntu clearly shows that the hard drive is there and everything is working with no errors.

Does anyone know what I have to do in order to be able to install windows?

Thanks.

---

### Post by Cypress421 on 2010-09-05
I would freshly reinstall XP, then use something like GParted or Partition Magic to resize the partiton, creating space for Ubuntu, then install Ubuntu in that partition.

---

### Post by Lexess on 2010-09-05
Thats just the problem. I can't install XP because it can't detect any hard drives to install to. I think it's because I had it as a dynamic drive.

I completely formatted the hdd and no bootable information is on it.

I tried an Acronis rescue disk and it won't detect any hard drives.

I tried EASEUS rescue disk and it detects everything.

---

### Post by pricetech on 2010-09-05
Check your BIOS.  You may have to change to configuration of the drives to make XP see them.  Third party driver may or may not help.

Just ran into this a couple of weeks ago with a Dell.  Had to change the way the BIOS presents the drives to the OS for the XP installer to see it.  Win7 and Ubuntu both saw it just fine.

I don't remember the exact setting that worked, so it'll be a "trial and error" thing until the installer sees the drive.

---

### Post by Lexess on 2010-09-05
Thanks. I googled this same problem with several people mentioning BIOS settings. Unfortunately I have no control on hard drive settings in my bios. It's a Phoenix bios in a Sony Vaio laptop. I searched everywhere and the only control I have is the boot order and changing time and date.

---

### Post by pricetech on 2010-09-07
> **Lexess said:**
> Thanks. I googled this same problem with several people mentioning BIOS settings. Unfortunately I have no control on hard drive settings in my bios. It's a Phoenix bios in a Sony Vaio laptop. I searched everywhere and the only control I have is the boot order and changing time and date.

That sucks.  Do you know someone with Windows 7 that can build you a Windows PE disk ??  Mine saw the drive even though XP couldn't.  It might give you a workaround.

---

