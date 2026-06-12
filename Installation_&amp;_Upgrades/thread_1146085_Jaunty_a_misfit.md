---
title: "Jaunty a misfit ?"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by eric stockman on 2009-05-02
Not so happy with the latest opus magnum from Canonical : Jaunty Jackalope 9.04 
  - The install ( via alternate CD ) makes a mess of the menu.lst file 
  - It got the screen resolution wrong ( 800 x 600  instead of 1440 x 900)
     without a preferences-entry to correct this .
      ( created an empty /etc/X11/xorg.conf file  ?? )
My multi-Linux-system is set-up with a separate partition for /home and a separate partition for /boot (+-500 mb) .
Every Ubuntu-version or other linux-variant lives also in it's own partition ( 4 gb will do ) .
Every partition ( created with gparted)  gets a label according to the usage of the partition : BOOT HOME HARDY JAUNTY IBEX  ( where IBEX == root: / partition where IBEX lives ).
The easiest way to label a partition is to boot with the SystemrescueCd (which should be in your toolbox anyway , easier to use for gnome-Ubuntu- users than Knoppix ) . Start gparted here and as your hard-drive partitions are not mounted in the systemrescueCd-environment you have the opportunity to change the labels . (right-click on the partition-lines ) .
When installing or upgrading (manual) via the alternate-cd take care to allocate the correct partitions . ( and don't format your home partition , the only partition to be formatted is the new created root/ partition for the new ubuntu-version ) )
( Use **ls -l  /dev/disk/by-label ** to view them beforehand) 

Afterwards You can edit the /boot/grub/menu.lst file to get rid of the ugly and unworkable UUID's  like this :

title		Ubuntu 10.04 JAUNTY, kernel 2.6.28-11-generic
label=BOOT
kernel		/vmlinuz-2.6.28-11-generic root=LABEL=JAUNTY ro quiet   splash 
initrd		/initrd.img-2.6.28-11-generic
quiet
#--------------
title		Ubuntu 9.04 IBEX, kernel 2.6.27-7-generic
label=BOOT
kernel		/vmlinuz-2.6.27-7-generic root=label=IBEX ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

#-----------------------------------------
Use labels in your /etc/fstab file too.
change p.e 
UUID=d7575f29-5edc-4d2a-8e14-29e5fa842344 /               ext3    relatime,errors=remount-ro 0       1 
into
LABEL=JAUNTY  /     ext3    relatime,errors=remount-ro 0       1 
# ---------------
ain't it sweet ?
Erics

---

### Post by Ericyzfr1 on 2009-05-02
Almost look like an upgrade, I used Gparted LiveCD to clean the drive before installing. It seems that Ubuntu has a hard time to install on top of Ubuntu even if the version is different.

---

