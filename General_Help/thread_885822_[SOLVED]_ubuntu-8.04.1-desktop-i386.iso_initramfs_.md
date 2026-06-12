---
title: "[SOLVED] ubuntu-8.04.1-desktop-i386.iso initramfs issue"
date: 2008-08-10
forum: General Help
---

### Post by Dirtbag1402 on 2008-08-10
Hi,

I'm new here, and am here due to an problem trying to use Ubuntu to help me fix a rogered Microsoft Windows XP Home installation.  A missing SYSTEM32 directory (and possibly the Admin account under C:\Documents and Settings).  Anyway....

I've been following the instructions on:[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-ii-getting-your-files/]("http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-ii-getting-your-files/")

I've now burnt two images - initially a ubuntu-8.04.1-desktop-i386.iso image (and when that failed) a ubuntu-7.04-desktop-i386.iso.  I get the same issue each time I boot off the DVD:

_**8.04.1 iso:**_

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

_**7.04 iso:**_

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs)

Now I've googled and searched and tried to get my tiny brain around it.  But to be honest, I've been following the guide monkey-see-monkey-do stylee as I ***really*** don't fully understand it all.  Most of the 'initramfs' threads I've seen have involved users upgrading from previous releases.  But taking on board the info I've seen in other posts, here is some info that may help:

_**7.04 iso:**_

The casper.log has multiple entries of:

mount: Mounting /dev/hda2 on /cdrom failed: No such device
stdin: error 0
stdin: error 0

cat /proc/cmdline:

BOOT_IMAGE=/casper/vmlinuz file=/casper/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

cat /proc/mounts:

none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0

cat /proc/partitions:

major   minor   #blocks   name
3       0       78150744  hda
3       1        7310488  hda1
3       2       70829640  hda2

I think the D:\ partition is the HP recovery partition (and may be NTFS), the C:\ partition is the Windows installation (FAT32)

PC is a HP Pavilion a1210.uk.  AMD processor, 80g Seagate ATA hard drive, 1250Mb RAM

I have tried changing the "quiet splash" to "all_generic_ide" but no difference.

If anyone is able to help me diagnose this problem to then in turn help me crack into my fried Windows installation I woul really appreciate it.  But please - this is my first time with Ubuntu so please be gentle (words of one syllable etc).  You really won't insult me if you spell it out keystroke by keystroke.

Thanks in advance

DB

---

### Post by gobbles414 on 2008-08-10
I don't understand. Are you saying that the Ubuntu LiveCD isn't loading correctly? Or, are you saying that the LiveCD loads but you can't access your computer's hard drive from the *Places* menu?

As far as I can tell, the directions at psychocats.net are 100% correct. But you should be aware that the procedure is NOT for repairing your Windows OS. The procedure only allows you to transfer your important files from your computer's hard drive to an external device -- like a USB flash drive, memory card, or external hard drive.

PS: In the USA at least, HP typically does not include true Windows installation disks with its computers. Like many computer companies today, HP favors recovery partitions and/or recovery disks. But if you can find a Windows installation disk for your version of Windows, you may be able to repair your Windows OS without having to reinstall.

---

### Post by Dirtbag1402 on 2008-08-10
> **gobbles414 said:**
> I don't understand. Are you saying that the Ubuntu LiveCD isn't loading correctly? Or, are you saying that the LiveCD loads but you can't access your computer's hard drive from the *Places* menu?

As far as I can tell, the directions at psychocats.net are 100% correct. But you should be aware that the procedure is NOT for repairing your Windows OS. The procedure only allows you to transfer your important files from your computer's hard drive to an external device -- like a USB flash drive, memory card, or external hard drive.

PS: In the USA at least, HP typically does not include true Windows installation disks with its computers. Like many computer companies today, HP favors recovery partitions and/or recovery disks. But if you can find a Windows installation disk for your version of Windows, you may be able to repair your Windows OS without having to reinstall.

