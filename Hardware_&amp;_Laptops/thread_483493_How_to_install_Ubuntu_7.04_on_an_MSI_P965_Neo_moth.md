---
title: "How to install Ubuntu 7.04 on an MSI P965 Neo motherboard"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by doug.moen on 2007-06-24
I have successfully installed Ubuntu 7.04 on a system with an MSI P965 Neo motherboard.  It wasn't easy, and I don't recommend it.  There may be an easier way to do it: read the forums.

My system has 2 SATA drives: one is the hard disk, the other is the CD/DVD player (a Lite-On sh-16a7s).  I have no IDE devices.

The MSI P65 Neo has 5 SATA slots numbered 1, 3, 4, 6, 7.  Slot #1 is attached to a JMicron controller (which isn't fully supported by Ubuntu 7.04), the other slots are controlled by an ich8 controller.

I plugged my hard drive into SATA slot #1 (the dreaded JMicron slot), and my optical drive into slot #3.  If you attempt an Ubuntu install using this configuration, then the installation will appear to succeed, but when you try to reboot, grub will fail with error 21.  Despite the grub error, this is the configuration I managed to get working.

I tried putting the optical drive in slot #1 and the hard drive in slot #3.  Ubuntu installed and booted.  But when I tried to reboot the machine from a CD, after this apparently successful installation, the BIOS ignored the CD in the drive, and booted from the hard drive instead.  But Ubuntu froze early during the boot process.  I decided this was a motherboard bug, and gave up trying to make this configuration work.

I tried putting the hard drive in slot #3 and the optical drive in slot #4.  Ubuntu installs, grub finds the hard drive and starts linux, and then Ubuntu freezes when the progress bar appears (similar to the freeze in the previous paragraph).  I got an error code "ata4.00: failed to set xfermode (err_mask=0x40)".  I abandoned this configuration as well.

Based on forum postings, I decided to use hd = sata#1 and cd = sata#3, and fix the grub problem by installing lilo.  To make this work, I first needed to get ethernet working.  This leads to another problem I observed.

Although I could boot Ubuntu 7.04 off the live cd, I couldn't make the onboard ethernet interface to work.  In addition, I booted into the live cd many times, and observed the sometimes the entire system would freeze, and sometimes the mouse pointer would freeze.  I noticed the mouse pointer would sometimes freeze if I inserted or removed an ethernet cable.  Based on this, I decided that the on board ethernet (Realtek 8110SC) was not going to work.  So I disabled the on-board ethernet using the BIOS, and installed a D-Link DGE-530T PCI LAN card.  I chose the D-Link because it was listed in the Ubuntu Hardware Support page ([https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)) as working with no problem.  The D-Link was automatically detected and configured by the live cd operating system: that's what made it possible for me to proceed to the next step, and install lilo, so that the system would boot.

Based on forum suggestions, I also disabled USB Keyboard and Mouse Support within the BIOS.  I thought this might eliminate some of the causes of the random freezes.  I don't know if this particular change was necessary, but I haven't had any random freezes since I made this change.

Here's a recap: at this point, I have successfully installed Ubuntu on the hard drive, but it won't boot, due to error 21 in grub.  But I can boot into the live cd, and in this environment, I've fixed the ethernet, so I have internet access, and I've eliminated the random freezes.  The next step is to replace grub with lilo.

I should mention that I chose to dedicate the entire disk to a single operating system, Ubuntu, and I used the default partitioning.  It's not a dual boot system.  With this configuration, my Ubuntu root partition is /dev/sda1, and my swap partition is /dev/sda5.

Here is a set of shell commands that mounts my ubuntu root partition as /mnt/ubuntu, then creates a chrooted shell with the hard drive mounted on "/".  From this shell, I can use apt-get to install software.
  sudo bash
  mkdir /mnt/ubuntu
  mount /dev/sda1 /mnt/ubuntu
  mount -t proc none /mnt/ubuntu/proc
  mount -o bind /dev /mnt/ubuntu/dev
  cat /etc/resolv.conf >/mnt/ubuntu/etc/resolv.conf
  chroot /mnt/ubuntu /bin/bash

The first time I tried this, I didn't update /etc/resolv.conf, and I didn't have working internet access from within the chrooted shell.  I could ping my IP gateway, but I couldn't resolve DNS hostnames.  The problem is that /etc/resolv.conf didn't exist on the hard drive (because I had never successfully booted from the hard drive).

The first time I tried to install Lilo, I had a problem with /etc/fstab.  It contained some lines that confused the Lilo installer:
# /dev/sda1
UUID=5149cd61-ed5a-4234-9db7-a0c9f3502f7c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e187c4cb-1c4e-4836-a910-6a3494a29a6c none            swap    sw              0       0

I changed these lines to look like this:
/dev/sda1  /  ext3  defaults,errors=remount-ro  0  1
/dev/sda5  none  swap  sw  0  0

Once in the chrooted shell with a working internet and a corrected /etc/fstab file, I installed Lilo like this:
  apt-get update
  apt-get install lilo
  liloconfig  # answer 'yes' or 'ok' to all questions
  /sbin/lilo  # answer 'yes' or 'ok' to all questions

Then I rebooted, and my system worked.

One consequence of replacing "grub" with "lilo" is that the Ubuntu boot and shutdown progress bars are replaced by lines of scrolling text that show you what the system is doing when it is starting up or shutting down.  This is actually preferable, because if something goes wrong during startup, you need to be able to see the error messages so that you can type them into google and find help.

While this kind of thing is fun for some people, in retrospect, I wish I had either purchased a pre-configured Ubuntu system, or consulted the Ubuntu Hardware Support page *before* purchasing the system.

Doug Moen.

---

### Post by DusanC on 2007-06-28
I installed 7.04 couple hours ago on the same mainboard (MSI P965 Neo) with SATA HDD on JMicron, and after reboot GRUB gave me error 21. Solved it by switching HDD on ICH8 1'st port.
Had to use PATA CDRom for installation because SATA wouldn't work "ata3.00: failed to set xfermode (err_mask=0x40)". Had same errors with HDD on ICH8.
Networking worked out of the box (r8169).

System is working OK now.

Bye

DusanC

---

### Post by DusanC on 2007-06-28
Murphy hits again.

When rebooting I get ata3.00: failed to set xfermode (err_mask=0x40). Sometimes even for different ata but I haven't moved HDD to different SATA port. But system boots OK if I boot it from install CDROM and pick the "boot from harddisk" option.

What is the difference?

TIA

DusanC

---

### Post by DusanC on 2007-06-28
Solved with adding piix to /etc/initramfs-tools/modules

---

