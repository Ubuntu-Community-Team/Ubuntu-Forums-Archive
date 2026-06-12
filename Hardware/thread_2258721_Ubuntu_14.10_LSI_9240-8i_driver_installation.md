---
title: "Ubuntu 14.10 LSI 9240-8i driver installation"
date: 2014-12-29
forum: Hardware
---

### Post by Stefanvds on 2014-12-29
I'm quite new to Linux and just got my LSI 9240-8i
I'm running ubuntu on a normal SSD on the Mobo sata port.

i've downloaded the drivers for ubuntu from here: [http://www.lsi.com/products/raid-controllers/pages/megaraid-sas-9240-8i.aspx#tab/tab4](http://www.lsi.com/products/raid-controllers/pages/megaraid-sas-9240-8i.aspx#tab/tab4)
they are however for 10.04 and 10.10, and i have no idea what to do with the provided files in the ZIP.

any guidelines? I've never installed drivers for anything on Ubuntu (or any other linux).

when I run the lspci command i can find my LSI Logic card.

the drivers in the ZIP file contain 3 files.
megaraid_sas-v00.00.05.30-src.gz
megaraid_sas-v00.00.05.30_k2.6.35-22-server.amd64.gz
megaraid_sas-v00.00.05.30_k2.6.35-22-generic.i686.gz

inside the gz is just a .amd64 file or in the other a i686 file...

---

### Post by Stefanvds on 2014-12-30
Ok, I've found the .deb file in their Latest Linux Drivers pack. but they are only for 14.04 whilst im running .10
i've installed them but I still don't see any drives.


when i install the deb:

stefan@server:~/Desktop/ubuntu/rpms-1$ sudo dpkg -i megaraid_sas_06.705.06.00-1-ubuntu14.04_x86_64.deb 
(Reading database ... 217629 files and directories currently installed.)
Preparing to unpack megaraid_sas_06.705.06.00-1-ubuntu14.04_x86_64.deb ...
pre 06.705.06.00
Unpacking megaraid-sas (06.705.06.00-1) over (06.705.06.00-1) ...
postun 06.705.06.00
grep: /boot/config-3.13.0-24-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_5POLxa/lib/modules/3.13.0-24-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_5POLxa/lib/modules/3.13.0-24-generic/modules.builtin: No such file or directory
Working files in /tmp/mkinitramfs_5POLxa, early initramfs in /var/tmp/mkinitramfs-FW_7c9eul and overlay in /tmp/mkinitramfs-OL_5EbYPL
Working files in /tmp/mkinitramfs_Sv4Sv7, early initramfs in /var/tmp/mkinitramfs-FW_pXqJ91 and overlay in /tmp/mkinitramfs-OL_ywjkGc
Working files in /tmp/mkinitramfs_RINtod, early initramfs in /var/tmp/mkinitramfs-FW_YkJKRv and overlay in /tmp/mkinitramfs-OL_eaTRV2
Uninstall Done.
Setting up megaraid-sas (06.705.06.00-1) ...
post 06.705.06.00
post Install Done.

---

### Post by tokyobadger on 2014-12-30
[quote="Stefanvds"]grep: /boot/config-3.13.0-24-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_5POLxa/lib/modules/3.13.0-24-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_5POLxa/lib/modules/3.13.0-24-generic/modules.builtin: No such file or directory[/quote]
14.10 uses kernel 3.16.xx so the attempt to find directories related to kernel 3.13.xx is giving you the output above.

2 things come to mind:

1) lspci shows your LSI card - can you share the output (using code tags)
2) you don't see any drives - [are you using the WebBIOS Configuration Utility?]("https://media.dustin.eu/media/120645/megaraid-8-port-9240-8i-sassata-6gbs-pcie-raid-kit.pdf")
Other possibilities 

1) Update your mobo BIOS
2) Update your LSI firmware
3) the manual states only support for SATA II - not clear if that means there is backwards and forwards compatibility for SATA I and III drives
4) does your mobo have onboard RAID? If yes then is the chipset also LSI? Is it disabled? You may need to blacklist drivers for an onboard RAID chipset if it is also LSI

---

### Post by Stefanvds on 2014-12-31
managed to get it working out of the box with 14.04. 
thanks for the help :)

---

