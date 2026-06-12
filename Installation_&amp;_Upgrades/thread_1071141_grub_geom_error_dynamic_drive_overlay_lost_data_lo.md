---
title: "grub geom error dynamic drive overlay lost data lost"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by charlesDarvin on 2009-02-15
Greetings

i have Ubuntu 8.10 desktop cd. my desktop computer freezes when trying to run Ubuntu in Live mode. The computer configuration (bought in Dec 2002) is Pentinum4, Intel 845GEBV2 motherboard, Samsung 80gb disk SP8004H running on dynamic drive overlay. Windows 2000 was being used by my dad on it since last 6 years.

To install ubuntu, i bought a segate 360gb SATA drive. since it did not have an interface on the motherboard, i bought an additional PCI card to connect to SATA drives. As, The Live mode freezing a few seconds after the welcome sound, I thought it would be better to install ubuntu on the newer disk directly.
The new drive 360gb was now detected as /dev/sda
The old drive 80gb was detected as /dev/sdb (primary master IDE)

I had selected hd0 as location for installing boot loader. Linux was successfully installedon /dev/sda. the system would not boot it in linux, making me assume that the boot record has not been written. So in the next installation trial, I attempted installing boot loader on /dev/sdb

here is where all hell broke lose.
on boot, i got "grub geom error". the dynamic drive overlay seemed to have been gone. on trying to boot through the windows 2000 cd, it resulted in error message suggesting that i should run the hardware diagnostic utility and windows 2000 cd would not continue.

is it possible to recover all the data? maybe by either reloading the dynamic drive overlay or anything else. currently the computer wont boot.

---

### Post by caljohnsmith on 2009-02-15
How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install lilo
sudo lilo -M /dev/[COLOR="Blue"]sdb[/COLOR] mbr
```
That will install a Windows equivalent MBR to your sdb drive, which should be your Windows drive if I understood your post correctly. That should allow you to boot back into Windows. Then to troubleshoot your Grub problem, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Live CD Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by charlesDarvin on 2009-02-16
Unfortunately, the Live CD does not work. It freezes after the welcome sound. release notes of ubuntu 8.10 say that Live cd will not work for laptops having intel 845 chipset. Mine is a desktop. so currently no os boots.

---

### Post by caljohnsmith on 2009-02-16
[QUOTE=charlesDarvin]As, The Live mode freezing a few seconds after the welcome sound, I thought it would be better to install ubuntu on the newer disk directly.[/QUOTE]
If you can't boot the Live CD, then how did you install Ubuntu "directly"? Do you have any other Live CDs you can try to boot on that computer? If you can find a Live CD that works, it would sure make troubleshooting a lot easier.

---

