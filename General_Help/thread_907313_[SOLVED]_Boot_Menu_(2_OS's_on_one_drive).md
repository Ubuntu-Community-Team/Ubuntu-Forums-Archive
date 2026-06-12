---
title: "[SOLVED] Boot Menu (2 OS's on one drive)"
date: 2008-09-01
forum: General Help
---

### Post by ^^rac on 2008-09-01
Hi guys!

Just a quicky, i have installed Ubuntu in a Windows partition! (Great!!!)

When i swith my PC on, i get a boot menu, witht XP as default, Ubuntu second......

Any way one can swop the 2 entries round? (Im not sure if this is a Windows function or Linux?)

Cheeeers! :guitar:

---

### Post by ^^rac on 2008-09-02
Hi anyone?

---

### Post by jigsaws on 2008-09-02
The easiest way is change default=0 to default=1 at /boot/grub/menu.lst
But of course you can also swap entires there.

---

### Post by Victormd on 2008-09-02
You need to edit your menu.lst. To do this, open a terminal and type:
```
sudo gedit /boot/grub/menu.lst
```
Look for the block that looks like this:
> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
and change the **default 0** to **default 1** (or 2 or 3, depending on how many lines show up during boot)

I personally prefer to use the "saved" function instead, that way the menu will remember the last OS loaded and will set that as the default, until you chose another OS. To do this, instead of a number, set it to **default saved**, then scroll to the end of the file and look for a block like this:
> title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=5610c634-bc0e-4ac8-bb50-6fc28ae9e0c3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet
**savedefault**

and add the **savedefault** line to it. Your windows block should already have this line...

---

### Post by jigsaws on 2008-09-02
yes, default 1 will be ok

---

### Post by ^^rac on 2008-09-02
> **jigsaws said:**
> yes, default 1 will be ok

Thanks guys!

I will try that!

---

### Post by ^^rac on 2008-09-02
Ooooooh yes!

Btw guys, is this safe?
I dont want to mess up my MBR etc.....

---

### Post by jigsaws on 2008-09-02
Don't worry. It's safe. It is only configuration file at boot partition (not MBR). In case of any mistake you can boot system from grub command line (or any Live CD) and correct mistake.

---

