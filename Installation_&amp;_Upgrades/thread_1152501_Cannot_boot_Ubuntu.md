---
title: "Cannot boot Ubuntu"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by Brian88 on 2009-05-07
Hi,
when I tried to run Ubuntu 8.04 installed with Wubi it appears error like this :

[HTML]
find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst

Error 15: File not found

Press any key to continue[/HTML]

How to resolve that issue?

Thanks for your support

---

### Post by caljohnsmith on 2009-05-07
That error means that Grub4DOS, which is Ubuntu's boot loader under Wubi, couldn't find the /ubuntu/install/boot/grub/menu.lst file in your Windows partition. When you installed Ubuntu, did you turn off all your virus protection programs in Windows? If you didn't, I would first suggest doing that, because they invariably interfere with installing Ubuntu, because a Wubi Ubuntu installation has to do lots of low-level operations that can appear dangerous to an anti-virus program. 

If you still run into problems, I would suggest booting your Ubuntu Live CD, downloading the **Boot Info Script** to the Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by Brian88 on 2009-05-14
No, I have installed my Hardy (Wubi) since some months ago.

And I can't do the live-cd trick, because my DVD drive is broken.

But on the D:\Ubuntu\winboot, the place where I installed Ubuntu, there is a file called menu.lst, is that same with the menu.lst I have lost?

Below is the CMD where I found it, you can examine the directory.

```
D:\ubuntu>dir
 Volume in drive D is Data
 Volume Serial Number is 6CD3-87AE

 Directory of D:\ubuntu

12/06/2008  09:34    <DIR>          .
12/06/2008  09:34    <DIR>          ..
12/06/2008  09:34                 0 curl_log.txt
12/06/2008  09:34    <DIR>          docs
12/06/2008  09:49    <DIR>          install
12/06/2008  09:41               225 metadl_log.txt
22/04/2008  20:57            25.214 Ubuntu.ico
12/06/2008  09:34           114.776 Uninstall-Ubuntu.exe
12/06/2008  09:34    <DIR>          winboot
               4 File(s)        140.215 bytes
               5 Dir(s)  13.912.473.600 bytes free

D:\ubuntu>cd winboot

D:\ubuntu\winboot>dir
 Volume in drive D is Data
 Volume Serial Number is 6CD3-87AE

 Directory of D:\ubuntu\winboot

12/06/2008  09:34    <DIR>          .
12/06/2008  09:34    <DIR>          ..
22/04/2008  20:57               782 menu.lst
22/04/2008  20:57           186.463 wubildr
22/04/2008  20:57           202.879 wubildr.exe
22/04/2008  20:57             8.192 wubildr.mbr
               4 File(s)        398.316 bytes
               2 Dir(s)  13.912.473.600 bytes free

```

---

### Post by Brian88 on 2009-05-14
Oh no, the menu.lst in \winboot dir is the "emergency" menu found in the error GRUB prompt.

Could you make the menu.lst? Or can you just copy your current menu.lst and I will modify it so it can boot my ubuntu at D:\ubuntu ?

Below is the content of the "emergency" menu.lst found at \winboot, and this is NOT the menu.lst I need to boot.

```
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 3
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot
```

---

