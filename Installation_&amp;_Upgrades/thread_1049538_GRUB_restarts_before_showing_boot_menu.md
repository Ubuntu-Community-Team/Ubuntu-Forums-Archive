---
title: "GRUB restarts before showing boot menu"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by jamoo1980 on 2009-01-24
I have just installed Ubuntu 8.10 from a LiveCD. The installation seems to work fine, but then when I restart the machine it won't boot. The pre-boot / BIOS checks all happen as usual, then I get the first couple of lines of GRUB console output for a fraction of a second, then the machine restarts itself. It looks like GRUB might be crashing for some reason, and causing a reboot. Either that, or the default run level is somehow being set to 6 (restart) but I don't know how to check for this. In any case, I can't get the machine to boot. Does anyone have any ideas on what I can try...?

Thanks :)
James

---

### Post by caljohnsmith on 2009-01-24
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

