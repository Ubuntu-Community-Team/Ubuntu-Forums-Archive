---
title: "Grub reinstall for dual boot vista/ubuntu"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by Brigrat on 2009-02-06
I had a good working dual boot system till I got bold and tried something new.  I installed tweakVI to stream line my boot process and messed up the whole shooting mtch.  No I get an error 17 on trying to boot to Linux/Ubuntu.  So How do I get grub reinstalled to manage boot-up with out (hopefully) having to do a full reinstall?  Yes I had tweakVI reinstall vista loader, so now the grub loader process are hosed up.  I coppied the following to paste in but I don't see whre I went wrong.  Can anyone out there help out this NOOB!

# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# [http://neosmart.net/wiki/display/EBCD](http://neosmart.net/wiki/display/EBCD)

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		af40d4e0-33d7-4aac-98bf-0368f0f2330f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=af40d4e0-33d7-4aac-98bf-0368f0f2330f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		af40d4e0-33d7-4aac-98bf-0368f0f2330f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=af40d4e0-33d7-4aac-98bf-0368f0f2330f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		af40d4e0-33d7-4aac-98bf-0368f0f2330f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=af40d4e0-33d7-4aac-98bf-0368f0f2330f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		af40d4e0-33d7-4aac-98bf-0368f0f2330f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=af40d4e0-33d7-4aac-98bf-0368f0f2330f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		af40d4e0-33d7-4aac-98bf-0368f0f2330f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

---

### Post by caljohnsmith on 2009-02-06
So is your goal to use Grub to boot both OSes instead of the Vista boot loader? In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Brigrat on 2009-02-06
OK, will get that out as soon as I can.  At work earning pennies now.  Is there a way to use the live CD to over write the MBR and put GRUB back in?  Either way I'll try and get that done tonight or in the morning.  Thanks for the fast reply.

---

### Post by caljohnsmith on 2009-02-06
Without getting a better idea of what your setup is, I can't say for sure, but you could try following these directions and it might be enough:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Brigrat on 2009-02-07
Caljohnsmith,

     The last thread and grub reinstall worked flawslessly, THANK YOU!!!!
just got my desktop up and running again.

---

### Post by caljohnsmith on 2009-02-07
Great, glad to hear your Grub is back; cheers and enjoy Ubuntu and Windows. :)

---

