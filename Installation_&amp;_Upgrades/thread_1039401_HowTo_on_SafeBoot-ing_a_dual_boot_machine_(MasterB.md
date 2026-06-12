---
title: "HowTo on SafeBoot-ing a dual boot machine: (MasterBootRecords and Partition Tables)"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by gmoore777 on 2009-01-14
SafeBoot and DualBoot


1.	This is to document the workings of SafeBoot and how to add Ubuntu Linux as a second operating system to a Windows XP machine either before or after SafeBoot has encrypted the Windows partition. Some of the document is based on assumptions and surmising. On my machine, partition #2 will have Windows, and partition #3 will have Linux. I may have a few things not exactly correct in the boot up process, but the spirit of how it works is there. I have done this with both GutsyGibbon and HardyHeron Ubuntu Linux. Version of SafeBoot is 5.x.

2.	When SafeBoot is installed on a machine for purposes of encrypting the Windows partition, SafeBoot  copies the MasterBootRecord (MBR) including the partition table, the first 512 bytes of the hard disk, and puts it somewhere for safekeeping. My guess, it goes in the Windows partition under C:\ or C:\Windows.
(ToDo: If this was true, then I should be able to find this file. Find it. And what is its name? ) 
This MBR will be called “the original MBR” in this document, and will be loaded eventually.
SafeBoot lays down its MBR in the first 512 bytes of the disk with a current partition table. We will call this the “SafeBoot MBR”

3.	When the machine boots, it runs through its BIOS POST routines then loads and runs the MBR, the “SafeBoot MBR”. Per the SafeBoot Documentation: **“SafeBoot boot code then starts the transparent hard drive decryption process, and loads the ‘original MBR’ and executes it.”**

4.	If this ‘original MBR’ is a Windows MBR, then it will look at its attached PartitionTable, bytes 447-510, to see which of the 4 partition records is the bootable partition, then go searching in that partition for C:\NTLDR.exe, loads it and runs it. Then, NTLDR.exe loads C:\boot.ini and a user is given choices of operating systems to boot up (if there are 2 or more choices.). So on and so forth until Windows actually is loaded and running.

5.	If this ‘original MBR’ is an Ubuntu Linux MBR, or GRUB MBR, then when it loads, it will look at its attached PartitionTable, bytes 447-510, to see which of the 4 partition records is the bootable partition, then go searching in that partition for files, such as stage2, in the /boot/grub directory, loads and runs it. Then stage2 loads menu.lst and displays a section of this to user to choose between 2 or more menu items. So on and so forth until Ubuntu Linux (or other choice) is running.

6.	So let’s back up a bit. Let’s say Windows XP is installed on a machine and takes up the whole disk drive. Then say the IT department installs SafeBoot on it, then hands you the machine to install Linux on it. You put in the Ubuntu Linux LiveCD and run the install. Linux will see the partition and its size but will not identify it as a Windows partition(cause its encrypted) and therefore will not give you the slide rule to resize this partition. So you are done right there and will not be able to proceed.

7.	But let’s say, the Linux installation was able to resize the Windows partition, and then create its 2 partitions by default: one for Linux and one for the swap space. Linux would be editing the MBR, the SafeBoot MBR by first overwriting the first 446 bytes with stage1 of GRUB and then updating the partition table with the 2 new partitions. Upon reboot of the machine, the GRUB MBR will load, and then load stage2 and the menu.lst and you will make a menu choice and Linux will load and run. Everything is fine in regards to Linux.
Now if you were to edit /boot/grub/menu.lst to add a Windows entry to make this machine dual boot able, with this entry:
title           Microsoft Windows XP Professional
root            (hd0,1)	
savedefault
makeactive
chainloader     +1

and then choose “Microsoft Windows XP Professional” when the GRUB menu is displayed, you will see an error message such as:
		“ Error 13: Invalid or unsupported executable format”

This is because, that partition #2, the Windows partition as mentioned in the above,  “root            (hd0,1)”, is still encrypted, cause the SafeBoot MBR was clobbered by the Linux installation and therefore the SafeBoot hard drive decryption process was never run. So the stage2 GRUB was not able to find and load C:\NTLDR.exe. So you have a great Linux machine but the Windows partition in not bootable. 
At this time, you would need to give your machine to the IT department to try and “recover” the MBR by laying down a SafeBoot MBR. I can not confirm  this can result in success. In theory, it should be recoverable, but our IT department could not bring the Windows partition back to life, we started from scratch again, by reformatting disk and reinstalling Windows and SafeBoot.

8.	Let’s start again, and do this a bit better. We will first have a machine with Windows on it, but be sure to have an empty partition for the eventual installation of Linux. Then say the IT department installs SafeBoot on it, then hands you the machine to install Linux on it. You put in the Linux LiveCD and run the install. Linux will see the partition and its size but will not identify it as a Windows partition(cause its encrypted) and therefore will not give you the slide rule to resize this partition. This is expected and OK. Luckily Linux sees the empty partition, and you can choose “Guided – use the largest continuous free space”. It will use the empty partition that we created in the beginning, for this very purpose.

9.	
When we get to the final window where it is ready to install there is an “Advanced Button”. Keep the box checked off next to “Install boot loader”, but change the device from (hd0) [which represents /dev/sda and the MBR of the hard disk] to (hd0,2) [which represents partition #3 on hard disk #1]. 
After the Linux installation we have managed to have preserved the SafeBoot MBR, and we also have a GRUB MBR (in the first 512 bytes of partition #3) from which to leverage.
Copy this GRUB MBR to a file via this command in a Linux window:

sudo dd if=/dev/sda3 of=/tmp/mbr_sda3.bin bs=512 count=1

Copy mbr_sda3.bin to a memory stick or floppy for later use. (the name of the file is not significant.)
You may need to `sudo chmod 777 mbr_sda3.bin` in order to copy it.

So although this Linux installation did not clobber the SafeBoot MBR, it did edit the partition table with the 2 new partitions and this is a problem. It toggled the boot flag in the partition table to make partition#3 (Linux) the boot partition, and untoggled the boot flag for the Windows partition, partition #2.

If the partition table is left as is, when user reboots machine, the SafeBoot MBR will be loaded, the SafeBoot boot code starts the transparent hard drive decryption process, and tries to find and load the ‘original MBR’. But it can’t. It now goes to partition #3, the Linux partition, to try and find the ‘original MBR’ that it had saved off. The error that you will see on a black screen is:
	Resetting hardware…
	Starting operating system..
	Error loading operating system.

So lets fix this either now after the Linux installation before we reboot, or after, using the LiveCD again, but we need to be able to run some commands.

`sudo cfdisk –P s`  # will print out the MBR’s partition table. Note which partition is the default boot one.
`sudo cfdisk`  # Will run a primitive console window: Arrow down to the Linux partition and hit “b” to toggle it from boot to none. Arrow down to the Windows partition and hit “b” to toggle it from none to boot. Hit “W” to write this out to the MBR. Hit “q” to quit.

Reboot. The SafeBoot logon will appear. After that, Windows will boot.

Copy mbr_sda3.bin from memory stick to C:\.
Then, edit C:\boot.ini file:
Start-->ControlPanel-->System-->Advanced-->Settings-->Edit
Ensure the option Time to display list of operating systems is ticked and select a delay time.

Add the following line:
c:\Windows\mbr_sda3.bin="Ubuntu Linux"

Reboot. The SafeBoot logon will appear. After that, user will get black screen with 2 choices: Windows or Linux to boot up. Choose Linux. The GRUB boot loader will then be run and load Linux kernel.

Now if you were to edit /boot/grub/menu.lst to add a Windows entry to make this machine dual boot able, with this entry:
title           Microsoft Windows XP Professional
root            (hd0,1)	
savedefault
makeactive
chainloader     +1

and then choose “Microsoft Windows XP Professional” when the GRUB menu is displayed, NTLDR.exe will be found and loaded by GRUB, cause the SafeBoot hard drive decryption process was run upon bootup with the preserved, unclobbered SafeBoot MBR. 

Done.

10.	Now lets change the order of installations.
Lets say, you already have a machine that is dual boot with both Windows and Linux. Windows was installed first, then Linux, choosing defaults. So the MBR is a GRUB MBR.
The IT department takes machine and installs SafeBoot on it, and encrypts the Windows partition.
SafeBoot saves off the GRUB MBR and installs its own MBR.
Everything will work with no further edits to anything.

Upon boot up, the SafeBoot MBR is loaded and runs the hard drive decryption process, then loads the ‘original MBR’ which is a GRUB MBR, and GRUB using the partition table that was saved off with it, will look in the bootable partition, partition #3 for the stage2 GRUB and so on and so forth.
The menu.lst, would already have had the lines in it by you from when Linux was originally installed:
title           Microsoft Windows XP Professional
root            (hd0,1)	
savedefault
makeactive
chainloader     +1
and Windows would boot up if this menu item was chosen, cause GRUB could find the NTLDR.exe since the SafeBoot hard drive decryption process was run upon bootup.
Done.

---

### Post by xflyboy on 2009-04-29
Thank you for good guide.
I installed my linux without first reading about this SafeBoot thing. Though completely loosing my configuration. Tried to recover my SB MBR and couldn't.

Now, you also can see [THIS]("http://blog.nixpanic.net/2008/06/starting-safeboot-with-grub.html") to Start SafeBoot with GRUB.

Regards. Max.

---

### Post by jwhendy on 2009-10-22
Sorry to dig up such an old post, but it's one of the few with knowledgeable posting about SafeBoot and applies to my situation.

Your 'HowTo' seems more like a 'what does or does not work', though. If I'm reading things right, your 'how to' basically says that the only way to dual boot with SafeBoot is to either have:

- a drive with windows and a free partition
- a drive with windows and linux already installed and then SafeBooted

Is this correct?

I don't know why my IT department would give me a machine in those conditions... they gave me a laptop with Windows on the whole drive and it's SafeBooted with v5.1 or so.

Is there any hope to make it dual boot?


Thanks!
John

---

### Post by gcbzzzz on 2010-03-15
my case:

1. got the laptop with windows. no safe boot
2. installed ubuntu. dual boot OK.
3. the windows IT update thingy installed safe boot.
4. dual boot ok.
5. ubuntu upgrade it kernel and rerun grub-mkconfig
6. dual boot not ok. I can only boot into ubuntu


how to I restore the windows part? do grub keep a backup of the previous files?

---

### Post by jwhendy on 2010-03-17
Eeeks.

Did you make a backup of your Win boot sector first? The key instructions above (for me) were to do this:

```
sudo dd if=/dev/sda1 of=/safe/location/mbr_sda1.bin bs=512 count=1
```

Then when I botched my safeboot a couple times, I was simply able to do the 'reverse' and execute:

```
sudo dd if=/safe/location/mbr_sda1.bin of=/dev/sda1 bs=512 count=1
```

This fixed things up. Without a backup of that initial safeboot sector, I think your not going to be able to get anywhere without a safeboot disk or someone in IT. There's just no way to restore it that I know of within your means. This is the kind of the point of safeboot -- if things get tampered with, you lose the data before you're able to fix it.


John

---

### Post by f1r3br4nd on 2010-07-09
> **gmoore777 said:**
> SafeBoot and DualBoot
10.	Now lets change the order of installations.
Lets say, you already have a machine that is dual boot with both Windows and Linux. Windows was installed first, then Linux, choosing defaults. So the MBR is a GRUB MBR.
The IT department takes machine and installs SafeBoot on it, and encrypts the Windows partition.
SafeBoot saves off the GRUB MBR and installs its own MBR.
Everything will work with no further edits to anything.

Upon boot up, the SafeBoot MBR is loaded and runs the hard drive decryption process, then loads the &#8216;original MBR&#8217; which is a GRUB MBR, and GRUB using the partition table that was saved off with it, will look in the bootable partition, partition #3 for the stage2 GRUB and so on and so forth.
The menu.lst, would already have had the lines in it by you from when Linux was originally installed:
title           Microsoft Windows XP Professional
root            (hd0,1)	
savedefault
makeactive
chainloader     +1
and Windows would boot up if this menu item was chosen, cause GRUB could find the NTLDR.exe since the SafeBoot hard drive decryption process was run upon bootup.
Done.

Okay, but supposing after SafeBoot is installed I install a kernel upgrade, change some of the options for menu.lst, or in some other way change GRUB. Will this blow away the SafeBoot MBR or cause SafeBoot to stop loading the 'original' GRUB MBR?

Would like to know, since I fiddle with my GRUB options quite a bit. Thanks.

---

### Post by jwhendy on 2010-07-09
@1r3br4nd:

I'm pretty sure the answer is yes. You can use my method (right above your post) to make a backup of your MBR and try it, but as far as I've been able to tell from researching this with my own computer, SafeBoot encrypts the entire MBR, on which grub data resides. If you change it, SafeBoot becomes corrupt.

The only situation seems to be to get whatever you want there *first*, prior to activating SafeBoot and letting it do its thing.

Make sense?

Since I was using a work computer... I gave up, said screw it, and just installed Linux right over the top of everything. I gave up dual boot, but it was much better than running Linux from an 8gb flash drive...

---

### Post by f1r3br4nd on 2010-07-11
Thanks for your reply jwhendy.

I guess what I'll need to do before returning my laptop to the IT department for SafeBoot install is to back up GRUB and then set it to default to Windows with a wait-time of 0. Then, after I get the laptop back, I can back up the SafeBoot MBR, restore GRUB, have GRUB go to the SafeBoot MBR when Windows is needed, which will in turn call up the old GRUB MBR but it will be transparent because it will default to Windows with a wait-time of 0.

Of course this would be even cooler if I could configure GRUB to choose between Windows and *another* GRUB instance that lives on a different partition where I can edit it freely without damaging the SafeBoot MBR. Unfortunately, I don't know the commands to make GRUB load another GRUB. Does anybody?

---

### Post by oldfred on 2010-07-11
With safeboot can you boot an USB key or does it prevent that?

I installed grub2 to my USB key to boot ISOs but manually added an entry to boot my install in sdc7.

Boot most up2date Lucid kernel on sdc7
menuentry "Lucid on sdc7" {
    set root=(hd1,7)
        linux /vmlinuz root=/dev/sdc7 ro quiet splash
        initrd /initrd.img
}

I also have a old grub partition with menu.lst chainbooting some other grub legacy installed in the partition boot sector. Grub2 does not like to be installed to a partition boot sector.

old grub entry Chain to MBR of sdc, I have done it with grub2 also:
title       Ubuntu 9.10 Karmic 64 bit @ sdc
root        (hd2)
chainloader +1

---

### Post by jwhendy on 2010-07-11
@f1r3br4nd:

It's not clear what you're looking to do... have grub but have it go right into Windows? Are you just going to put your Linux partition as a boot option in the Windows bootloader, then? I've done both (default to Win, then have an option for either Win or Linux as well as default to Grub, then have an option for Win or Linux...).

In typical Linux distros during installation I've seen an option to install the bootloader to the root partition vs. to the MBR. I'm not familiar with that at all but am sure Ubuntu has documentation somewhere.

@oldfred:

Re. usb stick... YES!!! This is how I ran Linux on my work computer for some time. For a complete write up, see my wiki entry on the [ZenWalk Wiki]("http://wiki.zenwalk.org/index.php?title=Bootable_usb_flash_drive#Compiling_a_USB_bootable_kernel").

It seems you just want it to boot grub on the usb key and use that to boot into another partition on the actual HD? Not so sure about that.

If you actually run Linux from a USB key, do yourself a favor and get a good one. I bought a SanDisk Cruzer 8GB from Walmart for $20 and it was absolutely horrible. I spend $27 on Amazon for a OCZ Rally2 and it was phenomenally different. The key is in the write speeds. My OCZ was somewhere around 11-15MB/s compared to like 2MB/s for the SanDisk.

Hope that helps...

---

### Post by f1r3br4nd on 2010-07-11
> **jwhendy said:**
> @f1r3br4nd:

It's not clear what you're looking to do... have grub but have it go right into Windows? Are you just going to put your Linux partition as a boot option in the Windows bootloader, then? I've done both (default to Win, then have an option for either Win or Linux as well as default to Grub, then have an option for Win or Linux...).


I want the first GRUB menu to offer a choice between Windows and Other.

If I choose 'Other', I want to be taken to a *different* GRUB instance that offers me the usual choice of available kernels and memory test.

This way, whenever I upgrade my kernel, or install an additional distro in another partition, or mess with the boot options or whatever, only the second GRUB MBR gets changed. The "top level" one, where I choose between Windows and Other never changes. This is necessary because once SafeBoot is installed, it will apparently make a hidden copy of whatever MBR was in place before it got installed and always go to that MBR after I log in.

In other words...

SafeBoot (never changes)
[INDENT]-> GRUB #1 (Windows or Other, never changes)
[INDENT]-> Windows
-> Other (GRUB #2, various kernels, can change freely)
[/INDENT][/INDENT]
Does that make sense?

---

### Post by jwhendy on 2010-07-11
Totally makes sense. The USB or Grub on root might be your best bets for that? Grub #1 on MBR, SafeBoot over the top of it... Grub #2 on /?

I posted a link to some potentially helpful info on my Zenwalk Wiki entry.

For grub on a disk partition vs. MBR, maybe check here (just some quick searching I did; some are outdated but might still offer some leads?):
- [http://ubuntuforums.org/showthread.php?t=282702](http://ubuntuforums.org/showthread.php?t=282702)
- [http://ubuntuforums.org/showthread.php?t=228104&highlight=gui+grub+configurator](http://ubuntuforums.org/showthread.php?t=228104&highlight=gui+grub+configurator)
- *[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)
- [http://linux.ioerror.us/2006/01/where-should-you-install-grub/](http://linux.ioerror.us/2006/01/where-should-you-install-grub/)

Good luck!

---

### Post by oldfred on 2010-07-12
Herman has instructions for both grub & grub2 dedicated partitions. The safeboot only controls the MBR not the grub menu. So I think you just need a permanent grub partition that the MBR boots to. Then you can edit the menu at will.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

If you are doing this you are doing a total work around and defeating the entire purpose of safeboot. Why keep safeboot or is that company policy and yet they will let you install Ubuntu? It would be easier if you have multiple drives so you have additional MBR's to chainload into. Old grub legacy is ok with install to a partiiton PBR but grub2 says it may be unreliable to install grub2 to a PBR.

---

### Post by f1r3br4nd on 2010-07-12
> **oldfred said:**
> 
If you are doing this you are doing a total work around and defeating the entire purpose of safeboot. Why keep safeboot or is that company policy and yet they will let you install Ubuntu?

Yup! You guessed it. If a laptop comes pre-installed with Windows, it has to get SafeBoot installed on it, even if I have no intention of using Windows.

For what it's worth, the Linux side is installed on a LUKS encrypted LVM group, so it's not as if I'm bypassing encryption altogether.

---

### Post by f1r3br4nd on 2010-07-12
> **oldfred said:**
> Herman has instructions for both grub & grub2 dedicated partitions. The safeboot only controls the MBR not the grub menu. So I think you just need a permanent grub partition that the MBR boots to. Then you can edit the menu at will.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)


Thank you for the helpful link. One thing I find confusing is the part about mounting the partition in /media/grub2 rather than in /boot. Does this mean that I have to make sure the new partition always gets mounted as /media/grub2, or only when I am installing GRUB2? What happens to the existing /boot and /boot/grub directories on the root file system?

When I installed Ubuntu (using the alternate install CD) I chose a small primary partition to be mounted as /boot and /dev/sda as the location of the MBR. Does this mean that in following Herman546's instructions I should just use --root-directory=/ or even omit the root directory altogether?

---

### Post by oldfred on 2010-07-12
I think Herman was just talking about mounting it as /media as that is to copy data to it.

I created my grub legacy partition while ago and forgot all the details. I originally was creating a separate /boot partition can copied everything from /boot to the partition. Then I decided I really only wanted a grub partition and put the files in /grub. I then went back just for consistency put the grub files into /boot/grub. Each time I moved things around I had to reinstall grub to the MBR so it could correctly find the location of the rest of grub's files.

I did see one user accidentally delete his grub parititon. Without changing MBR he was able to recreate same partition and put the grub (legacy) files  back and it worked. I was surprised it worked.

---

### Post by coogur on 2011-01-10
My apologies for reviving the discusion ..

My objective (as most other people) with getting Linux working on the work laptop with SafeBoot-activated Windows is to replace my personal computer which hosts Linux – to leverage the laptop's (better) hardware and PORTABILITY yet keep separation between work and play on the only laptop HD. 

 My options are as follows:
 
[LIST=1]
[LIST=1]
[LIST=1]
[*]Boot Linux using USB or live-CD 			(Ouch!!)
[*]Use Windows to X-remote to my 			personal computer (Inter-net ssh, or local-net)
[*]Virtual-ize Linux over Windows 			(eesshhhh!)
[*]Dual-boot Windows and Linux 			(Yeah Baby! Yeah!)
[/LIST]
[/LIST]
[/LIST]
 

 USB-LiveCD has confirmed is slow and I would have limited space for data storage (SafeBoot encrypted the Windows partition) so not really usable, of course I could have an external USB drive but again slow and not really a good solution and defeats the purpose.  Using Windows to remote to personal computer is acceptable however; will not achieve replacement of personal computer with work laptop.  Virtualize Windows maybe an acceptable alternative however; I would like to continue researching the last option of dual-booting with SafeGuard in place, which from what I gather from all of this is “near impossible”, everthing IS possible in the world.
 

 Our work policy is to install Windows (one partition taken the full drive!!) and then the activation of SafeBoot for laptops.  IT will not create an empty space at the end of the drive prior to activating SafeBoot (I asked!), this leaves me with only one bootable NTFS partition (original MBR), and encrypted by SafeBoot (and SafeBoot MBR).
 

 Can we resize with Windows running without a reboot? WinPE etc?  PartitionMagic or like requires a reboot to complete resizing a partition.  Does these software mock-up with the MBR?  Backup a copy, then overwrite the partition bootable code with there own, reboot, do it's work and restore the backed up MBR and original bootable partition code?
 

 In any case, if we tamper (resize) with the NTFS bootable partition and make any necessary corrections to the MBR and bootable partition area, we would need to make the same corrections to both the SafeBoot and original MBRs – which is unreadable (encrypted?) to make it boot to complete the resizing.  Has someone been able to achieve this?
 

 I assumed that without re-running SafeBoot afterwards – the existing SafeBoot MBR would not be able to decrypt the partition right - as it was changed?  Also, I assume that the current setup of SafeBoot MBR must only be able to decrypt the entire partition that was initially setup before activation (prior to resize), further to the point, it must have stored the partition start and end block and does integrity checking via digital signature and-or decryption would fail preventing the boot process?  If that is the case, I'm shot in the waters and back to square one.

---

### Post by brain salad surgery on 2011-03-30
Just wanted to know why this does not work:  [http://blog.nixpanic.net/2008/06/starting-safeboot-with-grub.html](http://blog.nixpanic.net/2008/06/starting-safeboot-with-grub.html)  when trying to boot windows, I get:  safeboot has been corrupted error 92h  I followed the steps...  Thanks

---

### Post by jwhendy on 2011-03-30
@brain salad surgery:

Need more details. What's your fdisk -l output. What's in menu.lst? The blog post seems to be booting a safeboot disk from a linux partition on the disk in sda6. If you just "followed the steps", we don't know what else you have on sda, what partitions you've used for what, etc.

Does that make sense? Please specify how the disk was partitioned, when safeboot was invoked (over a linux partition or only on the windows partition, etc.), and how you've setup grub.

If all else fails, you can just restore from the backup of the boot sector.

```
# dd if=/path/to/safeboot.mbr of=/dev/sda bs=512M count=1
```

For any others still checking posts, I'm getting a new company laptop soon and hope to try the following:
- perform a "live" cloning of my Win system while it's running, which will create an un-encrypted copy
- attempt to boot from that partition on another computer to ensure that it's bootable
- if successful, repartition my disk for both win and linux
- restore from my windows backup to an encrypted partition using something like TrueCrypt or otherwise
- install linux to another partition using dm-crypt/LUKS
- use grub to boot everything

I don't know exactly how this will work yet, but if making a bootable clone of Windows is possible... I should very well be able to find someway to have both living as encrypted partitions on my laptop. I'll post back when I attempt this. So... while you can't dual boot with safeboot, you might just be able to clone what's on there, wipe the disk, and put back both what was on there and linux next to it and have them both encrypted... just not with safeboot but with something open source.

---

### Post by brain salad surgery on 2011-03-30
Hi,  I found that I needed to map hd0 to hd1 and vice versa because I installed grub on the sd card from which I boot a linux system.  It works very well, very fast and all... sometimes I don't even see the point to install linux on the hard drive.  The only thing is that I cannot mount the windows partition and use its free space for data, but that's why external drives have been invented, isn't it ??  What you propose is very interesting (and painful) indeed !  Let me know what tool(s) you use if successful.  I am not sure about a live copy of windows (some files wouldn't accessible, i think).  Anyways, i prefer not messing up with my employer's system.  You should probably switch the hard drive to be precautious.  To conclude, I wish my employer would switch to open source encryption products instead of that stupid Mcaffee safeboot  Thanks

---

### Post by jwhendy on 2011-03-30
@brain salad surgery:

,---
| ...sometimes I don't even see the point to install linux on the hard drive. The only thing is that I 
| cannot mount the windows partition and use its free space for data, but that's why external drives 
| have been invented, isn't it ?
`---

I was doing the same for a while, except from a USB flash drive. I just got tired of it, especially with not being able to share information between the two, as you mentioned.

,---
| What you propose is very interesting (and painful) indeed! ...I am not sure about a live copy of 
| windows (some files wouldn't accessible, i think).
`---

Now that I'm not sure I agree with :) I think it will be pretty painless, just time consuming waiting for all that copying around and verification. I think that a live copy should be possible. I use [Carbon Copy Cloner]("http://www.bombich.com/") on my Mac and it's running when I make the copy... nevertheless, it's bootable. I'm hoping something similar exists for Windows, and I will definitely report on the tool suses.

,---
| Anyways, i prefer not messing up with my employer's system. You should probably switch the 
| hard drive to be precautious. To conclude, I wish my employer would switch to open source 
| encryption products instead of that stupid Mcaffee safeboot 
`---

This is a concern of mine as well. My current company-issue laptop is the one I used a USB drive on for a while. Then I just decided that I'd wipe windows completely and install linux over the top, which I did. I no longer have anything they issued on my laptop. I have a desktop with windows for CAD and this has come in extremely necessary at times for windows compatibility using Lotus Notes and/or Powerpoint or the like. I'm really glad I have it which is why I really want my dual-boot experiment to work.

My linux install is encrypted, so I figure I'm going my due diligence to be careful about it. I work for a company with 70,000 employees world wide; when they take my old computer very soon, I'll let you know if they comment on the linux install. While I'm sure they don't necessarily approve, the benefit to a large company is that it's probably a fairly low-powered IT employee who does the actual work of replacing computers around the entire company. He won't really care. And if he has a standard procedure for simply taking old computers, wiping the drives right away, and then putting them in a box to be shipped off to be recycled... who cares?

Nevertheless, linux isn't worth losing my job! I have talked to a fairly high up in IT and mentioned to him what I did and he's never objected strongly, only inserted comments about recommending proper licensing and that I run clamAV on it.

There's some rambling for you -- sounds like we might be in similar situations!

---

### Post by jwhendy on 2011-04-20
Success! I got my new computer, as expected, and just finished setting everything up. My plan didn't end up going exactly as I thought -- in fact, it ended up quite a bit better. I ended up with the following setup:
- Partition 1: Windows 7, exactly as my company provided it, only shrunk (encrypted with SafeBoot)
- Partition 2: Linux /boot (64M)
- Partition 3: Linux encrypted with LUKS/dm-crypt (30G)
- Partition 4: TrueCrypt device for sharing files between the two OSs

The advantage to this setup is primarily that it involved nothing risky in terms of the pre-installed company stuff. I used all Windows 7 tools to accomplish my ends. Many suggestions about how to manage dual-booting with SafeBoot pre-installed involve using dd to copy the entire encrypted partition away, re-partition, and then dd everything back, which I find quite scary, even if there's nothing much to it other than a few commands.

Since this is a company laptop, I just wasn't going to risk messing it up, hence my desire expressed above to make a decrypted clone, verify that everything was going to work on another computer, and only then taking the plunge on the real-deal!

Anyway, I wrote up my method on the Arch Linux wiki [HERE]("https://wiki.archlinux.org/index.php/Dual_boot_with_Windows_when_SafeBoot_is_installed").

Let me know if you have any comments, corrections, or questions! I hope this helps someone!

---

### Post by sbrbot on 2011-04-20
Recently I got new company notebook with preinstalled Win7. I shrinked the only primary partition where Win7 resides and created 3 additional primary partitions. Afterwards I installed Ubuntu on third partition with GRUB in MBR and created second partition as TrueCrypt partition used by TrueCrypt software from both OSes. So my partitions (partition table in MBR) now are:

* 1st primary partition for Win7
* 2nd primary partition for TrueCrypt
* 3rd primary partition for Linux
* 4th primary partition for Linux swap

So I have fully functional dual-boot machine with Win7 and Ubuntu and GRUB boot loader in MBR.

But Company IT now intends to install McAffee Endpoint Encryption (EE)!!!

According to your first post, EE will copy current GRUB MBR on some place and replace it with EE encrypted MBR with its own boot loader. During POST encrypted EE should be loaded with its driver for decryption, encrypted partition table will be read and EE bootloader will proceed with loading previous GRUB MBR. Since EE boot loader is booted first and decryption is enabled, that should result that both systems are able to load again!

Is that correct?

---

### Post by jwhendy on 2011-04-20
@srbot:

Perhaps the original poster will respond as well, but I haven't seen him in a while. I don't know what this will do... but don't think it will be good. I thought EE was full disk encryption, in which case everything will get encrypted over.

If that's the case, I'm not sure how you can boot into Linux, since you need EE to decrypt that partition for you. EE is on-the-fly-encryption, so it's constantly decrypting things as you're accessing them, thus (as it's a Win program), I'm not sure it would work so hot for Linux.

I could be wrong and would love to be corrected on this.

If it were me, I'd make a backup of any necessary files on both Ubuntu and Truecrypt partitions, prepare for the worst and expect that you'll get back either:
1) a computer with 1 partition using EE (they'll eliminate your other partitions), or 
2) an encrypted system with a usable Win partition and unusable partitions 2, 3 and 4

In either case, you might be up for re-installing.

If that happens, follow my Arch Wiki post [HERE]("https://wiki.archlinux.org/index.php/Dual_boot_with_Windows_when_SafeBoot_is_installed"), copy your important files back, and you should be fine.

I'll say that I *hope* it's otherwise for you (that Linux and TC still work), but in the interest of time, I'd definitely make backups before you have to surrender this.

One question... do they know, and will you be telling them that Linux is installed? If not, assume that they'll treat it as simply "foreign stuff" and get rid of it, returning back a laptop in company-issued shape.

---

### Post by sbrbot on 2011-04-20
> **jwhendy said:**
> 
Perhaps the original poster will respond as well, but I haven't seen him in a while. I don't know what this will do... but don't think it will be good. I thought EE was full disk encryption, in which case everything will get encrypted over.

Original poster stated in bullet [10] that it should work! I need somebody's else confirmation.

> **jwhendy said:**
> If that's the case, I'm not sure how you can boot into Linux, since you need EE to decrypt that partition for you. EE is on-the-fly-encryption, so it's constantly decrypting things as you're accessing them, thus (as it's a Win program), I'm not sure it would work so hot for Linux.

I could be wrong and would love to be corrected on this.

If it were me, I'd make a backup of any necessary files on both Ubuntu and Truecrypt partitions, prepare for the worst and expect that you'll get back either:
1) a computer with 1 partition using EE (they'll eliminate your other partitions), or 
2) an encrypted system with a usable Win partition and unusable partitions 2, 3 and 4

In either case, you might be up for re-installing.

If that happens, follow my Arch Wiki post [HERE]("https://wiki.archlinux.org/index.php/Dual_boot_with_Windows_when_SafeBoot_is_installed"), copy your important files back, and you should be fine.

I'll say that I *hope* it's otherwise for you (that Linux and TC still work), but in the interest of time, I'd definitely make backups before you have to surrender this.

However, I'll make backup copies before proceeding with EE! Actually IT department will push EE automatically via group policies on my next Windows active directory logon.

> **jwhendy said:**
> One question... do they know, and will you be telling them that Linux is installed? If not, assume that they'll treat it as simply "foreign stuff" and get rid of it, returning back a laptop in company-issued shape.I already told them about my Linux, I could have tried to hide GRUB but they are not stupid. They already started with "...this is against company security policy... blah, blah" you know how it goes. But I said that I needed Linux for some professional needs.

---

### Post by jwhendy on 2011-04-20
@sbrbot:

Well, not sure. I guess I'm just suggesting that no one may know, as this post was created over a year ago.

Do post back and let us know!

---

### Post by sbrbot on 2011-11-04
I'm glad you did not forget about this post because this issue is important to me! I just intend to proceed with this EE monster. Until now I did not have enough time to deal with this problem and I avoided installing it but now it time. I will send soon what happened.

---

### Post by jwhendy on 2011-11-04
Awesome -- let me know how it goes!

---

