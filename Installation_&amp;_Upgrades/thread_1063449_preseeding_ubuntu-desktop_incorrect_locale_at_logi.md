---
title: "preseeding ubuntu-desktop incorrect locale at login"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by NSharp on 2009-02-07
Hi,

after much reading, head scratching and jigging about with my test systems I have finally managed to get a pre-seeded install working off of apt-mirror.

The only problem is when the new build boots I have a non English locale and am unable to change it through the language menu.

I have tried with and with out setting locale on the boot section and with an with out d-i pkgsel/install-language_support booelean true

I have to build many systems shortly and getting a pre-seeded install working correctly is essential for me so any assistance would be greatly appreciated.

Below is my preseed file and below that my entry in the default file.


# Here we set up our locale/keyboard 
d-i debian-installer/locale string en_GB
d-i console-setup/layoutcode string en_GB
#d-i console-setup/modelcode string pc105
d-i console-setup/ask_detect boolean false
# We can set a specific nic up here
d-i netcfg/choose_interface select auto

# Any hostname and domain names assigned from dhcp take precedence over
# values set here. However, setting the values still prevents the questions
# from being shown, even if values come from dhcp.
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain

# Set the wep string automatically, quite handy 
d-i netcfg/wireless_wep string

### Mirror settings
# If you select ftp, the mirror/country string does not need to be set.
d-i mirror/country string enter information manually

# This is the IP address of our mirrored repository
d-i mirror/http/hostname string 192.168.0.25
# And this is the dist to platform to use
d-i mirror/http/directory string /ubuntu
# This is for a mirror proxy server which we dont use, it doesnt seem you can ignore this so leave it 
d-i mirror/http/proxy string

# Suite to install.
#d-i mirror/suite string testing
# Suite to use for loading installer components (optional).
#d-i mirror/udeb/suite string testing
# Here we can select the particular version we want, of course to install a different version you will have to include it in your mirror
d-i mirror/suite string hardy

### Partitioning
# If the system has free space you can choose to only partition that space.
# Note: this must be preseeded with a localized (translated) value.
#d-i partman-auto/init_automatically_partition \
# select Guided - use the largest continuous free space

# Alternatively, you can specify a disk to partition. The device name
# can be given in either devfs or traditional non-devfs format.
# For example, to use the first disk:
#d-i partman-auto/disk string /dev/discs/disc0/disc
d-i partman-auto/disk string /dev/sda
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
# Note: this must be preseeded with a localized (translated) value.
d-i partman-auto/choose_recipe \
select Separate /home, /usr, /var, and /tmp partitions
# This makes partman automatically partition without confirmation.
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition \
select Finish partitioning and write changes to disk
d-i partman/confirm boolean true

## Kernel image
d0i base-installer/kernel/image linux generic
### Clock and time zone setup
# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean true
# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string Europe/Dublin

### Apt setup
# We dont include thes in our mirror so rem them out
# You can choose to install non-free and contrib software.
#d-i apt-setup/multiverse boolean false
#d-i apt-setup/universe boolean false


# To create a normal user account.
d-i passwd/user-fullname string Ubuntu new login
d-i passwd/username string newlogin

# Normal user's password, either in clear text
d-i passwd/user-password password insecure
d-i passwd/user-password-again password insecure
# or encrypted using an MD5 hash.
# To create the hash string for the crypted password do the following in terminal
# echo "mypassword" | mkpasswd -s -H MD5
#d-i passwd/user-password password $somemd5string
d-i passwd/user-password password insecure
d-i passwd/user-password-again password insecure

# This is fairly safe to set, it makes grub install automatically to the MBR
# if no other operating system is detected on the machine.
d-i grub-installer/only_debian boolean true

# This one makes grub-installer install to the MBR if it also finds some other
# OS, which is less safe as it might not be able to boot that other OS.
d-i grub-installer/with_other_os boolean true

### Package selection 
tasksel tasksel/first multiselect ubuntu-desktop

# Individual additional packages to install
d-i pkgsel/install-language_support booelean true

### Finishing up the first stage install
# Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note
xserver-xorg xserver-xorg/autodetect_monitor boolean true
xserver-xorg xserver-xorg/config/monitor/selection-method \
select medium
xserver-xorg xserver-xorg/config/monitor/mode-list \
select 1024x768 @ 60 Hz 


And my entry in the default file

kernel ubuntu-installer/i386/linux
	append locale=en_GB console-setup/layoutcode=en_GB netcfg/choose_interface=eth0 netcfg/get_hostname=UbuntPXE url=http://192.168.0.25/Kickstart/preseed.cfg vga=normal initrd=ubuntu-installer/i386/initrd.gz --

---

### Post by NSharp on 2009-02-09
Dont worry about replying to this, I've given up on the idea as it wasnt acutally downloading off of my mirror after all just pulling the data straight off of the internet.

Project abandoned wasted to much time. Just wish it was as simple as setting up a RIS server


Thanks

---

