---
title: "Ubuntu Preseeding With Software Raid?"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by mhalligan on 2009-04-27
Has anybody ever actually gotten preseeding to work with software raid? I'm following the example pretty much verbatim here, but still no dice.  The error I get on the installer is "No root partition defined" .. If I shell in and look at /tmp/expert_recipe I note it does have the Raid setup but not assignments

d-i debian-installer/locale string en_US
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us
d-i netcfg/choose_interface select auto
d-i netcfg/dhcp_timeout string 90
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain
d-i netcfg/wireless_wep string
d-i mirror/protocol string http
d-i mirror/country string manual
d-i mirror/http/hostname string mirrors.kernel.org
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string [http://proxyhost:3142](http://proxyhost:3142)
d-i clock-setup/utc boolean true
d-i time/zone string US/Pacific
d-i clock-setup/ntp boolean true
d-i clock-setup/ntp-server us.pool.ntp.org
d-i partman-auto/disk string /dev/sda /dev/sdb
d-i partman-auto/method string raid
d-i partman-auto/expert_recipe string \
      multiraid ::                                         \
              1000 5000 4000 raid                          \
                      $primary{ } method{ raid }           \
              .                                            \
              64 512 3000 raid                             \
                      method{ raid }                       \
              .                                            \
              500 10000 1000000000 raid                    \
                      method{ raid }                       \
              .
d-i partman-auto-raid/recipe string \
    1 2 0 ext3 /                                           \
        /dev/sda/part1#/dev/sdb/part1    \
    .                                                      \
    1 2 0 swap -                                           \
          /dev/sda/part5#/dev/sdb/part5    \
    .                                                      \
    1 2 0 ext3 /home                                       \
          /dev/sda/part6#/dev/sdb/part6    \
    .
d-i partman-md/confirm boolean true
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i passwd/root-login boolean true
d-i passwd/make-user boolean false
d-i passwd/root-password password fakepass
d-i passwd/root-password-again password fakepass
d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/multiverse boolean true
tasksel tasksel/first multiselect standard
d-i pkgsel/include string openssh-server build-essential puppet
d-i pkgsel/update-policy select none
d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true
d-i grub-installer/bootdev  string (hd0,0) (hd1,0)
d-i finish-install/keep-consoles boolean true
d-i finish-install/reboot_in_progress note

---

