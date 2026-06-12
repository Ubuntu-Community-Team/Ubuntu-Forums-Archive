---
title: "Urgent help = dual OS"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by jaxxx on 2009-10-03
All,
I really need some help here re running 2 OSs on the same computer but different HDDs.
Windows is installed on the internal HDD and Ubuntu on an external. I made the CD do an automatic install of Ubuntu as I'm no IT dude.
Rebooted computer and it now doesn't start either Ubuntu or Windows automatically but gives a GRUB prompt.
How can I solve this... I'm now obliged to use only my mirror CD as I can't access the C drive to boot windows anymore and when the computer boots, it gives me the grub prompt.
Thanks a lot for your help!
JaxXx

---

### Post by kuadra on 2009-10-03
Hello jaxxx,

I'm affraid I don't understand the problem yet. Could you tell us to what extend does the current result differ from the one you had anticipated?

If you want to use more than one OS per machine, you'll naturally need a boot loader (e.g. GRUB) which allows you to select which OS you want to run after booting your machine.

Can you boot your Windows installation from GRUB? Is the GRUB entry for that broken or missing?

Or is the problem that you don't want a boot loader in general and perhaps want to start Ubuntu if your external HDD is plugged, and boot Windows automatically if it is not?

---

### Post by jaxxx on 2009-10-03
Hey! That's exactly what I want to do. Boot Windows if the external HDD isn't plugged in and Ubuntu if it is. 
As said, I'm completely new to Ubuntu and a lot of terms are a bit different.
Thanks 4 u'r time,
Jax

---

### Post by arrange on 2009-10-03
Doy you see **grub>_** with a non-blinking underscore OR do you see something like this:```
[Minimal BASH-like line editing is supported. For
the first word, TAB lists possible command
completions. Anywhere else TAB lists the possible
completions of a device/filename.]

grub>_


```or something else?

---

### Post by kuadra on 2009-10-03
> **jaxxx said:**
> Hey! That's exactly what I want to do. Boot Windows if the external HDD isn't plugged in and Ubuntu if it is.

OK, then lets first look at what has happened, and then how to fix it.

Although you might have selected the external HDD for the Ubuntu installation, the default for the install CD to write its boot record is the master boot record (MBR) on the first HDD that is booted (which is your internal HDD with the Windows installation).
The motivation behind this is that this guarantees that GRUB started before any other OS boots.
In the Ubuntu installation process, there has to be a point where you're asked in which boot record (of which HDD/partition) GRUB shall be placed, but as you've selected the automatic installation, you have probably missed this option.

One option would have been to place GRUB in the master boot record of the external HDD, and then configure the booting order in the BIOS to first try external HDDs and then the internal HDD.

Which means you have to accomplish 3 tasks:
1.) Installing GRUB in the master boot of your external HDD,
2.) restore the master boot record of your first HDD,
3.) Configure the booting order in the BIOS.

The first part is probably the simplest of them. Boot your Ubuntu system, open a terminal and issue the following:

```
sudo grub-install /dev/sdb
```

This assumes that your external HDD is /dev/sdb. If you have more than one internal HDD, it will probably be shifted to /dev/sdc or /dev/sdd. If your internal HDD is still listed as /dev/hda/, then its also possible that your external HDD might be listed as /dev/sda. If in doubt, please tell us how many HDDs you're currently using and which entries like /dev/hda, /dev/sda, etc. exist, e.g. which something like the following commands.

```
ls -1 /dev/hd*
ls -1 /dev/sd*
```

Here you can get further info about [grub-install]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html").

The second part concerning the master boot record of the internal HDD can either be done on the command line under Ubuntu, or via your Windows installation CD, which when booted, should give you some option of restoring the master boot record or "repairing the installation" or something like that.

If you have accomplished part 1.) and 2.), and have problems with part 3.), just let us know.

Hope it helps.

---

### Post by ackley on 2009-10-03
Another thing to check is making sure your computer supports USB booting. Most do now but mine, even though it was made only a year ago, does not.

