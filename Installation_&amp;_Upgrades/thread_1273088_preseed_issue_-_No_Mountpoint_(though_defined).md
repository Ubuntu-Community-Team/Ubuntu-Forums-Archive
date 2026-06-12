---
title: "preseed issue - No Mountpoint (though defined)"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by jasonjwwilliams on 2009-09-23
Hi,

When using a preseed file, I repeated get this message despite mountpoints being defined:

 No mount point is assigned for the xfs file system in partition #1 of SCSI1 (0,0,0) (sda).

Preseed.cfg contents is below, any help is greatly appreciated.

This is Ubuntu 8.04.3 (Hardy Heron) on a SunFire X2100M2.

-J

[FONT="Courier New"]# SunFire X2100M2 Pre-seed

# Locale sets language and country.
d-i debian-installer/locale string en_US

# Keyboard selection.
# Disable automatic keymap detection.
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us

# Network configuration
d-i netcfg/choose_interface select eth2
d-i netcfg/get_hostname string phasea

# Mirror
d-i mirror/country string manual
d-i mirror/http/hostname string archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

d-i mirror/suite string hardy

# Timezone
d-i clock-setup/utc boolean true
d-i time/zone string GMT

# NTP
#d-i clock-setup/ntp boolean true
#d-i clock-setup/ntp-server 10.1.48.23

# Partitioning
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
d-i partman-auto/expert_recipe string           \
    boot-root :: 57 10 57 xfs                   \
            $primary{ } $bootable{ }            \
            method{ format } format{ }          \
            use_filesystem{ } filesystem{ xfs } \
            mountpoint { /boot }                \
        .                                       \
        9626 9626 9626 xfs                      \
            method{ format } format{ }          \
            use_filesystem{ } filesystem{ xfs } \
            mountpoint{ / }                     \
        .                                       \
        1024 50 200% linux-swap                 \
            method{ swap } format { }           \
        .                                       \
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true

# User account (skip root)
d-i passwd/root-login boolean false
d-i passwd/user-fullname string <snip>
d-i passwd/user-password-crypted password <snip>

# Base Package Set
tasksel tasksel/first multiselect standard

#  Needed Packages
d-i pkgsel/include string   openssh-server  \
                            build-essential \
                            libpam-ldap     \
                            libnss-ldap     \
                            nss-updatedb    \
                            sudo-ldap       \
                            subversion      \
                            traceroute      \
                            portmap         \
                            nfs-common      \
                            git-core        \
                            puppet

# Boot Loader
d-i grub-installer/skip boolean true
d-i lilo-installer/with_other_os boolean true

# Reboot
d-i finish-install/reboot_in_progress note[/FONT]

---

