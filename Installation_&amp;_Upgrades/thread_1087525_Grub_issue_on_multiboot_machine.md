---
title: "Grub issue on multiboot machine"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by nick6196 on 2009-03-05
I have a dual boot PC with three partitions on the C drive containing Windows XP, Linux Mint 4, and a SWAP partition. Yesterday I installed Ubuntu 8.04 LTS onto a second hard drive. All seemed to go well until I tried to boot into the newly installed Ubuntu and all I got was my normal Linux Mint grub menu with no Ubuntu option on it. 

First I checked the menu.lst file in Ubuntu and it has been written correctly, it recognised both of the other operating systems and added stanzas for them.

Then I thought that perhaps I needed to switch the boot order in setup so that it would boot to the new Ubuntu partition first. I did that and yet still it is presenting me with the Linux Mint grub menu.

I did wonder about overwriting the Linux Mint menu.lst file with the Ubuntu one but I ultimately want to delete the Linux Mint partition to make more space for windows so even if it worked it would only be a temporary solution.

How can I get my PC to read from the Ubuntu grub menu on the second hard drive?

---

### Post by meierfra. on 2009-03-08
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and do:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

