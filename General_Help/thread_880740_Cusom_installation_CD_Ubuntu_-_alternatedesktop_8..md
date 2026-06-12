---
title: "Cusom installation CD Ubuntu - alternate/desktop 8.04 preseed doesn't work..."
date: 2008-08-05
forum: General Help
---

### Post by shaft on 2008-08-05
Hello!

I want to make a ubuntu 8.04 to be installed without the user asks nothing, but something is going wrong everytime...
Let's start from the beginning ... I've startet to read InstallCDCustomization in ubuntu documents. I've tried it of its VirtualBox and again asked how to split hard drive, layouts, etc ... 
Then i've started to read and shot and preseeding in ubuntu 8.04 - and now my things I want to ask me not in this file:

preseeded.seed
```

# Locale sets language and country.
d-i debian-installer/locale string bg_BG
# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
#d-i console-setup/modelcode string pc105
d-i console-setup/layoutcode string us
# To select a variant of the selected layout (if you leave this out, the
# basic form of the layout will be used):
#d-i console-setup/variantcode string dvorak
#
#PARTITIONIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIING !!!!
#
# If the system has free space you can choose to only partition that space.
# Alternatives: custom, some_device, some_device_crypto, some_device_lvm.
#d-i partman-auto/init_automatically_partition select biggest_free
# Alternatively, you can specify a disk to partition. The device name must
# be given in traditional non-devfs format.
# For example, to use the first SCSI/SATA hard disk:
d-i partman-auto/disk string /dev/sda
# Note: If you want to use whatever disk is available, no matter
# what its device name, comment the line above out. This will only work if
# the system only has one disk.
# In addition, you'll need to specify the method to use.
# The presently available methods are: "regular", "lvm" and "crypto"
d-i partman-auto/method string lvm
# If one of the disks that are going to be automatically partitioned
# contains an old LVM configuration, the user will normally receive a
# warning. This can be preseeded away...
d-i partman-auto/purge_lvm_from_device boolean true
# And the same goes for the confirmation to write the lvm partitions.
d-i partman-lvm/confirm boolean true
# You can choose from any of the predefined partitioning recipes.
# atomic: All files in one partition (recommended for new users)
# home: Separate /home partition
# multi: Separate /home, /usr, /var, and /tmp partitions
# small_disk (alpha architecture only):
#   Small-disk (< 1GB) partitioning scheme
d-i partman-auto/choose_recipe select atomic
#d-i partman-auto/choose_recipe select home
#d-i partman-auto/choose_recipe select multi
#d-i partman-auto/choose_recipe select small_disk
#This makes partman automatically partition without confirmation, provided
# that you told it what to do using one of the methods above.
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
# Avoid that last message about the install being complete.
tasksel	tasksel/first	multiselect ubuntu-desktop
d-i finish-install/reboot_in_progress note

```

In my isolinux.cfg added as normal/default ubuntu installation added option:

```


DEFAULT /casper/vmlinuz
GFXBOOT bootlogo
---------------------------------------------------------------------------------------------------------------------------------------------
APPEND  file=/cdrom/preseed/preseeded.seed boot=casper initrd=/casper/initrd.gz quiet splash --

---------------------------------------------------------------------------------------------------------------------------------------------

LABEL Preseeded Ubuntu
  menu label ^install Preseeded Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/preseeded.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --

---------------------------------------------------------------------------------------------------------------------------------------------


LABEL live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --


LABEL live-install
  menu label ^Install Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --


LABEL check
  menu label ^Check CD for defects
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --


LABEL memtest
  menu label Test ^memory
  kernel /install/mt86plus
  append -


LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -

DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

```
(Here I am hited enters and dashes for the forum, just for readability ... The normal file is clear from them...)

It still doesn't work... How can i get it to work?
Can someone help me? May be very few things, but I do not have much experience with ubuntu ... I'll be very grateful for any help!
I don't know how to add my custom packages too - i want to add some dictionaries, some custom movies programs and so on and so on...  
Thanks in advance !!! 

Regards,
Ventsislav Chochev

---

