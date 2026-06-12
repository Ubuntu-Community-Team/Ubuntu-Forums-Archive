---
title: "Install to External HD: Grub error 17!!! PLEASE HELP"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by boopit on 2009-09-02
I have installed kubuntu many times before, so I assumed that i knew what i was doing. I didn't want to install linux to my internal hard drive this time, though. So, I decided to install it to a partition on my external hard drive. I format the partition as ext4, and proceed with the installation. There were no installation errors, but when I reboot i get the all-too-familiar GRUB ERROR 17. I even tried just booting from my external hard drive, instead of letting GRUB do the work, but that didnt help. 

I'm afraid to do anything else, and i know my parents will be EXTREMELY pissed if they find out i screwed up my computer. 

PLEASE HELP!!! :(

Note: my computer normally has vista 64 bit on it, incase that helps.

---

### Post by ronparent on 2009-09-02
It's unclear what your boot drive is. If you set boot order to boot first to the external drive the solution may be trivial and allow you to boot directly to vista an the internal drive when the external is unplugged - providing you first restore the win boot loader to that drive. 

To setup grub on the mbr of the external drive, boot to the live cd and open a terminal session. In the terminal enter the following commands:

**sudo grub**

and from the grub prompt enter the command:

**find /boot/grub/stage1**

using the location in the output from the above enter:

[B]root (hdx,y) - x and y are the numbers in the above output
setup (hdx)[/B]

**quit** and restart

Everything should now present correctly on boot from the external drive.  Your work to fix grub should now be complete. If you have to fix the entry to boot vista from grub post a question here. Then you will also have to restore the mbr on the internal drive to boot directly to vista when the external drive is offline. That will require using the vista disk to repair the mbr (**fixmbr**). Enjoy and good luck.

---

