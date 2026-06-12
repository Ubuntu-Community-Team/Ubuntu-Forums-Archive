---
title: "Installing to USB Pen Drive."
date: 2004-11-16
forum: Hardware &amp; Laptops
---

### Post by jso23 on 2004-11-16
Hello Everyone!

  I have absolutely fallen in love with Ubuntu!  WOW!

  Here is my situation and here is what I want to do:

      I have a Toshiba Satellite A65-S1066 Laptop with USB 2.0 on it.  I have XP installed on the hard drive.  I want to be able to install Ubuntu onto a USB pen drive.  Unfortunately, my laptop does not boot from a USB device.

      Is there a way for me to:

1.  Install Unbuntu to a USB pen drive (1 GB or so)
2.  Boot to a CD that allows me to boot the pen drive with GRUB or something
3.  Run Ubuntu from the pen drive

  This is an ideal situation for me.  No, call it a DREAM situation for me.

  Any and all help would be greatly appreciated.

Love & Light,

  Justin

---

### Post by avallon on 2004-11-16
I would like to join you in your "dreamland", since my dream is very similar:

I have 2.5" 40GB notebook hard drive which is set in a Chronos USB external casing. Wonderful solution for extra space, very portable - about 200 grams of weight, and far bigger than any USB key/pen etc. and at the fraction of the cost.

I would like to install any Linux distribution on it, and then connect this to any PC/Notebook of my choice and boot it from there.

This is surely possible, since Mandrake have done it with their portable hard drive and Mandrake Move. The set up is called Globe Troter and it costs about 220 USD.

I have already my 40GB USB drive, Mandrake 10, Ubuntu live and Ubuntu install, and Impi 1, Impi2, Suse 9.1

Open for suggestions and experiments?

p.s. I have tried to do this with Partition Magic and Boot Magic and failed terribly.

---

### Post by rolf on 2004-11-17
[QUOTE=jso23]
      Is there a way for me to:

1.  Install Unbuntu to a USB pen drive (1 GB or so)
2.  Boot to a CD that allows me to boot the pen drive with GRUB or something
3.  Run Ubuntu from the pen drive
[/QUOTE]

1.)  Yes.  You can mount and install ubuntu on a USB device (just mount and install to that device).

2.)  Hmm.  Not that I am aware of.  There may be some experimental projects that force USB booting, but I am not aware of any that are publicly available.  Keep an eye on the Smart Boot Manager folks (google it for home page or sourceforge entry).  The easy answer may be a BIOS upgrade that enables USB booting!

3.)  You could drop the warty live cd image onto a USB device using something like partimage (google).

HTH,
rolf

---

### Post by zenwhen on 2004-11-17
Please keep in mind that flash media does not stand up to constant read/writes like a regular hard disk does. Yes, the number of read/writes it can take is HUGE, but with the swapping in and out of files that occurs when you are running an OS from the drive, I wouldn't expect the thumb drive to last long.

---

### Post by propagandhi on 2005-05-23
[QUOTE=jso23]Hello Everyone!

  I have absolutely fallen in love with Ubuntu!  WOW!

  Here is my situation and here is what I want to do:

      I have a Toshiba Satellite A65-S1066 Laptop with USB 2.0 on it.  I have XP installed on the hard drive.  I want to be able to install Ubuntu onto a USB pen drive.  Unfortunately, my laptop does not boot from a USB device.

      Is there a way for me to:

1.  Install Unbuntu to a USB pen drive (1 GB or so)
2.  Boot to a CD that allows me to boot the pen drive with GRUB or something
3.  Run Ubuntu from the pen drive

  This is an ideal situation for me.  No, call it a DREAM situation for me.

  Any and all help would be greatly appreciated.

Love & Light,

  Justin[/QUOTE]
 It's 100% possible for u to do this, however, on a 1GB drive, it'd have to be a pretty minimalistic installation. The following steps work on my 200GB External USB HDD.

STEP1: INSTALL THE OS

*IMPORTANT: when you boot the Ubuntu install CD, make sure you type 'expert' before pressing enter to start the installer.

The reason for this is that using the Expert installer, you get access to a shell before you have to reboot, and u have a bit more control over the install process THIS IS CRUCIAL IF YOU WANT TO AVOID PROBLEMS.

