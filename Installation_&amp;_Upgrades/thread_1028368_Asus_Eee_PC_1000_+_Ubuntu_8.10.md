---
title: "Asus Eee PC 1000 + Ubuntu 8.10"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by jlc on 2009-01-02
Asus eepc 1000
Ubuntu 8.10 i386

Install Ubuntu via the live cd option with the following partitions:
```

/             /dev/sda1    all ~7.4G
/usr/share    /dev/sdb1    4G
swap          /dev/sdb5    2G
/home         /dev/sdb6    rest ~24G

```

If you didn't install it via the live cd, when it is finished, boot into the live cd.

turning off ordered data writing for the journal with
```

$ sudo tune2fs -o journal_data_writeback /dev/sda1
$ sudo tune2fs -o journal_data_writeback /dev/sdb1
$ sudo tune2fs -o journal_data_writeback /dev/sdb6

```

Setup the array.org repos for a custom eee Kernel:
```

$ wget http://www.array.org/ubuntu/array-intrepid.list
$ sudo mv -v array-intrepid.list /etc/apt/sources.list.d/
$ wget http://www.array.org/ubuntu/array-apt-key.asc
$ sudo apt-key add array-apt-key.asc
$ sudo apt-get update

```

Install the EeePC-lean kernel.
```

$ sudo apt-get install linux-eeepc-lean linux-headers-eeepc-lean rt2860-dkms eeepc-config gsynaptics-elantech

$ sudo reboot

```

Make sure you select the eeepc kernel to boot into, press ESC at the grub prompt to select.

Remove the ubuntu generic kernels to keep them from updating.
```

$ sudo apt-get remove linux-generic linux-image-generic linux-restricted-modules-generic linux-headers-generic

```

You can remove all generic kernels giving you no fall back with:
```

$ sudo apt-get remove --purge linux-.*-generic
$ sudo apt-get autoremove
$ sudo apt-get remove --purge linux-headers-2.6.27-7

```

Enable laptop mode in acpi:
```

$ sudo vi /etc/default/acpi-support

    ENABLE_LAPTOP_MODE=true

$ sudo reboot

```

Tweaks:

1.) Using a ramdisk instead of the SSD to store temporary files will speed things up, but will cost you a few megabytes of RAM.
```

$ sudo vi /etc/fstab

    tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

```

2.) Firefox puts its cache in your home partition. By moving this cache in RAM you can speed up Firefox and reduce disk writes. Complete the previous tweak to mount /tmp in RAM, and you can put the cache there as well.

Open about:config in Firefox. Right click in an open area and create a new string value called browser.cache.disk.parent_directory. Set the value to /tmp.

3.) Change I/O scheduler to noop
```

$ sudo vi /boot/grub/menu.lst

Add "elevator=noop" to the # kopt=root* line with a space between and no quotes. My line looks like this:

# kopt=root=UUID=04d9cdcb-6cb4-4d0b-a04e-bfabd4e436b1 ro elevator=noop

```

Default is cfq you can also try deadline or anticipatory
```

$ sudo update-grub

```

4.) Tell the system not to use the swap partition as swap, and it will be used for hibernation only.
```

$ sudo vi /etc/sysctl.conf

and add "vm.swappiness = 0" at the end of the file.

```

5.) Encrypt a private directory
```

$ sudo apt-get install ecryptfs-utils
$ ecryptfs-setup-private

```

EXTRAS:
```

$ sudo apt-get install ssh nautilus-open-terminal xchat-gnome gnome-main-menu ubuntu-restricted-extra

```

Add medibuntu:
```

$ echo deb http://packages.medibuntu.org/ intrepid free non-free | sudo tee -a /etc/apt/sources.list
$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo aptitude update
    
$ sudo aptitude install w32codecs libdvdcss2 -y

```


Resources and thanks to:

[http://www.array.org/ubuntu/](http://www.array.org/ubuntu/)

[http://www.harald-hoyer.de/personal/blog/fedora-10-boot-analysis](http://www.harald-hoyer.de/personal/blog/fedora-10-boot-analysis)

[http://forum.eeeuser.com/viewtopic.php?id=49865](http://forum.eeeuser.com/viewtopic.php?id=49865)

[http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/](http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/)

---

