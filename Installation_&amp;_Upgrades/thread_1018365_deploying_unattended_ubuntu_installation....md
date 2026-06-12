---
title: "deploying unattended ubuntu installation..."
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by Mia_tech on 2008-12-22
guys I need to deploy ubuntu to 15 machines, and I need a suggestion on how would be the best way to do this... I first need to make a master image of a computer to be deploy to the rest, but I'm looking for an easy way, in the past I've used partimage, but partimage only deploy partitions and not the entire disk, another problem with partiamge is that the disk needs to be partitioned first, and the other option would be using dd, but also in the past dd has proven to be a little slow for my taste... I was thinking on booting the machines with pxe and deploying the image... advise me what approach should I take?

thanks

---

### Post by Partyboi2 on 2008-12-22
You could try a network install using preseed files
[http://www.debuntu.org/how-to-unattended-ubuntu-network-install](http://www.debuntu.org/how-to-unattended-ubuntu-network-install)

---

### Post by Mia_tech on 2008-12-23
I'm having difficulties getting the client machine reading the preseed.cfg file off the web server, it says that can't be found and I know is there and is correctly spelled, it is a windows 2003 server.


thanks

---

### Post by Mia_tech on 2008-12-23
is it possible to create a repository by just copying the content of the alternate cd and hosting it on a web server?, in this case is a 2003 server, or do I need Ubuntu for this, I'm trying to host a local repository where I can pull the installation of an unattended ubuntu install. Also I'm pulling the preseed.cfg file from a web server and I'm getting error "file is corrupt", I got a copy of this [preseed.cfg file]("http://www.debuntu.org/how-to-unattended-ubuntu-network-install-preseed-p5") and custmize it to my needs, basically what I've changed is the ip of the repository server... preseed.cfg file

>   d-i debian-installer/locale string en_GB

    d-i console-setup/layoutcode string en_GB

    d-i netcfg/choose_interface select auto

    # Any hostname and domain names assigned from dhcp take precedence over

    # values set here. However, setting the values still prevents the questions

    # from being shown, even if values come from dhcp.

    d-i netcfg/get_hostname string ubuntu-123

    d-i netcfg/get_domain string unassigned-domain

    d-i netcfg/wireless_wep string

    ### Mirror settings

    # If you select ftp, the mirror/country string does not need to be set.

    d-i mirror/country string enter information manually

    d-i mirror/protocol string http

    d-i mirror/http/hostname string 10.200.50.7

    d-i mirror/http/directory string /ubuntu-distro

    d-i mirror/http/proxy string

    # Suite to install.

    #d-i mirror/suite string testing

    # Suite to use for loading installer components (optional).

    #d-i mirror/udeb/suite string testing

    d-i mirror/suite string feisty

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

    ### Clock and time zone setup

    # Controls whether or not the hardware clock is set to UTC.

    d-i clock-setup/utc boolean true

    # You may set this to any valid setting for $TZ; see the contents of

    # /usr/share/zoneinfo/ for valid values.

    d-i time/zone string Europe/Dublin

    ### Apt setup

    # You can choose to install non-free and contrib software.

    d-i apt-setup/multiverse boolean true

    d-i apt-setup/universe boolean true

    # To create a normal user account.

    d-i passwd/user-fullname string Ubuntu Server Administrator

    d-i passwd/username string ubuntuadmin

    # Normal user's password, either in clear text

    #d-i passwd/user-password password insecure

    #d-i passwd/user-password-again password insecure

    # or encrypted using an MD5 hash.

    d-i passwd/user-password-crypted password $1$ApZFpRq5$X38skX90ZL36YOnbYt/3J

    # This is fairly safe to set, it makes grub install automatically to the MBR

    # if no other operating system is detected on the machine.

    d-i grub-installer/only_debian boolean true

    # This one makes grub-installer install to the MBR if it also finds some other

    # OS, which is less safe as it might not be able to boot that other OS.

    d-i grub-installer/with_other_os boolean true

    ### Package selection

    tasksel tasksel/first multiselect standard, lamp-server

    # Individual additional packages to install

    d-i pkgsel/include string openssh-server

    ### Finishing up the first stage install

    # Avoid that last message about the install being complete.

    d-i finish-install/reboot_in_progress note

    xserver-xorg xserver-xorg/autodetect_monitor boolean true

    xserver-xorg xserver-xorg/config/monitor/selection-method \

    select medium

    xserver-xorg xserver-xorg/config/monitor/mode-list \

    select 1024x768 @ 60 Hz 


thanks

---

### Post by Mia_tech on 2008-12-23
here's a  snapshot of the error

[http://pctechtips.org/preseed.cfg.jpeg]("http://pctechtips.org/preseed.cfg.jpeg")

thanks

---

### Post by Mia_tech on 2008-12-23
and when I press enter to get passed the previous error I get is "failed to download debconf configuration file"

here's a screenshot
[URL="http://pctechtips.org/pxe-error-2.jpeg"]
pxe error #2[/URL]

thanks

---

### Post by Mia_tech on 2008-12-24
ok, the problem was that the preseed file was containing some errors as far as formatting goes, now i"m getting error when trying to download ubuntu from the mirror, and here's what I did I downloaded and copy the content of the Alternate cd to a windows 2003 server.... could someone advise me how could I setup a mirror on windows machine?

thanks

---