Install Ubuntu to the USB drive, by selecting the '(sda)' or whatever the drive is (it will generally NEVER be (hdc) or (hda)

STEP 2: CONFIGURE THE MKINITRD SCRIPT

After you have finished all the installation items (IE: install base system, configure network, select input locales, copy remaining packages to HDD),
you need to select the option "Execute A Shell".

Once the shell is loaded, type the following:

'nano /target/etc/mkinitrd/modules'

This will load up the file that tells the mkinitrd script which modules need to preloaded in the kernel initialisation process.

ADD THE FOLLOWING LINES:

sd_mod
ehci-hcd
uhci-hcd
ohci-hcd
usb-storage

Once you have done this, type the following:

'nano /target/etc/mkinitrd/mkinitrd.conf'

EDIT the line that says DELAY=0 and change it to anything over 10 (i chose 15 to be safe).

This step just ensures that the kernel will wait long enough for the USB device to appear before attempting to mount the root partition. If it doesn't
wait long enough, you will get the message " Kernel panic: Unable to sync VFS!" or something similar.

STEP 3: BUILD THE INITRD IMAGE

Now that you have told the script which modules to build into the Initrd ramdisk, you simply need to type the following:

chroot /target
mount -tproc none /proc
mkinitrd -o /boot/usbinitrd.img-(kernel version OPTIONAL)

STEP 4: CONFIGURE GRUB BOOT LOADER

The last step will involve adding an entry to the new kernel/ramdisk in the menu.lst config file of GRUB. MY particular entry is as follows:


title Ubuntu Hoary (5.04 USB)
kernel (hd1,4)/boot/vmlinuz-2.6.10-5-386 ro root=/dev/sda5
initrd (hd1,4)/boot/usbinitrd.img

You can do this by typing 'nano /target/boot/grub/menu.lst' and adding the entry that's appropriate for your setup. After that u need to do a /sbin/grub-install /dev/sdaX (where X is the partition number).

Now just type exit until you see the installer again and choose the option "Finish Installation". Reboot, and u should be able to boot into your new linux USB installation.

---

### Post by wh0rd on 2005-08-23
In the last step what do you mean by 

> After that u need to do a /sbin/grub-install /dev/sdaX (where X is the partition number). 

i under stand the x portion but what is "doing a ...." do i grub-install?

---

### Post by polpo on 2005-09-09
I followed all the indications of Propagandhi but I couldn't boot from USB.
I managed to boot using LILO instead of GRUB.

I would like to use GRUB but when I boot the system hangs prompting:

GRUB
ERROR 2

- What can I do?

- Using LILO how can I change config from the startup or from another system? (like in the case of GRUB using grub-install /dev/sda)

thanx

---

### Post by b.treu on 2006-10-14
You don't need to go through all of this.[-X  You can do the install SIMPLY and completely through the GPU. You just need to disable the automatic mounting of drives. I found the following exactly as you see it on the [Ubuntu Switch]("http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/") website. You only need to do the following:

To install Ubuntu on the external USB hard drive, I simply ran the install from the live CD just as if I were going to install normally. Before running the install, I plugged the USB hard drive in and Ubuntu detected it. Not only did Ubuntu detect it, but in mounted the drive. ](*,) This became a problem later when trying to partition the drive and create a file system because the drive was mounted.

To fix the problem System > Preferences > Removable Drives and Media and deselect the following options

    * Mount removable drives when hot-plugged
    * Mount Removable Media When Inserted
    * Browse Removable Media When Inserted

I then proceeded to install Ubuntu on the USB Hard Drive by clicking through the defaults in the installer. I chose to wipe my external hard drive and do a fresh install. If you have data on the disk you want to keep, choose to partition the disk appropriately. Be sure you are dealing with the right disk. The installer lists your main internal hard drive as /hda1/ more than likely and your external hard drive will be listed as /sda1/ or something similar.

The last step after actually installing Ubuntu on the external USB Hard Drive was to get my laptop to boot from the USB. This was nothing more than pressing F2 at a normal boot to change the boot order to load my USB before my internal hard drive.\\:D/ 

Best to all!

---

