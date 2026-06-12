---
title: "XP and Ubuntu attempted dual boot...fail"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by sawick61 on 2009-11-11
Okay, so using third party software I separated my HDD into 3 partitions.
The first a logical recovery partition with a .wim of my XP system
The second, an ext3 primary active in preparation for Ubuntu install.
The third, an NTFS primary in preparation for applying my XP image.  

So, I went ahead and installed Ubuntu on the second...all is well.
Then, I applied the XP image to the third.

Does anyone know with the configuration that I described, how I can choose to boot into XP because as it is now Ubuntu still boots automatically?   I made the XP partition active and it still auto boots Ubuntu.  I know the .wim is legit because I've applied it before.  I'd really rather not have to first have my running Windows config up and then make an Ubuntu partition from that same one.

---

### Post by duds2008 on 2009-11-11
You could edit your /boot/grub menu.lst file to make windows boot first? Or if you are having a problem booting windows you could download "super grub disk" This could help you. Sorry I am not entirely sure what exactly you are trying to do?

---

### Post by darkod on 2009-11-11
Two things.

1. I am not sure XP can work at all if not on the first and/or primary partition. Are you sure it would work like this?

2. Did you try a manual entry in grub for the windows OS? Because ubuntu was installed first it wouldn't have a working XP to detect and make an entry in grub automatically. Look in similar thread for manual entries, or google.

---

### Post by duds2008 on 2009-11-11
> **darkod said:**
> Two things.

1. I am not sure XP can work at all if not on the first and/or primary partition. Are you sure it would work like this?

2. Did you try a manual entry in grub for the windows OS? Because ubuntu was installed first it wouldn't have a working XP to detect and make an entry in grub automatically. Look in similar thread for manual entries, or google.

Does this not all depend on the MBR? Windows could be anywhere on the disk. The MBR would point the system in the right direction to boot the system the user chooses? Correct me if I am wrong! :p

---

### Post by sawick61 on 2009-11-11
> **darkod said:**
> Two things.

1. I am not sure XP can work at all if not on the first and/or primary partition. Are you sure it would work like this?

2. Did you try a manual entry in grub for the windows OS? Because ubuntu was installed first it wouldn't have a working XP to detect and make an entry in grub automatically. Look in similar thread for manual entries, or google.

Yeah thats exactly my issue I didn't know that I could myself make that change manually.  Can you tell I'm new to linux? lol Thanks!!

---

### Post by sawick61 on 2009-11-11
> **darkod said:**
> Two things.

1. I am not sure XP can work at all if not on the first and/or primary partition. Are you sure it would work like this?

2. Did you try a manual entry in grub for the windows OS? Because ubuntu was installed first it wouldn't have a working XP to detect and make an entry in grub automatically. Look in similar thread for manual entries, or google.

Though the Ubuntu partition was at first the primary active, i used acronis to change the one that has XP to primary active.  I searched grub entries but i didn't find a post similar to mine.  ANy suggestions?

---

### Post by darkod on 2009-11-11
Yes, you can and you should write a manual entry. Just be careful, if you installed 9.10 that probably installed grub2, not grub. Take that into account when googling.

I know what the entry is like in grub but not in grub2. Sort of new to linux myself. :)

---

### Post by duds2008 on 2009-11-11
> **sawick61 said:**
> Yeah thats exactly my issue I didn't know that I could myself make that change manually.  Can you tell I'm new to linux? lol Thanks!!

This is the brilliance of Linux! You can do everything manually! Open a terminal and type:
sudo gedit /boot/grub/menu.lst
Modify it so that windows boots first. A # at the beginning of a line is a comment and is ignored by the boot process. (PS: you can use other editors, I normally use vi or nano) Good luck!

---

### Post by sawick61 on 2009-11-11
yeah i assume i have grub2 since i did a fresh install of 9.10

---

### Post by sawick61 on 2009-11-11
> **duds2008 said:**
> This is the brilliance of Linux! You can do everything manually! Open a terminal and type:
sudo gedit /boot/grub/menu.lst
Modify it so that windows boots first. A # at the beginning of a line is a comment and is ignored by the boot process. (PS: you can use other editors, I normally use vi or nano) Good luck!
  yeah i'm a big fan of vim

---

### Post by sawick61 on 2009-11-11
> **duds2008 said:**
> This is the brilliance of Linux! You can do everything manually! Open a terminal and type:
sudo gedit /boot/grub/menu.lst
Modify it so that windows boots first. A # at the beginning of a line is a comment and is ignored by the boot process. (PS: you can use other editors, I normally use vi or nano) Good luck!

i dont have that file..


