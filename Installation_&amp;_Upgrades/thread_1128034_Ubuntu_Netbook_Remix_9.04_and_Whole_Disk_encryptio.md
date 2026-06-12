---
title: "Ubuntu Netbook Remix 9.04 and Whole Disk encryption"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by Gekitsuu on 2009-04-17
I recently installed the beta 9.04 on my Asus EEE 1000HE and I didn't see any way to do whole disk encryption through the installer. I was wondering if anyone knows if 9.04 UNR supports whole disk encryption and if so, are there any good write ups on it. The info I'm look for is how to do it and pros/cons.

---

### Post by Kissake on 2009-04-18
If 9.04 is similar to 8.04, the reason is that encrypted root is only available using the alternate install CD.  I hope I am wrong, because one of the things I would like to do is use an encrypted disk with my netbook.

The following link may be helpful, but it looks a bit painful to me:
[https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid](https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid)

As for pro's and con's, I have an encrypted root laptop, and it works great.  If there is a performance penalty, I don't sense it.

---

### Post by jco on 2009-04-27
Hi, I also had a look to 9.04 UNR and it seems it's not possible.

I'm currently using the LVM+crypted root setup using 8.10 alternate CD and on my Lenovo Ideapad S10e works great (using XFCE as desktop).

I'll probably try to upgrade my 8.10 using the 9.04 alternate CD, then convert it to something similar to UNR, maybe getting some hints there:

[https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/TurnUMPCDesktopIntoNetbook](https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/TurnUMPCDesktopIntoNetbook)

or similar...

jco

---

### Post by LonelyAppleHater on 2009-04-28
I also need to know how to get encrypted lvm on UNR.  I was thinking about just using Fedora to make the encrypted volumes, then try to load up UNR 9.04 to see if I can somehow load up the modules I need and let the installer try to install UNR on the encrypted volumes.  

I'm going to try it in Virtual Box right now.

Has anyone had any luck with this?  Thanks.

---

### Post by LonelyAppleHater on 2009-04-29
Good News!

I'm happy to say that I finally figured it out and now have a Virtual Box image running of UNR with an encrypted filesystem and swap!

See my next post on how I did it.

---

### Post by LonelyAppleHater on 2009-04-30
Ok, I was able to successfully install it again.  I couldn't avoid using Fedora 10 to do the encrypted volumes and partitioning for me, as I was tearing my hair out trying to figure out how to do it from the CLI.  

Here were my steps:

1.  Download the Live USB image (or CD) of Fedora 10 and install the image on a USB stick, CD-ROM, whatever you're preferred media is.

2.  Install Fedora 10 as you normally would, but make sure you check the box that says "encrypt" when you are formatting your drives.  Also, there is a checkmark at the bottom that says "Review and modify partitioning layout", make sure that is checked as well, as you may want to switch your partitions to ext2, add a /home volume, etc.  The volume group name should be VolGroup00 and your Logical Volume names should be LogVol00 and LogVol01.  **REMEMBER THE PASSWORD TO DECRYPT YOUR DRIVES**

3.  Once the installation is finished, shutdown.  

3a. Now download Ubuntu Netbook Remix 9.04 Live USB image and install it to a USB key using Unetbootin, the new USB Startup Disk Creator Utility, etc.

4.  Once booted up, go to Accessories and click the Terminal Application.

5.  Type in the following:
```

# sudo su -
# apt-get install lvm2 cryptsetup
# modprobe dm-crypt
# modprobe aes
# cryptsetup luksOpen /dev/sda2 sda2_crypt  
(enter password)
# vgchange -a y VolGroup00

```

Now your encrypted swap and root (and your home if you made a separate /home volume) volumes should show up in the installer.

Leave this terminal open, as you'll need it for later.

6.  Go ahead and go back to the Favorites tab and start the installer.

7.  When you get to the partitioner, you should see all your encrypted volumes, as well as the sda1 partition.  Make the sda1 partition your /boot, and click "New Partition Table" for your volumes and set the mount point and filesystem type.  I heard you should use ext2 if you have a netbook with a solid state drive.  Otherwise, go nuts :P

8.  When the installer finishes, don't reboot the machine just yet.  If you do accidentally, just boot from the UNR installer again and do just Step 5 again, but don't run the installer.

