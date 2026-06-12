---
title: "PXE installation"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by subin_hutton on 2009-07-04
Hi Guys,

I'm a newbie in ubuntu.We are tryin to develop a software to automate pxe installation.Now we are testing ubuntu.We've configured dhcp.tftpd and preceed.cfg and installation started without any issues.But it got stucked after mesasge 
[B]
"INFO:Menu item 'network-preseed' selected".[/B]

Loader configuration
===============
DEFAULT install
LABEL install
kernel ubuntu-installer/i386/linux
append vga=normal ramdisk_size=14984 initrd=ubuntu-installer/i386/initrd.gz preseed/url=http://192.168.2.22/cimt/repo/ks/11-11-22-22-11-22/preseed.cfg debian-installer/locale=en_US console-setup/layoutcode=us netcfg/choose_interface=auto netcfg/get_hostname=test 
PROMPT=1
TIMEOUT=300

Preseed.cfg
=========
##LANGUAGE ##
d-i debian-installer/locale string en
d-i console-setup/ask_detect boolean false
d-i console-keymaps-at/keymap select us
d-i netcfg/choose_interface select auto

## MIRROR ##
d-i mirror/country string manual
d-i mirror/http/hostname string 192.168.0.209
d-i mirror/http/directory string /repo/ubuntu/
d-i mirror/http/proxy string

## CLOCK & TIME ##
d-i clock-setup/utc boolean true
d-i time/zone string Asia/Calcutta

## PARTITION ##
d-i partman-auto/method string lvm
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-lvm/confirm boolean true
d-i partman-auto/choose_recipe select atomic
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true

### Account setup
# Root password, either in clear text
d-i passwd/root-password password calpine
d-i passwd/root-password-again password calpine
d-i passwd/user-fullname string sample
d-i passwd/username string sample 
# Normal user's password, either in clear text
d-i passwd/user-password password insecure
d-i passwd/user-password-again password insecure

## GRUB INSTALL  ##
d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true
d-i finish-install/reboot_in_progress note
### APT SETUP 
d-i apt-setup/local0/repository string [http://192.168.0.209/repo/ubuntu/](http://192.168.0.209/repo/ubuntu/)

# PACKAGE SELECTION
tasksel tasksel/first multiselect ubuntu-desktop
## POST INSTALL ##

your help is much appreciated.

Thanks.
Subin Hutton
d-i preseed/late_command string mkdir -p /tmp/subin;cd /tmp/subin;wget [http://192.168.2.22/cimt/repo/script/dbupdate.sh;touch](http://192.168.2.22/cimt/repo/script/dbupdate.sh;touch) a.txt;echo "Download Success" > a.txt

---

