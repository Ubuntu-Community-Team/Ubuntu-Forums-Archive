---
title: "Installed 8.10 on XP box for dualboot, no grub/ubuntu?"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by cwelch on 2009-02-25
I recently inherited a box from another desk at my office. Windows was loaded on D (which is a 60gb SATA) and C (160gb IDE) was just unformatted space. Had to reload XP and it went back to that D, boots just fine, all that stuff. I assume when it said it needed to do something for setup to the unpartitioned space that it was just writing something for a boot sector or whatever to flag D as bootable. After getting XP off the ground I tried (with horrible failure) to install 8.10 onto the unpartitioned 160 drive. The setup was fine, but no grub or anything! So I wiped it back off using gparted with the live cd and tried splitting that 60gb to do it. Still failed. Install was ok, but again no grub. How do I fix this? I can't get into Ubuntu to check out my menu.lst, and I'm not quite sure where to go on it. Could running update-grub from live cd fix it? I can't really afford to jack the loader for windows up just on a hunch. I have it loaded with Wubi now, but I'd just assume do it full on in case Windows dies later. I could do a VM but I would RATHER to Ubuntu with an XP VM though one one side of the cube. I'd jsut be handier since I have a lot of ssh/telnet stuff going and hate SecureCRT.

Thanks!

-Charlie

---

### Post by TimDaniels on 2009-02-25
> **cwelch said:**
> I recently inherited a box...

If you want to dual boot XP and Linux with XP installed 1st and you want Grub to be the boot manager, check this out:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

if you instead want to use XP's ntldr as the boot manager, check this out:
[http://jaeger.morpheus.net/linux/ntldr.php](http://jaeger.morpheus.net/linux/ntldr.php)

*TimDaniels*

---

### Post by caljohnsmith on 2009-02-25
So is Ubuntu still installed to its own partition, or did you delete its partitions? If Ubuntu is still installed, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

