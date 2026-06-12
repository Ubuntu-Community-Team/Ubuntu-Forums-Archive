---
title: "USB Installation"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by vegetarianshrimp on 2009-06-26
I created a LiveUSB of Linux Mint on a 1 GB USB drive. I then used the LiveUSB to install Linux Mint (non Live) on a second 8 GB USB drive. I created 3 partitions. A 3 GB ext4 / labeled as boot from gparted , a 4 GB ext4 /home, and a swap. When I try to boot from this 8 GB drive, it just says loading Grub, and nothing happens. How can I get the installation to work, and still have a seperate /home partition?

---

### Post by Herman on 2009-06-26
I don't think the fact that you have a separate /home has anything to do with your booting problem. In my personal opinion though, it's much better to install all in one single partition. That will make better use of your disc space. Even the swap area can be in a swap file instead of a partition.

One of your problems might be that Linux Mint, (although based on Ubuntu), chooses not to use UUID numbers in GRUB.
The use of UUID numbers for booting is one of the biggest improvements we've had for years, and is especially handy if you happen to install in any kind of removable media like a USB drive of any kind, or even hard discs if you like to remove or add hard disks from time to time.
The simple solution would be to forget about Linux Mint and re-install with Ubuntu.
The slightly more challenging solution would be to edit your /boot/grub/menu/lst in Mint with UUID numbers.

An example of a menu.lst with UUID numbers is here, [Customizing Your GRUB Menu]("http://members.iinet.net.au/%7Eherman546/p15.html#menu.lst").
This link explains things in more detail, [uuid]("http://members.iinet.net.au/%7Eherman546/p15.html#root").

Regards, Herman :)

---

### Post by vegetarianshrimp on 2009-06-26
Linux Mint is based on Ubuntu, wouldn't it have this?

---

### Post by Herman on 2009-06-26
No, they have different ideas of their own, I suppose that's why Mint isn't Ubuntu.

I have a couple of installations of Mint myself, just to try it out and see the differences. It's quite a nice distro. They use a graphical GRUB, which a lot of people like. They have a different way of organizing their menus, more Windows-like a bit perhaps.

It seems that somebody with some authority in their forums didn't like the idea of using UUID numbers in GRUB at all, and there's an anti UUID blog in their web forum in a closed thread so nobody can reply to it. 
Later, on a more obscure page there's a bit added mentioning that you can use UUID numbers in Mint's GRUB if you really have to.

---

### Post by Herman on 2009-06-26
Just boot with your Live CD and plug in your USB stick and use the blkid command to find out your file system UUID numbers.
Then edit your /boot/grub/menu.lst in Mint with the uuid command and the right UUID numbers.
It has the same version of GRUB, it can handle the uuid command, it's just that Mint people prefer to keep the old style boot entry commands. Anyone can update it.

---

### Post by vegetarianshrimp on 2009-06-26
> **Herman said:**
> Just boot with your Live CD and plug in your USB stick and use the blkid command to find out your file system UUID numbers.
Then edit your /boot/grub/menu.lst in Mint with the uuid command and the right UUID numbers.
It has the same version of GRUB, it can handle the uuid command, it's just that Mint people prefer to keep the old style boot entry commands. Anyone can update it.
I installed uuid, and cd to the 8 GB's boot folder. What is the command I should use? uuid -o menu.lst? Or am I totally off? (I have no idea what I'm talking about :))

---

### Post by Herman on 2009-06-26
[LIST=1]
[*]boot your Linux Live CD
[*]Open a terminal
[*]run the command: 'sudo blkid' for a list of the file system UUID numbers
[*]copy the UUID number of your Linux Mint boot partition
[*]open your USB drive, (if it isn't already mounted, mount it first)
[*]open your /boot/grub/menu.lst file, (with a sudo command in your terminal - like 'gksudo gedit /media/disk/boot/grub/menu.lst', or similar)
[*]find the command 'root' in your boot entry and replace it with 'uuid' command
[*]after the root command, paste the UUID number you copied in step 4, for your Mint installations boot file system (the one that contains your linux kernels)
[*]in the line that starts with the 'kernel' command, find the word 'root=", and after it type: UUID=
[*]paste the UUID number for your root partition (the one that contains /sbin/init), right after the 'UUID='. I think it will be the same number, in most cases it is, unless you have a separate /boot partition.
[*]click 'save' and close the file
[*]reboot
[/LIST]
If you're still not sure what you're doing, re-read the links I gave you, and any sub-links those contain. They should explain everything, or at least I think they do.

Regards, Herman :)

---

### Post by vegetarianshrimp on 2009-06-26
OK, thanks a lot! I did all that, and am about to reboot.

---

### Post by vegetarianshrimp on 2009-06-26
Hmm, it didn't work. What did I do wrong?
> 
title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic
uuid        08eaa50c-ffef-439c-a90a-fe5830966bec
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=08eaa50c-ffef-439c-a90a-fe5830966bec ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode)
uuid        08eaa50c-ffef-439c-a90a-fe5830966bec
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=08eaa50c-ffef-439c-a90a-fe5830966bec ro single
initrd        /boot/initrd.img-2.6.28-11-generic

---

### Post by Herman on 2009-06-26
I don't know, it looks okay to me.
What error message are you getting?

---

### Post by vegetarianshrimp on 2009-06-26
> **Herman said:**
> I don't know, it looks okay to me.
What error message are you getting?
Oh sorry, never mind, It works. I thought it wasn't loading, guess I'm just impatient. Well, thank you so much for all your help!

---

### Post by Herman on 2009-06-26
:D Alright! - I'm glad you got it working! Happy USB-ing!

Regards, Herman :D

---

