---
title: "Need help starting brand new PC"
date: 2011-06-06
forum: Hardware
---

### Post by ratcheer on 2011-06-06
I just received my new PC. I did not want Windows, so I ordered it with a formatted disk drive, only.

The Ubuntu 11.04 Live DVD boots, then churns for a while and says, "Unable to find a medium with a live file system."

I thought, no problem, I'll just make a Parted Live CD and partition the drive. It does the exact same thing!

How do I get started with an empty, formatted disk drive?

Thank you,
Tim

---

### Post by coffeecat on 2011-06-06
I don't believe the empty hard drive is the problem. The Ubuntu live CD would boot even if you had no hard drive at all in the machine. The message about "live file system" refers to the filesystem that is created when a live CD runs. It's not to do with the hard drive. This sounds like a problem either with the CD/DVD itself or with the CD/DVD drive. Curious that the Parted CD should do the same.

---

### Post by ratcheer on 2011-06-06
Thanks, coffecat. That is the same thing they are telling me in #ubuntu at freenode.

Also, the Natty DVD and the Parted CD were downloaded and burned on different machines. But, my old Linux PC has been temporarily set aside, so all I have to work with now is my old Win XP machine.

I'm trying to figure out a way of re-doing this without re-downloading the DVD image. It takes hours to download on a 3 mn DSL connection. All the Natty cd images appear to be gone.

Tim

---

### Post by collisionystm on 2011-06-06
This might sound silly, but are you making sure to boot from the cd? You can choose boot device at the bios prompt with a Function Hot key, or change the boot order in your bios. Also, check your bios options, because sometimes they will have a setting that say's 'operating system install mode'. Something along those lines. Just check it out, dont give up on your cd yet.

---

### Post by Yellow Pasque on 2011-06-06
CD's suck and are prone to burn errors. Get yourself a cheap 2GB USB stick. Just verify the md5 of the .iso and use unetbootin or such and you have yourself a much easier/quieter/faster setup. USB sticks are pretty handy for BIOS flashing and other stuff too.

---

### Post by mastablasta on 2011-06-07
exactly USB and also check the md5 of the iso.
 
how are you downloading? perhaps torrent would be an option you can just leave it overnight to be downloaded. it will also automaticly check that the download matches the file on server.

---

### Post by Bucky Ball on 2011-06-07
> **mastablasta said:**
> exactly USB and also check the md5 of the iso.
 
how are you downloading? perhaps torrent would be an option you can just leave it overnight to be downloaded. it will also automaticly check that the download matches the file on server.

+1. IMHO the hard drive is completely blank and not recognised by Gparted or the LiveCD. Sounds like it is unformatted. Sounds like the CDs are booting fine else you wouldn't get a message at all. Both these CDs would be looking for a HD, yes? That is their purpose. They are finding none. 

Could be totally wrong but that's my two cents worth and probably where I'd be looking. The USB option may give further insight. That might be fine but when you boot from it ... but won't find a hard drive either.

---

### Post by ratcheer on 2011-06-07
A Google search reveals that many people have been having this problem over a period of several years.

1) It is not the CD's / DVD's. All of them run fine on another computer. I now have a total of four newly made CD's and DVD's that all get the exact same error on the new PC. Two of them were made from fresh downloads on two different PC's.

2) Lots of people have tracked it down to a BIOS or hardware settings problem. People have given many different ways that they say they have solved it. One said get rid of the Win7 partition. Another said reset the jumper on the DVD player to make it the master and the hard drive the slave. One said unplug the DVD player from the SATA III port and plug it into a SATA II port. Lots of people talk about moving USB plugs from port to port. I probably saw several other "solutions".

3) Even though I paid for a PC without Windows, it actually does have Windows 7 installed. When I booted the PC with no boot CD in the drive, Win 7 configured itself. It is up and running on Win 7, now.

4) As many or more people have the exact same error trying to use USB sticks as with CD's / DVD's.

My next idea is to try an alternate install CD. I don't really think it will work, but it is something to do.

Tim

---

### Post by ratcheer on 2011-06-07
Ok, the alternate CD install fails, too. It actually starts the installer, detects the keyboard, and when it gets to the step "detect and mount CDROM", it fails. It suggests inserting a CD and trying again, but that also fails. For crying out loud, the system has already booted to the CD, but now it cannot find it!

