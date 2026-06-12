---
title: "Grub is gone, I blame Vista.."
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by nlakes on 2009-01-22
Hi everyone, 

I have just upgraded to vista from xp, and grub has disappeared. I assume Vista took it upon it self to overwrite it. 

I am not the most tech-savvy person, so if anyone is willing and able, could they please walk me though getting grub back so I can use my beloved ubuntu again.

Many thanks.

---

### Post by nlakes on 2009-01-22
Is there anything I can do other than reinstall ubuntu?

---

### Post by ajgreeny on 2009-01-22
Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

---

