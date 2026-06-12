---
title: "Multiple instances installation"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by bntlinux on 2009-06-14
Hello everyone,

I work in an 24/7 office and we have a computer at our disposal for our personal use.

Since every user is installing software for his use we often end up with a messed up system and so we decided to install an instance per user and a reference installation, this way, each user can boot up his own instance and do whatever her likes with it.

We also need a reference installation with the system and common are already installed so that if a user crashes his session, or when someone leaves and we need to overwrite his session with a fresh one, we can just duplicate the reference partition rather than reinstall from scratch.

We are 5 users so we need 6 instances, and.... not all will have to be ubuntu, let alone linux...

Ideally, when we boot up the computer, we should get something like this at the boot level:

user1
user2
user3
user4
user5
ref (do not boot on this instance)

The user will then scroll to his(her) instance and boot from it

Any ideas how this can be done?

Thanks in advance
B

---

### Post by wpshooter on 2009-06-14
Why don't you just install Ubuntu and then setup ever how many users/logins you need ?

Each users session, programs, etc. should be unique to that particular user. 

Is that what you are wanting to do ?

---

### Post by bntlinux on 2009-06-14
WPSHOOTER, thanks for the reply

There are 2 reasons why I can't do this:


1- Not all users will be using ubunto, some will have other distros and some even windows...

2- All installed software will be available on the system and this would make up a big mess and maybe even some conflicts with the software in terms of default usage (more than one mail client, web client, IM client...)

I really need to have a partition per session

Unless (just thought about that one) there is an ultra lightweight virtual machine software that can be started from the command line of a non XServer enabled linux, which leaves most of the system ressources to the virtual machine that is running.....?

---

### Post by wpshooter on 2009-06-14
Hmmmmmmmmmm, multiple users and multiple versions of various O/Ss on same machine - choice at boot.

Not aware of what this might be, but would be interested in seeing if there is such an animal !!!

---

### Post by bntlinux on 2009-06-14
I guess if I install Windows first then the rest it should be ok, but my problem is installing on a logical drive on an extended partition and the other is forcing the other partitions to stay hidden from the one that was booted...

---

### Post by wpshooter on 2009-06-14
bntlinux:

Minor spelling error in your sage saying.  Think you mean, THEN they laugh at you.

---

### Post by bntlinux on 2009-06-14
Right you are [wpshooter]("http://ubuntuforums.org/member.php?u=41796"), thanks for the info...

---

### Post by ramnarayan on 2009-06-14
> **bntlinux said:**
> WPSHOOTER, thanks for the reply


I really need to have a partition per session


Unless (just thought about that one) there is an ultra lightweight virtual machine software that can be started from the command line of a non XServer enabled linux, which leaves most of the system ressources to the virtual machine that is running.....?

Hi

Ok it seems like you have one machine and everyone using the machine needs their own distro.

I have been experimenting to see how many distro's i can fit in on one hard disk (or multiple)

Its quite easy. (and there is no need to make windows the first OS)

Take your normal machine (am assuming with windows installed) and install your most favorite and much used Ubuntu (or Linux). Make sure this has a separate /boot partition /root partition and a separate /home as well.

While this is on make sure you partition your hard disk into as many more distros / users that you want. If you have the possibility add another physical HD - this will give you more options. Each partition should be sufficient to maintain a root and a home (data) so it maybe big or small as per your requirements.

I think that a fully loaded distro requires around 7 gig (with really tonnes of software loaded on) so add some space for /home as well.

Alternatively you could create a large data section where all the folks can have their data (if you want it shared). This can be shared by all users.

After you have partitioned your hard disks then begin the installation of your other distro's
 
pop your install CD / DVD in and when it comes to the partitioning make sure you select manual partitioning. This is the first important step.

Make sure you know where your main distro is installed 

you can use df -h to know

or just have a look using the partition editor. Note it down on paper you will need to remember and not make a mistake.

Once you are in the manual partitioning section check out which partition you want to install the said distro on and select to your file system of choice (ext2, ext3 etc) and mark it as / (/root). Don't select any other partition. Doing this it will force the install to keep /boot and /home along with the /root.

Continue with your installation (note the device its on)

/dev/sdax etc


*very important* when it asks you where to install the bootloader - 
a) do not install it to MBR - Master Boot Loader
b) install it to first sector of root partition
c) if asked to choose from a drop down menu chose your /dev/sdax
d) if asked to choose and hd0 then its 
sda1 = hd0,0, 
sda2 = hd0,1 . 

If its a second HD  it is sdb
sdb1 = hd1,0 
sdb2 = hd1,1 

and so on

post installation reboot - you should get a normal screen with your first Linux OS and not the freshly installed one. But thats ok.

Boot into your Master OS

open a super user terminal
find the partition where you installed the second (or x number Linux OS)
navigate to /dev(or media)/sdax/boot/grub/menu.lst

pick up the entries from there and open your Master /boot/grub/menu.lst

Find the section where the entries start and place your second (or third or fourth Linux OS ) menu.lst entries in any sequence of your choice and save the file.

reboot and you should be able to see your freshly installed OS

Am putting down my current menu.lst which has 4 OS's working together. Only my HD space prevents me from installing more Linux OS's 


## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		dd3799a7-81db-49a7-8c03-e972859199f8
kernel		/vmlinuz-2.6.28-11-generic root=UUID=febd703e-8639-47f6-bafd-81602f266bfb ro quiet splash usbserial.vendor=0x0451 usbserial.product=0x3410
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		dd3799a7-81db-49a7-8c03-e972859199f8
kernel		/vmlinuz-2.6.28-11-generic root=UUID=febd703e-8639-47f6-bafd-81602f266bfb ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		dd3799a7-81db-49a7-8c03-e972859199f8
kernel		/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		OTHER LINUX OS's
root

title Pardus 2008.2 Canis aureus
root (hd0,10)
kernel (hd0,10)/boot/kernel-2.6.25.20-114 root=LABEL=PARDUS_ROOT vga=791 splash=silent quiet
initrd (hd0,10)/boot/initramfs-2.6.25.20-114

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=437c8e29-88f1-45f4-a8c6-93f9f22e1b53 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=437c8e29-88f1-45f4-a8c6-93f9f22e1b53 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,9)
kernel		/boot/memtest86+.bin
quiet


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title		OTHER NON LINUX OS's
root

title		Microsoft Wincedows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

***

To keep your menu.lst clean you could comment out all the recovery and memtest modes for all except your master OS.

Also you could replace the title for each DISTRo with user specific Names

like
title		Ubuntu 7.10, kernel 2.6.22-14-generic

could become
title		USER FOO BOOT THIS (Ubuntu 7.10, kernel 2.6.22-14-generic)

Hope this is useful

ram

---

### Post by ramnarayan on 2009-06-14
An addition 
its best to keep /home a totally separate partition. - make it as big as you can.

So assuming you are making separate distro installs for all your users make sure you give them totally separate names.

Then during the partitioning process mark the /home (/dev/sdafoo) as home

What this will do is create a /home/foo_user section within the /home and this would be unique for each user - 

However if data is not to be shared you will need to ask on how to prevent other users from accessing other /home/foo_users data sections. (am sure there will be a way)

---

