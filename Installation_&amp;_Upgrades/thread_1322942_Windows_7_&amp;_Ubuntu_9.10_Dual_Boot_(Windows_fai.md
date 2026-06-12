---
title: "Windows 7 &amp; Ubuntu 9.10 Dual Boot (Windows failed to start)"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by James2k on 2009-11-11
On my laptop I was running a Dual boot configuration of Windows 7 and Ubuntu 9.10. Windows 7 is my primary OS so when I installed Ubuntu I had to resize my partition. Installation wise everything went well and I was using Ubuntu and Windows 7 together in harmony for about a week before my problem started happening.

Basically whenever I booted into Windows 7 from selecting it from GRUB just before the Windows boot screen would disappear and go to the windows login screen my laptop screen would flash a screen similar to a video card reseting and then find my laptop has rebooted. When I try to boot into Windows 7 for the second time it would say "Windows has failed to start" and then give me the option of start up repair or to continue to start Windows normally. I have ran the start up repair and it seems to find and fix something but whatever it fixed didn't last because booting into Windows 7 most of the time kept giving me this error.

At this time I have removed Ubuntu and replaced GRUB with the Windows Boot loader to make sure it wasn't a problem with my Windows 7 installation and since removing Ubuntu this problem has never happened. I have been looking for solutions to my problem but I haven't found anything.

I hope I can get my problem fixed as I really enjoy Ubuntu and would love to have 9.10 back on my laptop.

**Final note: At the moment I am currently defragmenting my C:/ and then will be running chkdsk of my hard drive to make sure there are no problems with the HDD and try installing Ubuntu again**

Thanks for your help,

James

---

### Post by Mark Phelps on 2009-11-11
Stop me if I'm guessing wrong, but you used the Ubuntu installer to shrink the Windows 7 partition, right?

If so, that's likely to have cause a filesystem corruption -- which was partly repaired when you ran Startup Repair.

But, you often have to run Startup Repair several times, and sometimes, even using the command line booting from the Windows 7 DVD!  Seems like MS's own repair utilities can not be trusted to work reliably.

In future, do NOT use Linux utilities to shrink Windows 7 partitions; use the built-in Disk Management utility instead.

Then, use the Ubuntu LiveCD to create partitions in the free space, and use Manual Partitioning option to install Ubuntu to those partitions.

That will avoid any problems with Windows 7 filespace corruption.

---

### Post by James2k on 2009-11-11
Mark thanks for your reply.

This would seem like the explanation as I have just installed Ubuntu and as soon as I've tried to boot into my Windows partition and it restarted as it does before. Strange thing is when I can get into the partition I run chkdsk to check the drive for errors (With Ubuntu installed) and it finds nothing. Yet start up repair does something. I think I will look at the report of the startup repair to see exactly what it flags up.

Thanks for your reply.

---

### Post by James2k on 2009-11-11
Mark, your theory of a filesystem error seems to be correct as I finally managed to boot into my Windows 7 partition and chkdsk was automatically ran and corrections were made the filesystem, as well as something about modifying the USN journal.

---

### Post by James2k on 2009-11-11
I followed your advice by shrinking the partition before installing Ubuntu and it seems to have moderate success. On one boot attempt after installing Ubuntu I did get the Windows could not start error, but after chkdsk ran everything seems to be OK. Thanks for your help again Mark.

---

### Post by James2k on 2009-11-20
I never replied to this thread again, but the problem still remains (I was just to quick to come to the conclusion) Even when I shrink the partition using Disk management in Windows 7 I still have problems going into my Windows 7 partition from GRUB. I've even tried installing Ubuntu using gParted but still the same result. I have no idea what the problem is.

---

### Post by darkod on 2009-11-20
Could you boot into Ubuntu LiveCD and in terminal do:
sudo fdisk -l (small L)

so we can see the partition layout? Copy the result.

---

### Post by James2k on 2009-11-20
Thanks for replying. The fdisk command gave back the following:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82df4bb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13574   109025612    7  HPFS/NTFS
/dev/sda2           18143       19457    10559488    7  HPFS/NTFS
/dev/sda3           13575       18142    36692460   83  Linux

Partition table entries are not in disk order

```

Just so I don't cause any confusion. Windows 7 is sda1 and sda2 is a recovery partition

---

### Post by darkod on 2009-11-20
You see, the same happened to someone else, he had vista and 9.10 and vista was not starting. We tried everything and after 3 days troubleshooting, the last resort was trying to delete the utility partition he had. And everything worked perfect after. :)
I never like to suggest people to delete recovery or utility partitions, but your problem seems very similar. Also in his case the partition was at the back of the disk.
Your is also at the back, you can see it by the start/end values. That's why the message "not in disk order".
Think about this. As I said, I never like to recommend deleting partitions, I haven't even seen your system. But after 3 days that was the only thing that helped the other person.
That's why I asked for fdisk. These todays systems seem to have a very strange partition layout from factory/dealers. As good as Ubuntu is, it obviously can't handle it sometimes.

---

### Post by James2k on 2009-11-20
Thats a very interesting story, I can't imagine that the recovery partition would be the cause of all this but it's funny because the recovery partition is actually a Vista recovery partition which has been in place since I bought the laptop. Since I had to clean install Windows 7 because I couldn't upgrade from the Vista version I was on, the recovery partition is useless. I actually burnt a set of a recovery disks just in case (Before I clean installed Windows 7) but  I have a full Windows 7 installation disk, so I can remove the recovery partition with no risk of not being able to recover if *touch wood* something happens. I guess I should give removing my recovery partition a try?

---

### Post by darkod on 2009-11-20
Definately. :) As long as you're happy with that. Plus it will free some space for you on the HDD, it's quite big 10GB.

PS. It might create some confusion for grub because deleting/dev/sda2 will probably move the naming convention of /dev/sda3 to /dev/sda2 which might be problematic to locate Ubuntu. But that can be sorted out if it happens.

---

### Post by James2k on 2009-11-20
Very well. I shall remove the recovery partition. It might take me a few times to boot into Windows but once I get to disk management I should be OK. Am I right in saying I can simply use the Windows Disk Management tool to remove the recovery partition or must I use gParted?

---

### Post by darkod on 2009-11-20
Windows disk management is enough.

---

### Post by James2k on 2009-11-20
OK. Third time lucky on booting into Windows 7. Im in.

I have removed the Recovery D:/ partition but I've noticed that I can't fully remove the partition so I can't extend my C:/ volume, whats up with that?

Anyway I'll reboot now.

**Edit: As you and I both thought. GRUB now has an error and says error: no such partition. I assume I have to restore GRUB. Can you tell me how to do this?**

---

### Post by darkod on 2009-11-20
You have a very short and precise guide here:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Look at item 2) Using Ubuntu 9.10 LiveCD
That means booting with ubuntu cd and selecting Try Ubuntu option. The procedure is fairly simple.

---

### Post by James2k on 2009-11-20
Thanks for that.
[B]
Edit: Do I have to mount both partitions or just the Ubuntu partition and then let GRUB discover the Windows 7 partition.[/B]

---

### Post by darkod on 2009-11-20
Just ubuntu, win7 will get discovered by grub2.
Like the instructions say, you need to mount only / (root) unless you had separate /boot partition which I guess you didn't.

---

### Post by James2k on 2009-11-20
No I don't I've mounted the Ubuntu partition again. See if it works rebooting now.

---

### Post by James2k on 2009-11-20
OK basically the GRUB error is fixed but when the GRUB loads I get a prompt with grub> wanting me to put in something

---

### Post by darkod on 2009-11-20
Can you try in terminal:
sudo mount /dev/sda2 /mnt
sudo update-grub

It will return few lines, take a look whether it locates Ubuntu and Win7.

After that also you can open:
gedit /boot/grub/grub.cfg

and look where the Ubuntu 2.6.31 entry is, towards the middle of the file, and copy that entry here to see if the partition it is looking at is correct.

---

### Post by James2k on 2009-11-20
Seems to have mounted but when I run sudo update-grub:

```
grub-probe: error: cannot find a device for /.
```

**Edit: Managed to get it to work. It hasn't recongised the Windows or Ubuntu Partitions, only memtest**

---

### Post by darkod on 2009-11-20
How about the part from grub.cfg file? As explained in previous post.

---

### Post by darkod on 2009-11-20
So, is it working now? If not, take a look in grub.cfg in a section starting with *** BEGIN 10_linux etc.
There will be entry
menuentry Ubuntu Linux 2.6.31 etc
and few lines below
root=(hd0,2)

It needs to be (hd0,2). If it's not that's probably the problem.

---

### Post by James2k on 2009-11-20
Sorry I've been away from my keyboard. Basically I ran the grub update and it says:

```
searching for splash image.... None found, skipping....
Found Kernel: /boot/memtest86+.bin
Found Kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... Done

```

---

### Post by darkod on 2009-11-20
Whoops. What is menu.lst doing there? It's not used in grub2 only in grub1.

OK. In terminal run:
gedit /boot/grub/menu.lst

Copy the part starting title Ubuntu ....etc

Then in terminal open:
gedit /boot/grub/grub.cfg (if it exists)

Copy the part menuentry Ubuntu Linux 2.6.31... etc just the next few lines until the }

---

### Post by James2k on 2009-11-20
Nothing is in menu.lst. I think I have screwed up GRUB quite badly, and think the best option is to just re-install Ubuntu. I shall overwrite the MBR with the Windows 7 one and start again sounds like the best option right now

---

### Post by darkod on 2009-11-20
And in /boot/grub/grub.cfg?

---

### Post by James2k on 2009-11-20
Nothing in grub.cfg either.

---

### Post by darkod on 2009-11-20
You might be right. Restoring Win7 MBR and then reinstalling Ubuntu might prove faster. :) Sorry.

---

### Post by James2k on 2009-11-20
Not a problem I thank you for taking the time to help me out. Everything you've said is correctly it's probably just me being thick, but yeah I'll start again. Besides it will make sure the partitions are correctly mounted as sda 1 and sda 2 etc. Thanks for your help, hopefully the removal of the recovery partition will be the last of my problems :D

---

### Post by James2k on 2009-11-21
So far so good. I haven't had a problem accessing the Windows partition since installing Ubuntu yet. Removing the recovery partition seems to have done the trick. Thanks darkod

---

### Post by darkod on 2009-11-21
No problem. Glad you got it going.
There are more and more threads about problems with dual booting and with more and more desktops and laptops being shipped only with recovery partitions and without windows OS media, it seems those partitions are creating a lot of the problems.

@moderators: Maybe time for a sticky on this subject?

---

### Post by James2k on 2009-11-22
Looks like I spoke to soon again, as I've had the same problem again booting into the Windows 7 partition, same problem just before the boot screen disappears the laptop reboots back to the BIOS again. This never happened on 9.04 with Windows 7.

---

### Post by darkod on 2009-11-22
Oopss...  :( No error messages of any kind?
And did you restore vista botloader first after removing the recovery partition?

---

### Post by James2k on 2009-11-22
Nope no error. Just when I boot back into the partition says Windows failed to start. And I didn't restore anything on the recovery partition.

---

### Post by darkod on 2009-11-22
I didn't ask precisely. :)
You deleted the recovery partition.
After that it was better to restore win7 bootloader on the MBR to simulate the situation like 7 was always installed like that. Even though that would destroy grub2 on the MBR.
After you have confirmed 7 is booting few times and working OK, you then restore grub2 on the MBR using Ubuntu LiveCD.

I can not be sure, but not restoring the win7 bootloader might have created issues for win7 to boot normally. Part of the bootloader process might have even been on the recovery partition, I have no idea how they organized it. That's why I hate those partitions. :)

You don't have win7 dvd do you?

---

### Post by James2k on 2009-11-22
That could be true, Im actually at my dads house at the moment so I can't do anything with boot loaders right now as I'll lock my Ubuntu partition out.

So you suggest writing the Windows 7 MBR then boot into the Live CD and restore GRUB 2.

Yes I have a full Windows 7 DVD.

---

### Post by darkod on 2009-11-22
Yes, exactly. Remember when I said I don't like giving advice to people to delete partitions? This is exactly why. In some strange way they might have involved the recovery partition in the boot process and that link is now broken.

After you restore win7 mbr and you make sure win7 is working fine, restoring grub2 from ubuntu cd shouldn't be a problem.

If win7 doesn't work even after restoring mbr, then the problem lies there and not in grub/ubuntu.

Hope it works.

---

### Post by James2k on 2009-11-22
It is possible that there is a customized boot loader, but it doesn't matter so I wouldn't worry the recovery partition didn't work anyway. I'll find out if it works later tonight.

---

### Post by treonaut on 2009-11-22
I was following the conversation very attentive, because whenever I installed Ubuntu 9.10 after a few starts I can't acces any of the two Systems. Windows is not found and Ubuntu either.
Now I keep Windows 7 for a while until I find a solution here.
Please keep us informed whatever you find.

---

### Post by James2k on 2009-11-22
I certainly will. I will be writing the Windows 7 MBR and then writing the GRUB loader again when I get back home. Until then sit tight and I'll post feedback.

---

### Post by Bigadada_saba on 2009-11-22
I  found out the hard way that after a dual boot is install windows 7 does nt like you saving data on it's partition  if you have it that they share the same my document. saving something into windows partition corrupts some files so what i have is four partitions windows, ubuntu, swap and a data partition formatted in fat

---

### Post by James2k on 2009-11-22
Sadly, I restored the Windows 7 MBR and then restored GRUB 2 and I still have problems accessing my Windows 7 partition. Same problem, select Windows 7 from GRUB loader then just as Windows will go to the login screen, my laptop screen flashes as if the video card is reseting and they hey look BIOS screen, laptop has restarted.

Right now I think since restoring GRUB has made things worse it took me four attempts to get into Windows 7 successfully. Not to sound like a quitter but im getting pretty fed up of this now. In my honest opinion I think this is a problem with GRUB 2 because this never happened on Ubuntu 9.04 which doesn't have GRUB 2.

Seems like a few people are having problems with Windows 7 and Ubuntu 9.10 dual boot. If anyone is having similar problems keep this thread alive.

[B]My next and final attempt is to install Ubuntu 9.04 then upgrade the distribution to Ubuntu 9.10 but doing it this way will not install GRUB 2 which I think seems to be the problem with Windows 7 and Ubuntu 9.10 dual boot
[/B]

---

### Post by eljonny on 2009-11-23
I had this problem with my newer laptop, which is an HP G60-120US. I reformatted and reinstalled Vista on /dev/sda1 (210 GB) after hours of frustration running the Startup Repair tool as well as chdsk on sda1 from the recovery partition that is also on the system. I have a FAT32 6 GB storage partition (for easy encryption, universal pnp access, etc) (/dev/sda4), a 23 GB ext3 /dev/sda3 partition for Ubuntu Karmic, and a 1.1 GB swap partition. So, crazy amount of splitting my main partition and shrinking and expanding partitions to get my desired configuration. After I upgraded to Karmic, as people have also had this general problem, Vista stopped loading. Since I am still using Vista, the recovery partition is a really nice thing to have and as such makes it really not an option to delete it. I originally had Jaunty and used the Distribution Upgrade through the Update Manager, and therefore still had GRUB1. After reformatting sda1 and reinstalling Vista, I had to [reinstall GRUB ]("http://www.astahost.com/info.php/Restoring-Grub-Boot-Loader_t14048-10.html") since the recovery partition rewrote the MBR on sda. I then ran into the sh:grub> prompt issue. [I found this guide]("http://grub.enbug.org/Manual#GrubShell") to be very useful in getting my 9.10 installation back. You have to use the 'root' command before the 'linux' command to mount the partition which contains your linux installation: sh:grub> root [partition] 
eg. sh:grub> root hd0,3
Pressing the Tab key is helpful as a command list. 'help' is virtually useless.
After such you can boot into Ubuntu and use Synaptic to remove GRUB1 (package: grub) and install GRUB2 contained in the grub-pc package. After GRUB2 is installed, use the terminal to run sudo update-grub2 and it will automatically scan and add all boot options into /boot/grub/grub.conf. If that doesn't work, [go here.]("http://ubuntuforums.org/showthread.php?t=1195275")
I have found GRUB2 to be much more forgiving when it comes to loading the Vista installation from the boot menu. I still had it restart once after the loading screen came up the first time rebooting after installing GRUB2 (freaked me out a little), then did the Startup Repair thing and havn't had a problem after that. Since the Vista and 7 kernals are very similar, this may help with the issue dual-booting with 7. Will be using my newer laptop regularly and will try to remember to edit my post if any issues come up, and hopefully this helps someone out.

If you are having the issue with Windows 7 where it won't load with GRUB2, maybe try reinstalling GRUB2 through synaptic or the terminal and using update-grub2, then running the startup recovery tool if it doesn't boot?

@Bigadada_saba: Good consideration. This is always a possiblity. Will try to remember to stay away from mounting my Vista partition in Karmic and use the 6 GB partition for sharing files between OS's.

---

### Post by dot.man on 2009-11-24
I am having a similar issue with dual-booting Windows 7 and Ubuntu 9.10 but on an MSi A6000 laptop, however, my issue is a little bit different.  My system does not hang at Grub loading, it just flashes "Grub loading" on the screen for about 1/2 of a second and reboots, repeating this over and over.  I have not done any manual editting of the Grub files nor is it customized.  I had no issues logging into Ubuntu but I did experience the quick "blue screen of death" the couple of times when selecting Windows 7 and then the "failure to launch windows" screen, but I chose "Start normally" instead of repair both times.  The last action performed was choosing "restart" from Windows during the shutdown to get it to reboot so I could log into Ubuntu.  After this is when I started getting the "Grub loading" and reboots.  Any ideas?  Do I need to start a new thread for this or is it close enough/related?

---

### Post by James2k on 2009-11-24
Sounds like your GRUB 2 got seriously messed up. The only option I can suggest to you is to recover GRUB 2 using the Ubuntu Live CD. Myself I would restore the Windows 7 Boot loader first to make sure your Windows 7 partition is all good and then proceed with the recovery of GRUB 2.

**Recovering Windows 7 by overwriting GRUB with the Windows 7 MBR (Master boot record)**

[LIST=1]
[*]Boot into your Windows 7 DVD
[*]Select the language and keyboard layout to your settings
[*]Instead of clicking "install now" look for "Repair your computer" in the bottom left of the window
[*]Windows will then search for your Windows 7 partition. Once it has stopped searching select your partition and proceed.
[*]Open up a command prompt window and type the following command
[/LIST]
```
bootrec.exe /FixMBR
```Press enter. A confirmation of the execution of this code should be a message saying "**Operation completed successfully**". This means you have wrote the Windows 7 boot loader successfully. Type exit to close the command prompt window and click restart. **You can now remove your Windows 7 DVD.**

Now on start up you will no longer have grub but instead go straight to windows as you have overwrited the boot loader, but you will no longer be able to access your Ubuntu partition. Follow these steps to recover GRUB 2:

**Restoring GRUB 2 (Using a Ubuntu 9.10 Live CD i.e booting into the try ubuntu without making any changes option)**

**[COLOR=Red][A guide has already been wrote for recovering GRUB 2 in Ubuntu 9.10 so just click me to recover GRUB 2]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")[/COLOR]**

I hope I've helped you.

---

### Post by mt1234 on 2009-11-27
> **James2k said:**
> 
[B]My next and final attempt is to install Ubuntu 9.04 then upgrade the distribution to Ubuntu 9.10 but doing it this way will not install GRUB 2 which I think seems to be the problem with Windows 7 and Ubuntu 9.10 dual boot
[/B]

Is this what you ended up doing? Did it work? 

I just bought a new HP Pavilion dv4t with Windows 7 and would like to setup a dual boot system, but I am a bit reluctant now that I have read about some of the problems people are having. I'm not very Linux savy (not extremely Windows savy either). I setup a dual boot system on an old laptop with XP & Karmic. It went very smooth. I don't have the Windows 7 DVD (didn't come with the laptop). I created a Recovery disk and also created an image of the hard drive on a separate hard disk. I read in another post that if you don't have the Windows 7 install DVD that it's not a good idea to delete the Recovery partition. Is this correct?

How often are people experiencing problems with setting up a dual boot with Windows 7? What is the likelihood of me having success?

---

### Post by garvinrick4 on 2009-11-27
You can look into Windows Vista or 7's boot by "cmd" in search box
open command prompt as administrator. "bcdedit" at prompt and you
will get your DOS boot. As you see there will be 2, the 1st is boot manager. The second will look be the Window s 7 boot loader instructions with recovery enabled. UBUNTU sees that 
recovery as Vista in its Grub2.
That is just the way it is. As long as you have Ubuntu and recovery, Windows 7 and recovery
which says VISTA. Mem test. I would not worry. If there is one in 7 that says recovery and
it boots to an error and you have the VISTA that boots into recovery do not worry. If you
want to look into grub2 to see if you want to delete the recovery that needs Windows 7
attention and get rid of it. Have at it Isee nothing but trouble. It does not bother one thing where it is. If you want to change sequence of boot do it in Ubuntu Start-up Manager.
Wubi people if you do not uninstall just take out Wubi install through Add-Remove programs
you can leave your Wubi boot inside of Dos4grub of Windows. Have to edit it out in "bcgedit"
at dos command prompt. It will flat say Wubi so it is safe to edit out. 
bcdedit/delete {boot loader identifier} once it is out it is gone make sure it says Wubi.
 
If the Windows 7 recovery that boots to error can be fixed by using live recovery or installtion
disc's but I do not see why leave good enough alone. You already have a recovery that just
says Vista. They say that will change in later versions of GRUB2.

---

### Post by eljonny on 2009-11-29
I have come across a possible solution: Use a different boot loader. I found a boot loader called GAG That is graphical and has not failed to load both Ubuntu Karmic or Windows Vista a single time and I have been using it for about a week. If I have any problems I will try to get back here for another reply.
[Here is the SourceForge page for GAG]("http://gag.sourceforge.net/").
I had some issues booting Karmic because GRUB wrote nothing to the boot sector on the partition that it is installed on, so I had to boot a live CD and do a grub-install to the partition that Ubuntu was installed onto, ../sda3, since GAG is written to the boot sector on ../sda. It seems that Windows has a boot sector written to its installed partition ../sda1, so booting it is not an issue. I don't know what the heck GRUB does (and don't really have the time to find out) when it boots from different partitions from the MBR, but it's obviously doing something that MS did not pay attention to, see, or care about. The GAG is pretty convenient and super easy to set up, and very lean. It has the potential to boot 9 different OS's from 8 different hard drives. Woohoo! Good stuff. Anyway.... That's what's new. Peace.

---

### Post by BAMA199224 on 2009-11-29
what is a partition?? i want to install either windows xp or windows 7 over this ubuntu,,i have disks but i can't get them to load.

---

### Post by James2k on 2009-12-06
Just thought I'd update people that are still following this thread. Ever since the recent Ubuntu Kernel update my problem has seemed to be less regular and I haven't had a problem booting into my Windows partition without problem for the past few days, I don't think it's fixed, but something happened to make it less regular. I suspect a recent update to the kernel.

---

### Post by James2k on 2010-01-27
I believe the problem may now be fixed. I ran the command

```
bootrec.exe /fixboot
```Through a command prompt on window while booted into my Windows 7 DVD and I haven't had a problem booting into Windows 7 yet.

Rather than the problem being with GRUB it may have been my boot record all along. Windows must not of liked something when Ubuntu was installed. After running that command, I checked my Ubuntu partition and it remains unaffected, just as well really!

I successfully booted into Windows first time and now it's performing a hell of a lot of updates to the registry (6551 to be exact). Hopefully fixing this problem once and for all. Someone back hand Microsoft for making Windows 7 even more of a pain to dual boot.

---

### Post by pSYcl0Ne on 2010-03-17
I am having this exact problem with Vista on a friends laptop. My own netbook boots 7 mac and karmic just fine (but im using grub-legacy) is this really the case of a grub2 vs vista loader.. will a downgrade to grub-legacy and a fixmbr then re setup-grub repair this or have i mucked up vista by repartitioning it with ubuntu??

---

### Post by James2k on 2010-04-16
This is still on going months later, as I never could fine a solution/confirmed cause to my issue. Im currently running Ubuntu 10.04 BETA 2 and have had various failed to start messages when attempting to boot into Windows 7 from GRUB 2 with the same thing happening. Boot up laptop, get to GRUB 2 menu, select Windows 7, laptop restarts when it's about to go to the login screen, laptop restarts as if something failed. Attempting to boot Windows again, usually shows the failed to start screen, select boot normally the cycle repeats. It's also random on when booting Windows 7 will fail, sometimes it happens once, sometimes it takes me about seven attempts to get to Windows and sometimes I can get in first time. 

Yet I still haven't got the fainted idea as to why, either my laptop has got a special boot loader (Which I've probably wiped from all the /FixMBR and /Fixboot commands anyway) Or Microsoft designed a boot loader that programmed to punish people for using anything other than Windows.

All of those "perfect" dual boot guides never worked for me. I installed Ubuntu with Windows 7 first. Shrunk the partition in Windows Disk Management and then told the Ubuntu installer to use the Unallocated space that was created from the shrink volume process. Apparently thats how your meant to install Windows 7 and Ubuntu in a perfect dual boot, but im yet to have a perfect dual boot where by I can't get into Windows first time every time.

Im not going to be all pissy and drop Ubuntu simply because the boot loader doesn't want to play nice, because afterall I love Ubuntu and it would be very vein in doing so. But if anyone has new information on this, please post it as I want to have the perfect setup! I think I've waited long enough after me googling hours on hours finding nothing thats getting me closer!

Thanks.

---

### Post by eljonny on 2010-04-19
@James2k: Check my post about a different boot loader on page 5 of the thread. I have been using the GAG boot loader ever since I posted that with zero problems. You simply have to write 0's over the first 446 bytes of the MBR (writing 0-512 will overwrite your partition tables. Obviously a bad thing lol. 0-446 contain the master boot record), then install the GAG boot loader onto the MBR. After which you will need to load an Ubuntu live CD, doesn't matter which version as long as it's newer, and install GRUB2 to the boot sector of the partition that Ubuntu is installed on. It gives you a warning that it's a bad idea to install GRUB2 to a partition boot sector instead of the MBR, but I have seen no problems and I have been using GAG for like 6 months to boot successfully between OS's.
Here is the command for writing zeros to that area of the drive:
dd if=/dev/zero of=/dev/hda bs=446 count=1
Windows has a boot record on it's own partition, so it will show up right off the bat in GAG.
A sidenote: Your drive might not be hda. Make sure you have the right drive in the of statement: of=/dev/<yourDrive>
Peace.

---

### Post by James2k on 2010-08-24
I got fed up with the constant boot failures, so I decided to install Ubuntu via Wubi instead, this has solved any failed to start errors regarding windows.

---

### Post by James2k on 2010-10-08
I actually managed to find what the problem was with GRUB and Windows. If I rebuild my Windows BCD completly the boot errors completly stop and I can boot into Windows fine without any problems, but as soon as a grub update comes along it seems to mess up again. But rebuilding my BCD completly seems to stop the errors.

Running bootrec /rebuildbcd doesn't work on it's own, I had to actually remove my BCD and then rebuild it.

Hope this helps anymore who has had problems like this.

---