The CD is fine - it loads and brings up the Language selection and menu screen.  But if I select the "Try Ubuntu Without any change to your computer" it continues to load before bombing out to the initramfs prompt - it never gets as far as the Places menu option.  Either version does this.

You are correct - I'm not trying to repair Windows - just get all those family Pics not backed up before I trash the drive with a clean install.

I've looked into the Windows 'repair' install.  Here in the UK (like the USA) HP uses a recovery partition and doesn't ship installation CD's.  But I'm lead to believe even with the correct disks a Repair Install may not work due to the 'OEM' nature of the buid itself.  I'm pursuing this line as a secondary option, but also trying the Ubuntu route as well.

I'm stumped why it's bombing out.  The psychocats site has been spot on and I have no reason whatsoever to think it's wrong - just the expected result I'm supposed to be getting isn't happening!

I'm awaiting a Ubuntu genius to have a eureka moment and spot my problem....

regards

DB

---

### Post by gobbles414 on 2008-08-10
Okay, now I understand. Try this:

1. Disconnect all devices from your computer except your monitor, mouse, and keyboard.

2. Go into your computer's BIOS. Some BIOS have an option called something like "load failsafe settings". If your computer's BIOS has an option such as that, try it. You may also wish to try the opposite preset option, which is often called "load optimized settings" or "load default settings".

3. If you don't see any presets in your computer's BIOS, I recommend that you at least disable "legacy USB support". You may also wish to try modifying other settings in the BIOS. It's generally safe to change settings in your computer's BIOS, as long as you don't modify anything pertaining to RAM, processors, or fans/temperature.

4. You may want to consider finding a computer with which at least one of your Ubuntu LiveCDs functions correctly. Then, just put your computer's hard drive in that computer, and you should be able to access your Windows data.

Please, let me know if any of these ideas are helpful.

PS: Have you run the "Check CD for Defects" tool? That option appears immediately after you chose your language.

---

### Post by Dirtbag1402 on 2008-08-11
> **gobbles414 said:**
> Okay, now I understand. Try this:

1. Disconnect all devices from your computer except your monitor, mouse, and keyboard.

2. Go into your computer's BIOS. Some BIOS have an option called something like "load failsafe settings". If your computer's BIOS has an option such as that, try it. You may also wish to try the opposite preset option, which is often called "load optimized settings" or "load default settings".

3. If you don't see any presets in your computer's BIOS, I recommend that you at least disable "legacy USB support". You may also wish to try modifying other settings in the BIOS. It's generally safe to change settings in your computer's BIOS, as long as you don't modify anything pertaining to RAM, processors, or fans/temperature.

4. You may want to consider finding a computer with which at least one of your Ubuntu LiveCDs functions correctly. Then, just put your computer's hard drive in that computer, and you should be able to access your Windows data.

Please, let me know if any of these ideas are helpful.

PS: Have you run the "Check CD for Defects" tool? That option appears immediately after you chose your language.

Hi,

Point 1 - everything bar mouse, monitor and keyboard already disconnected.

Point 2 & 3 - Only option I can find is "Load Default Settings" so I've actioned this, and I've disabled the "USB Legacy support"

I need to verify the CD works in another computer - can't use my laptop as it has an encrypted hd.  But the Check on the CD verified they're good (both versions) with no defects.  I'm certain the issue is some hardware setting/config on my busted PC not the Ubuntu iso/disk.  From the casper.log it seems like the cdrom cannot mount the /dev/hda2 partition.....quest is....why?

Thanks for the help, please keep it coming.  Even if I can't get my data of the PC - I at least want to get Ubunto live CD to work
out of principle!!

Regards

DB

---

### Post by gobbles414 on 2008-08-11
I'm currently on vacation, and away from my Ubuntu PC. But as soon as I get home (a couple more days), I'll conduct some tests with my LiveCDs that may give me some more ideas on how to help you.

---

### Post by Dirtbag1402 on 2008-08-11
Hey - no worries.  I appreciate any help I can get.  And maybe when we get to the bottom of this issue we'll all have learnt something and maybe even have improved the product.  I've seen several issues similar to this (exit to initramfs) but I'm really not sure how to proceed - it's an Ubuntu Expert kind of thing.