It all seems very similar to old bug 143958, which they claim they fixed, but I believe it is a regression.

Tim

---

### Post by Bucky Ball on 2011-06-07
Do you get the same issue with 10.04 LTS? You might have mentioned so apologies if you have ...

---

### Post by ratcheer on 2011-06-07
> **Bucky Ball said:**
> Do you get the same issue with 10.04 LTS? You might have mentioned so apologies if you have ...

Thanks, I haven't tried it yet, but I see the problem in my searches occuring across many versions of Ubuntu, Mint, and Debian. I might try 10.04, but I am considering trying Fedora 15, next, just to see if getting away from Debian-based will help.

I am also going to add an "affects me too" or open a new bug at Launchpad.

Tim

---

### Post by Yellow Pasque on 2011-06-07
So did you try a different SATA port for the CD drive?

---

### Post by ratcheer on 2011-06-07
> **Temüjin said:**
> So did you try a different SATA port for the CD drive?

I wouldn't know one SATA port from another. I guess if it comes down to doing that, I'll have to get into the motherboard manual. It will be a last resort, for me.

Fedora crapped out, too. It gave me even less info than Ubuntu when it fell into a shell prompt.

Finally, I tried installing the iso to a flash drive. I cannot get the system to recognize it exists. It has boot options for USB cdrom, USB floppy disk, and USB hard drive, but nothing for a USB flash stick. I tried all three USB options, but it always fell through to boot to the hard disk.

Tim

---

### Post by oldfred on 2011-06-07
My computer has many USB boot choices. None worked with my flash dirve even USB-HDD. But I found by accident that if choose to boot a different hard drive the USB flash is listed there. Look under hard drives not USB devices.

Do you have an Intel MB? Intel motherboards used to require a boot flag on a primary partition as if you were booting with windows. Grub does not use a boot flag. But BIOS will not let you boot without boot flag.

If a very new system is it  UEFI or BIOS or selectable?

---

