---
title: "Keyboard doesn't work on GRUB"
date: 2017-12-06
forum: Hardware
---

### Post by EthioJOB on 2017-12-06
[COLOR=#111111][FONT=Ubuntu]I have Ubuntu 16.04 installed on an Acer Aspire VN7-792G laptop.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The keyboard was working normally until one day it suddenly stopped working on Grub menu. I can't select OS or even enter BIOS. But it normally boots into Ubuntu after waiting out the normal GRUB timeout (10 seconds I think), and the keyboard works fine then.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried to do some research and come across 'ohci_pci' and 'initramfs' but I couldn't understand how to apply them to my case or if they are even relevant to my case.

For what it's worth, when I press F2 or F12 during the boot splash it does enter to BIOS, but can't proceed from that because I previously setup a password for it, and the keyboard doesn't work so I can't type it :-(.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I would appreciate it if anyone can help.[/FONT][/COLOR]

---

### Post by linuxsecrets on 2017-12-06
Sounds like you have the wrong keyboard map?


You could insert the GRUB_TERMINAL_INPUT="at_keyboard" to verify keyboard.  Usually c or e during grub, then add the line to the end of your kernel grub line.


You could also add the line to your /etc/default/grub file so it's added automatically after kernel upgrade or compiling.

---

### Post by EthioJOB on 2017-12-07
> **linuxsecrets said:**
> Sounds like you have the wrong keyboard map?


You could insert the GRUB_TERMINAL_INPUT="at_keyboard" to verify keyboard.  Usually c or e during grub, then add the line to the end of your kernel grub line.


You could also add the line to your /etc/default/grub file so it's added automatically after kernel upgrade or compiling.
Thanks a lot! I couldn't press 'or c' or 'e' as I couldn't use the keyboard on grub, but I added the entry through gedit on /etc/default/grub as per your second suggestion and it worked. So my major problem is solved.

However, it still won't work when I try to enter BIOS. As I mentioned the keyboard won't work so I can't type the password. Do you have any suggestions?

---

### Post by gordintoronto on 2017-12-07
Does the keyboard work once you are in Ubuntu? If you can't get into the BIOS, that has nothing to do with Ubuntu, I would expect it to be a hardware problem.

---

