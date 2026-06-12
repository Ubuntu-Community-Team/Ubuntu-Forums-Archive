---
title: "Ubuntu and Windows 7"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by regunus on 2009-10-17
Hey all. I'm having an issue and I would like some help.

I'm doing my work with Ubuntu but I still Windows for games (can't play all of them via Wine...). Recently I got meself a new computer and I installed Windows 7 on it. After that I tried to setup Ubuntu. And here is where the problem starts. The setup of my pc is this :

M/B : Asus Maximus III Formula
CPU : Intel Core i5-750
RAM : 8GB DDR3
HDD : 2 x Corsair SSD 64GB Extreme Edition.


note that my case has a hotswap function on (Zalman GS1000).

First time I tried to install Ubuntu (9.04) I couldn't. After a few tries, I found out that there was a problem when I had SATA Cables on the hotswap positions. I disconnected all of them so the installation went ok. 1 SSD for Win7, 1 SSD for Ubuntu.

But...

Rebooted them computer and never even saw the grub menu. Went directly to windows 7 boot. Something messed up with grub setup?

That's fine. Reinstalling Ubuntu and select /dev/sda to put grub instead of (hd0). Nothing. Reinstalled again and again and again using every possible location for grub and the right hdd to bood from bios of course, but nothing.

I even tried to use supergrub but... :(

Any ideas on this one?

Thanks in advance!

---

### Post by darkodelta on 2009-10-17
well i have same problem but i have xp install already and linux ubuntu 9.04 then i install Windows 7...i remove Windows 7 but it don't show any boot loader on star-up...sorry but no answer yet...but i think i have an idea

---

### Post by hal10000 on 2009-10-17
> That's fine. Reinstalling Ubuntu and select /dev/sda to put grub instead of (hd0).

/dev/sda is the same as (hd0), so nothing was changed, but take a look into your BIOS ans verify the boot order, maybe that your boot order is just set to boot from /dev/sdb first (resp. (hd1))

---

### Post by regunus on 2009-10-17
> **hal10000 said:**
> /dev/sda is the same as (hd0), so nothing was changed, but take a look into your BIOS ans verify the boot order, maybe that your boot order is just set to boot from /dev/sdb first (resp. (hd1))

> **regunus said:**
> 
That's fine. Reinstalling Ubuntu and select /dev/sda to put grub instead of (hd0). Nothing. Reinstalled again and again and again using every possible location for grub and the right hdd to bood from bios of course, but nothing.


Alleady tried that. It's on my first post, but thank for the reply. Any other ideas?

---

### Post by hal10000 on 2009-10-17
Then the only idea i have is that your grub was not installed at all.

You should boot your live-cd and
mount your ubuntu system partition:
```
sudo mount -text3 /dev/sdb1 /mnt
```
In the example i assume your ubuntu system resides in /dev/sdb1, you have to fit it to your needs.

Then check the /mnt/boot/grub/menu.lst file on your ubuntu system partition. You may post the output here to see if it has an entry to boot your windows system as well as ubuntu

You may then manually install grub with the following steps:

1.) create a chroot environment:
```
sudo chroot /mnt
```
(i assume your ubuntu system is mounted under the /mnt directory)

2.)run grub:
```
sudo grub
```

3.)on the grub prompt do
```
find /boot/grub/stage1
```
it will hopefully give you an answer like **(hd1,0)** if your ubuntu system is on /dev/sdb1 as stated in my example

4.) take the answer you get and do
```
root (hd1,0)
```
you have to fit it to the answer you got from the last (find) command

5.)Install grub to the mbr of the disk where you installed your ubuntu system:
```
setup (hd1)
```
And again, fit this to your needs

6.) exit grub:
```
quit
```

7.) exit the chroot environment:
```
exit
```

8.) In your BIOS settings set the boot order to boot first from the drive where you installed ubuntu.

9.) reboot

10.) you should now see the grub boot manager.

11.) You should now have fun with ubuntu.

---

### Post by regunus on 2009-10-17
ok. tried it and here's the result :

in  /mnt/boot/grub/ there is no file at all :confused:

went to step 1. got chroot and then passed to step 2, run grub. the result :

> 
The program 'grub' is currently not installed.  You can install it by typing:
apt-get install grub
grub: command not found


lol?

ok. I installed grub and went to step 3. result : 

> Error 15: File not found

and then stopped trying...

---

### Post by hal10000 on 2009-10-17
> ok. I installed grub and went to step 3. result How did you install the grub package?
Was it by using your Software manager from your live cd? This would'nt work here.

You have to install it in your chroot environmment: boot your live-cd and then

1.)```
sudo mount -text3 /dev/sdb1 /mnt
```
2.) ```
chroot /mnt
```
3.)sudo apt-get install grub

and then perform all actions from posting #5, beginning wth step 3 again

---

### Post by regunus on 2009-10-17
> **hal10000 said:**
> How did you install the grub package?
Was it by using your Software manager from your live cd? This would'nt work here.

You have to install it in your chroot environmment: boot your live-cd and then

1.)```
sudo mount -text3 /dev/sdb1 /mnt
```2.) ```
chroot /mnt
```3.)sudo apt-get install grub

and then perform all actions from posting #5, beginning wth step 3 again

yeap. grub was installed in chroot.

---

### Post by hal10000 on 2009-10-17
So you don't have a file called /etc/grub/stage1 ???? on your ubuntu system?
Then smething went terribly wrong.

But since you have installed grub in your chroot you should at least have a file /usr/lib/grub/x86_64-pc/stage1 (these paths are all apply only to your chroot environment)

You may try to copy it to /boot/grub:
```
 sudo chroot /mnt
sudo cp /usr/lib/grub/x86_64-pc/stage1 /boot/grub

```
and then again from step 3 in post #5,

If this does'nt work, then post the output of
```
 ls -l /boot /boot/grub
```
to see if there are other files missing.

---

### Post by Mark Phelps on 2009-10-17
If you installed Windows 7 to an empty drive, it created two partitions -- a 100MB "boot" partition, and a regular NTFS partition.  From lots of other posts, it looks like GRUB can't handle this situation -- which is new to Windows 7.

---