### Post by eeried on 2006-10-20
> The last step after actually installing Ubuntu on the external USB Hard Drive was to get my laptop to boot from the USB. This was nothing more than pressing F2 at a normal boot to change the boot order to load my USB before my internal hard drive.

So you didn't have to edit any files at all? Does your GRUB include Windows as well?

see [http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

---

### Post by gkokaisel on 2007-03-26
> **b.treu said:**
> You don't need to go through all of this.[-X  You can do the install SIMPLY and completely through the GPU. You just need to disable the automatic mounting of drives. I found the following exactly as you see it on the [Ubuntu Switch]("http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/") website. You only need to do the following:

To install Ubuntu on the external USB hard drive, I simply ran the install from the live CD just as if I were going to install normally. Before running the install, I plugged the USB hard drive in and Ubuntu detected it. Not only did Ubuntu detect it, but in mounted the drive. ](*,) This became a problem later when trying to partition the drive and create a file system because the drive was mounted.

To fix the problem System > Preferences > Removable Drives and Media and deselect the following options

    * Mount removable drives when hot-plugged
    * Mount Removable Media When Inserted
    * Browse Removable Media When Inserted

I then proceeded to install Ubuntu on the USB Hard Drive by clicking through the defaults in the installer. I chose to wipe my external hard drive and do a fresh install. If you have data on the disk you want to keep, choose to partition the disk appropriately. Be sure you are dealing with the right disk. The installer lists your main internal hard drive as /hda1/ more than likely and your external hard drive will be listed as /sda1/ or something similar.

The last step after actually installing Ubuntu on the external USB Hard Drive was to get my laptop to boot from the USB. This was nothing more than pressing F2 at a normal boot to change the boot order to load my USB before my internal hard drive.\\:D/ 

Best to all!



I have tried this several times with the Ubuntu Feisty Live Cd, and then with the Edgy Eft one (as I thought it might be a feisty problem), and install crashes right after I tell it to partition the usb drive.

---

### Post by fimblo on 2007-05-19
> **zenwhen said:**
> Please keep in mind that flash media does not stand up to constant read/writes like a regular hard disk does. Yes, the number of read/writes it can take is HUGE, but with the swapping in and out of files that occurs when you are running an OS from the drive, I wouldn't expect the thumb drive to last long.

Very true. It costs to write to flash memory- so you can only write to it so many times. On the other hand, the price of reading from flash is much cheaper. At least thats my impression after googling around. 

So what I've done is install the system onto three usb pen drives - one for root partition, one for /var, and one for /usr. my /tmp directory is symlinked from /var/realtmp. As almost all runtime writes go to /var and /tmp on my htpc, this works quite well. I used a separate 4G flash memory for /usr, since I'll be wanting to install more stuff on the machine later on.

This being said, I've just installed the system and Im hoping my plans work out. It would be a pain if the system died suddenly due to worn out flash...

---

### Post by Waldo323 on 2007-05-25
> **fimblo said:**
> Very true. It costs to write to flash memory- so you can only write to it so many times. On the other hand, the price of reading from flash is much cheaper. At least thats my impression after googling around. 

So what I've done is install the system onto three usb pen drives - one for root partition, one for /var, and one for /usr. my /tmp directory is symlinked from /var/realtmp. As almost all runtime writes go to /var and /tmp on my htpc, this works quite well. I used a separate 4G flash memory for /usr, since I'll be wanting to install more stuff on the machine later on.

This being said, I've just installed the system and Im hoping my plans work out. It would be a pain if the system died suddenly due to worn out flash...

ah but there is the beauty of your setup, you can back those flash drives up periodically(possibly have 6 and rsync the data with a backup flash drive, or you could back up to a hard drive, cd/dvd or whatever works for you) so if/when one fails you can copy the latest back up to a new flash drive (or if the media you backed up to is rewritable you could just use that)

---

### Post by fimblo on 2007-05-26
I've tested it now for some six days or so, the OS itself worked beautifully, but I felt that it was... alittle slow. It was fun to play with, but the day before yesterday I decided to ditch the solution in favour of using a 2.5" hdd I had lying around. At 5400rpm its quite silent- but still a heck of a lot faster than the USB disks.

Aw well. It was fun while it lasted :)

---

