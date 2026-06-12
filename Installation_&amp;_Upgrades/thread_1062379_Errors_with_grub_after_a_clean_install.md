---
title: "Errors with grub after a clean install"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by Lt Tinkle on 2009-02-06
I've been dual booting Ubuntu and XP for some time now and i decided to give Ubuntu some more HDD space.
I bought 1TB HDD for ubuntu to use and i reinstalled with the latest version (8.10).
After this reinstall when i boot grub gives error 15.
I tried changing the priority of my HDDs and that resulted in error 17.

I'm assuming this is because i added a new HDD and grub no longer points to the right directory but i deleted all the old Ubuntu partitions and reinstalled on the new HDD.

---

### Post by Lt Tinkle on 2009-02-06
I changed the priorities of the HDDs in the BIOS and can now boot into Ubuntu but i require a boot disk to get into XP. because the NTLDR is missing

---

### Post by caljohnsmith on 2009-02-06
If you would like some help sorting out your problem booting Windows, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

