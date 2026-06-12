---
title: "How to change old SSD (Ubuntu 11.10 dual-boot/ Win 7) to new SSD (Ubuntu 11.10 only)"
date: 2012-02-21
forum: Hardware
---

### Post by rhills on 2012-02-21
I have a Toshiba T130 with a single 64GB SSD that is dual-booting Ubuntu 11.10 and Windows 7.  I have recently bought a 128GB SSD and I'd like to migrate my Ubuntu 11.10 installation onto that, leaving the Win 7 out altogether.

I've followed several different guides for migrating a Ubuntu partition to a new HDD, but while I've been able to copy the partitions over to the new drive, I've not been able to get to the point where I can boot from it.  I suspect my problem relates to Win 7 being on the primary partition on the old SSD.

Does anyone know of any good guides that might cover this particular scenario?

TIA,

Rob Hills
Waikiki, Western Australia

---

### Post by Grenage on 2012-02-21
> **rhills said:**
> I have a Toshiba T130 with a single 64GB SSD that is dual-booting Ubuntu 11.10 and Windows 7.  I have recently bought a 128GB SSD and I'd like to migrate my Ubuntu 11.10 installation onto that, leaving the Win 7 out altogether.

I've followed several different guides for migrating a Ubuntu partition to a new HDD, but while I've been able to copy the partitions over to the new drive, I've not been able to get to the point where I can boot from it.  I suspect my problem relates to Win 7 being on the primary partition on the old SSD.

Does anyone know of any good guides that might cover this particular scenario?

There is probably a wonderfully elegant way to do this, but until someone mentions it, I'll post the options that spring to mind - copying the data across to the new drive, and reinstalling grub2 from a live CD.

As I'm especially lazy, I'd probably clone the drive, boot from a liveCD and use gparted to delete and expand partitions, then reinstall grub.

---

### Post by ahallubuntu on 2012-02-21
Not sure how you copied the partitions.  Some cloning utilities would probably do it.  The Partimage utility might work but I'm not sure it supports ext4.

Manually, I recently did something similar with dd, but the partition I was copying was only a few GB.  Maybe you already used dd.  In any case, here's what I did:

1. Using a live CD or another Ubuntu machine (NOT using the partition you are copying), start up Gparted and create new partitions on new drive (assume you will have just / and swap?) at the sizes you want.

**BE CAREFUL with the dd command, as it is very dangerous if used incorrectly.  If you reverse your drive partition numbers by accident, you could very quickly wipe out your original partition!!!***

2. dd to copy original / partition to new / partition on new drive (make sure new partition is AT LEAST as big as old partition).  For example:

sudo dd if=/dev/sda1 of=/dev/sdb1 bs=1024

if your original partition is sda1 and new one is sdb1 .

3. You now have two partitions with same UUID, so probably best to shut down and remove original drive, then restart live CD with just your new drive attached.
 
4. Start up Gparted again and resize the NEW partition just slightly - make it 1MB less, then resize it back 1MB.  This will correct the partition size after the dd.

5. Reinstall Grub.  I prefer the chroot method.  Never done it on 11.10 but it should work:

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

For example:
sudo mount /dev/sda /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
update-grub
grub-install /dev/sda
exit
for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
sudo umount /mnt


6. Check the /etc/fstab file to make sure the UUIDs match your partitions.

sudo blkid

to see current UUIDs of your partitions.  If you created a new swap partition, make sure the UUID matches.  Assume you didn't change UUID of your / partition.

7.  Reboot - that should do it.

---

### Post by rhills on 2012-02-21
Hi Ahallubuntu,

Thanks for your very detailed reply.  I should probably have provided more detail but it has been several weeks since I last tried to do this so details were hazy.

I had previously tried the dd approach but hadn't been aware that it also copies the UUID so that information is very helpful.

