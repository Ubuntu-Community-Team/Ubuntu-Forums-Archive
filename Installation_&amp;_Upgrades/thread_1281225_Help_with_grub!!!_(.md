---
title: "Help with grub!!! :("
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by Gogeden on 2009-10-03
So I attempted to install openSUSE on another partition that I made on my HDD (I still have Jaunty). After it's install I rebooted and I was expecting Grub to come up and ask me which OS I wanted to boot. Of course, that didn't happen. Instead, Suse's bootloader popped up and ran SUSE. So I rebooted and spammed the hell out of the ESC key and the only bootloader that came up with SUSE's. So I rebooted again, threw in Jaunty's live CD and when it loaded I opened gparted and changed the boot flag over to the Ubuntu partition in hopes that it would finally boot. Rebooted. Didn't happen. Instead it said there was no bootable device and no OS. So I threw my Live CD back in and checked to see if my crap was still there on that partition and luckily it is. Now, I'm trying to reinstall Grub and I deleted the Suse partition. I tried reinstalling it by going to "sudo grub" in the terminal and proceeded to attempt to reinstall it instead I got Error 11 and I couldn't get it to work. So then I did this:



ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ grub-install
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.
ubuntu@ubuntu:~$ grub-install hd(0,0)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ grub-install hd0,0
mkdir: cannot create directory `/boot/grub': Permission denied
ubuntu@ubuntu:~$ sudo grub-install hd0,0
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install hd0,0
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install hd(0,0)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ chroot hd(0,0)
bash: syntax error near unexpected token `('



How do I fix my problem so I can use Ubuntu again WITHOUT having to format it and reinstalling Ubuntu? PLEASE HELP!!!!! :confused:

---

### Post by ackley on 2009-10-03
If you're positive you're booting from (hd0,0), all you should have to do is this.

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

If you get an error after running "setup (hd0)", post back here.

---

### Post by Gogeden on 2009-10-03
Before I was getting an error and I did EXACTLY what you just said and the install supposedly completed perfectly. I will now reboot and repost the result! Stay tuned! XP

---

### Post by Gogeden on 2009-10-03
And the result is that it worked! Thank you much man! ^_^

---

### Post by Gogeden on 2009-10-03
Now, for a better understanding on HOW to dual boot, how would I dual boot OpenSUSE and Jaunty? ^_^

---

### Post by ackley on 2009-10-03
I apologize for taking 4 hours to get back to you. I was playing with my new server. :D

Here's what I normally do when I want to dual boot another Linux OS.

Boot into Ubuntu, mount the other Linux partition, navigate to the menu.lst file (usually located at /boot/grub/menu.lst), copy the entry for whatever OS you're wanting to boot, then copy it to Ubuntu's menu.lst. 

ALWAYS ALWAYS ALWAYS make a backup of your menu.lst file first. You can do that easily by typing ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```I felt the need to reiterate always a few times because I know I've screwed things up by not making backups a few times.

Now, Ubuntu's menu.lst usually doesn't have where on the hard drive the OS should be booting from, so you may have to add that in yourself. 

Example:

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        b0a4ac81-620b-4fe5-b04b-1e6d197d8e8d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b0a4ac81-620b-4fe5-b04b-1e6d197d8e8d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```That's my entry for Ubuntu. Notice how it doesn't have any place specifying where to find the boot files.

Check wherever your /boot partition (if you have one) is for Opensuse. Most likely, it's just in your root (/) partition. Which works. Finding out what partition this is is very simple. Run ```
sudo fdisk -l
```That will give you a list of your partitions. Look for your Opensuse partition. For example, if it's sda3, grub will read this as (hd0,2).

If you're still with me here, this is what you'll want to add to your menu.lst file.

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,2)
uuid        b0a4ac81-620b-4fe5-b04b-1e6d197d8e8d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b0a4ac81-620b-4fe5-b04b-1e6d197d8e8d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
``` Notice the line right under the title line. It's a new one entitled "root". Also remember not to copy mine as it's for Ubuntu. Just add the root line to your Opensuse entry.

Remember, grub always lists the partitions one number down. 1=0, 2=1, 3=2 etc.

Hopefully I explained that well enough. It's 4:30 here & I'm very sleepy.

Cheers!

---

