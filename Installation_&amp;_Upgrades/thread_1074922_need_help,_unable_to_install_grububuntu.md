---
title: "need help, unable to install grub/ubuntu"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by crhis on 2009-02-19
I am trying to install either ubuntu alongside xp. Xp was installed first and I am using it as a media center pc. I dont want to reformat because I have a lot of video and music on the xp side and nowhere to put it. When trying to install I get stuck on 94%, getting the fatal grub error. Ive tried using ext2 and changing where grub is installed to. I tried skipping the installation of grub and installing it later. When I tried typing "find /boot/grub/stage1" and it did not work. I then thought I new which drive I wanted to install on, hd(0,5), and I tried root (hd0,5) and I got the error "selected cylinder exceeds maximum supported by bios". Please help, I have installed ubuntu before on many systems and run across problems before, but after a day of googling I gave up. My specs are 

FOXCONN M61PMV AM2+ GF6100 RT
AMD|A64 X2 4800+ 2.5G AM2
2 gigs of ram
300 watt power supply
1.5 terabyte hdd

---

### Post by caljohnsmith on 2009-02-19
In order to get a clearer picture of your present setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Grub installation problems might be.

---

