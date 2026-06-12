---
title: "Grub on Ubuntu Where is? and How is?"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by sanumala on 2009-10-09
Hi

I have dell xps 430 two 750GB HDD's.  By default it came with vista and raid enabled. I disabled raid and restored my vista using restore disks on 1st hdd without RAID.

After that i installed ubutnu 9.04 and using since 6 months i guess.

[SIZE=4]**I don't remember exactly what i did with grub options while installing. but i am sure i haven't changed any default options.**[/SIZE]

Now due to space constraints I am planning to completely unplug 1st HDD and replace with 1.5TB.

Right now i have a partitions like

1ST HDD:

250GB for C drive
500GB for D drive

2nd HDD:
24GB Swap
725GB /(root partition)

So. my Question is while installing Ubuntu and I have seleted use 2ND HDD did it wrote anything in !st HDD MBR or not?

If it wrote some thing into 1St HDD MB how can i safely remove that Hard Drive with out loosing boot loader and Ubuntu on second drive...

[SIZE=5]I don't care if i loose windows and all files inside first HDD but i don't want to loose boot loader and 2ND HDD...[/SIZE]

Please help..

---

### Post by drs305 on 2009-10-09
Go to this thread and download and run the boot_info_script. It will tell you everything you need to know about your current boot situation:

[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")

Then you can tell us what you need, if anything.

---

### Post by sanumala on 2009-10-09
While installing ubuntu I have selected to use entire 2HDD. Did grub wrote anything in frist HDD since i haven't selected.

And one more question; Since i have two separate hard disks how many MBR's they will have

1 or each or 1 for both?

Thanks

---

### Post by presence1960 on 2009-10-09
> **sanumala said:**
> While installing ubuntu I have selected to use entire 2HDD. Did grub wrote anything in frist HDD since i haven't selected.

And one more question; Since i have two separate hard disks how many MBR's they will have

1 or each or 1 for both?

Thanks
each disk has an MBR of it's own

we won't know if GRUB will be affected until you run the boot info script as drs305 asked. That script is a godsend as it gives all info about your setup & boot process.

until we get that info the best we can do is guess.

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by sanumala on 2009-10-09
Hi  Guys

I just ran boot manager script and got following results.   Boot loader is installed on /dev/sda which is my first Hard drive.

Can anybody guide me to move that boot loader stuff from first hdd to second hdd without loosing any data...

Please see attached results

---

### Post by sanumala on 2009-10-09
bump! Guys Any help is really appreciated

---

### Post by presence1960 on 2009-10-09
> **sanumala said:**
> bump! Guys Any help is really appreciated

Ok do this to put GRUB on sdb MBR:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

When you reboot go into BIOS and put sdb as first in the hard disk boot order. This will bring up GRUB when you boot. Save changes to CMOS and exit BIOS. Boot into Ubuntu and open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

Scroll down to your windows entry and change it to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1
```

You can probably delete the references to osx as it looks like that is no longer installed on sdc.

---

