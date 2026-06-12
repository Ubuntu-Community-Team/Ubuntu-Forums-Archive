---
title: "grub &quot;error 2&quot;"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by slam888 on 2009-02-13
i install xubuntu on an external HDD then when i first boot it up it say
grub error 2

been lookin at some post and have past my fdisk blah blah

dsl@box:~$ sudo fdisk -lu

Disk /dev/sda: 15.1 GB, 15103033344 bytes
255 heads, 63 sectors/track, 1836 cylinders, total 29498112 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/sda1   *          63    28161944    14080941   83  Linux
/dev/sda2        28161945    29495339      666697+   5  Extended
/dev/sda5        28162008    29495339      666666   82  Linux swap
dsl@box:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
dsl@box:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
ff00

---

### Post by caljohnsmith on 2009-02-13
Sounds like your Grub error 2 might be a result of how your HDD is set up in BIOS; but first it would help to get a clearer picture of your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