I will be getting a friend to verify both the 8.04 and 7.04 ISO's tomorrow to check the disks are good.

In the meantime, I'll continue to scour the web in search of the answers!

Regards

DB

---

### Post by Dirtbag1402 on 2008-08-11
Is this of interest:  I decided to look at other options on the 8.04 iso and thought why not do the 'Test Memory'..... well if I'm reading the screen output correctly - somethings wrong with my RAM.  I've attached the pics to the bottom :)

Even if this isn't the reason for the failure - it still doesn't look good!

Taking out the 2 521Mb cards I reran the test on just the 256Mb card and it passed - no red screen just passes, no failures.

Thoughts?

Db

---

### Post by gobbles414 on 2008-08-11
> **Dirtbag1402 said:**
> Is this of interest:  I decided to look at other options on the 8.04 iso and thought why not do the 'Test Memory'..... well if I'm reading the screen output correctly - somethings wrong with my RAM.  I've attached the pics to the bottom :)

Even if this isn't the reason for the failure - it still doesn't look good!

Taking out the 2 521Mb cards I reran the test on just the 256Mb card and it passed - no red screen just passes, no failures.

Thoughts?

Db I think that you've found the cause of your problems! Bad RAM would definitely explain why the LiveCDs have failed, and it might even explain how Windows got corrupted.

Since you only have 256 MB of healthy RAM at the moment, I recommend that you forget about the 8.04 LiveCD for now. Instead, try loading Ubuntu using the 7.10 LiveCD. Then, post your results.

PS: If your computer's two 512 MB of RAM support it, you can enable ECC in your computer's BIOS.

---

### Post by Dirtbag1402 on 2008-08-12
Such high hopes.....

.....sadly still getting the initramfs 'error' even with the 7.04 iso.

So something else is wrong.

From a hardware perspective, what else could be causing this problem?  Next step is to whipe the HD out and try it in another PC with either the 7 or 8 Ubuntu iso.  That will at least

1). Verify the CD's
2). Verify the HD is/is not **another** problem

Just wondering - if I've now found and taken out the bad ram, and if I find the disk and Live CD's have burnt fine - what hardware is left to cause the problem.:confused:

Not to be defeated - I will continue to find the truth :lolflag:

Regards

DB

---

### Post by gobbles414 on 2008-08-12
The next step is indeed to test the LiveCDs on another computer. But, there's no need to remove the hard drive from your computer at this time. For most accurate test results, I'd recommend that you use the newest possible PC.

PS: I arrived home from my vacation earlier today. So, I finally have access to my Ubuntu PC and LiveCDs!

---

### Post by Dirtbag1402 on 2008-08-14
OK - issue resolved.  My fault entirely.  You can start the heckling and flicking poo now.....

......not sure why it makes a difference, but I had somewhow managed to burn the iso's to a DVD not a CD.  Maybe it was the first blank media I grabbed.  Maybe I didn't think it made a difference.

But it did.

So now I can load Ubuntu. :popcorn:

Sadly I still can't find any of my files.  An entire scan of the HD found 8000 .jpg images - but none, not even ONE of my family snaps that were stored in a subdirectory of My Documents (called Our Pictures) of the Admin account.  And only SYSTEM32 directory I can find is under C:\cmdcons - Windows Recovery Console.

So I suspect a corrupt Registry, but whichever way you cut it - Windows commited suicide on my PC.

Thanks for all the help, I'm off to lick my wounds.....

DB

---

### Post by gobbles414 on 2008-08-14
I've made my share of stupid mistakes, so I would never flick poo at you! Two final ideas...

First, you might be able to recover more of your Windows files if you were to install Ubuntu on a different hard drive (or USB flash drive). This will allow you to install one or more of the many recovery/forensics programs that are available in the Ubuntu repositories.

Second, if you consider this issue resolved, you may wish to mark this thread as "solved".

---

