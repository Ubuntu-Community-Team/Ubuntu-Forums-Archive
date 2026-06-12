---
title: "executing 'grub-install hd0 ' failed"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by impervius on 2009-07-01
Hey, im trying to install Ubuntu on my laptop as the sole operating system. I chose to use the whole disk to install, and it was working fine until it hung for about 30mins on "configuring hardware" 94%, and the it eventually gave an error message saying

executing 'grub-install hd0 ' failed

what should i do?

i am installing from a cd which i downloaded, and there are no errors on the disk.

---

### Post by presence1960 on 2009-07-01
Did you do MD5SUM and check the results against Ubuntu hashes?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

The MD5SUM should match the hashes exactly, if not your iso is corrupted.

---

### Post by impervius on 2009-07-01
i did this:

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

---

### Post by presence1960 on 2009-07-01
> **impervius said:**
> i did this:

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

it is recommended in the how to get ubuntu documentation to do an MD5SUM prior to burning the iso image to CD/DVD.

---

### Post by colau on 2009-07-01
> **impervius said:**
> i did this:

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)
Check the .iso file with md5sum
```

md5sum filename.iso

```

---

### Post by presence1960 on 2009-07-01
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by RJARRRPCGP on 2009-07-01
> **impervius said:**
> Hey, im trying to install Ubuntu on my laptop as the sole operating system. I chose to use the whole disk to install, and it was working fine until it hung for about 30mins on "configuring hardware" 94%, and the it eventually gave an error message saying

executing 'grub-install hd0 ' failed

what should i do?

i am installing from a cd which i downloaded, and there are no errors on the disk.

There's still a good chance that your HDD is bad. Sorry. :(

---

