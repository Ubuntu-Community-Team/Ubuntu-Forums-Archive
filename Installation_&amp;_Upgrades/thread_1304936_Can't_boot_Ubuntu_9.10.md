---
title: "Can't boot Ubuntu 9.10"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Elkaz on 2009-10-29
Hello all. I am from Russia, so please sorry for some mistakes in the text.
I upgraded my 9.04 to 9.10. Also I wanted grub2, so I installed it like in the article ([http://debianworld.ru/articles/ustanovka-grub-2-na-debian-ubuntu/](http://debianworld.ru/articles/ustanovka-grub-2-na-debian-ubuntu/) - do not read comments, just read the code of commands). After it I rebooted and have Error 15 - file not found. I have livecd of 9.04 so what I can do now? I tried to return first grub, but couldn't. I don't want clear install, because it will be very hard - /home is not mounted as a device. So can you help me solve the problem? What shall I do?

```

ubuntu@ubuntu:/media/disk$ sudo grub
Probing devices to guess BIOS drives. This may take a long time. (~1 min)

find /boot -- Error 15: File not found
find /boot/grub -- Error 15: File not found
find /boot/grub/stage1 -- Error 15: File not found

```

```

ubuntu@ubuntu:/media/disk$ ls /boot/
abi-2.6.28-11-generic     System.map-2.6.28-11-generic
config-2.6.28-11-generic  vmcoreinfo-2.6.28-11-generic
memtest86+.bin

```

/dev/sda1 - Windows
/dev/sda2 (extended)
  /dev/sda5 - My media
  /dev/sda6 - My games
  /dev/sda7 - SWAP
/dev/sda3 - Ubuntu

Please, any help?

---

### Post by w4r3zh4ck™ on 2009-10-29
try reformatting ur hard drive to ext3 or 4 and try making a clear install the 9.10

---

### Post by Elkaz on 2009-10-29
I don't want to make a clear install, I said it above

---

### Post by w4r3zh4ck™ on 2009-10-30
> **Elkaz said:**
> I don't want to make a clear install, I said it above
well clear install is ur solution but as said above its ur problem.
Good Luck.

---

### Post by longlegs on 2009-11-24
Hi Elkaz

find /boot -- Error 15: File not found
find /boot/grub -- Error 15: File not found
find /boot/grub/stage1 -- Error 15: File not found

This probably wont solve your problem but I have found that using 
sudo find /boot...  will give results sometimes when 
find /boot.... will not.

Be aware that grub 2 of ubuntu 9.10 counts hd0,1 as first drive, first partition where grub 1 of 9.04 and earlier counts hd0,0 as first drive, first partition.

Be aware that grub 2 appears NOT to have a shell . That is, there is no grub> prompt. ( at least I can't get to it!)

I have been trying to boot to 9.10 for 10-12 days now (2-3 hours per day) with no luck. I have found that many otherwise fine sounding instructions are written by peopls who did not try their instructions.

For what it's worth, since you seem to have only one hard drive, you may be able to boot from the windows bootloader by booting ubuntu with a Super Grub Disk (downloadable from many sites)then open a terminal and type

sudo dd if=/dev/sda3 of=/home/bootsda3.ubu bs=512 count=1

This wil generate a file in your home folder named bootsda3.ubu
Move it or copy it to your windows root directory. Reboot to windows and open the file named boot.ini (it may be hidden with readonly set so you would need to unhide it and change it to read/write) with notepad and add a line at the bottom like

C:\bootsda3.ubu="Ubuntu"

Also set the [timeout] to 30 seconds for now. Later you can set however you like.

Save it. (I have never reset the hidden readonly bits and have had no problems.) Reboot and a menu giving choice of windows or ubuntu will appear. Click on the ubuntu choice and it "may" boot to ubuntu.
Some times this works and some times it does not but won't normally work when there is more than one hard drive.

Good luck!
H.M.Jones

---