Last night (before your reply), I had another go at this using the Gparted approach detailed in [http://askubuntu.com/questions/69283](http://askubuntu.com/questions/69283). Part of my difficulty is that I have 2 partitions to copy, root and data.  Anyway, using this approach I ended up with the correct UUIDs for my root and data partitions, but my swap partition had a different UUID, so I updated fstab to use the new swap partition UUID.  I also used the "grub-install" command detailed on the above URL.

Rebooting fails.  I have 2 problems that I can see:

1.  The Grub menu still shows the menu list I had on my old HDD.  I had previously checked in /boot/grub but couldn't find any menu.lst to edit.  I'll try your approach to fixing grub to see if it fixes this problem;

2.  More importantly, the boot process stops with a "resume failure":

> resume: libgcrypt version: 1.5.0
resume: Could not stat the device file '/dev/sda6'...

Of course, in my new setup, my swap partition is /dev/sda2.

I have edited my initramfs-tools/conf.d/resume file to replace the old swap partition UUID with the new one, but this made no difference.

Is there any way I can either edit something on my new boot partition to temporarily switch off "resume" mode or edit something to make it look in the right place for the new swap partition?

I'd go back and try your "dd" approach, but AFAICT, it wouldn't fix my "resume" problem.

Cheers,

Rob Hills
Waikiki, Western Australia

---

### Post by ahallubuntu on 2012-02-21
Are any of your partitions encrypted?

---

### Post by rhills on 2012-02-21
I have not encrypted any partitions.  However, I suspect that any data stored during a "suspend" process probably would be.

---

### Post by ahallubuntu on 2012-02-21
Sure the swap partition didn't get encrypted?  Look in /etc/fstab .

This may or may not help - the poster there was able to boot despite the error and then fix it.

Perhaps you can disable swap in your /etc/fstab (just comment out the swap partition) and see if you can boot?  If so, you can start up Gparted and re-format your Swap partition then do "Swap-on."

---

### Post by rhills on 2012-02-21
Hi Ahallubuntu,

> **ahallubuntu said:**
> Sure the swap partition didn't get encrypted?  Look in /etc/fstab .
The only option against the swap partition in fstab is 'sw'.  I've looked through man pages for fstab and swapon but haven't found what that option means, but intuitively it doesn't seem to indicate encryption.

> **ahallubuntu said:**
>  This may or may not help - the poster there was able to boot despite the error and then fix it.
I assume you missed out a URL here somewhere?

> **ahallubuntu said:**
>  Perhaps you can disable swap in your /etc/fstab (just comment out the swap partition) and see if you can boot?  If so, you can start up Gparted and re-format your Swap partition then do "Swap-on."
I'll give that a try.

BTW, I tried your "chroot" method on the Grub configuration and it seems to have fixed that, the Grub menu now reflects my new setup rather than the old one, so thanks for that.

Cheers,
Rob Hills
Waikiki, Western Australia

---

### Post by rhills on 2012-02-21
> **ahallubuntu said:**
> Perhaps you can disable swap in your /etc/fstab (just comment out the swap partition) and see if you can boot?  If so, you can start up Gparted and re-format your Swap partition then do "Swap-on."
For the record, I've just tried this, but I still get the "libgcrypt" error.

I'd like to try that URL you referred to in your message if you could post it for me.

Cheers,

Rob Hills
Waikiki, Western Australia

---

### Post by ahallubuntu on 2012-02-21
Sorry, this is the URL I left out:

[http://ubuntuforums.org/showpost.php?p=9991994&postcount=26](http://ubuntuforums.org/showpost.php?p=9991994&postcount=26)

It's not exactly your situation but could still help you.

---

### Post by rhills on 2012-02-21
> **ahallubuntu said:**
> Sorry, this is the URL I left out:

[http://ubuntuforums.org/showpost.php?p=9991994&postcount=26](http://ubuntuforums.org/showpost.php?p=9991994&postcount=26)

It's not exactly your situation but could still help you.

Thanks for that, it looks like good info, I'll give it a go.

Meanwhile, some Googling lead me to this thread: [http://forums.fedoraforum.org/showthread.php?t=111565](http://forums.fedoraforum.org/showthread.php?t=111565) which is for Fedora, but it seems relevant.

Following this, I established that in my boot image (boot/initrd.img-3.0.0-16-generic), I had a reference to the old Swap File UUID in the conf/conf.d/resume file there.  I have edited that and zipped it back up into a new boot image file (initrd.img-3.0.temp) but I now need to be able to add this to the Grub menu so I can try booting from it to test it.  The link above refers to a boot/grub/menu.lst file but this doesn't exist on my system, so I assume Ubuntu (or this version of Grub) uses something else.  How can I add a different boot image to my Grub setup?

Cheers,

Rob Hills

---

### Post by ahallubuntu on 2012-02-22
Right, Ubuntu has used Grub2 since 9.10.   So you rebuild the Grub menu with

sudo update-grub

(or use the chroot method if using the live CD, as you already did.)

---

### Post by rhills on 2012-02-22
> **ahallubuntu said:**
> Right, Ubuntu has used Grub2 since 9.10.   So you rebuild the Grub menu with

sudo update-grub

(or use the chroot method if using the live CD, as you already did.)

Thanks for that info.  For the record, I tried this method (manually tweaking the boot image file) and after rebooting, I got a kernel panic.

Have since tried what you suggested originally ([http://ubuntuforums.org/showpost.php?p=9991994&postcount=26](http://ubuntuforums.org/showpost.php?p=9991994&postcount=26)) but still not getting it to boot.  I tried fsck on my root partition (via the Live CD of course) - errors were found and fixed, but it still won't boot.

Think I'll start afresh, wipe the new HDD, re-create and format the partitions and then use dd to copy the old partitions over again.  After that, I'll follow your suggestions to sort out Grub and the swap partition.

Cheers,

Rob Hills
Waikiki, Western Australia

---

### Post by oldfred on 2012-02-22
While you can do what you are doing, UUIDs are in various places the most important fstab and grub2's files. So updating settings can work.

But to throw a monkey wrench in the works, I might suggest this:

But I think it is just easier to start over and install a clean (housecleaned then) new system. You can copy over /home and any specific system settings from files in /etc. You can export a list of installed applications and easily reinstall. I have been doing clean installs of new versions since 10.10 and my backup plan is just a reinstall and recover from my backups. My new install take about an hour including reinstall of apps and some manual reconfiguring. But I do have high speed Internet.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

If a new install you can also reformat to gpt which is recommended in the arch site for SSDs. With gpt you cannot use dd as the internal structures cannot be correctly dd'd from mbr partitions.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by rhills on 2012-02-22
Hi Oldfred,

> **oldfred said:**
> But I think it is just easier to start over and install a clean (housecleaned then) new system.

Thanks for the suggestion and especially the very useful links.  The stuff about GPT looks interesting too and I'd like to go down that path if it doesn't add too many more complications!

I had been thinking of going down the "fresh install" path, but even though this is a home notebook, I do have a **lot** of apps to reinstall, so it'd be a bit more than an hour for me to go down that path.

That said, I've been many hours on the current path without any success so far!

Anyway, I'm starting to think that my new SSD may be faulty.  I'm having frequent errors doing basic things like setting up and formatting partitions.  Almost every time I do partition work using GParted, I get some sort of error, usually during formatting (eg most recently "mke2fs 1.41.14: warning, had trouble writing out superblocks").

I need to go away and find out how to do low-level hardware testing on my SSD so I can confirm or refute this (and have evidence to give to the Vendor if I have to return the SSD).

Cheers,

Rob Hills
Waikiki, Western Australia

---

### Post by rhills on 2012-02-22
Hardware checking is not looking good.

When I fire up Disk Utility, it recognises the drive manufacturer and model (OCZ Octane) but SMART status is "not supported".  If I try and run the benchmarking test, it fails immediately with:
> Error benchmarking: helper exited with exit code 1: Error reading 104857600 bytes at 104857600 from /dev/sda when guesstimating buffer size: Input/output errorI installed smartctl:[INDENT]sudo apt-get install smartmontools
[/INDENT]and then ran a background test:[INDENT]sudo smartctl -t short /dev/sda
[/INDENT]which it happily went away to do, however subsequent executions of:[INDENT] sudo smartctl --all /dev/sda
[/INDENT]simply return:
>  Vendor:               /0:0:0:0
Product:              
User Capacity:        600,332,565,813,390,450 bytes [600 PB]
Logical block size:   774843950 bytes
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
Following the advice given in the failure message, I ran:
[INDENT]sudo smartctl --all -T verypermissive /dev/sda
[/INDENT]which resulted in:
> Vendor:               /0:0:0:0
Product:              
User Capacity:        600,332,565,813,390,450 bytes [600 PB]
Logical block size:   774843950 bytes
>> Terminate command early due to bad response to IEC mode page

Error Counter logging not supported
Device does not support Self Test logging


So, I guess I need to trot off to the OCZ forum to find out what this all means.  It looks to me like some sort of major HW problem though, or am I missing something?

Cheers,
Rob Hills
Waikiki, Western Australia

---

### Post by Grenage on 2012-02-23
While it could be firmware, I'd probably get it replaced.  It doesn't sound particularly healthy.

---

### Post by oldfred on 2012-02-23
Another OCZ
Issues with OCZ Vertex II SSD and discard option
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

But sometimes it is BIOS settings:
BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

---

### Post by rhills on 2012-02-23
OK, when I work it out, I'll come back and let people know what was the solution and then mark the thread appropriately.

Meanwhile, for anyone following along at home, the discussion with OCZ starts [here]("http://www.ocztechnologyforum.com/forum/showthread.php?99343").

Cheers,

Rob Hills
Waikiki, Western Australia

---

### Post by Grenage on 2012-02-23
> **rhills said:**
> OK, when I work it out, I'll come back and let people know what was the solution and then mark the thread appropriately.

Meanwhile, for anyone following along at home, the discussion with OCZ starts [here]("http://www.ocztechnologyforum.com/forum/showthread.php?99343").

Cheers,

Rob Hills
Waikiki, Western Australia

Good luck. :)  For your info, I can pull up firmware information etc using smart controls such as:

```
sudo smartctl -i /dev/sdc
```

Which yields (on my Vertex):

```
=== START OF INFORMATION SECTION ===
Model Family:     SandForce Driven SSDs
Device Model:     OCZ-VERTEX3
Serial Number:    OCZ-V5O6IN059GSAV9KT
LU WWN Device Id: 5 e83a97 e3adb4745
Firmware Version: 2.15
User Capacity:    60,022,480,896 bytes [60.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ACS-2 revision 3
Local Time is:    Thu Feb 23 15:32:32 2012 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
```

I assume such a command fails as readily as the previous attempts on your drive.

---

### Post by rhills on 2012-02-23
Hi Grenage,

> **Grenage said:**
> Good luck. :)  For your info, I can pull up firmware information etc using smart controls such as:

```
sudo smartctl -i /dev/sdc
```


I had also tried the "-i" option but hadn't mentioned it.  I got the same result as I did for the other smartctl options.  It's good to see your example to know what I should have been getting.

Cheers,

Rob Hills

---

### Post by rhills on 2012-08-29
Much time has passed, but as detailed in [this thread on the OCZ forum]("http://www.ocztechnologyforum.com/forum/showthread.php?99343-Octane-128GB-on-Toshiba-T130-Ubuntu-11-10&highlight=rhills"), the problem ended up being due to a faulty SSD which has now been replaced under warranty.  Thanks to everyone for the assistance.

Cheers,
Rob Hills

---

