---
title: "Multi-Boot question"
date: 2008-08-22
forum: General Help
---

### Post by Gondee on 2008-08-22
Hi, i recently installed Fedora 9 and OpenSUS 11 on my hard drive, and just now installed Ubuntu 8.04. I want to edit the GRUB so that i can boot from all of them, but i cant find the kernal name since i cant boot to the other OS's

Any solution would be awesome. Thanks guys, these forums are awesome.

---

### Post by Thingymebob on 2008-08-22
try
```

sudo update-grub

```
should locate all kernels and add them for you, if not then look in /boot in each distro, the kernel name will be someting like vmlinuz-2.6........

---

### Post by Patb on 2008-08-22
Gondee, normally Ubuntu would have given you the option to set up Grub to multi boot any of the OSs it finds.  This happens towards the end of the install process.  

You could try reinstalling Grub using [Catlett's How to restore Grub from a Live Ubuntu CD]("http://ubuntuforums.org/showthread.php?t=224351"). 

If you want to manually edit Grub's menu.lst you can find the kernel names under the /boot directory within each of the partitions where an OS is installed.  For more information on Grub see Herman's Grub page at 
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Cheers, Pat.

---

### Post by Gondee on 2008-08-22
I tried the sudo-update grub. And it didnt work,

The problem is i cant boot to the OS'S to get the kernal name. and the Live CD does not show it. It also wont open in Ubuntu

Is there a way to force my way in to Fedora or OpenSUS

---

### Post by colobix on 2008-08-22
it's sudo update grub.
None dash

---

### Post by Gondee on 2008-08-22
> **colobix said:**
> it's sudo update grub.
None dash

Thats not a command. lol


I just need to be able to get in to the other ones.

---

### Post by malspa on 2008-08-22
It's **sudo update-grub**, isn't it?  See **man update-grub**.

If you're going in manually with the live CD you have to make sure the other distros' partitions are mounted.  And with the Ubuntu CD if I remember correctly you also have to set mount points for them first.  But then you should be able to find the kernel names under their /boot directories, if those distros are like other distros I'm familiar with.

---

### Post by caljohnsmith on 2008-08-22
Gondee, you could mount your Fedora and OpenSUSE partitions from the Live CD or your Ubuntu on your HDD. Just do:
```
sudo fdisk -lu
```
Find your Fedora/OpenSUSE partitions; they should be type "linux" under the heading "system". Say if they are sdaX and sdaY, then mount them:
```
sudo mkdir /media/sdaX /media/sdaY
sudo mount /dev/sdaX /media/sdaX
sudo mount /dev/sdaY /media/sdaY
```
Once they are mounted, you can go looking in their /boot directories for the files you are looking for.

Do those distros each have their own menu.lst or grub.conf files? In other words, did you install Grub with them? Because if they do have menu.lst or grub.conf, you could boot them with:
```
title    Fedora
root 		(hd0,X)
configfile	/boot/grub/menu.lst
```
Replace (hd0,X) with whatever is your Fedora partition, and also give the correct path to its menu.lst or grub.conf. That way you don't have to use the "kernel", "initrd" method. I think you can get the idea, but if you need more details, let me know. :)

---

### Post by colobix on 2008-08-22
I mean, the command is sudo update grub.
but you wrote sudo-update grub.

---

### Post by malspa on 2008-08-22
> **colobix said:**
> I mean, the command is sudo update grub.
but you wrote sudo-update grub.

Looks like you're writing it wrong, too.  It's **sudo update-grub**.

---

### Post by Gondee on 2008-08-22
Thanks guys, can some one post there Ubuntu GRUB file. 

I ened up trying to re-install OpenSUS just trying to get to the dam GRUB file. and now that i got it i dont have the the thing so i can put ubuntu on the grub list. oo man. I wish i would have read your post caljohnsmith before i plunged in to this. O_0

But yeah, your grub file for the ubuntu part would be awesome =)

---

