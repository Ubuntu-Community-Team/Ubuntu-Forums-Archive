---
title: "how to avoid grub&gt; command prompt at restart vista installed"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by avdaga on 2008-12-23
I had vista and ubuntu installed on my vaio CR-36 laptop but due to a virus in vista I had to format my C drive by restoring C drive. Now after restoring when my computer restarts grub command prompt opens 

grub>

and i am not able to anything. Please help

---

### Post by ajgreeny on 2008-12-23
Either at the grub prompt you get, or using the ubuntu live CD do the following:-

Boot into the ubuntu live CD and open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line like you are already seeing.
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

### Post by caljohnsmith on 2008-12-23
Do you have Ubuntu installed on the same drive as Vista now, or is the drive only Vista? If you have Ubuntu installed, ajgreeny's advice should work, but if the drive is now only Vista, you will need to restore a Windows MBR to the drive in order to boot Vista. If your Windows Install CD allows you to go to the command line, just run:
```
bootrec /fixmbr
```
Or if you can't do that, instead you could boot your Ubuntu Live CD (the install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo lilo -M  /dev/sda mbr
```
And that will install a Windows equivalent MBR to the sda drive, which should be your internal Vista drive. Let us know how it goes or if you run into problems.

---

