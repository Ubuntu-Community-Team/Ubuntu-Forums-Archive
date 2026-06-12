---
title: "Whats wrong with Ubuntu ??"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by donhamilton on 2009-10-21
I have tried to install 9.04 on a eMachines computer.

The CD booted and I clicked the install icon.

After much grinding, Ubuntu seemed to install on my hard drive.

I exited and removed the CD.

Resetting the machine, I am told there is no boot record.

I repeated the entire process and same result.

Why did the install Cd not make the hard disk bootable ??

Am I suppose to use Ubuntu with the Install CD all the time ??


don

---

### Post by stlsaint on 2009-10-21
im assuming you are on desktop and if so ho many hdd do you have in that desktop and are you trying to do a dual boot with windows and linux or do you just want ubuntu installed as main os on system?

---

### Post by donhamilton on 2009-10-21
> **stlsaint said:**
> im assuming you are on desktop and if so ho many hdd do you have in that desktop and are you trying to do a dual boot with windows and linux or do you just want ubuntu installed as main os on system?

Yes, it is a desktop.

I have one 40GB disk that had been wiped.

This will be a dedicated Ubuntu machine.

don

---

### Post by Niko Johnson on 2009-10-21
How did you set up your partitions during the install?

---

### Post by stlsaint on 2009-10-21
> **donhamilton said:**
> Yes, it is a desktop.

I have one 40GB disk that had been wiped.

This will be a dedicated Ubuntu machine.

don


boot into the livecd and if you can get internet post the contents of your menu.lst file by doing the following in a terminal:

```
gksudo gedit /boot/grub/menu.lst
```

this will bring up a file showing your menu.lst...copy and paste the contents of that file here and we will be able to see if you have grub installed and where.

---

### Post by mikechant on 2009-10-21
Did you get all the normal pre-install stuff (set timezone, create initial user etc.)?
The very last screen of the pre-installation setup (screen 7) has an 'advanced' button bottom right which leads to the screen where you choose whether to install the boot loader. You should check that the 'install to mbr' option is ticked (should be the default).
The installation process should then run through and if I remember correctly the last thing it does is report that it's installing the boot loader - did you see that message?

Another thing to check is your BIOS settings - when getting the LiveCD to boot did you accidently set the boot order to boot from 'CD only' rather than 'CD then HD'?

---

### Post by donhamilton on 2009-10-21
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

---

### Post by stlsaint on 2009-10-21
is that the entire contents of your menu.lst...if so than you need to reinstall grub to your hdd as you dont have it on there!


 1. Boot your computer up with Ubuntu LiveCD
   2. Open a terminal window or switch to a tty.
   3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
   4. Type "grub"
   5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
   6. Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
   7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
   8. Quit grub by typing "quit".
   9. Reboot and remove the bootable CD.

---

### Post by donhamilton on 2009-10-21
I have re-installed Ubuntu again.

This time I installed it after booting the Live CD. The HDD now boots.

When I tried the "Install Icon" after booting, the HDD would not boot.

Go figure.

don

---

### Post by stlsaint on 2009-10-21
so can you boot into hdd from grub? if so please mark thread as solved...if not than post error output.

---

### Post by donhamilton on 2009-10-21
[QUOTE=stlsaint;8140419]is that the entire contents of your menu.lst...if so than you need to reinstall grub to your hdd as you dont have it on there!

This is the entire contents.

Who ever created the ISO for 9.04 needs to fix this.

This ISO is confusing and un-installable as distributed.

don

---

### Post by donhamilton on 2009-10-21
> **stlsaint said:**
> so can you boot into hdd from grub? if so please mark thread as solved...if not than post error output.

Yes, I can now boot.

However, the ISO needs to be fixed.

I will mark this as resolved.

don

---

### Post by stlsaint on 2009-10-21
> **donhamilton said:**
> [QUOTE=stlsaint;8140419]is that the entire contents of your menu.lst...if so than you need to reinstall grub to your hdd as you dont have it on there!

This is the entire contents.

Who ever created the ISO for 9.04 needs to fix this.

This ISO is confusing and un-installable as distributed.

don

you can redownload the iso from here: [ISO]("http://releases.ubuntu.com/jaunty/")

---

