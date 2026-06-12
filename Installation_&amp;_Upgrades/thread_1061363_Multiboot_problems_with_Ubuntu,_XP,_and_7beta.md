---
title: "Multiboot problems with Ubuntu, XP, and 7beta"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by Ubuntnoob1219 on 2009-02-05
Please try to be relatively simple in any instructions, I am new to Ubuntu, and do not understand using the terminal very well. Anything which requires that I use the terminal or other command line type utilities needs to be carefully explained. Thank you so much.

I have a laptop with Windows XP, Windows 7 beta, and Ubuntu 8.10. Currently, when I turn it on, I get the GRUB bootloader with an option to boot Ubuntu (as well as related options, such as 640x480 mode, etc.) and an option to boot Vista/Longhorn bootloader, which in turn presents me an option to choose between XP and 7. How can I condense this all into one bootloader?
When I installed the system, First I installed XP, then I repartitioned my Hard drive into 3 partitions: 90GB for XP, a 75GB partition which I installed Windows 7 on, and a 30GB unpartitioned space which I had reserved for Ubuntu. When I was installing Ubuntu, I formatted 28GB of the partition as ext3 for ubuntu, and 2GB as a swap file (this is similar to the page file used by windows as virtual RAM, correct?).
My computer is a Dell Inspiron 6400 laptop with the original hard drive replaced (by me, not Dell) a 7200 rpm model. 1GB RAM, 1.6 GHz Centrino Dual core processor

---

### Post by sedawk on 2009-02-05
Run this command to edit your /boot/grub/menu.lst
```

sudo gedit /boot/grub/menu.lst

```

You will see a section like this in that file:
```

title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

First you can rename the misleading title (e.g make it say "XP").
Then you can copy the whole section and paste it below
the existing section. Replace the title with something
like "Windows 7" and the value for root with "(hd0,1)".
(This will work if Windows 7 is on /dev/sda2. If it is
 not you have to change the second number, e.g. "(hd0,2)").

After saving the file and rebooting selecting "Windows 7" in
the grub menu should boot Windows 7.

Some remarks:
The reason that booting "Vista/Longhorn" asks you for
XP or Windows 7 is (if I remember right) the boot manager
of XP, e.g. there are now two options in boot.ini.
If you booting Windows 7 with grub works you might try
your luck and remove the second entry from boot.ini.

You can alter the boot configuration on the fly.
Boot the machine, interrupt grub, go to Vista/Longhorn line,
press 'e' for edit, go to "root" and press 'e' for edit again.
Now change (hd0,0) to (hd0,1) and after pressing return press
'b' to boot. So you can test changes without editing menu.lst

---

### Post by Ubuntnoob1219 on 2009-02-05
I run the command by opening up terminal, typing it in and pressing enter, right?

---

### Post by Ubuntnoob1219 on 2009-02-05
I tried changing the second number (hda 0,x) in a duplicate of the existing windows entry, but it didnt work. ultimately, I want to cease to use the windows bootloader and have both windows systems botting directly from GRUB. Is there something else I'm supposed to do besides changing that second number to skip the bootloader and go directly to one of the versons of windows? And how can I find out for sure what I need to put into grub to make it go to the particular version?

---