david@octoberfest:/boot/grub$ pwd
/boot/grub
david@octoberfest:/boot/grub$ ls
915resolution.mod  efiemu64.o     lspci.mod       reiserfs.mod
acpi.mod           efiemu.mod     lvm.mod         scsi.mod
affs.mod           elf.mod        mdraid.mod      search.mod
afs_be.mod         ext2.mod       memdisk.mod     serial.mod
afs.mod            extcmd.mod     memrw.mod       setjmp.mod
aout.mod           fat.mod        minicmd.mod     sfs.mod
ata.mod            font.mod       minix.mod       sh.mod
ata_pthru.mod      fs_file.mod    mmap.mod        sleep.mod
at_keyboard.mod    fshelp.mod     moddep.lst      tar.mod
befs_be.mod        fs.lst         msdospart.mod   terminfo.mod
befs.mod           fs_uuid.mod    multiboot.mod   test.mod
biosdisk.mod       gfxterm.mod    normal.mod      tga.mod
bitmap.mod         gptsync.mod    ntfscomp.mod    true.mod
blocklist.mod      grub.cfg       ntfs.mod        udf.mod
boot.img           grubenv        ohci.mod        ufs1.mod
boot.mod           gzio.mod       part_acorn.mod  ufs2.mod
bsd.mod            halt.mod       part_amiga.mod  uhci.mod
bufio.mod          handler.lst    part_apple.mod  usb_keyboard.mod
cat.mod            handler.mod    part_gpt.mod    usb.mod
cdboot.img         hdparm.mod     partmap.lst     usbms.mod
chain.mod          hello.mod      part_msdos.mod  usbtest.mod
cmp.mod            help.mod       part_sun.mod    vbeinfo.mod
command.lst        hexdump.mod    parttool.lst    vbe.mod
configfile.mod     hfs.mod        parttool.mod    vbetest.mod
core.img           hfsplus.mod    password.mod    vga.mod
cpio.mod           iso9660.mod    pci.mod         vga_text.mod
cpuid.mod          jfs.mod        play.mod        video_fb.mod
crc.mod            jpeg.mod       png.mod         video.mod
datehook.mod       kernel.img     probe.mod       videotest.mod
date.mod           keystatus.mod  pxeboot.img     xfs.mod
datetime.mod       linux16.mod    pxecmd.mod      xnu.mod
device.map         linux.mod      pxe.mod         xnu_uuid.mod
diskboot.img       lnxboot.img    raid5rec.mod    zfsinfo.mod
dm_nv.mod          loadenv.mod    raid6rec.mod    zfs.mod
drivemap.mod       loopback.mod   raid.mod
echo.mod           lsmmap.mod     read.mod
efiemu32.o         ls.mod         reboot.mod

---

### Post by darkod on 2009-11-11
Because /boot/grub/menu.lst exists only for grub. Like you said you probably have grub2.

Go here [http://ubuntuforums.org/showthread.php?t=1322287&page=2](http://ubuntuforums.org/showthread.php?t=1322287&page=2)

and see post #12.

After that you need to do in terminal
sudo update-grub

Hope it helps.

PS. When opening the file for editing don't forget you need root privileges otherwise it will open as read-only.
sudo gedit /etc/grub.d/40_custom or something like that

---

### Post by oldfred on 2009-11-11
With grub2 as part of Karmic you do not have menu.lst. It is a little different for grub2 as in effect menu.lst is divided up into several files that can be edited and then the updater combines these into grub.cfg which you are not to edit. One of the other advantages of grub2 is that it has an os prober that finds other operating system in most cases if the operating system is configured correctly.

Try running:

sudo update-grub2

If that does not work, your windows may not be correct, but we could try adding a manual entry.

---

### Post by darkod on 2009-11-11
> **oldfred said:**
> 

Try running:

sudo update-grub2

If that does not work, your windows may not be correct, but we could try adding a manual entry.

Not to be a pain but the command is update-grub. Yes it relates to grub2. I'm sure you know that, just a typo. :) I am new to ubuntu so I don't know if it would find the XP.

OP, you better try this approach first than, just without the "2". :)

---

### Post by sawick61 on 2009-11-11
i did a sudo update-grub2   problem solved THANKS!!

---

### Post by darkod on 2009-11-11
OK, my apologies to oldfred. I thought update-grub2 is a typo.

But I am slightly confused now because I have used update-grub and I definitely have grub2 too.

---

### Post by sawick61 on 2009-11-11
Correction, not solved.  Tried booting XP but says its missing hal.dll.

---

### Post by Bartender on 2009-11-11
Start over.
Put the primary NTFS partition first, and install Windows.  Install Ubuntu second, at the back end of the HDD.
Problem solved.