---

### Post by jaxxx on 2009-10-03
Yesm that's what it said...

---

### Post by jaxxx on 2009-10-03
> **kuadra said:**
> OK, then lets first look at what has happened, and then how to fix it.


Hey,
I think I should have been more cautious b4 starting all this stuff...
I tried all the codes you indicated and the result doesn't seem promising to me:

ubuntu@ubuntu:~$ sudo grub-install /dev/sdb
/dev/sdb does not have any corresponding BIOS drive.
ubuntu@ubuntu:~$ ls -1 /dev/sd*
/dev/sda
/dev/sda1
/dev/sdb
/dev/sdc
/dev/sdc1
/dev/sdc2
/dev/sdc5
ubuntu@ubuntu:~$  

FYI, My original config was as follows:
=> One internal HDD with WinXP installed.
Then, I did as follows:
=> Installed Ubuntu from CD drive to external HDD automatically;
=> Set BIOS to run 1. Off CD; 2. Off Ext HDD; 3. Off internal HDD (thinking it'd allow me as such to choose which OS to use;
=> Booted my system but landed on a Grub Prompt. I had no clue what to do then so I restarted my computer without the ext HDD connected and well, nothing happened.
=> rebooted my computer with the Ubuntu mirror CD and am now spending my time trying to solve this with you.

Again, thanks and if you're not too busy with other stuff, I'd really appreciate some more of your time (if ever you come to Belgium, I'll buy you a beer or chocolates depending on what you prefer!)
JaX

---

### Post by sendblink23 on 2009-10-03
> **jaxxx said:**
> Hey,
I think I should have been more cautious b4 starting all this stuff...
I tried all the codes you indicated and the result doesn't seem promising to me:

ubuntu@ubuntu:~$ sudo grub-install /dev/sdb
/dev/sdb does not have any corresponding BIOS drive.
ubuntu@ubuntu:~$ ls -1 /dev/sd*
/dev/sda
/dev/sda1
/dev/sdb
/dev/sdc
/dev/sdc1
/dev/sdc2
/dev/sdc5
ubuntu@ubuntu:~$  

FYI, My original config was as follows:
=> One internal HDD with WinXP installed.
Then, I did as follows:
=> Installed Ubuntu from CD drive to external HDD automatically;
=> Set BIOS to run 1. Off CD; 2. Off Ext HDD; 3. Off internal HDD (thinking it'd allow me as such to choose which OS to use;
=> Booted my system but landed on a Grub Prompt. I had no clue what to do then so I restarted my computer without the ext HDD connected and well, nothing happened.
=> rebooted my computer with the Ubuntu mirror CD and am now spending my time trying to solve this with you.

Again, thanks and if you're not too busy with other stuff, I'd really appreciate some more of your time (if ever you come to Belgium, I'll buy you a beer or chocolates depending on what you prefer!)
JaX




I'll help you out.... FIRST   RECOVER  MBR to the WINDOWS hard drive

*Do Not Have Connected Your External HD, Only have connected your internal Hard Drive

Boot Ubuntu Live CD > Terminal 

sudo lilo -M /dev/sda mbr




Now after this, Reboot to see if Windows manages to Boot as it used to.


If it all went well, Reboot again using Ubuntu Live CD, THIS TIME...    When turning on your External Hard Drive...   Once you see it on your Desktop.. Right-Click it and Un Mount Volume

We are going to Reinstall Ubuntu into that external.... (i don't like to mess with commands, so I prefer reinstall OS)

> 
Super Simple - *THIS IS THE CORRECT WAY* Using the Normal GUI Installation

Boot with Live CD

Connect USB Device (Once detected right-click "unmount")

Choose Install from Desktop

After the language, keyboard etc.. and enter the choose where to install Ubuntu area, Choose use Guided Entirely and select the USB Device HD

Do all the normal filling username, password... and when you get to the final Page Where you choose to begin the Process *Click the Button Advanced*

In there choose where to install the Boot Grub - Just select the USB Device HD(Make sure its the Second Option *not the usb HD name*) and Ok

And confirm the Instalation Process


THERE YOU GO DONE! Full Ubuntu Install on a USB Device Hard Drive / Flash Drive

*no coding, or partitioning.. or casper thingy .. Just Regular Install GUI of Ubuntu Live CD


Now afterwards simply REBOOT computer & and boot up *F12 or what ever you do to Choose what to boot from when booting up the computer...  choose USB to boot Ubuntu, or choose internal Hard Drive to boot Windows Normally

---

### Post by kuadra on 2009-10-03
Ok, then you're now using the Live system on the installation CD.
To install GRUB in a boot record, you have to be in the actual ubuntu installation (if I'm not mistaken).
But first things first:

If you don't have any /dev/hd* devices, and if you don't have other hard disk drives under Windows apart from C:, then /dev/sda is most certainly your internal drive.
As /dev/sdb has no partitions (e.g. no /dev/sdb1...) I would suspect that this might be an optical drive (i.e. your CD/DVD drive).
So /dev/sdc (which has 3 partitions) is most certainly your external drive. I haven't done any automatic partitioning with Ubuntu yet, but I suspect that those 3 partitions are the root partition, the swap partition, and the last maybe a separate boot or home partition.

The easy and time consuming way would be to reinstall Ubuntu again and searching for the option where to place the boot loader there. The difficult but probably faster way is to:
1.) identify the partitions on /dev/sdc,
2.) mounting them in the Live system,
3.) doing a "chroot" into the installed system,
4.) installing the boot loader from there.

For 1.), start fdisk to check the size and type of the partitions:
```
sudo fdisk /dev/sdc
[...]
Command (m for help): p <shows the partition table>
<now you should see a table, post that please>
Command (m for help): q <quits fdisk>

```

One of the partitions probably will be the swap partition, which is of no interest to us. For the other 2, please mount them to a temporary directory and tell us the content. E.g. if /dev/sdc1 is not a swap partition:

```
sudo mount /dev/sdc1 /mnt
ls -1 /mnt
sudo umount /mnt
```
(The same with the other partition which is not a swap one.)

One of the outputs should look simillar to the following:
```
bin
boot
cdrom
dev
etc
home
initrd.img
initrd.img.old
lib
lost+found
media
mnt
opt
proc
root
sbin
selinux
srv
sys
tmp
usr
var
vmlinuz
vmlinuz.old
```

That is your root partition. If you have found that, issue the following command before unmounting it again:

```
cat /mnt/etc/fstab
```

Post that output please. It will tell us what the remaining partition is.

After we know the partition layout we can continue with step 2.)

