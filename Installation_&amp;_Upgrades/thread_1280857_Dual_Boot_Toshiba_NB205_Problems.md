---
title: "Dual Boot Toshiba NB205 Problems"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by PherricOxide on 2009-10-02
I'm attempting to dual boot a Toshiba NB200/NB205 netbook with Windows XP and Ubuntu Netbook Remix. I shrunk the main Windows XP partition and left the recovery partition alone. Then I created a new partition and installed Ubuntu to it. 

Ubuntu is working great, but now Windows XP will no longer boot. The option is available in the Grub menu, which then leads directly to the XP Safe mode/Normal mode menu. It seems to skip XP's own bootloader, even though the chainloader option is enabled.

The problem is, XP will begin booting, the little blue loading bar will go across almost once, and then it will BSOD and reboot. I'm unable to enable logging to even get a dump of the BSOD even though I can access the Windows partition in Ubuntu.

Attempting to use the recovery partition also failed due to the following errors,
"Windows cannot find C:\Bin\ErrorDialog.exe"
"Windows cannot find C:\BootPriority.exe"

Since I can not access the recovery partition and do not have recovery CDs, I'm basically unable to reinstall XP. Does anyone have any ideas of what to try?

---

### Post by PherricOxide on 2009-10-02
Update,

I managed to get it to stop rebooting long enough to see the error. Which was, 

STOP: 0x00000024 (0x00190203, 0x85BD2490, 0xC0000102, 0x00000000)

Which apparently translates into,

This issue can occur if a problem occurred within the Ntfs.sys file. The Ntfs.sys file is the driver file that enables your computer to read and write to NTFS partitions. Damage in the NTFS file system, damaged portions of your hard disk, or damaged SCSI or IDE drivers can also cause this issue.

I'm thinking Gparted somehow corrupted the NTFS partition? I think CHKDSK might fix the problem, but I'm having trouble running it without a CD drive.

---

### Post by lrcaballero on 2009-10-02
Hi there,

I just helped a friend that also had a partition problem. Windows 7 would't boot up but it would show in the GRUB, Reinstalled Windows 7 then installed a program called Partition Wizard for Windows 7, also available for XP and Vista and then installed Ubuntu and as default you know that Ubuntu will take care of the partition as you indicated..... Hope this can help, GOOD LUCK......:lolflag:

Luis

---

### Post by houstonmacbro on 2009-10-05
I really don't want Windows on my nb205 any more, but I am afraid to wipe that partition. I know Jaunty didn't recognize the wireless card (it had to be enabled in Windows first) but I took the plunge and installed Karmic beta and life is great. 

Can I now safely remove the Windows partition? It won't boot anyhow.

---

### Post by reegmas on 2009-10-05
I got mine to work it took a while but i didnt have to wipe anything.  You need an XP cd doesnt matter which one as long as it has recovery console.  Do not choose repair that will install over your existing xp install.  From the recovery console you can run chkdsk /f and you should be back in business.

---

### Post by PherricOxide on 2009-10-06
Did you actually get a Windows CD to boot off a USB drive? Or did you just go out and buy an external CD drive? I eventually got the recovery consul to work, reinstalled Windows, and gave up on Ubuntu for a while.

I tried to run chkdisk with both NTFS4Dos and BartPE, but didn't have any luck with either, and I couldn't get a Windows CD to load properly from a USB stick.

---

### Post by ajlewis2 on 2009-10-18
If this is the problem that I think it is, I'm wondering how you got the recovery console to work.  Are you talking about the one you boot off the toshiba?

I am almost certain what the problem is.  I have the nb205 and had the same problem. I also had the problem a few years ago on another laptop.  I read about it quite a bit before it happened to me personally and it is really weird.  There are 3 things involved.  One is that the hard drive is set as auto in the BIOS rather than having the actual disk geometry set and it is a large drive.  These days most drives are large.  Two is that some form of parted is used to repartition the drive.  Three is that the kernel sees the geometry of the drive differently than it is being seen by the BIOS.

So, you boot with a Linux install cd and the kernel reads the geometry.  You repartition and parted very nicely does its job and then writes the geometry to the BIOS.  

Not bad until you try to boot Windows which has the information it needs about the disk geometry stored in a little space (not the mbr where grub is).  That lets Windows find the boot files it needs.  The trouble is that the geometry it has is different than the BIOS now has and the files cannot be found.  My experience was that the special partition likewise could not boot.

The solution is to run fixboot from a Windows install cd, but the netbook has no drive.  Also the Toshiba does not come with the cd, not even a restore cd.  My solution was to buy an external cd drive and also a restore disk from Toshiba.  

