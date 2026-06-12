---
title: "grub bootloader problem"
date: 2008-10-23
forum: General Help
---

### Post by davidmiller252 on 2008-10-23
hi, I had both ubuntu and vista running on my laptop, and I decided it would be neat to have my external hd have ubuntu on it as well so I could use it with other computers. So I installed it via my laptop. Now everytime It boots into grub, if the ext hd is not connected it returns error 21. I also checked both filesystems and in my internal installation of ubuntu it has the old grub (the one I want for my laptop) and in the external installation it has the new grub. How do I change the settings so that I can disconnect my external hd and use my laptop without it?
Thanks!

---

### Post by plucky on 2008-10-24
> **davidmiller252 said:**
> hi, I had both ubuntu and vista running on my laptop, and I decided it would be neat to have my external hd have ubuntu on it as well so I could use it with other computers. So I installed it via my laptop. Now everytime It boots into grub, if the ext hd is not connected it returns error 21. I also checked both filesystems and in my internal installation of ubuntu it has the old grub (the one I want for my laptop) and in the external installation it has the new grub. How do I change the settings so that I can disconnect my external hd and use my laptop without it?
Thanks!

You have to re-write the MBR to point to your original installation.

1) Boot the original installation
2) open a terminal and input these commands
```
sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hd0)
quit
```
[LIST]
[*]The sudo grub requires your password
[*]The find command should show you which partitions have stage1 files on them and should be bootable.
[*]The "root" command tells grub on the MBR which partition to look at to find stage1.
[*]The "setup" command writes to the HD0 MBR.
[/LIST]
Reboot to see if it worked.If it doesn't,you will need a Live Cd to fix or [The Supergrub Disk](http://www.supergrubdisk.org/)

See this [link](http://ubuntuforums.org/showthread.php?t=724817&highlight=grub+mbr) for more information about Grub and the MBR.

After you have done this,you won't be able to boot the external partition until you add the boot commands to the old menu.lst file.Just copy the relevant part of the command from the menu.lst on the external drive.

e.g ```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=03aa7483-5b8f-4c1e-bd09-5db055ead5eb ro splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

```

Or add these lines to the old menu.lst to do a chainloader boot ```
title		Ubuntu chainloader Boot
configfile (hd1,0)/boot/grub/menu.lst
``` Alter the (hd1,0) to suit your configuration to point to the external disk partition.


Good Luck

---

### Post by caljohnsmith on 2008-10-24
What happened is by default Ubuntu installs Grub to the MBR of (hd0), which is your internal drive, even though you installed Ubuntu to your external drive; they do that because usually /dev/sda or (hd0) is the drive that boots on start up, so that's where the installer puts Grub.

If you follow plucky's advice about installing Grub to the MBR, you should actually get two responses from the "find" command in the grub command line; one will be Ubuntu on your internal drive (hd0), and one will Ubuntu on the external drive (hd1). In order to make sure you install Grub to the MBR properly of each drive so you don't get the error 21 again (have your external HDD independent of your internal drive so you can disconnect it), please do the following:
```
sudo grub
grub> find /boot/grub/menu.lst
```
That should return two responses (hd0,X) and (hd1,Y) where X and Y are numbers. Proceed with:
```
grub> root (hd0,X)
grub> setup (hd0)
grub> root (hd1,Y)
grub> setup (hd1)
grub> quit

```
Then you can link to your external drive's menu.lst to the internal drive menu.lst using the "configfile" notation that plucky gave. Or if you want to set your BIOS to boot the external drive when you want to use it, you'll have to slightly reconfigure the menu.lst on your external drive. Let me know what you want to do, and I can give further instructions if you want. :)

---

### Post by davidmiller252 on 2008-10-24
Thanks guys! that helped! now I have my internal installation back. How would I go about creating a portable installation on my external drive? So I can take my usb hdd to any computer and boot from it?

---

### Post by caljohnsmith on 2008-10-24
If you want to boot your USB drive from any computer, I think you would want to install the Ubuntu Live CD to your USB drive so that it is hardware independent. You can get info about doing that from [here]("https://help.ubuntu.com/community/Installation/FromUSBStick"). Let me know how it goes. :)

---

### Post by davidmiller252 on 2008-10-24
I tried it and it worked, but it's kind of restricting, because the homefolder is only 1gig and I made a new username and password with admin rights but I'm still restricted to many things, for example i can't change the appearance to a new set of icons or copy files to and from external drives.

---