---

### Post by Bartender on 2009-10-03
> **jaxxx said:**
> Installed Ubuntu from CD drive to external HDD automatically;
Set BIOS to run 1. Off CD; 2. Off Ext HDD; 3. Off internal HDD (thinking it'd allow me as such to choose which OS to use;
 Booted my system but landed on a Grub Prompt. 

With the automatic install, part of GRUB was placed on the internal Windows MBR, as kuadra explained.  But you went into BIOS and told the PC to boot from the external USB drive first.  

That's why GRUB is hung up.  If you change the BIOS to boot from the internal drive first, I'm guessing things will work correctly, but you would have to have the USB drive connected and spinning every time you start up or you'll get a different kind of GRUB error. 

sendblink's advice makes sense to me.  Fix the Windows MBR, then install ALL of Ubuntu & the GRUB bootloader to the external drive.  If you then set up the BIOS to boot from the USB drive, the PC will go to Ubuntu when the USB drive is connected and spinning, or BIOS will see no bootable drive on USB and proceed to Windows.

If your PC has it, you could also use what I call the "quickboot" option.  Most BIOS'es have this option nowadays, and the typical key is f8.  Early in the boot process, you tap the appropriate key and get a choice of devices to boot into.  This is NOT the same as changing boot device priority in BIOS - it's a one-time thing that only affects that boot-up rather than changing BIOS settings "permanently".

---

### Post by jaxxx on 2009-10-03
All, Thanks for the input.
I tried recovering the MBR to the internal drive exactly **_as explained_** and got the following message:

ubuntu@ubuntu:~$ lilo -M/dev/sda mbr
The program 'lilo' is currently not installed.  You can install it by typing:
sudo apt-get install lilo
bash: lilo: command not found
ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 407kB of archives.
After this operation, 1307kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main mbr 1.1.10-2 [23.0kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main lilo 1:22.8-7ubuntu1 [384kB]
Fetched 407kB in 4s (90.4kB/s)
Preconfiguring packages ...
Selecting previously deselected package mbr.
(Reading database ... 105940 files and directories currently installed.)
Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-7ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-7ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian


ubuntu@ubuntu:~$ lilo -M/dev/sda mbr
Fatal: Cannot open /dev/sda: Permission denied
ubuntu@ubuntu:~$ 
Any ideas. I'm running from a live CD and there's no admin of user config...

Cheers.

Thanks

---

### Post by kuadra on 2009-10-03
> **jaxxx said:**
> ubuntu@ubuntu:~$ lilo -M/dev/sda mbr
Fatal: Cannot open /dev/sda: Permission denied


Probably because this time you've omitted the "sudo" in

```
sudo lilo -M /dev/sda mbr
```

:)

---

### Post by jaxxx on 2009-10-03
yeah - that's bcs I'm a lawyer... THANKS. Am going to reboot and will check. Pray all the Gods available (is there one for computers?) ;-)