### Post by mb_webguy on 2008-08-22
Having a copy of someone else's GRUB menu.lst won't help you, since none of the entries will match your system.

---

### Post by Gondee on 2008-08-23
> **caljohnsmith said:**
>  but if you need more details, let me know. :)


So i tryed what you said and it didnt seem to work. I dont know why. 

I did get them to mount, but i cant open the files, it says i dont own the media, and dont have permisons. but i cant change them. What should i do from here?

---

### Post by malspa on 2008-08-23
Open them as root.

---

### Post by Gondee on 2008-08-23
I thought i was always a root in live CD. how can i log in as one in root

---

### Post by malspa on 2008-08-23
Now that I think of it, usually when I am using a live CD for anything other than doing an installation, I use a Mepis CD, and you have the option of logging in as a user or as root.  Seems to be a bit easier to do things with the Mepis live CD than with the Ubuntu live CD.  The Ubuntu live CD is different and I can't remember how it goes once it's booted.  I'll try it and get back to you if nobody replies before I do it.

---

### Post by malspa on 2008-08-23
Oh, yeah, sorry, how silly of me, of course you are not running that live CD as root, that is why you have to use sudo in your commands.

Maybe this example will help.  My Hardy root partition is on sdb9 so if I want to open Hardy's /boot/grub/menu.lst with the live CD (once I have it mounted and everything) I think I have to use the following from the terminal:

sudo gedit /media/sdb9/boot/grub/menu.lst

That should open the menu.lst file with the text editor gedit, and with root access.

---

### Post by caljohnsmith on 2008-08-23
Gondee, were you able to mount your Fedora and OpenSUSE partitions OK? If you can, then just go look in those partitions for a /boot/grub directory or a /grub directory, and then see if they have a menu.lst or a grub.conf file in those directories. Those are what you would put in your Ubuntu's menu.lst to boot them (using the notation I gave earlier).

If you're still having problems mounting Fedora and OpenSUSE, please post the output of:
```
sudo fdisk -lu
```
Also, post the output of the following:
```
sudo grub
grub> find /boot/grub/menu.lst
grub> find /grub/menu.lst
grub> find /boot/grub/grub.conf
grub> find /grub/grub.conf
```

---

### Post by Gondee on 2008-08-23
ops, double post

---

### Post by Gondee on 2008-08-23
I got all the drives mounted. But i could not open them, Permissions denied.

It was late last night and i was kinda frushtraed so i re-installed all 3 and got the Grub information on a flash drive. So its all working now, but i have to use the grub instlaled on the last OS, in this case it was fedora. 

What would happen if i were to install say, Elive Gem but not install the boot loader. Does this mean theres no grub file, and therefor no way to find the info needed.

---

### Post by sandysandy on 2008-08-23
just install it. generally u can install bootloader to partition (and chain load from other bootloader, but i have not tried that) also if u dont want it on MBR and mess up existing MBR.

see this

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

even if u install to MBR, u can always restore fedora's GRUB using super grub disk.

regards

---

### Post by caljohnsmith on 2008-08-23
One of the easiest ways to manage multiple installed Linux distros is to first decide which distro you want to control the MBR; then whenever you install another distro, let it go ahead and install its boot loader (grub/LILO), but *install the boot loader to the partition of the distro you are installing*, and not the MBR. In other words, if the distro is in partition sda5 for example, in Grub's World that is (hd0,4); so when you install the distro's bootloader, tell it to install to (hd0,4) instead of (hd0) which is the MBR. Then in your menu.lst or grub.conf of the distro that controls the MBR, just put an entry for the other distro like:
```
title   Linux Distro #2
root    (hdX,Y)
chainloader   +1
```
Where (hdX,Y) is the distro's partition. That's all there is to it.

EDIT: SandySandy all ready pointed this out, beat me by 30 seconds. :)

---

### Post by Gondee on 2008-08-23
lol, i wish i would have known that before last night. Ill be trying that though


Thanks alot for the help guys. =)

---

