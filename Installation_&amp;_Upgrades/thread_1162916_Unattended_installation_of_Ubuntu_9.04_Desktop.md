---
title: "Unattended installation of Ubuntu 9.04 Desktop"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by piddewest on 2009-05-18
Hi!

How does one use kickstart configuration file to make an unattended cdrom installation of ubuntu 9.04 desktop?

I have tried to follow some examples on the net and on ubuntus homepage but have never succeded to get the installation running.

Is there a good guide somewhere. Im keen on getting this to work because there might be a chance for me to introduce this fantastic operating system on my work.

---

### Post by wuhaa on 2009-06-15
Hi,

I'm also looking for the same thing. Anyone know how to do this??

Thanks,

---

### Post by haltbarmilch on 2009-06-20
Hello!

I have made a automatic installation with a preseed file. For me it works on 9.04. I hope it will work also for you. This is the entry in the ../pxelinux.cfg/default file for automatic installation.

```
LABEL Ubuntu_Server
kernel ubuntu-installer/i386/linux
append ramdisk_size=14984 debian-installer/locale=en_AT console-setup/layoutcode=de netcfg/get_hostname=ubuntu-client netcfg/get_domain=test.net url=http://192.168.0.1/preseed.cfg vga=normal initrd=ubuntu-installer/i386/initrd.gz --

```

You must give the locale settings as boot parameter, elsewhere you get a popup.

And here is the preseed file:

```

# Locale sets language and country.
d-i debian-installer/locale string en_AT

# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string de

### Network configuration
# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
d-i netcfg/choose_interface select auto

# Any hostname and domain names assigned from dhcp take precedence over
# values set here. However, setting the values still prevents the questions
# from being shown, even if values come from dhcp.
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain
d-i netcfg/get_hostname seen true
d-i netcfg/get_domain seen true

### Mirror settings
d-i mirror/country string manual
d-i mirror/http/hostname string at.archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

# Suite to install.
#d-i mirror/suite string jaunty;
# Suite to use for loading installer components (optional).
#d-i mirror/udeb/suite string jaunty;
# Components to use for loading installer components (optional).
d-i mirror/udeb/components multiselect main, restricted, universe, multiverse

### Clock and time zone setup
# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean true

# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string Europe/Vienna

# Controls whether to use NTP to set the clock during the install
d-i clock-setup/ntp boolean true
# NTP server to use. The default is almost always fine here.
#d-i clock-setup/ntp-server string ntp1.xyz.com

### Partitioning
# If the system has free space you can choose to only partition that space.
# Alternatives: custom, some_device, some_device_crypto, some_device_lvm.
d-i partman-auto/init_automatically_partition select biggest_free

# The presently available methods are: "regular", "lvm" and "crypto"
d-i partman-auto/method string regular

# If one of the disks that are going to be automatically partitioned
# contains an old LVM configuration, the user will normally receive a
# warning. This can be preseeded away...
d-i partman-lvm/device_remove_lvm boolean true
# The same applies to pre-existing software RAID array:
d-i partman-md/device_remove_md boolean true

# You can choose one of the three predefined partitioning recipes:
# - atomic: all files in one partition
# - home:   separate /home partition
# - multi:  separate /home, /usr, /var, and /tmp partitions
d-i partman-auto/choose_recipe select home

# This makes partman automatically partition without confirmation, provided
# that you told it what to do using one of the methods above.
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true

### Account setup
d-i passwd/root-login boolean true
# Password must be more then 8 characters, elsewere you get a security warning
d-i passwd/root-password password test1234
d-i passwd/root-password-again password test1234 

# To create a normal user account.
d-i passwd/user-fullname string Ubuntu
d-i passwd/username string ubuntu
# Normal user's password, either in clear text
# Password must be more then 8 characters, elsewere you get a security warning
d-i passwd/user-password ubuntu test1234
d-i passwd/user-password-again ubuntu test1234

# Set to true if you want to encrypt the first user's home directory.
#d-i user-setup/encrypt-home boolean false

### Apt setup
# You can choose to install restricted and universe software, or to install
# software from the backports repository.
d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/backports boolean true
d-i apt-setup/multiverse boolean true

# Select which update services to use; define the mirrors to be used.
# Values shown below are the normal defaults.
d-i apt-setup/services-select multiselect security
d-i apt-setup/security_host string security.ubuntu.com
d-i apt-setup/security_path string /ubuntu

# Additional repositories, local[0-9] available
d-i apt-setup/local0/repository string \
       http://packages.medibuntu.org/ jaunty free non-free
d-i apt-setup/local0/comment string Medibuntu
d-i apt-setup/local0/key string http://packages.medibuntu.org/medibuntu-key.gpg

### Package selection
tasksel tasksel/first multiselect ubuntu-desktop

# Individual additional packages to install
d-i pkgsel/include string openssh-server build-essential non-free-codecs w32codecs

# Policy for applying updates. May be "none" (no automatic updates),
# "unattended-upgrades" (install security updates automatically), or
# "landscape" (manage system with Landscape).
d-i pkgsel/update-policy select unattended-upgrades

# Some versions of the installer can report back on what software you have
# installed, and what software you use. The default is not to report back,
# but sending reports helps the project determine what software is most
# popular and include it on CDs.
popularity-contest popularity-contest/participate boolean false

### Boot loader installation

# This is fairly safe to set, it makes grub install automatically to the MBR
# if no other operating system is detected on the machine.
d-i grub-installer/only_debian boolean true

# This one makes grub-installer install to the MBR if it also finds some other
# OS, which is less safe as it might not be able to boot that other OS.
d-i grub-installer/with_other_os boolean true

### Finishing up the installation

# Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note

# This will prevent the installer from ejecting the CD during the reboot,
# which is useful in some situations.
d-i cdrom-detect/eject boolean false

### X configuration

# Monitor autodetection is recommended.
xserver-xorg xserver-xorg/autodetect_monitor boolean true
# Uncomment if you have an LCD display.
xserver-xorg xserver-xorg/config/monitor/lcd boolean true

# This command is run just before the install finishes, but when there is
# still a usable /target directory. You can chroot to /target and use it
# directly, or use the apt-install and in-target commands to easily install
# packages and run commands in the target system.
#d-i preseed/late_command string apt-install zsh; in-target chsh -s /bin/zsh;
```

I have added the Medibuntu Repository to the automated installation.

Greetings from Austria and i hope it will work for you.

---