---

### Post by Bartender on 2009-10-03
lilo??

Hold up, you're going off in the wrong direction.  lilo is an entirely different bootloader.  Ubuntu uses GRUB!  I've been told that the Super Grub Disc is an easy way to fix the mbr.

---

### Post by djchandler on 2009-10-03
Agree with Bartender; download Super GRUB @:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by kuadra on 2009-10-03
I'm not familiar with lilo, but if it still doesn't work, there's also the manual way to write a standard DOS boot record into the MBR, which will then boot the active partition on the specific HDD.

In old DOS times one could use something like "fdisk /mbr", but the Linux equivalent fdisk doesn't support this option. There is a more generic way. The package **syslinux** contains the file */usr/lib/syslinux/mbr.bin*, which is a standard DOS boot record. You can use the following code to write it to your first HDD:

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
That command copies the content of /usr/lib/syslinux/mbr.bin (which is 404 bytes in size) at the start of the device /dev/sda.

But keep in mind that this can damage your disk if you (or I) make an error, so maybe Super GRUB Disk might be a safer way to do this, although I must admit that I've never tried it before.

---

### Post by jaxxx on 2009-10-03
Hey all!
Thanks all for the input. I got to recover my MBR and reinstalled Ubuntu on the external HDD and selected to install the Boot Grub on the 2nd option of the USB drive as advised by sendblink23.
Rebooted the system and chose in the "choose boot" menu to boot from the USB drive...
"No operating system detected"...
Nearly there I think.
Jacques

---

### Post by djchandler on 2009-10-03
Sounds like there's no MBR on the external drive to me.

---

### Post by jaxxx on 2009-10-03
OK - and the solution there would be?

---

### Post by kuadra on 2009-10-03
If it says "No operating system detected", then I guess this message is from a standard DOS boot record which is still on the external HDD. This means that the Ubuntu installation process hasn't written the boot record in the MBR, but maybe in the boot record of a partition of the external HDD.

If that is the case, then the lazy but time consuming way would be to reinstall Ubuntu again and double checking that the boot record is written in the MBR of the external HDD.
If the boot record was written into the boot record of another partition of the external HDD and if the master boot record is indeed untouched, you might also try to activate the one of the partitions on the external HDD. If you select the right one, the DOS MBR will continue booting from the activated partition where the boot record resides.

In terms of code, boot the Life System, and enter the following into a terminal

