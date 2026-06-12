---
title: "Windows corrupted after grub recovery"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by andreselsuave on 2009-02-04
Hi there!
I had a ubuntu computer and wanted to install windows xP so I made a partition for it and installed it. After that I had to reinstall grub, which I did with the following commands in the live CD:
```
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quit

```
Now I added a line for windows in the grub menu.lst, and it starts booting up, but suddenly I get a nice blue screen and instant reboot (no matter if I try safe mode, normal mode, etc..)
What can it be? If I can't install grub to the MBR, then how can I dual boot?

thanks a lot

---

### Post by caljohnsmith on 2009-02-04
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by andreselsuave on 2009-02-04
Hi,
I post my results in a txt file.

EDIT:
my problem is not with the boot :P it is that windows doesnt support SATA. I need 2 install the drivers. Thanks anyways. its solved

---

### Post by caljohnsmith on 2009-02-04
Glad you figured it out.

---