### Post by srs5694 on 2011-06-07
Over in [this thread,](http://ubuntuforums.org/showthread.php?t=1773655) you identified the motherboard as a Gigabyte Z68A-D3-B3. I've just downloaded the manual for this board from Gigabyte's Web site, and on p. 43, there's mention of an EFI CD/DVD boot option. This means that the board definitely has UEFI support. Whether that support is currently enabled I cannot say. I'm not sure if the status of this support would affect Ubuntu's behavior. My suspicion is that it wouldn't produce the symptoms you report, but it's worth checking out. Look on the "Advanced BIOS Features" page of your CMOS settings for this option. Note that if you change this option, Windows may stop booting until you change it back. In theory, Ubuntu will install using either mode -- but we discussed UEFI issues in the earlier thread.

p. 24 of the manual identifies the six SATA connectors on the board. Two of these are for 6 Gb/s devices and four are for 3 Gb/s devices. All six connectors are supposedly controlled by the Intel Z68 chipset. It's conceivable that Linux isn't working correctly with all of these ports, or that there's some subtle incompatibility between your DVD drive and one of the port types. Thus, it's worth moving the SATA cable from a 3 Gb/s port to a 6 Gb/s port or vice-versa.

---

### Post by ratcheer on 2011-06-08
> **oldfred said:**
> My computer has many USB boot choices. None worked with my flash dirve even USB-HDD. But I found by accident that if choose to boot a different hard drive the USB flash is listed there. Look under hard drives not USB devices.

Do you have an Intel MB? Intel motherboards used to require a boot flag on a primary partition as if you were booting with windows. Grub does not use a boot flag. But BIOS will not let you boot without boot flag.

If a very new system is it  UEFI or BIOS or selectable?

Thanks, I will look into all that. The system is very, very new, with the revised Sandy Bridge chipset. The motherboard is a Gigabyte Z68A-D3-B3. It has an Award "Touch BIOS - Hybrid EFI Technology". Yes, I can turn EFI off, but so far that has made no difference.

Tim

---

### Post by ratcheer on 2011-06-08
> **srs5694 said:**
> O

p. 24 of the manual identifies the six SATA connectors on the board. Two of these are for 6 Gb/s devices and four are for 3 Gb/s devices. All six connectors are supposedly controlled by the Intel Z68 chipset. It's conceivable that Linux isn't working correctly with all of these ports, or that there's some subtle incompatibility between your DVD drive and one of the port types. Thus, it's worth moving the SATA cable from a 3 Gb/s port to a 6 Gb/s port or vice-versa.

Thanks. I guess that's what I have to try, but I hate tearing into a brand new PC and moving cables around. But, since its not fulfilling my needs, anyway...

BTW, I am quite ticked off at the company I bought it from. I emailed them about the problem and received a terse reply that they "don't support OS's they didn't install and, even if they did, it would only be (MS) Windows". I angrily replied, "Thank you very much for all your help."

Tim

---

### Post by srs5694 on 2011-06-08
I forgot to mention in my earlier post: The computer can presumably boot from the optical drive because it's the firmware that reads that drive during the initial boot stages. Under the direction of the boot loader, the firmware reads the Linux kernel and an initial RAM disk image. The kernel then executes, mounts the initial RAM disk, and runs programs stored in it. Thereafter, the kernel is in control, so if the kernel lacks drivers for the hardware, the drive will seem to "disappear," even though it worked well enough to get the OS started in a minimal sort of way.

---

### Post by ratcheer on 2011-06-08
> **srs5694 said:**
> I forgot to mention in my earlier post: The computer can presumably boot from the optical drive because it's the firmware that reads that drive during the initial boot stages. Under the direction of the boot loader, the firmware reads the Linux kernel and an initial RAM disk image. The kernel then executes, mounts the initial RAM disk, and runs programs stored in it. Thereafter, the kernel is in control, so if the kernel lacks drivers for the hardware, the drive will seem to "disappear," even though it worked well enough to get the OS started in a minimal sort of way.

Thanks. That sounds exactly like what is happening. I have noted that quite a few drivers can be seen in the Win7 Control Panel as having been installed on the system. This is why I am "scared" to go switching SATA ports and other such changes. The maker of the PC will not support anything besides Windows. The maker of the motherboard will not support anything but Windows. They (Gigabyte) refer me to "the maker of the chipset" for Linux drivers. Presumably, that is Intel. When I look for drivers and such for the Z68 chipset on the Intel site, every single thing is for Windows. It seems that I have managed to purchase a "Linux proof" PC.

I have made a tiny amount of progress. I edited the BIOS settings to boot from USB-HDD, as suggested by oldfred. Then I put a stick on which I had installed the 11.04 alternate image for AMD64 into one of the front USB ports. It booted to the Ubuntu installer, but the menu entries did nothing. But after a while, the install started, let me select the keyboard, timezone, etc. Then I got a message from Boot loader: "/casper/vmlinuz: file not found".

So, thinking it might be a USB 3 problem, I moved the stick to a port on back of the PC which is clearly labeled "USB2". This time, the PC booted to a message on a black screen saying, "Loading Operating System ...". But, after several minutes, nothing else at all had happened.

I mentioned in an earlier post that I have verified the checksum of the alternate iso image I used to make this USB stick and also one of the CDROM's I cannot get to work. I am pretty confident that the media is good. I would test it on another PC, but all my other PC's are 32-bit, except my wife's Win7 PC, which I don't dare touch with this kind of stuff.

Tim

---

### Post by ratcheer on 2011-06-08
I finally got it working!

Some guys at dslreports.com suggested that I first insert the USB stick in a port, go into BIOS settings, and change the Hard Disk boot priority. That showed my hard drive, my USB backup drive, and the USB stick. I moved the USB stick to the top, saved the changes, and rebooted with the stick in the port.

The install is still running, but I feel confident it is working. Hooray!

Tim

PS- I will not mark the thread as solved until I am actually up and running in Ubuntu.

---

### Post by ratcheer on 2011-06-08
No such luck, of course. The installation ran through partitioning and installation of base components. Then, it asked for my name, userid, and had me choose a password. Then it started installing software, which ran for a while, then failed. I tried a few times to get that going again, but it would not work.

So, I went to the next step of installing grub. That failed, too.

Now, I almost have a brick. It still will not run a live or alternate install CD. It told me I could manually boot /vmlinuz kernel on partition /dev/mapper/vg01-vol01 with kernel argument root=/dev/mapper/vg01-vol01. I don't know how to do that, but I will try to learn.

Tim

---

### Post by oldfred on 2011-06-08
Are you running RAID or LVM? Those are advanced configurations.

> /dev/mapper/vg01-vol01

Those add additional complications to an install, but still should work if installed correctly (I do not know as I do not use them). Only the alternate installer would work with those as the drivers are not on the LiveCD as they are not common on standard desktops. But once RAID settings are added to a drive, that drive retains hidden metadata that interferes with standard installs.

---

### Post by srs5694 on 2011-06-08
It's critically important to know more about why the installation failed. What error message(s) did it report? Likewise for the GRUB installation.

It's also critically important to know if you're installing in BIOS mode or in UEFI mode. Check your firmware option for that detail. You may also want to boot the installation medium into the "try before installing" mode (or whatever term it uses) and type the following diagnostic commands in a terminal window:

```

dmesg | grep EFI
sudo parted -l

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] lines to preserve legibility. If the first command returns a bunch of entries about EFI memory options and whatnot, you're booting into EFI mode; if no such lines appear, you're using BIOS mode. The second command should identify the partition table type (msdos or gpt) and will show what special partitions are (or are not) present that may be required for booting, particularly on a GPT disk.

---

### Post by ratcheer on 2011-06-08
dmesg | grep EFI returns nothing.

parted is not installed. I tried to install it, but that asked me to insert the installation CD into the drive and press enter. /media/cdrom is not mounted, so that didn't work.

I did get grub installed and I can boot to a black screen, do Ctrl-Alt-F1 and get a command prompt. I believe I now have problems with ATI video driver.

I am becoming very tired...

Tim

---

### Post by ratcheer on 2011-06-08
More info. I cannot paste output because I am having to post from my old WinXP PC.

fdisk -l shows the following

/dev/sda1 Boot * Start 1 End 4861 ID 8e Linux LVM

Disk /dev/dm-0 9999MB This is my root
Disk /dev/dm-1 20GB This is my /home
Disk /dev/dm-2 1996MB swap

/dev/sdf1 ID 7 HPFS/NTFS This is my external UDB drive (2 TB)

Really, I could reinstall at this point and nothing would be lost. I still don't think I could install from a CD, though. I would have to do it from the USB stick, again, and I bet the Software Install step would fail, again - it has already failed, twice.

Tim

---

### Post by Yellow Pasque on 2011-06-08
And you did verify the md5 sum of the .iso if you downloaded it directly, correct?

---

### Post by srs5694 on 2011-06-08
Please post the ***complete*** "sudo fdisk -lu" output, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. If Windows is installed, it *must* have a partition, so what you've shown is incomplete; and depending on what else is there, that might indicate a source of problems -- or not, more likely, but I'm trying to rule out possibilities right now....

As I said before, it's also critically important that we know what error message(s) you're seeing. Without that information, all we can do is make wild guesses about what might be wrong.

One comment I can make: You seem to have used LVM for your installation. This is fine, but it's got its pitfalls, too. In theory, you can do an LVM installation to a single Linux LVM partition, but I personally have always used a separate /boot partition of ~200 MiB when using LVM. In theory, GRUB 2 doesn't need this, but GRUB Legacy does, so I always provide it for flexibility. If you don't have a separate /boot partition, it's conceivable that GRUB isn't installing for that reason. (See -- I'm guessing already, since I don't have the full fdisk output.) Also, if you're using the desktop installation, you've got to install the lvm2 package manually after it's finished or the computer won't boot properly. (Ubuntu's lame that way, I'm afraid.)

---

### Post by ratcheer on 2011-06-08
> **Temüjin said:**
> And you did verify the md5 sum of the .iso if you downloaded it directly, correct?

Yes, I did.

Thanks,
Tim

---

### Post by ratcheer on 2011-06-08
> **srs5694 said:**
> Please post the ***complete*** "sudo fdisk -lu" output, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. If Windows is installed, it *must* have a partition, so what you've shown is incomplete; and depending on what else is there, that might indicate a source of problems -- or not, more likely, but I'm trying to rule out possibilities right now....

As I said before, it's also critically important that we know what error message(s) you're seeing. Without that information, all we can do is make wild guesses about what might be wrong.

One comment I can make: You seem to have used LVM for your installation. This is fine, but it's got its pitfalls, too. In theory, you can do an LVM installation to a single Linux LVM partition, but I personally have always used a separate /boot partition of ~200 MiB when using LVM. In theory, GRUB 2 doesn't need this, but GRUB Legacy does, so I always provide it for flexibility. If you don't have a separate /boot partition, it's conceivable that GRUB isn't installing for that reason. (See -- I'm guessing already, since I don't have the full fdisk output.) Also, if you're using the desktop installation, you've got to install the lvm2 package manually after it's finished or the computer won't boot properly. (Ubuntu's lame that way, I'm afraid.)

Ok, I blew away Win7 in my first install (the one we have been talking about). I didn't want it and I didn't pay for it.

Second, I did another install since my last post, so I could identify the error messages. Here is what I found:

```
 Well, I reran the install and looked at syslog immediately after the installation failure. These are not the full details, but they are pretty close:

It was going along checking package after package, saying that each was "already the newest version". Then,

"Some packages could not be installed. This may mean (blah blah blah). The following info may help to resolve the situation:
The following packages have unmet dependencies:
gnome-media: Depends: libpulse-mainloop-glib0
gnome-settings-daemon: Depends: libpulse-mainloop-glib0
indicator-sound: Depends: libpulse-mainloop-glib0
libnm-glib2: Depends: libnm-glib-vpn1 (>= 0.8.4)
pulseaudio ...
ubuntu-desktop ...
xserver-xorg-input-all: Depends: xserver-xorg-input-synaptics
xserver-xorg-video-all: Depends: xserver-xorg-video-nouveau
xserver-xorg-video-ati: Depends: xserver-xorg-video-mach64
E: broken packages
tasksel: aptitude failed 100
Warning: Configuring 'pkgsel' failed with error code 1
Warning: Menu Item 'pkgsel' failed. 
```

With all that, its no wonder the system doesn't work. However, my source ISO is supposed to be the production 11.04 release image. I downloaded it from Ubuntu.com's link. I verified the MD5 sum.

Also, in the most recent install, I went to a conventional partitioning scheme. /boot is 300 MB primary, / is 12 GB logical, /home is 38 GB logical, and swap is 9 GB logical.

Tim

---

### Post by srs5694 on 2011-06-08
What's the size of the system on the USB drive you're using for installation? Was it created from a CD or a DVD image? It's possible that the transfer of files from the original was incomplete. Another possibility is that the transfer was damaged in some way -- perhaps corrupting filenames, for instance, in which case some packages wouldn't install when you ran the installer.

If you're using a CD image, the installer might be trying to download some package off the Internet. If your network connection isn't configured, it obviously wouldn't be able to do this and it would fail. (I'd expect it to complain about this, but I don't know for a fact that it would.)

---

### Post by Bucky Ball on 2011-06-08
Again, do you get the same issues with 10.04 LTS? Curious ...

---

### Post by ratcheer on 2011-06-08
I finally have it reinstalled, up and running. I made a new USB stick of  the Live CD image, installed from that, and it ran to successful  completion.

I still have a lot of configuration work to do, but I think I'm over the biggest hurdles.

Thanks everyone for your help and advice.

Tim

---

### Post by ratcheer on 2011-06-11
> **Temüjin said:**
> So did you try a different SATA port for the CD drive?

My apology to you. Even after getting Natty installed from a USB stick, I have still been unable to access the DVD drive in Ubuntu. The proposed answer on Launchpad was also to move the DVD cable from a SATA III port to a SATA II port. The drive is now working, perfectly.

It still irritates me that Windows 7 was utilizing the drive perfectly via the SATA III connection, but Ubuntu cannot.

Tim

---

### Post by Yellow Pasque on 2011-06-11
> My apology to you.
No worries.
> It still irritates me that Windows 7 was utilizing the drive perfectly via the SATA III connection, but Ubuntu cannot.
It comes down to whether the kernel has support for the SATA controller in question. With a very recent mobo, it might take a very new kernel for proper support. Ubuntu (and most other major distros) lag behind on kernel version for stability's sake.

---