```
sudo cfdisk /dev/sdc
```
and there, set one of the partitions to "Bootable", "Write" the partition table and then "Quit".
After that, retry a reboot. If the error message is still the same, try to activate the other partition (but always only one at a time) until either you get to your Ubuntu installation or all partitions tried and none contained the boot record.

Either way, after one of these methods we'll be a bit wiser. :)

---

### Post by Bartender on 2009-10-03
OK, jaxx, let me see if I'm up to speed here - vista is working from the internal HDD, correct?
And you're sure that your BIOS supports boot from USB?  If so, that option is turned on in the BIOS?

If you're brand new to Ubuntu and messing around with the command line is a little frightening, there's another way to ensure that Ubuntu installs completely to the external.  I suggest this especially now after you've downloaded lilo and God knows which bootloader is in charge now...

Physically disconnect the internal HDD.  Or you can try "disable" in the BIOS, but physical disconnection is absolutely fool-proof.  Set your BIOS boot priority to boot from the internal optical drive.  Drop the Ubuntu install CD in the optical drive, plug in your USB external, make sure it's on, and restart the PC.  The Ubuntu install CD should spin up, you go thru the first four steps, when it gets to the partitioner make sure that it sees the external drive.  It "should" be recognized as sdb or some such.  Check the size and look at the partitions to make sure Ubuntu sees the external USB drive and no others.  If you go to the little box in the upper right hand corner and try to scroll up or down there should only be the one drive.

Install Ubuntu.  Let it auto-install if you want.  Since the installer sees only one drive, the whole bootloader goes to that drive instead of dropping the scrap of code into the Windows MBR.  When it's done, pop out the CD, restart the PC, go into BIOS, set it to boot from the USB drive first.

If this doesn't work, something else is wrong.  The installCD is flawed, or maybe your external USB drive doesn't spin up fast enough to be recognized by BIOS, or whatever.  Is your external powered by a wall wart, or powered off the USB port?  Mine is powered via wall wart, and what I described above works for me but the USB drive is up and running before the PC boots so there are no questions about detection during BIOS.

EDIT:  jaxx, take a read thru this [post]("http://http://ubuntuforums.org/showthread.php?t=1245199") from a few weeks back.  Very similar to your deal.

---

### Post by presence1960 on 2009-10-03
let's see exactly what you have here.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Unless you borked the install you will probably have to put GRUB on MBR of the external and windows on MBR of the internal disk. Then set your external to boot before the internal disk. This way when the external is unplugged you boot into windows, when the external is plugged in you get GRUB and boot to Ubuntu.

Kindly run that script and post the results back here so we can get you up & running.

---

### Post by sendblink23 on 2009-10-04
He's doing everything FINE...he probably choosed the WRONG installing grub in the Drop Down list inside *ADVANCED

Jaxxx TRY IT AGAIN, Reinstall just choose another option from the Advanced Menu (MAKE SURE ITS NOT THE INTERNAL HARD DRIVE)  =P

---

### Post by presence1960 on 2009-10-04
> **sendblink23 said:**
> He's doing everything FINE...he **_probably_** choosed the WRONG installing grub in the Drop Down list inside *ADVANCED

Jaxxx TRY IT AGAIN, Reinstall just choose another option from the Advanced Menu (MAKE SURE ITS NOT THE INTERNAL HARD DRIVE)  =P

why reinstall when you can easily fix what you have now.? I don't know about you but i would be tired of installing over & over again. This thread is 3 pages long and so far not close to finding the solution. That is why I insist on using the Boot Info Script when I try to help someone. it shows exactly what you have and what your boot process is. This way you can see **_EXACTLY WHAT NEEDS TO BE DONE INSTEAD OF GUESSING OR SHOOTING IN THE DARK._**

My experience has shown me that even though users with problems do not lie to us, a lot of the time what users say they have and what they actually have as reported by the boot info script are usually far apart.

Run the script please. You already expended how much time? Another couple minutes will not hurt!

---