9.  Go back to the open terminal window and enter the following:
```

# mkdir /target
# mount /dev/mapper/VolGroup00-LogVol00 /target/
# mount /dev/sda1 /target/boot
# chroot /target
# mount -t proc proc /proc
# mount -t sysfs sys /sys
# apt-get install lvm2 cryptsetup

```

10.  Using your favorite text editor (I used nano), enter the following entry in /etc/crypttab:
```
sda2_crypt     /dev/sda2     none      luks
```

11.  Now put the following in /etc/initramfs-tools/modules:

```

aes-i586
dm-crypt
dm-mod
sha256

```

12.  Now edit /etc/fstab.  What you need to do here is comment out or delete the UUID that is associated with your encrypted volumes and put in the actual path for the volume.  Apparently, the UUID's might be wrong, so you need to use the path instead.  

So, for example, it might say in the comment "Was on /dev/mapper/VolGroup00-LogVol00 during installation."  You should see the UUID below.  So, replace the UUID with /dev/mapper/VolGroup00-LogVol00.  Repeat for the encrypted swap volume as well.  There's no need to do this for any other partition in the fstab file.

13.  Finally, save and close the fstab file and enter one final command:
```
# update-initramfs -k all -c
```

14.  Once that's done, go ahead and reboot and take out your USB key.  You now should see UNR magically prompt you for your password and load up your newly encrypted Ubuntu Netbook Remix!

I've only tried this on Virtual Box so far.  Once I get a netbook, I'll report back if it worked, but I don't see why not.  

I hope this works out for some of you.  Feel free to take this, repost it, improve on it, etc. 

Good Luck!

---

### Post by jinnk on 2009-05-01
Thanks LonelyAppleHater for the steps to getting root encrypted.  I've done this successfully on my EeePC 702 today and I get the unlock prompt at boot during the splash.

No need to do 2 installs.  Just boot off the Ubuntu Netbook Remix image on a USB stick and in the terminal, repartition your drives with a tool such as cfdisk.  Only /boot needs to be un-encrypted - I chose to use only 64Mb for it - though you may want to double that for comfort.

As my system only has an SSD I chose not to use a swap partition, and I've chosen to format my partitions with ext2 as that reduces the writes.  You may want to consider having a swap partition as I believe it would also be used in hibernation.

Here's an update to step 5 including the command to initially create the crypt'd volume, then use it for LV's.  Complete these steps before entering the partitioner in the installer and you won't have to create a new partition table on each LV (step 7) - allowing you to take advantage of the resizing features of LVM.

```

# sudo -i
# cfdisk /dev/sda
### Create first partition with type 83 (Linux) for /boot
### Create second partition with type 8e (Linux LVM) for our encrypted volumes

```

Setup the encrypted volume to contain our LV's
```

# apt-get install lvm2 cryptsetup
# modprobe dm-crypt
# modprobe aes
# cryptsetup -y -s 256 -c aes-cbc-essiv:sha256 luksFormat /dev/sda2
# cryptsetup luksOpen /dev/sda2 sda2_crypt  
(enter password)

```

Now the encrypted volume is ready - let's use it for Logical Volumes.
```

# pvcreate /dev/mapper/sda2_crypt
# vgcreate vg /dev/mapper/sda2_crypt
# vgchange -a y vg
# lvcreate -L 3G -n root vg
# lvcreate -l 100%FREE -n home vg

```

Finally format the volumes so the installer partitioner recognizes them.  There's no need to format again in the partitioner after this.
```

# mkfs.ext2 -L boot -M /boot /dev/sda1
# mkfs.ext2 -L root -M / /dev/vg/root
# mkfs.ext2 -L home -M /home /dev/vg/home

```

---

### Post by LonelyAppleHater on 2009-05-02
Thanks jinnk!  Now I don't have to fool around with Fedora.  I tried to Google on how to setup the encrypted volumes via the CLI, but no luck.  

And I like the cfdisk utility better, too!

A couple of questions:

1.  I'm planning on getting a netbook with an SSD as well.  I know that using swap on the SSD is a bad idea, but can you really just not have a swap at all without any issues?  I've seen tutorials where they just change a config file to use the swap space very sparingly, but I haven't heard of not having a swap space at all.

2.  I've seen a couple of posts of people using ext4 on their SSD drives, and said that it improves performance.  Is ext4 SSD friendly, or should I just play it safe and stick with ext2?

Thanks in advance.

---

### Post by jinnk on 2009-05-03
Good questions LonelyAppleHater.  I did a bit or research on both these topics recently and came to the following conclusions.

