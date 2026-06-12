---
title: "Thought I was being smart"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by mgallag on 2007-10-08
I purchased a Seagate Freeagent pro 320GB external hard drive for the purposes of installing Ubuntu and being able to take it where I wanted to. I used our Dell laptop to achieve this. I found the External drive with the Live CD and used a full disk install. Worked great, until..... I unplugged the hard drive and started the comp. Came up with a error code 21, something about not being able to find the kernal. I had to plug the drive back in to start up XP, then unplugged it and have it running without issue. Now, I took the External drive and hooked it up to another comp, ran Boot throught the bios to load on it, and NOTHING. Uh, I have obviouslly done something wrong, but am not sure what? HELP.




:confused:

---

### Post by darkness_s on 2007-10-08
I think you installed the grub loader on the external drive. You could try to reinstall it while you are in Ubuntu, but make sure you install it in your internal hard drive.

---

### Post by mgallag on 2007-10-08
Alright, how do I do that? If I go back to live CD and attempt to load the grub, do I have to partition the Laptop drive which is not what I want to do. Also I still have the issue with the External Drive not booting on a different computer.

---

### Post by synss on 2007-10-09
I would say you installed grub in the MBR of your internal hard disk drive (HDD) and but its files on the external HDD, to solve it, boot linux (the live CD is fine) and become root. Plug your HDD. Mount it if it does not automount. 

run the command 
```
mount
```and look where it is mounted, you should have a line like
*/dev/sdb1 on /media/HARDDISK*do
```
ls /media/HARDDISK
```to make sure, it should show bin, sbin and boot...
```
ls /media/HARDDISK/boot
```anything there? the kernel, I hope.

if all that went OK, do```
grub-install --no-floppy --root-directory=/media/HARDDISK/boot /dev/sdb
```
where /media/HARDDISK/boot is on your external HDD, where the kernel is and /dev/sdb is your external HDD. If that does not work, try
```
grub-install --no-floppy --root-directory=/media/HARDDISK /dev/sdb
```I never remember whether you need to specify the /boot directory or not... (but if grub did not complain, then you are fine.)

of course, if you have a floppy drive, do not use the --no-floppy option to grub install.

When you boot on your HDD, you might have to change the menu.lst file to boot on your hard drive, if grub does not find the kernel. If so and you cannot fix it yourself (it should be something simple like changing 
root (hd1,0) to root (hd0,0)
in /boot/grub/menu.lst on both the kernel line and in the comments) just open a new thread.

---