### Post by NULL712 on 2007-08-03
I would like to know how you installed ubuntu on multiple flash drives! And all the specs for your sett up like the size of the drives, number of drives, version of ubuntu, etc. I think this project is entertaining and would like to attempt to breath life back into it. I also have other ideas that won't be reviled at the moment.

Thanx alot :)

---

### Post by eeried on 2007-08-03
> **NULL712 said:**
>  I also have other ideas that won't be reviled at the moment.

I hope you mean "revealed" not "reviled at" :)

---

### Post by NULL712 on 2007-08-03
sorry about that i was typing faster than i could think. lol

---

### Post by fimblo on 2007-08-05
> **NULL712 said:**
> I would like to know how you installed ubuntu on multiple flash drives! And all the specs for your sett up like the size of the drives, number of drives, version of ubuntu, etc. I think this project is entertaining and would like to attempt to breath life back into it. I also have other ideas that won't be reviled at the moment.

Thanx alot :)

Hiya,

Im afraid I've reformatted the usb flash sticks, cant give you details from there. But I think I remember some stuff:

I used the Ubuntu Alternative installation CD. (Feisty)

Like I wrote earlier, I used three sticks, each with one partition on it. In retrospection I think a 1G stick for root was superfluous, since the two directories there which take up most space (/usr and /var) were already on separate partitions on other physical sticks (I dont install things into /opt). 

I skipped creating a swap space, since I seldom need it. I figured that should I find myself needing it, I could stick in another stick and do a mkswap/swapon, alternatively create a swap file.

So if you're just testing around with a mediabox, this would be my minimal recommendation of usb stick sizes and where to mount them.

64M   root (/)
2G       /usr   (question is if you even need this much, depends on what you install)
2G       /var   (again, depends on what applications you have installed)

I used 
1G root
4G /usr
4G /var

If you want to be able to save video/audio, you'll want a real hard disk around tho. USB flash is still too expensive if you want a 100G of it.

Finally: I think you should test around and get the feel of it. If you're secret project is a business startup I suggest you spend a week or two reading thru relevant parts of the excellent documentation over at the linux documentation project ([http://www.tldp.org](http://www.tldp.org)). Read the LFS (linux from scratch) documentation ([www.linuxfromscratch.org](www.linuxfromscratch.org)), for some real good tips. Then take a look at how others have crammed linux into various media. I suggest starting to look at how tomsrtbt is set up, then following thru with damnsmalllinux and finishing with slax, together with the "linux live!" toolkit. Quite useful.

Hope this helps

---

### Post by NULL712 on 2007-08-06
thanx for the info! I am actually trying to get my friend into linux but he is being stubborn and won't let go of *indows. He cant afford an external HDD but he has some flash drives laying around, so i figured i could install ubuntu on those because he dosn't want ta' install on hda. But maybe now that i got beryl working and figured out virtualbox I could get him to budge. =)
   
Thanx Again :guitar:

---

### Post by formulaben on 2007-12-27
> **zenwhen said:**
> Please keep in mind that flash media does not stand up to constant read/writes like a regular hard disk does. Yes, the number of read/writes it can take is HUGE, but with the swapping in and out of files that occurs when you are running an OS from the drive, I wouldn't expect the thumb drive to last long.

So does that mean that the solid state hard drives will fail quicker too?  How many cycles are we talking about here?  I just bought an 8GB USB drive just for this purpose... :confused:

---

### Post by fimblo on 2007-12-28
> **formulaben said:**
> So does that mean that the solid state hard drives will fail quicker too?  How many cycles are we talking about here?  I just bought an 8GB USB drive just for this purpose... :confused:

I really dont think you need to worry about it. Just make sure that your root partition and /usr partitions are mounted read-only once you've gotten everything installed. Like I wrote earlier, you could place the partitions which get written to alot (that would be /tmp, /var, /home and possibly /usr/local) onto a separate stick. That way you can get the most out of your base OS, which, after all, is mostly placed on the root and /usr.

Have you checked how fast your usb flash memory is? Thats really what got me to skip this project... It just took too long (in my judgement) to write stuff.

---

### Post by formulaben on 2007-12-28
oh, I'm sure it's probably too slow.  Oh well, I'll just resort back to a dual-boot setup like I had before (now that I know how to make Vista the default and how to change the timer.)

---