There is a way to prevent the problem by giving the correct geometry as a boot parameter when you install or to set it in the BIOS.  The BIOS on the netbook doesn't allow for that. 

I had thought that the bug had been fixed by now since I first read about it back in 2004. Here is what I wrote about it then: [http://www.linuxbasics.org/tutorials/during/lose_windows_boot](http://www.linuxbasics.org/tutorials/during/lose_windows_boot)

---

### Post by ajlewis2 on 2009-10-18
PS.  Here is an article from a guy who used Ubuntu 8.10 without having this problem.  [http://ubuntuguru.wordpress.com/2009/07/23/ubuntu-for-netbooks/](http://ubuntuguru.wordpress.com/2009/07/23/ubuntu-for-netbooks/)  Unfortunately I used 9.04 and had the problem.  I'm guessing you also used 9.04 two weeks ago.  This guy later installed 9.10, but the problem happens with the repartitioning and he had done that with 8.04.

---

### Post by holycrapitsoj on 2009-10-21
Hey all, for the record, I believe I fixed the lost recovery partition errors in the NB205 by removing the 'hidden' flag on the HDDRECOVERY partition using gparted.  I'm thinking somehow this flag was added during the UNR install.

I'm not 100% positive this was the only step I had taken to resolve this problem, but I can't think of anything else I had done previous to removing the hidden flag that would have contributed to it.

Let me know if this helps.

---

### Post by holycrapitsoj on 2009-10-21
Ah - forgot to add that yes, I was able to factory restore to XP.  

Until there are better wireless and audio drivers available, I'm sticking to Windows.

---

### Post by Nethus on 2009-11-23
Hi PherricOxide.
Did you solve the problem with your netbook and win xp?
I have de same problem and im trying everything with no success. You will know how I feel.

I've removed the hidden flag to HDDRECOVERY but didnt fixed. What more can I do?


Please, any help will be welcome.

---

### Post by lisati on 2009-11-23
The only time I've had problems on my M200 latop after installing Ubuntu (a problem with NTOSKRNL or something of that nature) I was able to use a recovery DVD I'd made using the "recovery disc creator" tool preinstalled by Toshiba.

I'm not sure about other models but on my laptop, holding down the "0" (Zero) key while the Toshiba splash screen is showing will start recovery using the recovery partition. It has been a while since I've needed to use it, so I'm not sure what options are available in addition to the "restore to an out-of-the-box condition".

---

### Post by Hieptastic on 2009-12-08
After getting Ubuntu Netbook Remix 9.10 to work (stable network and headphone only sound) in dual boot mode.  I had inconsistent boot up time from 45s to 3 minutes.  I found that changing the SATA bios to Compatibility (instead of ACHI?) got it down to 45s consistently.  But since hibernate didn't work for me, I decided to get Windows working.  That's when I discovered Windows was inaccessible and unrecoverable.

Trying suggestions from different posts didn't help. Windows would hang at loading mup.sys or when attempting to recover, I got "unable to find C:\bin\errordialog and C:\bin\bootpriority.exe".

But I eventually was able to restore the original factory image from the recovery partition.  I don't know which specific step was key but here are the steps leading to it:  

1. Remove partitions (/dev/sda5 and /dev/sda6) created by the ubuntu install in an attempt to restore the drive to its original state.
2. Merge the deleted partitions back into the main windows partition (/dev/sda1)
3. Reset the MBR on /dev/sda1 to windows
4. Set the boot flag on sda1 (or was it sda2?)


(1 & 2) Removing Ubuntu partitions and merging with the original windows partition:
My attempt at installing Ubuntu with dual boot options resulted in two more partitions (/dev/sda5 and /dev/sda6). The resulting partition table looked like this:

/dev/sda1: windows partition
/dev/extended logical(?)
   /dev/sda5: ubuntu linux
   /dev/sda6: swap
/dev/sda2: toshiba recovery


My solution was to use gparted from the systemrecuecd ([www.sysresccd.org](www.sysresccd.org)) booting from a USB drive.  I used unetbootin and the system rescue cd image from their site (rather than have unetbootin download it).  Having unetbootin download seem inconsistent.  System rescue cd will complain about not being able to find a linux image and it will promp for a login but it will boot up properly if you leave it unattended for a 30s or more.

Run gparted and delete sda5 and sda6.  Only after deleting sda5 and sda6 will it allow you to remove the extended logical(?) partition.

Tell gparted to perform these queued actions before continuing.

Now use gparted to resize sda1 to include/merge with the deleted partions above.

Tell gparted to perform these queued actions before continuing.

(3) Resetting the MBR on the windows partition:
While still in System Rescue CD, I used TestDisk (under System Tools menu):
Run TestDisk, choose No Log.
Select /dev/sda, then Intel.
Select MBR Code, then Y to "Write a new copy of MBR code to first sector? (Y/N)"

(4) Set the boot flag
Here's where my memory is hazy (it was late).  I used gparted to set the boot flag on sda1, rebooted, it didn't boot, booted back into System Rescue CD, set the boot flag on sda2 instead, then it successfully booted into the Toshiba Recovery tool.  Or the order was reversed, that is I set the boot flag on sda2 first then sda1.  If the first approach doesn't work try the second.

This worked for me.  I make no guarantee it will work for you, but it's worth trying.

BTW, once the recovery tool has restored the partitions to factory state, it apparently isn't done yet and has to individually install and reboot per components like Norton Security, then Atheros, and on and on...  Initially I didn not pay close attention to why it kept rebooting and I thought it was stuck in a loop.  I redid the recovery again then realized it was rebooting between each component install.  I let it do it's thing and by morning I had a factory fresh netbook again.

If this worked for you, please spread the word.  In my research to find a solution, I noticed a number of people having the same problem.

Good luck.

---

### Post by robm15 on 2010-01-03
I just experienced the same problem as the one described above. I did pretty much exactly what had been done by anyone else. Taken my perfectly working NB205 laptop with Windows XP. And used the Ubuntu 9.10 netbook remix installation to shrink my XP partition, add the required partitions, and installed Ubuntu 9.10. My NB205 worked just as everyone else’s under Linux. When I decided to boot up XP just to test it, it failed, exactly as described above. 



 Over the course of the day I tried, and failed to fix the XP partition so that it would boot up, and the HD RECOVERY partition so I could get into the recovery console. All failed with the same errors described above. I even have a old Windows XP Home Premium OEM CD that I tried to use to boot from, but it was an original version from before SP1, and it failed to boot up also. I am assuming because it didn’t have the SATA drivers that are needed to boot up a SATA drive. Inspiration hit me about 2 hours ago. I had a Vista Home Premium OEM DVD. I didn’t know if it would work to repair XP, but I booted it up using my old obsolete XBOX 360 HD-DVD player plugged into the NB205 USB port, and let it boot. When it got to the recovery console, I told myself not to get excited yet. When the recovery console reached the step to select the operating system I wanted to fix, and none were listed, I saw that note above the selection box that said: “Only Vista OS’s can be repaired”… My heart sank. But I hit next, expecting to see that a selection had to be made to continue. But what did I see? I saw a menu of choices!!! Without missing a beat I clicked on command line, and had a wonderful DOS screen, with blinking prompt, I couldn’t have been happier. I entered, DIR C:, and was greeted with, this drive is corrupt, no data available. No problem, I wasn’t shocked. So I went further and entered DIR D:, DIR E:, DIR F:… and so on, just to make sure I saw all the partitions I knew were on my hard drive. I could not see the linux partitions, but I wasn’t surprised since they were formated in EXT4, and I doubted that any windows version could access an EXT4 partition. Next I entered chkdsk c:, and it said that there was a corrupt field in the table, but couldn’t be fixed in read only mode. It also listed the drive label as the NB205’s XP partition, so I went for it, chkdsk C: /R After almost a hour, it was done, and the only problem was the corrupt entry in characteristics table, which was deleted. Holding my breath, I restarted the PC, selected the Windows XP selection, and waited! Success!!! I now have a fully restored Windows XP, with no data loss, and a fully working Ubuntu 9.10 Netboot Remix boot partition, with the exceptions that everyone else has, not perfect but working.


 I hope this helps someone.
 Robm15

---

### Post by pswans.449 on 2010-01-10
Hi, I got ubuntu 9.10 to dualboot with xp on a nb205 by using AESEUS partition manager from inside xp instead of using GParted from within ubuntu to resize the xp partition. Then I just did a basic install onto the largest continuous unused space. Now I have have a great dualboot machine. 

Unfortunately, I'm really new to Ubuntu, so I can't explain why this worked, but I hope this post helps someone. 

Also if you are having trouble getting your restore partition to load, I was able to access mine doing the following:
1. boot 9.10 from the usb
2. use GParted to delete everything except the restore partition
3. install 9.10 on the remaining empty partition
4. you should now be able to access the restore partition from grub. I'd recommend going with the factory restore

**note I'm talking about 9.10, not 9.10 UNR, I know somebody on this forum said to use UNR, but I like regular ubuntu better and it works fine.

---

