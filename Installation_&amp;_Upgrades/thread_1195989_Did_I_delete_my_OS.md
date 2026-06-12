---
title: "Did I delete my OS?"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by PartsMan on 2009-06-24
PartsMan here. First off I am a total newb to linux.

Loaded 8.04 on a Dell 2400 that was given to me after I cleared the hard drive.

Everything was working fine so I decided to mess with it.

Tried to do my first partition. Made a partition of the last 60g of my 80g hard drive leaving the first 20 "unalocated".

Now when I turn on the computer I get.

Error 17

How do I go about fixing this?

---

### Post by izizzle on 2009-06-24
Take a look [HERE]("http://ubuntuforums.org/showthread.php?t=442945").

---

### Post by raymondh on 2009-06-24
> **PartsMan said:**
> PartsMan here. First off I am a total newb to linux.

Loaded 8.04 on a Dell 2400 that was given to me after I cleared the hard drive.

Everything was working fine so I decided to mess with it.

Tried to do my first partition. Made a partition of the last 60g of my 80g hard drive leaving the first 20 "unalocated".

Now when I turn on the computer I get.

Error 17

How do I go about fixing this?

Let me try to 'visualize' this ..

You installed 8.04 and then partitioned " the last 60GB of my **80GB hard drive**".... if so, and the partitioning was successful, you have written over the 8.04 install.

If that is right ..... time for a new, fresh installation.

Some links for reference

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Good luck.

---

### Post by PartsMan on 2009-06-24
By leaving the first 20g unalocated I deleted it?

Can I load back to the first part or just the 60g partition?

---

### Post by raymondh on 2009-06-24
Hello Partsman,

I'm going by this sentence

```
Made a partition of the last 60g of my 80g hard drive leaving the first 20 "unalocated"
```

Ubuntu file system (root) will install on the first available part of the drive or partition. When you installed 8.04, it may have been in front of the drive (which is now Unallocated when you partitioned afterwards). 

Leaving it unallocated means leaving it blank/epmty.  The only way to preserve a partition is to NOT format it.

Boot into the liveCD and in Live Session (TRY WITHOUT CHANGING ANYTHING) > system > administration > partition editor (gparted).  Look at the output.  If you wish, take a screenshot (applications > accessories) and post/load it here.

---

### Post by raymondh on 2009-06-24
> **PartsMan said:**
> 
Can I load back to the first part or just the 60g partition?

You can choose where to install ubuntu when you get to the partitioning stage of the installer.  For this, you will have to choose MANUAL.

At this stage ... how do you plan to use your system?  Do you plan to dual-boot with another OS or Do you plan to just single boot ubuntu?  Do you intend to load a lot of media files?  If indeed loading a lot of media files, you may run out of space soon in a 20GB partition if your files are big or plentiful.

You can also install on the 60GB partition and keep the first 20GB as extra space for anything you wish.  Keep in mind though that the bootloader (GRUB) will be in the 60 GB partition unless you plan to create a separate boot partition.  If you have an older BIOS' and systems, there is a cylinder limit where the BIOS will only go as far into the HD (starting from the front) to detect an OS before looping back hence give you booting errors later on. 

I certainly don't want to give you any FUD.  I'm just sharing with you my installation experiences (and it's pros and cons) to help you decide how/where to proceed to suit you best.

Good luck and happy Ubuntu-ing.

---

### Post by jimv on 2009-06-24
HOLD ON, don't listen to any of these guys...yet.

Did you resize your Ubuntu partition to free up the first 20 gigs?  If that's the case, then you're fine.  Your UUID for the Ubuntu partition changed when you resized it and you just need to fix a few things.

First, boot up from a Live CD.
Second, once you're booted, open a terminal.
Type this:

```
cd /media/disk/boot/grub
sudo blkid
```

This will show a list of long strings like this:

```
/dev/sda1: UUID="**d7b1bede-f719-4e0e-8e90-89057be371c3**" TYPE="ext4" 
```Look for the one that says EXT3 or EXT4 at the end.  Copy this string (the part between the quotation marks...I bolded it so you can see what I'm referring to) by highlighting at, and then right-clicking it and clicking Copy.

Then type this in the terminal:

sudo gedit menu.lst

This will open the menu for Grub....scroll down until you see a section like this:

```
title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        **d7b1bede-f719-4e0e-8e90-89057be371c3**
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=**d7b1bede-f719-4e0e-8e90-89057be371c3** ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet
```It should be near the bottom.  Where it says "uuid", delete the string that is there and paste the one that we copied.  Do the same thing for the line that says kernel.  The lines should then look like this:

```
uuid        **some-long-string**
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=**some-long-string** ro quiet splash
```Save the file and reboot.

Once you are booted into Ubuntu, run these two commands:

```
sudo mv /boot/grub/menu.lst /boot/grub/menu.old
sudo update-grub
```

---

### Post by raymondh on 2009-06-24
You're right Jim ... 'did not think about the OP possibly resizing.  I was thinking he created 2 partitions by deleting and then creating the 60GB.

@ partsman, if you did resize, then editing the menu.lst is your first choice of action.  My apologies for possibly confusing you.

---

### Post by PartsMan on 2009-06-25
Wow thanks for all the help. 

I only wish I could have seen it last night. :( 
Using computer at work for net until I get this thing going.

Was able to boot with the CD. Fixed my partition error and made a 20g and a 60g. Opposed to a 60g with a 20g blank spot in front of it.
Then when I tried to load Ubuntu on the 20g. Ubuntu would not let me. 
Said that their was not enough room. ???.
I went ahead and let it load on the whole disc. Everything worked fine.
Then went to partition manager and warned me that I would erase the drive if I partitioned.

I just wanted to keep my documents separate from my OS. 
For the trouble it has caused me I should just buy another HD.

---

### Post by philcamlin on 2009-06-25
hmm tough luck i would go get a new hard drive their cheap these days :P

---

