---
title: "server installation on /dev/sda4  and grub error"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by pdc124 on 2009-02-08
ive got gentoo on dev/sda1 (boot) and /dev/sda3 (root) and /dev/sda2(swap) and im wanting to install ubuntu-server to /dev/sda4.
its seem to be OK up to the grub install. 

Im happy to overwrite whats there and then add back te kernel boot line for the gnetoo installation, but when i tell it to install grub to hd (0,0) it just says 'error'.

or i can tell it not to install grub and then edit the existing grub config to include ubuntu off hd(0,4) 

So either 

how do i get it to (re)install grub to hd(0,0) 
or
what is the config going to be that i can add manually to my existing grub setup ?

---

### Post by caljohnsmith on 2009-02-08
Installing Grub to (hd0,0) is the boot sector of sda1, your Gentoo /boot partition. Is that what you want? Or do you want to install Grub to the MBR? In other words, do you want Ubuntu Server to take over handling the booting process, or do you want to leave it with Gentoo or however it is configured now? Also, do you have a Live CD you can boot? If so, in order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