Yes, yes, supposedly you can tweak grub so that Windows will work even if it was installed second, but in the long run it's often easier to just start over and do it the "easy" way.

---

### Post by sawick61 on 2009-11-11
> **Bartender said:**
> Start over.
Put the primary NTFS partition first, and install Windows.  Install Ubuntu second, at the back end of the HDD.
Problem solved.

Yes, yes, supposedly you can tweak grub so that Windows will work even if it was installed second, but in the long run it's often easier to just start over and do it the "easy" way.
  i tried to do that initially but the damn partitioner that comes with it wouldn't let me.  it kept forcing me to put it on a different partition.

---

### Post by oldfred on 2009-11-11
hall.dll is a file in windows/system32? My portable shows that with a relatively new date 4/13/2008 so I know it was updated.

I have seen both update-grub and update-grub2 and /usr/sbin/grub-mkconfig. I am not on my Ubuntu system now so I cannot check but I think they are all the same. I have used the update-grub2 just to highlight it is the newer grub, but I do not know if that will always be the case. I think it was some very early documentation I saw that had the update-grub2.

This says it is update-grub
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

According to Herman it should be grub-mkconfig.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig)

---

### Post by pwrcul on 2009-11-11
I found a workaround (of 2 suggested)that might work for some folks.

I put the desktop version of Kubuntu 9.10 on an Athlon 64 X2 system.  The install succeeded, but the boot failed with Error 15 and nothing more--it crashed.

The workaround is to reinstall from the Live CD, but first choose the live session and once there push the Install button.

Somehow, the choice of the direct install from the early menus of booting the live CD does not seem able to cope with a system with multiple drives.  I had XP on sda1, a backup disk for XP on sdb1 (both formatted as NTSF), and Linux on sdc (sdc1 boot, sdc2 extended, sdc5 swap).  (Earlier I had installed on a dual boot netbook with no Grub 2 problems.)

I found the forum options by Googling.  While I was checking the Ubuntu and Canonical's Launchpad forum threads and posts and trying to figure out what to do I ran sudo fdisk -l and saw that only sdc1 was recognized as have boot and none on sda1.  (Now, after I succeeded I see that a boot sector on sda1 is also recognized.)

Here's the tip (Workaround 1 below) I was able to follow and where I found it:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/159333](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/159333)
Nicolas_Raoul  wrote on 2008-05-22:  Workarounds          #9
In two days I have found two workarounds:
Workaround 1:
At boot, do not select "install" directly. Instead, load the live desktop, and from there, click on the icon to install.
Workaround 2:
Use the alternate CD (when downloading from the Ubuntu website, check the "alternate" checkbox)

---

### Post by sawick61 on 2009-11-11
> **sawick61 said:**
> Okay, so using third party software I separated my HDD into 3 partitions.
The first a logical recovery partition with a .wim of my XP system
The second, an ext3 primary active in preparation for Ubuntu install.
The third, an NTFS primary in preparation for applying my XP image.  

So, I went ahead and installed Ubuntu on the second...all is well.
Then, I applied the XP image to the third.

Does anyone know with the configuration that I described, how I can choose to boot into XP because as it is now Ubuntu still boots automatically?   I made the XP partition active and it still auto boots Ubuntu.  I know the .wim is legit because I've applied it before.  I'd really rather not have to first have my running Windows config up and then make an Ubuntu partition from that same one.


Problem solved, overview:

so the first thing i had to do was run the command   sudo update-grub2

This updated Grub to then recognize that I have Windows XP installed.  However, when I then tried booting XP I got the following error:

missing hal.dll

So, I thew in my Windows XP cd, brought up Recovery Console, and from C:\ did the following command (THE FOLLOWING WINDOWS COMMANDS WITH A FEW ACCEPT IONS ARE CASE SENSITIVE..)

 DEL C:\Boot.ini
(permission denied)
Bootcfg /Rebuild

This rescanned for any installations of Windows I had and allowed me to add it to the MBR.  However, since it denied me when trying to delete the original, I then had two entries for XP...one working and one non-working essentially.  Which would have been fine except I couldn't leave it that way so..

Once booted up on the working xp install, from CMD.exe i did the following...

Attrib -H -R -S
DEL C:\Boot.ini

Restarted computer back into Recovery Console
from C:\
Bootcfg /Rebuild 

(it asks for entries for sys load and os load, you can name it whatever you'd like but I just put an entry in for the first option as "Microsoft Windows XP Professional" and left the second blank)

Restarted and was able to boot up fine with there only being a single entry for XP.  Thanks all@

---

