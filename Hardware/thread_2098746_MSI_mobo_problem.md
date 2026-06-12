---
title: "MSI mobo problem"
date: 2012-12-27
forum: Hardware
---

### Post by KegHead on 2012-12-27
Hi!

i'm building a new system.

msi mobo, amd cpu and a used wd sata hd.

problem..i can only run ubuntu via the usb drive.

i can't boot from my hd.

i've set up bios correctly, but still no luck.

any ideas?

---

### Post by Bashing-om on 2012-12-27
KegHead; Hi !

Is grub installed to the hard drive ?
```
sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
```[INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

---

### Post by KegHead on 2012-12-27
ubuntu@ubuntu:~$ sudo debconf-show grub-pc
  grub2/kfreebsd_cmdline:
  grub2/linux_cmdline:
  grub-pc/install_devices_failed: false
  grub-pc/chainload_from_menu.lst: true
  grub-pc/postrm_purge_boot_grub: false
  grub2/kfreebsd_cmdline_default: quiet
  grub2/linux_cmdline_default: quiet splash
  grub-pc/hidden_timeout: true
  grub-pc/install_devices:
  grub-pc/partition_description:
  grub2/device_map_regenerated:
  grub-pc/kopt_extracted: false
  grub-pc/disk_description:
  grub-pc/install_devices_empty: false
  grub-pc/timeout: 10
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/install_devices_disks_changed:
  grub-pc/mixed_legacy_and_grub2: true
ubuntu@ubuntu:~$ sudo grub-probe -t device /boot/grub
grub-probe: error: failed to get canonical path of /cow.
ubuntu@ubuntu:~$

---

### Post by Bashing-om on 2012-12-27
KegHead;

Your debconf-show output is nothing like my working system output. I do not see this line as referenced from my system:
> * grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW1463479Your grub-probe output also does not indicate grub installed anywhere (which begs the question, how in the world are you booting?).
My output:
> 
sysop1@1204-a:~$  sudo grub-probe -t device /boot/grub
/dev/sdc1Do you need guidance to install grub onto the hard drive ?[INDENT][INDENT]try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by KegHead on 2012-12-27
Hi!

I got it working!

re installed.

KegHead

---

### Post by Bashing-om on 2012-12-27
That is one solution that is guaranteed to work !

Please mark this thread as solved (thread tools) so other's time is not consumed with a solved situation.

[INDENT][INDENT][INDENT]Best regards <== BDQ

[/INDENT][/INDENT][/INDENT]

---

