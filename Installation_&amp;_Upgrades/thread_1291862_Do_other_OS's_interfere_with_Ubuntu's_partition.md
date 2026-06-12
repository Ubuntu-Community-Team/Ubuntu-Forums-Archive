---
title: "Do other OS's interfere with Ubuntu's partition?"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by Statics on 2009-10-15
Hey, I am thinking about installing Linux Ubuntu on a seperate partition from Vista in a few days. However, my main question is that, once Ubuntu is installed, and when Windows 7 comes out, will I be able to upgrade my Vista to Windows 7 without Windows 7 interfering with the Ubuntu partition that's already installed?

Thanks a lot.

---

### Post by DrMelon on 2009-10-15
> **Statics said:**
> Hey, I am thinking about installing Linux Ubuntu on a seperate partition from Vista in a few days. However, my main question is that, once Ubuntu is installed, and when Windows 7 comes out, will I be able to upgrade my Vista to Windows 7 without Windows 7 interfering with the Ubuntu partition that's already installed?

Thanks a lot.

Windows 7 will probably overwrite the boot sector, so you'll need to re-install grub.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by earthpigg on 2009-10-15
> **DrMelon said:**
> Windows 7 will probably overwrite the boot sector, so you'll need to re-install grub.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

+1. yup.

---

