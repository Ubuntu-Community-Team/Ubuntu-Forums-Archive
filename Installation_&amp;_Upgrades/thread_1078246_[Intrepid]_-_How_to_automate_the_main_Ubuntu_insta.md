---
title: "[Intrepid] - How to automate the main Ubuntu installation screen (syslinux)?"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by julio.maranhao on 2009-02-23
Hi, people! This is my first post. Maybe somebody can help me.

I just figured out how to do a headless installation (ssh) from a USB stick. Of course all my tests were using a head (KVM). The stick was generated using an Intrepid Alternate CD and the app "System" -> "Administration" -> "Create a USB startup disk".

To automate to the point to get an ssh connection, I changed two files in the stick:

**/syslinux/text.cfg:**
default automatic
label automatic
  menu label Install Ubuntu via ^SSH
  kernel /install/vmlinuz
  append  noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu-ssh.seed initrd=/install/initrd.gz auto=true priority=critical console-setup/layoutcode=br console-setup/variantcode="" console-setup/modelcode=abnt2 quiet --

**/preseed/ubuntu-ssh.seed:**
d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string ps2-server1
d-i network-console/password password 1234
d-i network-console/password-again password 1234
d-i preseed/early_command string anna-install network-console

ubutu-ssh.seed was created and is referenced by the new menu item "automatic".

What I want is to get rid of the "Choose a language" auto pop-up (F2) and to timeout to the default menu item. These are syslinux related. I can bypass it just modifying syslinux.cfg:

prompt 1
timeout 10
default install
label install
kernel /install/vmlinuz
append  cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed initrd=/install/initrd.gz auto=true priority=critical console-setup/layoutcode=br console-setup/variantcode="" console-setup/modelcode=abnt2

But this is an ugly solution since I loose the beautifull menu advantage of a head installation.

Any hints? 

Cheers

Júlio

---

### Post by mintaka77 on 2010-03-22
Maybe this can help You:
"Automating the installation using preseeding"

[https://help.ubuntu.com/7.04/installation-guide/i386/preseed-creating.html]("https://help.ubuntu.com/7.04/installation-guide/i386/preseed-creating.html")

---

