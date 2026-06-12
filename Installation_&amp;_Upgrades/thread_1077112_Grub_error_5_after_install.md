---
title: "Grub error 5 after install"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by Rahu on 2009-02-22
I just attempted to install ubuntu on my external drive. I manually formatted the partitions with a 2gb swap and the rest as ext3.

The install went fine, when I rebooted grub came up with error 5

When looking at the partition table after the install I noticed that my / partion wasn't flagged as bootable, so I assume I may have done something wrong.

In addition, the gui option on the vista install cd to fix the MBR (I don't recall its name) said there were no problems that would stop windows from booting.

Now whenever I boot my computer I get error 5, is there anything I can do to fix this?

EDIT: I was able to get the vista mbr back in and working again, but I'd still like to be able to get ubuntu working if anyone can help.

---

### Post by caljohnsmith on 2009-02-22
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