The jury is still out on which is the best filesystem for SSDs.  Any journaling filesystem will perform more writes, which in theory will wear out the flash storage quicker, however, how soon the flash storage will fail is down to several different factors and still is not clear.  There is a trade off between the resilience of journaling and the simplicity of not.  I've read that the upcoming BtrFS will address some of the needs of SSDs.  I've also read that ReiserFS currently performs well on SSDs.  I believe I can live without journaling and so chose the simplest filesystem - ext2, with the thought that if not having journaling becomes a problem there's an easy upgrade path to ext3/4 using the tune2fs tool.

Swap is not essential for a system to function normally.  On small devices the main benefit is being able to hibernate, in which case you need unencrypted swap that has at least as much space as there is RAM.  First off, having unencrypted swap compromises the security of having an encrypted system.  Additionally, losing this much space on the already conservative SSDs may not be ideal for many folks.  Having swap space means the kernel will write to it, which brings us back to the question of how long will the SSD last?  Sure you can disable swappiness, but if you're pushing your little netbook to the limit that it needs swap, then perhaps you should consider using a bigger system.

On my EeePC 702 (8G SSD, 1G RAM) Ubuntu Jaunty NBR runs well without swap.  The system responds well with ext2 on an encrypted volume, though if the system were to shutdown ungracefully there would be a rather long fsck on the next boot.

There are some other tweaks that can be done to improve SSD life - the [EeePC Community Ubuntu Docs]("https://help.ubuntu.com/community/EeePC") is a good place to start.

---

### Post by Hated On Mostly on 2009-05-14
Great posts. Hopefully in the near future Ubuntu will integrate whole disk encryption into the GUI installers of every variant of Ubuntu. In this day and age there is no excuse for any operating system to not offer easy-to-use whole disk encryption.

For whole disk encryption via the command line here is a nice guide from the Linux Mint forums:

[http://forums.linuxmint.com/viewtopic.php?f=42&t=18743](http://forums.linuxmint.com/viewtopic.php?f=42&t=18743)

[quote="wuying_ren"]***Updated on 13 Nov 2008:** Made some minor corrections.*
***Updated on 25 Nov 2008:** Made some more minor corrections.*

Hi!

This is my first howto ever! First of all I would like to advise that all the work has been done by others and all the credits are for them. This howto is just a little summary for those who get confused...or are too lazy  :P Please, check the links at the end of the post. The intro is mine, but almost all the steps of the howto are based on them.

I hope many people would find it useful. I think that if you install Ubuntu with the alternate cd, it gives you the possibility of encrypting the root filesystem. But if you use the desktop cd (the LiveCD like Mint's one) you don't have this option, and you can only encrypt a folder onto your /home after installation. Fedora also lets you encrypt the whole system during installation...but we want to install Mint, didn't we?


Some people thinks encryption is not necessary for the average user, but that's not true. If you lose your laptop, or if anyone stoles it, the personal information (yes, last picnic pics included  :twisted: ) on it can be used against you. Sometimes we don't realise that we don't protect some personal information at all. Think of it, how many times do you let your browser store your passwords so you don't have to remember them? Is the one for accessing your bank's webpage included? If someone uses your browser and "accidentally" gets to one of these webpages...dangerous, huh? Well, maybe I'm getting paranoic... :roll:

Anyway, encryption is not the holy grail...specially while the computer is running. Encryption will lock your computer and if anyone gets physical access to your computer, it is possible to take the hard drive and connect it to another computer but, if the cipher is good and the password is strong enough, it will take years to decrypt it.

OK, here is the recipe...I don't want to scare you. It has been tested on Felicia RC1, but it should work in older releases. It will also work if you are dual-booting and also if you have your windows partition encrypted with Truecrypt (Truecrypt bootloader can chainload partitions).

1 - First of all, make a backup of your data. Then, boot your Mint LiveCD. Make sure you have Internet connection, we need to install a package. Once at the desktop, type on a terminal (press Alt+F2 and type "xterm"):

```
sudo apt-get install cryptsetup

```


2 - OK, now you should fill your hard disk with random data. **This will destroy your partition scheme and all your data on the disk.** To do this, type:

```
dd if=/dev/urandom of=/dev/sda
```

Change sda for the name of the hard disk you want to use. Use sudo if needed. It can take hours because random data has to be "prepared"...so you can use /dev/zero, which will fill it with zeros instead of random data:

```
dd if=/dev/zero of=/dev/sda
```

Now partition your hard drive as normal. Take point that we will need a separate /boot partition (about 50-100 mb) because it's not possible to boot from encrypted partitions. So, for example:
> 
/dev/sda1         /boot
/dev/sda2         swap
/dev/sda3         /
/dev/sda4         /home

If you like your actual partition scheme, just make room for /boot (if you don't have it yet) and use dd commands above with them separately so you don't need to repartition.

3 - Now, we need to load some modules for crypto...things to work

```
sudo modprobe dm-crypt
sudo modprobe aes-i586
```

4 - It's time to encrypt / and /home partitions. Change XX to the correct parameters as needed and, please, **CHECK THEM TWICE**...i've lost my data lots of times... Also, don't use the same password for both partitions. If you want, use a shorter password for your /home partition. If you are afraid of forgetting them, use a sentence from a film, or a verse from a song...whatever lets you remember them without having to write them on paper (**NEVER** do this). Passwords should also be hard to guess, your name, your birthday or names/birthdays from your family do not work here  :P 

```
sudo cryptsetup -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /dev/sdXX
```

In our example, we will do:

```
sudo cryptsetup -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /dev/sda3
```
```
sudo cryptsetup -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /dev/sda4
```

Remember, /boot is not going to be encrypted. And the swap partition will be "dynamically" encrypted. I mean, we will configure cryptsetup to execute the command above on every boot, so swap will have a random key...so, *dd it!*

5 - Now we have two encrypted containers. One in /dev/sda3 and one in /dev/sda4. Once finished, we must open them in order to format them. In our example:

```
sudo cryptsetup luksOpen /dev/sda3 croot
```
```
sudo cryptsetup luksOpen /dev/sda4 chome
```

"croot" and "chome" are just names, you can change them if you want. But remember them, they will be used lately.

6 -  Format them.

```
mkfs.ext2 -j /dev/mapper/croot
mkfs.ext2 -j /dev/mapper/chome
```

I warned you, "they will be used lately".


7 - Install as normal. When the installer asks you for partitioning, select "Manual". In our example we should set mountpoints like this:

> /dev/mapper/croot          /
/dev/mapper/chome       /home
/dev/sda1                      /boot

Do nothing with /dev/sda2, /dev/sda3, /dev/sda4. If you have windows partitions or other like /usr, /var, ... mount them as normal (If you want /usr, /var, to be encrypted proceed as for / and /home).

**Note for Truecrypt users:** If you have your windows system partition encrypted with Truecrypt, remember to install grub to /boot. To do this, click "Advanced" on the last step of the installer and type /dev/sdXX (your /boot partition) on the "Install grub to..." field. On our example, we would type /dev/sda1.

Click "Install", and let it be.

8 - Once the installation has finished, let the installer know that you want to keep using the LiveCD. We need to work some more.

Go back to the terminal and create a temporal mountpoint:

```
cd /mnt

sudo mkdir root

```

Mount your / and /boot partitions:

```
sudo mount -t ext3 /dev/mapper/croot /mnt/root

sudo mount -t ext2 /dev/sda1 /mnt/root/boot
```

And chroot onto your new system:

```
sudo chroot /mnt/root
```

We need to mount proc, sys and /dev/pts to get it work properly:

```
mount -t proc proc /proc

mount -t sysfs sys /sys

mount -t devpts devpts /dev/pts

```


9 - Update your apt and install cryptsetup and initramfs-tools:

```

apt-get update

apt-get install cryptsetup initramfs-tools
```

10 - Finally we need to set up some config files. Remeber to change partitions as needed:

nano /etc/crypttab

> cswap /dev/sda2 /dev/urandom cipher=aes-cbc-essiv:sha256,size=256,hash=sha256,swap # this line auto-mounts the swap partition at boot and ciphers it with a random key
croot	/dev/sda3 none luks
chome  /dev/sda4 none luks

nano /etc/fstab

Remove the swap line added by the installer and add this:

> /dev/mapper/cswap none swap sw 0 0
/dev/mapper/croot / ext3 relatime,errors=remount-ro 0 1
/dev/mapper/chome /home ext3 relatime 0 2

The lines added by the installer for croot and chome didn't work for me. I think it's because of using UUIDs. So, don't use them.

nano /etc/initramfs-tools/modules

> dm_mod
dm_crypt
sha256_generic
aes-i586

11 - Update your initramfs:

```
update-initramfs -k all -c
```


12 - Exit chroot environment (CTRL+D) and umount /boot and /:

```
umount /mnt/root/boot

umount /mnt/root
```

13 - Reboot :D You may loose your usplash...I wonder if there's a solution for this...

**Extra (get your /home partition mounted automatically when you log in):** (Credits for [http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu))

14 - Remove entries for chome on /etc/fstab

15 - Change chome entry on /etc/crypttab to:

> chome /dev/sda4 noauto luks

16 - Install pam_mount

```
sudo apt-get install libpam-mount
``` (Don't use sudo if you're still on chroot session)

17 - Update config files as seen:

nano /etc/security/pam_mount.conf.xml (add it at the end of the file, before </pam_mount>)

> <volume user="*yourusername*" fstype="crypt" path="/dev/sda4" mountpoint="/home" />

**Note:** Don't forget to replace *yourusername* with...your username  :P 

nano /etc/pam.d/common-auth (add the line at the end of the file)

> auth optional pam_mount.so use_first_pass

nano /etc/pam.d/common-session (add the line at the end of the file)

> session	optional	pam_mount.so

18 - Finally, change your user's password to match the one you put on your /home encrypted partition:

```
sudo passwd <yourusername>
```

Now you will be asked for your / partition password at early boot. Then, you'll logon as normal with your new password and /home will be mounted for you automatically  8) 

If it does not work for any of you, or you have questions, etc just tell me. And I'm sure this howto is full of mistakes, tell me so  :D

This Howto is based on information from:

[http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu)
[http://www.hacktimes.com/?q=node/48/print](http://www.hacktimes.com/?q=node/48/print)
[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)
[https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto)
[http://wiki.archlinux.org/index.php/LUKS_Encrypted_Root](http://wiki.archlinux.org/index.php/LUKS_Encrypted_Root)
[https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid](https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid)[/quote]

---

### Post by binary10 on 2009-05-19
The guide is good for clean installs.

It's also quite simple (with a spare disk or large partition and a bit of time) to take your existing 9.04 system and with a few rsyncs to have it encrypted. Taking away the need of re-installing/configuring bits.

Only fiddly part is sorting grub menu.lst at the end, remembering to replace your existing root=UUID= entries with root=/dev/mapper/croot, and then making sure that you store that back into ucfr otherwise you'll be forever getting asked about keeping your existing menu.lst at the next kernel upgrade.

---

### Post by LonelyAppleHater on 2009-05-29
BTW, I'm able to resume and hibernate with my encrypted swap.  I have a hard drive, not an SSD, so I don't have to take care with excessive writes.  

Here's the updated procedure without the need for the Fedora install (thanks jiink):

Encrypted Linux Install

1.  Set up partitions.

```
# sudo -i
# cfdisk /dev/sda
### Create first partition with type 83 (Linux) for /boot
### Create second partition with type 8e (Linux LVM) for our encrypted volumes
```

2.  Setup the encrypted volume to contain our LV's

```
# apt-get install lvm2 cryptsetup
# modprobe dm-crypt
# modprobe aes
# cryptsetup -y -s 256 -c aes-cbc-essiv:sha256 luksFormat /dev/sda2
# cryptsetup luksOpen /dev/sda2 sda2_crypt  
(enter password)

```

3.  Now the encrypted volume is ready - let's use it for Logical Volumes.

```
# pvcreate /dev/mapper/sda2_crypt
# vgcreate vg /dev/mapper/sda2_crypt
# vgchange -a y vg
# lvcreate -L 3G -n swap vg
# lvcreate -l 100%FREE -n root vg
```

4.  Finally format the volumes so the installer partitioner recognizes them. There's no need to format again in the partitioner after this.

```
# mkfs.ext4 -L boot -M /boot /dev/sda1
# mkfs.ext4 -L root -M / /dev/vg/root
# mkswap -L swap -M /home /dev/vg/swap
```

5.  Start installer. No need to reformat partitions. Don't reboot after installer is done.

6.  Using your favorite text editor (I used nano), enter the following entry in /etc/crypttab:

```
sda2_crypt     /dev/sda2     none      luks
```

7.  Now put the following in /etc/initramfs-tools/modules:

```
aes-i586
dm-crypt
dm-mod
sha256

```

8.   Now edit /etc/fstab. What you need to do here is comment out or delete the UUID that is associated with your encrypted volumes and put in the actual path for the volume. Apparently, the UUID's might be wrong, so you need to use the path instead.

So, for example, it might say in the comment "Was on /dev/mapper/VolGroup00-LogVol00 during installation." You should see the UUID below. So, replace the UUID with /dev/mapper/VolGroup00-LogVol00. Repeat for the encrypted swap volume as well. There's no need to do this for any other partition in the fstab file.

9. Finally, save and close the fstab file and enter one final command:

```
# update-initramfs -k all -c
```

---

### Post by SpzToid on 2009-06-20
Hi Folks,

This thread taught me a lot, so I want to thank everyone that contributed so far, and also contribute how I managed to get my own netbook disk  encrypted and running well.

Even though I followed instructions written to this point, several times, I didn't realize success this way. So I tried something else, and it worked well for me. Here's what I did, (written from memory at least a week after the fact, meaning everything tests 100% perfect since installation.):

1. I downloaded the 32bit Ubuntu Jaunty 9.04 **Alternate installer**, which includes the encrypted LVM installer during the partition phase of the text installation. So I did a normal Ubuntu installation, with LVM encrypted options set while partitioning.

2. Select System > Administration > Software sources, then click the Third Party Sources tab, and then click Add... and paste the follow line:

**deb [http://ppa.launchpad.net/netbook-remix-team/ppa/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ppa/ubuntu) jaunty main**

and then repeat again with this line:

**deb-src [http://ppa.launchpad.net/netbook-remix-team/ppa/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ppa/ubuntu) jaunty main**

3. From within Synaptec, install the following apps:

Desktop Switcher (**desktop-switcher**) - Allows the user to switch between two desktop modes. Currently supports switching between Ubuntu Netbook Remix mode and "Classic Ubuntu" (two panels, gnome-like) mode.

Go Home Applet (**go-home-applet**) - A gnome-panel applet that, when clicked upon, displays the desktop. Used in a netbook-based desktop, the desktop-window will normally be the launcher. Go Home Applet also works in conjunction with the netbook-remix-launcher whereby dragging and dropping a file/url/application to the go-home-applet will automatically add it to the launcher's favorites section.

Human Netbook Theme (**human-netbook-theme**) - A gtk theme for use with Ubuntu Netbook Remix

Maximus (**maximus**) - A desktop daemon which will automatically maximize and, optionally, un-decorate windows. Has support for exclusion lists and will work with any EWMH-spec compliant window-manager.

Ubuntu Netbook Remix Launcher (**ume-launcher**) - An easy-to-use program/places/favorites launcher which resides on the desktop, replacing the main-menu.

Window Picker Applet (**window-picker-applet**) - A gnome-panel applet that displays open windows as icons on the panel, and has integrated window title-bar functionality. Optimized for use on netbook-size screens.

The easiest way to do this from within Synaptec is to select **Edit > Mark Packages by Task...** (and then check Ubuntu Netbook Remix ON).

4. That completes the installation, to switch back and forth between UNR and normal desktop modes, select System > Administration > Preferences > Switch Desktop Modes.

- - -

Suspend and hibernate works. Suspend doesn't require a password to wake, whereas hibernate is fully encrypted and requires a password to restore the running system as it was.

If you're so motivated as I was, go here to install a netbook-specific kernel: **[http://array.org/ubuntu/setup-jaunty.html](http://array.org/ubuntu/setup-jaunty.html)**.

And possibly go on to add a nifty ACPI/hardware control panel: **[http://greg.geekmind.org/eee-control/](http://greg.geekmind.org/eee-control/)**

Addendum, for installing 32bit Karmic Koala 9.10 on a netbook you can skip step 2, and only pay attention to the last detail of step 3: mark packages by task, (selecting Ubuntu Netbook Remix).

To place the alternate install image on a USB stick, use Ubuntu's System > Administration > USB startup disk creator, from a machine booted off an Ubuntu Live CD. That's the best option I have found, but Unetbootin (google it) works well too, also from Windows PCs.

---

### Post by yosef on 2009-10-21
I'm using a livedisc of 9.04. Everything seems to go ok until I get to to step 6. At the end of step 5 I did not reboot and thus each consecutive step in which files are edited only affects the live session and not the actual files on the harddrive.  I seem unable to mount the harddrive in order to edit the files there.  How can I handle this?

---

### Post by probatom on 2009-12-22
> **jinnk said:**
> Thanks LonelyAppleHater for the steps to getting root encrypted.  I've done this successfully on my EeePC 702 today and I get the unlock prompt at boot during the splash.

No need to do 2 installs.

Just tried your guide with UNR 9.10 and with this version it also works (so thanks for this guide)!

I only ran into a problem that after partitioning, cryptsetup would just fail after asking for the initial password with only a 'Command failed.' message. Solution was to reboot after the partitioning (and start the installer again, and then in the console run the commands again, except for the partitioning of course).

Reason was that the kernel doesn't always correctly "see" the right partitions after changing the partition table on disk (it's apparently still a good idea to reboot after partition table changes these days).

---

### Post by Unostot on 2010-04-23
> **yosef said:**
> I'm using a livedisc of 9.04. Everything seems to go ok until I get to to step 6. At the end of step 5 I did not reboot and thus each consecutive step in which files are edited only affects the live session and not the actual files on the harddrive.  I seem unable to mount the harddrive in order to edit the files there.  How can I handle this?

I tried the HowTo above as well, and wondered why it didn't work for me...  

After several attempts i checked the first page of this thread, and found the missing piece... LonelyAppleHater forgot in his last posted howto the chroot command... 

After i inserted this step it worked for me...  
as i don't want to create any more confusion i'm pasting his HowTo again with the missing pieces from page one at step 5.5, as well as some minor corrections which are obvious but may still be confusing for beginners. The HowTo worked for me with the additional Steps in red without problems.

all credit goes to LonelyAppleHater.
   

> **LonelyAppleHater said:**
> BTW, I'm able to resume and hibernate with my encrypted swap.  I have a hard drive, not an SSD, so I don't have to take care with excessive writes.  

Here's the updated procedure without the need for the Fedora install (thanks jiink):

Encrypted Linux Install

1.  Set up partitions.

```
# sudo -i
# cfdisk /dev/sda
### Create first partition with type 83 (Linux) for /boot
### Create second partition with type 8e (Linux LVM) for our encrypted volumes
```2.  Setup the encrypted volume to contain our LV's

```
# apt-get install lvm2 cryptsetup
# modprobe dm-crypt
# modprobe aes
# cryptsetup -y -s 256 -c aes-cbc-essiv:sha256 luksFormat /dev/sda2
# cryptsetup luksOpen /dev/sda2 sda2_crypt  
(enter password)

```3.  Now the encrypted volume is ready - let's use it for Logical Volumes.

```
# pvcreate /dev/mapper/sda2_crypt
# vgcreate vg /dev/mapper/sda2_crypt
# vgchange -a y vg
# lvcreate -L 3G -n swap vg
# lvcreate -l 100%FREE -n root vg
```4.  Finally format the volumes so the installer partitioner recognizes them. There's no need to format again in the partitioner after this.

```
# mkfs.ext4 -L boot -M /boot /dev/sda1
# mkfs.ext4 -L root -M / /dev/vg/root
[COLOR=Red] # mkswap -L swap /dev/vg/swap[/COLOR]
```5.  Start installer. No need to reformat partitions. Don't reboot after installer is done.

[COLOR=Red]5.5 [/COLOR]
```

[COLOR=Red]
# mkdir /target2
[/COLOR]  

```
[COLOR=Red]
as /target/ existed on my live unr version after the installer was finished i createt a new directory called target2
[/COLOR]
```

[COLOR=Red]
# mount /dev/vg/root /target2/
# mount /dev/sda1 /target2/boot
# chroot /target2
# mount -t proc proc /proc
# mount -t sysfs sys /sys
# apt-get install lvm2 cryptsetup

```[/COLOR]

6.  Using your favorite text editor (I used nano), enter the following entry in /etc/crypttab:

```
sda2_crypt     /dev/sda2     none      luks
```7.  Now put the following in /etc/initramfs-tools/modules:

```
aes-i586
dm-crypt
dm-mod
sha256

```8.   Now edit /etc/fstab. What you need to do here is comment out or delete the UUID that is associated with your encrypted volumes and put in the actual path for the volume. Apparently, the UUID's might be wrong, so you need to use the path instead.

So, for example, it might say in the comment "Was on /dev/mapper/VolGroup00-LogVol00 during installation." You should see the UUID below. So, replace the UUID with /dev/mapper/VolGroup00-LogVol00. Repeat for the encrypted swap volume as well. There's no need to do this for any other partition in the fstab file.

9. Finally, save and close the fstab file and enter one final command:

```
# update-initramfs -k all -c
```

---

