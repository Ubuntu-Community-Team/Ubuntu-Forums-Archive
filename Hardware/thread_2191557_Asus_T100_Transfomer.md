---
title: "Asus T100 Transfomer"
date: 2013-12-03
forum: Hardware
---

### Post by oly on 2013-12-03
Starting this for tips on getting the asus t100 notebook working with ubuntu, there is currently a thread on this at the xda forums.

[http://forum.xda-developers.com/showthread.php?t=2500078](http://forum.xda-developers.com/showthread.php?t=2500078)

I have got it booting using usb, and managed to install to disk but i can not get to grub yet currently it loops at boot and does not display grub.

copied boot efi 32 to the windows boot partition pointed at the file in windows using bcdedit copied custom grub.cfg to the installed ubuntu but no luck actually getting to grub.

any suggestions ?

I will update here if i figure out whats wrong.

---

### Post by oly on 2014-01-03
Some links for anyone else who attempts this,

Currently the best source of information there is also a report of getting intel graphics working on 14.04 though i could not get xrandr to work for me and still have to use nomodeset and fbdev driver.
[http://forum.xda-developers.com/showthread.php?t=2500078](http://forum.xda-developers.com/showthread.php?t=2500078)

sound driver does not seem to exist, bug report here [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1259099](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1259099)

---

### Post by Jhongy on 2014-02-13
I just got mine, will be working on getting this up and running.  I picked up the 32G version with a 500G hdd in the keyboard.

Have you tried running Ubuntu 64 bit? From my understanding, it's not wise to run from a 32-bit bootloader; but I do wonder if this can be bypassed by using rEFInd. I plan to target a working 14.04 x86_64.

For the sound, hoping it's not too dissimilar from the alc5632 driver -- it should be a good starting point.

Graphics look promising -- Intel has new drivers, have seen reports of the VESA BIOS bug being fixed....

I think the devil will be in the detail to make this a satisfying experience -- power management, screen rotation, light sensor, etc.

---

### Post by Jhongy on 2014-02-13
... looks like according to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1082059"), cross-arch is now supported in the kernel. So ultimately there should be no problem booting a 64-bit image from the T100's 32-bit UEFI.

---

### Post by Jhongy on 2014-02-14
OK, so I've managed to get Ubuntu running and installed, accelerated graphics working. Testing wifi and screen rotation now...

I'm using the 14.04 livecd daily build, with a drm-intel-next kernel. To get GRUB working you need to compile a bootia32.efi, using grub-mkimage and copy it to /EFI/Boot on the USB stick; and again (to /boot/efi/EFI/ubuntu) once you're installed. [ you need to compile for x86 despite being on x86_64]. To boot you need to hit 'e' in grub and add a kernel parameter: nomodeset

Then, with the drm-intel-next kernel, you can replace nomodeset with video=VGA-1:1366x768e . 

I'll come up with simplified instructions in a blog post once everything is up...

[IMG]http://i.imgur.com/9FHNXbCh.jpg[/IMG]

---

### Post by awilliamson on 2014-02-21
> **Jhongy said:**
> OK, so I've managed to get Ubuntu running and installed, accelerated graphics working. Testing wifi and screen rotation now...

I'm using the 14.04 livecd daily build, with a drm-intel-next kernel. To get GRUB working you need to compile a bootia32.efi, using grub-mkimage and copy it to /EFI/Boot on the USB stick; and again (to /boot/efi/EFI/ubuntu) once you're installed. [ you need to compile for x86 despite being on x86_64]. To boot you need to hit 'e' in grub and add a kernel parameter: nomodeset

Then, with the drm-intel-next kernel, you can replace nomodeset with video=VGA-1:1366x768e . 

I'll come up with simplified instructions in a blog post once everything is up...


edit: oops, misread. also, wrong account. why do I seem to keep accumulating new Ubuntu accounts?

---

### Post by davejrice on 2014-02-27
Hi,

How are you getting along? I've got a friend's T100 that has destroyed itself - Win 8!!!!!

If I can get Ubuntu on there then it's a winner. I've rebuilt it to Win 8 once already - not pleasant - so Ubuntu on there would be a treat.

thanks for any reply

---

### Post by Jhongy on 2014-03-03
Getting there...

Can boot and install, the following is now working:

- Graphics (including accelerated graphics)
- Restart (use kernel command line reboot=pci,force)
- Proper CPU frequency scaling (need 3.14-rc4 kernel or later!)
- Wifi (but very poor connection -- you need to copy across your NVRAM; this is difficult to get in 64-bit, so see my repo below)
- Touchscreen
- Light sensor (with my driver; see my repo below)

The following only work on 32-bit:
- Power off, suspend/resume (require mixed-mode EFI runtime services for 64 bit, which should be coming to the kernel soon. I've been trying patches but no luck yet.)

Almost working with lots of patches:
- Sound (with latest patches from the intel/haswell-audio-dsp branch of the "asoc" linux git repository. However sound is mono/scratchy and causes mine to become meltingly hot [i.e. some chips are red hot and will burn you through the casing] -- so give it a few days! Will update when it's usable)

Not working yet:
- ac/battery status
- Tablet buttons (I've half-written a driver, but the underlying subsystem doesn't seem to be ready -- give it a few more days)
- orientation / accelerometer sensor (I'm trying to update the inv_mpu6050 driver to work with this (mpu6500; there's a driver in android), will update my repo when ready; there's already an applet in the repo for screen [including touchscreen] rotation though, so once this is done it will be more "tablet like")
- Backlight adjustments
- Some hotkeys (fn+F1 - F7)

All the "stuff" I have is in here: [https://github.com/jfwells/linux-asus-t100ta](https://github.com/jfwells/linux-asus-t100ta)

Once I've got sound safely working, I'll post a blog post on how to get everything working, but for now, here's a quick rundown:

- Create a bootable USB image (GPT FAT with EFI folder) using a latest Daily CD image of trusty. The "Rufus" tool is useful for this in Windows.
- Add a grub EFI bootloader compiled for 32-bit, regardless of the architecture of the CD image you chose, rename it to "bootia32.efi" and put it in the EFI folder. There are instructions in the Ubuntu wiki on how to do this, but I've put in a howto below. You'll obviously have to do this from a different computer.
- in "BIOS" disable secure boot, and boot from the USB
- In grub, hit "e" on "try ubuntu", and replace the "quiet splash" command line with "video=VGA-1:1368x768e reboot=p,f"
- You can then install. After installing, fix up the command line options in /etc/default/grub, run update-grub, and copy over the bootia32.efi you made earlier to /boot/efi/EFI/Boot (backing up the one that's already there). Also copy over /boot/efi/EFI/ubuntu/grub.cfg to /boot/efi/EFI/Boot . (the "ubuntu" boot entry is not used; if using 64-bit, you can't use efibootmgr to update it, so I just ignore it).
- Set your bios to boot from the internal MMC disk (ignore the "ubuntu" option).
- After installation, replace the kernel with the latest compiled mainline kernel (3.14-rc5), then check out the above for any fixes.


Again, once this is stable and more is working, we can package up everything so it is easier for new users. But for now, with no power management or tablet buttons, it's best only for users who want to test and submit patches / bug reports.


Instructions for making bootia32.efi:
```

mkdir dev
cd dev
sudo apt-get install git bison libopts25 libselinux1-dev autogen m4 autoconf help2man libopts25-dev flex libfont-freetype-perl automake autotools-dev libfreetype6-dev texinfo ia32-libs build-essential
git clone git://git.savannah.gnu.org/grub.git
cd grub
./autogen.sh
export EFI_ARCH=i386
./configure --with-platform=efi --target=${EFI_ARCH} --program-prefix=""
make
cd grub-core
../grub-mkimage -d . -o bootia32.efi -O ${EFI_ARCH}-efi -p /boot/grub ntfs hfs appleldr boot cat efi_gop efi_uga elf fat hfsplus iso9660 linux keylayouts memdisk minicmd part_apple ext2 extcmd xfs xnu part_bsd part_gpt search search_fs_file chain btrfs loadbios loadenv lvm minix minix2 reiserfs memrw mmap msdospart scsi loopback normal configfile gzio all_video efi_gop efi_uga gfxterm gettext echo boot chain eval

```

---

### Post by oly on 2014-03-03
nice information, i cant compile grub myself though i get this error
checking for target linking format... unknown
configure: error: no suitable link format found

any ideas ? on 13.10 64bit

---

### Post by davejrice on 2014-03-03
indeed, great information, thank you.

I'll get on it now!

cheers

---

### Post by Jhongy on 2014-03-03
Make sure the line

```
export EFI_ARCH=i386
```
is copied exactly and in the same terminal session;
and the part:
```
 --target=${EFI_ARCH}
``` is copied properly

Or you can just use 
```
--target=i386
```

and later:
```
-O i386-efi
```

This is because the UEFI firmware can only boot 32-bit EFI executables. However these 32-bit executables can happily boot a 64-bit kernel (a 64-bit kernel can be chain-loaded from 32-bit or 64-bit no problem). So you can choose a 64-bit Ubuntu, but need to specify to grub to generate a 32-bit executable.

---

### Post by oly on 2014-03-04
I copied the commands exactly into the terminal, i have tried again specifying --target=i386 but still get this.

checking for target linking format... unknown
configure: error: no suitable link format found


could i be missing some kind of dependancy for building i386 on 64 bit ?

---

### Post by Jhongy on 2014-03-04
Apologies, I copied down the dependencies from when I initially compiled on an i386 netbook. I did subsequently compile on x86_64, but need to update the instructions for that. Try also installing ia32-libs and build-essential. I've added them to the earlier post...

---

### Post by oly on 2014-03-05
already had those but started again from scratch and it seems to work now, also running 14.04 on the machine i built it on so either something in the git repo changed or the upgrade pulled in something.

---

### Post by Jhongy on 2014-03-05
An update on my progress with getting stuff to work...

I've been watching Matthew Garret's EFI repository for a while. By the look of it, he's been working on getting EFI runtime services working in mixed mode. That should mean that things that require access to EFI runtime services (suspend/resume, poweroff... and maybe eventually utilities like efibootmgr) will work on 64-bit.

Until now I've not been able to merge his changes into the mainline kernel and have it compile, but he's just made a new branch (mixed-mode-merged) that merges without conflicts. I'm trying to compile it now. 

There also seem to be some changes to the wifi driver (brcmfmac) in the wireless repository. Hopefully that will improve the terribly buggy wifi. I've pulled in those changes too.

I'm still tracking the intel audio (the haswell-audio-dsp branch in the ASoC repository). They also need a firmware to work which you can get from ChromiumOS for now... But I haven't had much luck yet. Best I've had is scratchy sound accompanied by a chronic overheating problem. Still working on that.

My plan is to put all of these (once working) in a patch that applies against the 3.14 kernel. Then hopefully users will be able to easily patch the Ubuntu trusty kernel to get things working.

Not had much luck on the g-sensor / orientation sensor (Invensense MPU6500). I'd really like to get this working for tablet auto-rotation. It looks like Android is using a driver from Invensense that supports multiple Invensense devices. However, this driver was initially rejected from the mainline kernel for being too complex, as far as I can see. In the end the original Invensense submission was simplified to only support the MPU6050 in the first instance, with the intention of adding to it later. Unfortunately that "adding" doesn't seem to have happened. Some flavours of Android seem to have included the original Invensense driver in their tree, so I tried porting across the plain driver from Android, but it relies on changes to IIO (industrialio) that aren't in mainline Linux either, so the changes are too severe, and lots of stuff would be broken. Furthermore, I haven't found any reports of people using the mpu6050 driver in Linux successfully -- for people playing with the sensor directly (e.g. on drones and stuff), they seem to have resorted to just bit-banging the i2c bus to get it to work. So now I'm trying to decide whether to try to modify the inv_mpu6050 driver (which I honestly don't really understand as it has lots of bells and whistles) to work with the mpu6500, or just aim for a simple stop-gap orientation sensor driver that we can use to determine device orientation (which I can hopefully get my mostly copying existing code).

---

### Post by oly on 2014-03-06
been having some wierdness on my asus where it will not boot directly into grub, it goes into a reboot cycle i can bring up the boot device menu and that lets me choose ubuntu. however that option takes me into the bios i then hit ctrl + alt + del and it displays grub.
Looking in the bios the only boot option is ubuntu, i knwo there is another disk built in called something like mmcblk0boot so i wonder if this is related, other than that its a full install erasing the entire disk.

any ideas guessing it related to this efi stuff.

---

### Post by Jhongy on 2014-03-06
Did you blow away all the partitions on the disk, including Windows, restore, EFI etc? Sorry, I should have mentioned you needed to keep around the EFI partition.

Anyway, you can recreate it.

The partition table needs to be GPT format (not MBR). In addition to / (and maybe /boot, /home, etc), you need an EFI partition at least. and labelled "EFI00" I think (can check mine later; but you can probably just select 'efi' partition type in gparted), and marked with a "boot" flag. Needs to be formatted to FAT32. In there you need to have a folder named "Ubuntu", and in there can put your bootia32.efi and grub.cfg.

In the meantime you may be able to  manually boot to the installed system using the EFI partition on your USB stick. In Grub there, drop to a grub prompt and type 
```
linux (hd1,1)/boot/vmlinuz-xxxxx root=/dev/mmcblk0p1 video=VGA-1:1358x768e reboot=p,f
initrd (hd1,1)/boot/initrd-xxxx
boot

```
The disk numbers and paths will be different, but you can tap TAB twice to help with auto-completion

---

### Post by brainwreck on 2014-03-07
Hello

Im trying to get Ubuntu installed on my t100 alongside windows 8.1

I need to keep windows 8.1 installed (for now) because I use it for work (word excel etc)

once this gets more stable I will wipe windows and run Linux 

I have the following partitions

/dev/mmcblk0p1 EFI 

I have the other windows partitions mmcblk0p2(ntfs) mmcblk0p3(recovery) mmcblk0p4(windows 8.1)
and I have installed Ubuntu 14.04 to 

/dev/mmcblk0p5 

I have the bootloader install selection to /dev/mmcblk0p1 this is the EFI partition 

I am able to get grub to boot but it goes right into the command line version

I compiled a bootia32 and placed it in /dev/mmcblk0p1 in EFI/ubuntu and I placed the grub.cfg from my Ubuntu install on /dev/mmcblk0p5 from /boot/grub/grub.cfg -- to /dev/mmcblk0p1 EFI partition in the folder /EFI/ubuntu

but it still loads to grub command line

am I doing something wrong??

thanks in advance
** update **

I was able to get it to boot using the method you described by using the usb stick grub to boot the Ubuntu I installed any suggestions?

** update ** 

I am able to boot from the grub command line using the commands you used above from boot

it seems I cant get the grub boot menu to show on boot... any ideas how to get this to appear on boot??

---

### Post by Jhongy on 2014-03-07
In the ubuntu folder, the grub.cfg should be very short -- like, 2 lines. It just points grub to the main grub.cfg file in /boot/grub. The installer should have put it there. That way works (and ensures update-grub works).

However, in my case it didn't work as the installer had set up the 'ubuntu' entry to load grubx64.efi.

If it doesn't work, try copying over that grub.cfg and bootia32.efi to the /EFI/Boot folder, backing up the bootia32.efi that's there. Then just set the disk as the first BIOS boot option (ignore the 'ubuntu' option).

---

### Post by Jhongy on 2014-03-07
I put up a draft (ugly) walkthrough of how to get everything set up, including sound, wifi, etc... at least, as far as I've got.

[http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/)

Let me know if there's anything that I've remembered wrongly. (I disclaim all responsibility if you brick your laptop).

---

### Post by brainwreck on 2014-03-07
thanks ill check it out when i get home from work

can you upload or post a link to the grub.cfg file you use so i can use that i think i overwrote the one that was in EFI/ubuntu the small one that was 117 bytes i believe

also i noticed the link to your guide is not working :)

thank you for you help

---

### Post by oly on 2014-03-07
yeah i removed all partitions 32 gb was to restrictive for both, i had the same issue when duel booting as well though in that i had to reboot to get to grub correctly.

seems ubuntu auto detects and creates an EFI partition and it does boot, its just the inital power on then doing a soft reset ie ctrl + alt + del and it detects the efi partition and boots grub.

> **Jhongy said:**
> Did you blow away all the partitions on the disk, including Windows, restore, EFI etc? Sorry, I should have mentioned you needed to keep around the EFI partition.

Anyway, you can recreate it.

The partition table needs to be GPT format (not MBR). In addition to / (and maybe /boot, /home, etc), you need an EFI partition at least. and labelled "EFI00" I think (can check mine later; but you can probably just select 'efi' partition type in gparted), and marked with a "boot" flag. Needs to be formatted to FAT32. In there you need to have a folder named "Ubuntu", and in there can put your bootia32.efi and grub.cfg.

In the meantime you may be able to  manually boot to the installed system using the EFI partition on your USB stick. In Grub there, drop to a grub prompt and type 
```
linux (hd1,1)/boot/vmlinuz-xxxxx root=/dev/mmcblk0p1 video=VGA-1:1358x768e reboot=p,f
initrd (hd1,1)/boot/initrd-xxxx
boot

```
The disk numbers and paths will be different, but you can tap TAB twice to help with auto-completion

---

### Post by brainwreck on 2014-03-08
Well i am still getting the grub console... my EFI partition is (hd0,gpt1) however when i use the command configfile (hd0,gpt1)/EFI/boot/grub.cfg the menu will show up and ubuntu boots fine, however on boot it just goes to the grub command console

also if i use the command configfile (hd0,gpt1)/EFI/ubuntu/grub.cfg the menu will also load and ubuntu works fine? 

could my bootia32.efi be pointing to the wrong area?? do i need to set it to look for the grub.cfg on (hd0,gpt1)/EFI/ubuntu ?

---

### Post by Jhongy on 2014-03-08
> **brainwreck said:**
> also i noticed the link to your guide is not working :)

Fixed... sorry about that

> **oly said:**
> yeah i removed all partitions 32 gb was to restrictive for both, i had the same issue when duel booting as well though in that i had to reboot to get to grub correctly.

seems ubuntu auto detects and creates an EFI partition and it does boot, its just the inital power on then doing a soft reset ie ctrl + alt + del and it detects the efi partition and boots grub.

I had the same problem for a while -- I thought I had fixed it with the steps in my blog. However, I did also do a grub-install using the compiled grub2 from the latest grub source. Maybe it was that that did the trick? You may wnt to try. Before that, try with grub in both "ubuntu" and "boot"... 

> **brainwreck said:**
> Well i am still getting the grub console... my EFI partition is (hd0,gpt1) however when i use the command configfile (hd0,gpt1)/EFI/boot/grub.cfg the menu will show up and ubuntu boots fine, however on boot it just goes to the grub command console

also if i use the command configfile (hd0,gpt1)/EFI/ubuntu/grub.cfg the menu will also load and ubuntu works fine? 

could my bootia32.efi be pointing to the wrong area?? do i need to set it to look for the grub.cfg on (hd0,gpt1)/EFI/ubuntu ?

The grub.cfg file there should be pretty small -- it directs grub to the main grub.cfg file.  grub-install should have created it properly. It looks something like:

```

search.fs_uuid xxxx-xxxxx-xxxxx-xxxx root 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

```

where xxxx-xxx-xxx-xxx-xx is the UUID of your boot partition

Once you update to the patched kernel with mixed-mode, update-grub can create the proper EFI firmware entries using efibootmgr.

---

### Post by Jhongy on 2014-03-08
I just updated the walkthrough with newer instructions and downloads -- these should work better (there was so much trial and error on my side, I think I simplified them too much).

Please let me know if they still don't work.

Also, my sound appears to be permanently distorted now, even in Windows. I thnk this was from playing with all the options at high volume whe nthe driver was less developed. Either way, reinstalling the windows driver and linux firmware oesnt seem to have helped, so it may be hardware damage. Please be careful....

---

### Post by oly on 2014-03-09
got most things working to some degree but although wifi is detected it will not connect with the firmware in the post, i have just got a new router so that could a possible reason. i have had it working before from the thread on xda. any one else not able to connect at all ?

---

### Post by oly on 2014-03-11
tried at work and i can not connect either, it scans and picks up the connections fine and asks for the security key however always fails to connect, i tried the same settings as before ie using nvramtool and could not get any where.

any ideas will try a few more things when i get another chance.

---

### Post by oly on 2014-03-12
well i cut my ownfile with nvram and the wireless seemed to stay connected the entire time i have used it thats has never happened, left it on over night and it was disconnected by the morning.
rebooted it and seems to be working again no disconnect yet. not sure whats different its ubuntu nightly with no real modificatoins so not done.

also can not get it connected at work at all, so perhaps the type of encryption is having an effect, or signal strength.

---

### Post by oly on 2014-03-13
well not changed much deleted all connections in network manager, and now it seems to be connected to work and home with out disconnect so far, not sure if this is due to updated packages in ubuntu or what has caused it to start working well.

---

### Post by Jhongy on 2014-03-13
Did you try one of the modified NVRAMs that I posted? I find some are more reliable but throughput is slower. I think it's a bug in the kernel driver really, but the NVRAM variables certainly make a difference.

Would be interested to see your nvram if you get one that works really well -- on my side, wifi works, but its weak; I tend to use an external adapter.

---

### Post by oly on 2014-03-14
I tried the ones in your guide then i went back to how i did it previously using nvram tool as described on the xda threads, the file is here and it seems to be working well [http://ubuntuone.com/2PymXjoUwBcQ2axVtYfHll](http://ubuntuone.com/2PymXjoUwBcQ2axVtYfHll) if its just week signal though could be i am close enough to the wireless points to not hit an issue.

---

### Post by Jhongy on 2014-03-20
Thanks -- I think that's effectively the same as an empty nvram file. Try taking any of my nvram files, and add garbage at the beginning (e.g. ^@^@^@^@), and try that -- the result seems to work about the same. Once the mixed-mode EFI stuff is compiled in, you can view the nvram directly in the EFI vars :-)

Anyway; more wireless fixes to the brcmfmac driver seem to be in the wireless-next tree. I've merged that into 3.14-rc7 and will see if it makes any difference... fingers crossed!

---

### Post by Jhongy on 2014-03-22
I've updated the howto with the latest patches. Battery and AC status now works :-)

[http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/)

---

### Post by oly on 2014-03-23
awesome the battery status in particular will be very handy :)

---

### Post by oly on 2014-04-01
efi support is in the newer kernel now [http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI) bit late for 14.04 but should mean things will be easier in the next release :)

---

### Post by oly on 2014-04-14
Anyone else finding the latest updates have broken wifi and the touchscreen completely ?, i last updated on saturday, but  can no longer update with out the wifi may try a format not sure if it will help though, anyone else hit the same issue ?

---

### Post by jdj2 on 2014-04-20
I follow this guide yesterday and was able to boot ubuntu from USB. I was trying to access it today to install ubuntu to disk but seems like the link is dead. 

Any other site where this guide is posted?

Thanks

> **Jhongy said:**
> I put up a draft (ugly) walkthrough of how to get everything set up, including sound, wifi, etc... at least, as far as I've got.

[http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/)

Let me know if there's anything that I've remembered wrongly. (I disclaim all responsibility if you brick your laptop).

---

### Post by brainwreck on 2014-05-01
Hello all

i am using the latest ubuntu 14.04 base

I have gotten battery working on 3.15.0-rc3, i have gotten bluetooth working, i can connect my phone, bluetooth headset can use bluetoth as a headset but not input device... dont have a blue tooth keyboard or mouse so i cant test those...

still seems to be some wireless instability with the brcmfmac driver... has anyone had luck with the driver?

have been working with jhong over at

[http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/)

been posting my work over there, cant post to XDA yet as i am a new user

will keep working on it

---

### Post by brainwreck on 2014-05-02
did some more work


its seems in the file


/lib/firmware/brcm/brcmfmac43241b4-sdio,txt 


on the line devid=0x4374


should be devid=0x4324 


i got this from the kernel wifi here


[http://wireless.kernel.org/en/users/Drivers/brcm80211](http://wireless.kernel.org/en/users/Drivers/brcm80211)


you can see it lists brcm43241 as devid 0x4324 not 0x4374


with devid=0x4374 i kept getting massive error messages but once i changed it i only get 


brcmfmac: brcmf_fil_cm_data:failed err=-23


once i changed this most of my error messages went away and i can disconnect and reconnect with no problems


bluetooth still works and wifi connectivity is alot more stable, test it out seems to help me... let me know your findings




also i am using wicd network manager and under advanced settings using the nl80211 protocol, it seems Wext is giving me lots of problems... whereas nl80211 allows me to disconnect and reconnect at will..


any thoughts??


Enjoy!


-Brainwreck

---

### Post by oly on 2014-05-02
nice work brainwreck, just a quick post on how i am repairing my grub as each time i install 14.04 i get no menu :/

sudo mkdir -p /tmp/d1
sudo mount /dev/mmcblk0p1 /tmp/d1
sudo mkdir -p /tmp/d1/boot/grub/
sudo grub-mkconfig -o /tmp/d1/boot/grub/grub.cfg

this assumes ubuntu only with an efi partition and seperate root, seems grub install to partition one but ubuntu does not place the config on the partition which is where grub is looking, i would love to know if there is a way to change it so updates will automatically update the grub menu at this location.

---

### Post by shakma on 2014-05-05
Thinking of picking up this 2-n-1.  TigerDirect has it for $400 with a $150 rebate until the end of May.  Rebate is after shipping them any PC with working (bootable) Windows XP, Vista, 7, or 8.  

As a very happy Asus 1005 user, this price makes it worth the risk for me.  I was in on the early days of shaky 1005 functionality (I remember 10.10 was the first release to have "Fn" keys all working!), and now it's been my daily driver for the past 3+ years.  I'm kind of excited to join the fun on this new model which seems to have significant community support and interest!  I am no coder, but I'll try everything you guys are putting out there and report back on my experiences.

Quick question, are you folks dual-booting the Win8.1 that comes on this machine?  Is it possible to still dual-boot while following the instructions currently available in this thread and on Jfw's site?

---

### Post by oly on 2014-05-06
I think you can do both, i originally duel booted both however i struggled with space on the 32 gb model so now i am only running 14.04 and nothing else on the device.

---

### Post by shakma on 2014-05-06
> **oly said:**
> I think you can do both, i originally duel booted both however i struggled with space on the 32 gb model so now i am only running 14.04 and nothing else on the device.

"Duel" boot - that sounds about right!  Thanks for the response, Oly.  I've never even had an SSD, so I didn't think about space management.  If all goes well (like it did with my current netbook over the years), I will keep squishing my Win partition until one day it just pops out, never to be used again!

Alright, I'm convinced.  Thank you.  Ordering now.  Ubuntuforums have done it again!

---

### Post by oly on 2014-05-07
I would get one that larger than 32gb else you will likely hit the same issues.

Also on mine i have noticed it will not boot with out the keyboard anyone else encountered this ?

grub loads and i can use the buttons on the touchscreen to select grub options but on selecting it attempts to boot then shows the grub menu again in a non working state.
works fine if the keyboards plugged in anyone got any ideas on this one ?

---

### Post by johnlocke2342 on 2014-06-22
Hi.
I needed a laptop with great battery life for an internship I'll be starting this september, and I was dreaming of a 2 in 1 computer so I picked a t100 two weeks ago. Unfortunately, I haven't been able to properly boot a fresh Ubuntu install since then. I tried with 13.04, 14.04 and many daily 14.10 builds. I think I'm entering the right commands into the Live USB but the boot hangs on a recurring error that has something to do with the SSD (the tablet) part, while I'm installing to the HDD. I even tried installing Ubuntu to a large USB drive from my Mac mini, but still, I can't boot it on my t100.

If anyone can help, thanks in advance.

---

### Post by oly on 2014-06-23
It might be good to know the error, and when its happening ?
does it happen booting from the usb stick or after the install, also is this pure ubuntu or ubuntu / windows setup ?
not sure what help i can be but these would be useful things to know.

---

### Post by johnlocke2342 on 2014-06-23
Thanks for your reply.
I'd want a dual boot using rEFInd (that I managed to get working fine), ideally having Ubuntu in my micro SD card, but it doesn't seem possible so a dual boot with Ubuntu on the HDD would be good enough for me.
I'm following jfwells' blog instructions. Booting the LiveUSB is fine, the install is fine (although I'm not sure where I should install grub. In doubt I installed it to my root partition, as I use to do on my Mac. This is my first UEFI based PC). Things get ugly when I reboot using the liveUSB: buffer I/0 error times infinity, then a black screen (if I'm lucky) after minutes of waiting. 
I tried using rEFInd, selecting the USB as my primary drive in the UEFI, and pressng "esc" while turning the PC on.
Furthest I went was by booting from the liveUSB to start the fresh install I installed on a large UsB drive from my Mac. And I only got to the bootscreen splash (pressing "esc" would switch between that sreen and text errors). I'm currently trying again an install from my Mac as I'm not even sure what version I installed (either 14.04 or a 14.10 daily from last week).

---

### Post by oly on 2014-06-23
That sounds like an issue on your usb stick have you tried another one ?
Also grub goes onto the first partition, there is a seperate efi partition which you need to keep and this is where grub boot loader will go along with the grub config.
I am not using refind myself so no idea on how that works.

---

### Post by johnlocke2342 on 2014-06-23
No, the errors all point to the 32 GB SSD partition (mmcblkx), whether I'm using this stick, another one or none (using the HDD). However I might have found a loophole using my Mac for the install. I'm trying right now, with the settings you advised.

---

### Post by johnlocke2342 on 2014-06-23
OK, I have a successful install from my Mac on my USB drive, that rEFInd sees and boots on my T100TA. I copied its contents to my hard drive's dedicated partition, Ubuntu appears in rEFInd... and when I select it, it shows me a "GRUB rescue" shell. What do I do?

---

### Post by oly on 2014-06-25
I hit this problem i think it was due to it looking in the wrong place, if you manually type does it boot ? if it does update grub.cfg and copy it to the efi partition.

It could be that you dont have grub.cfg on the efi partition at all.

---

### Post by johnlocke2342 on 2014-06-25
> **oly said:**
> I hit this problem i think it was due to it looking in the wrong place, if you manually type does it boot ? if it does update grub.cfg and copy it to the efi partition.

It could be that you dont have grub.cfg on the efi partition at all.
Is that all? I've been trying to update grub (which succeeded) but then grub-install failed with an error message that I can't translate into English because of a key word I don't understand (my install is in French). I just know it has something to do with something ext2 doesn't support... while I formatted to ext3 (???). Will try to copy grub.cfg to the efi as you suggested.

Thanks

---

### Post by johnlocke2342 on 2014-07-07
Hi. 
Oly, I did what you told me, now it boots fine except I still have these mmcblk errors for ages during boot, which may last about 10 minutes before I can log in. Wifi isn't working either and when I try to compile the 3.15.x kernel following jfwhome.com tutorial  I'm getting an "error 2" message, whether I try on my T100 or on my Mac mini. 
Thanks.

---

### Post by johnlocke2342 on 2014-07-16
Anyone?

---

### Post by Buovjaga on 2014-08-18
For latest progress:
[http://asus-t100-ubuntu.blogspot.com/](http://asus-t100-ubuntu.blogspot.com/)
[https://plus.google.com/communities/117853703024346186936](https://plus.google.com/communities/117853703024346186936)

---

