---
title: "Vista doesn't boot after Ubuntu install"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by JMC8501 on 2007-02-28
Hi all:

Strange problem. I have an Dell E1505 laptop. Core2Duo 5200, 1GB RAM, 80 GB HD. By default, comes with Vista home premuim. 
I wanted to try Linux, so I downloaded and burned Ubuntu 6.10 ("Edgy Eft").

I booted from the Ubuntu CD, and resized my NTFS partition, and created a linux  partition, and a swap partition (actually an extended partition since I couldn't have more then 4 partitions for some reason). I installed Ubuntu, rebooted, and it works. Works well. I set up my Vista partition to automount, and I am able to browse it just fine from Linux, can access files (readonly) just fine.

However, when I try to boot back to Vista, it no longer works. From the Grub bootloader, I can choose the Vista bootloader, and it boots up to the moving green lines, then HD stops, and the lines keep moving. I've tried booting in safe mode, no go, it stops at a certain point (screen eventually goes black ).

Here's the weird part - I tried booting from my Vista DVD, and the same thing happens. I'm not sure what the problem is here - Dell support says that "sectors might be corrupt" or something. after some research online, I find this site:

[http://support.microsoft.com/kb/919529](http://support.microsoft.com/kb/919529)

which describes my problem exactly, except with xp dual boot instead of my Ubuntu. Of course, this means I can't use their solution, but maybe someone knows how to fix the problem.

I've read a few different ways to have vista & linux, but most of them assume access to the vista, or to being able to format the HD, which i'm not sure how to do (like I said, the vista reinstall DVD doesn't work). I'd be very disappointed if this was a permanent disability of the new OS.

Any ideas?

---

### Post by timjayko on 2007-02-28
honest answer.. scru vista clear your hard disk for all ubuntu lol.. sorry cannot help you.. I will never touch microsoftware anymore

---

### Post by JMC8501 on 2007-02-28
Honestly, I'm in the sciences, and Ubuntu has helped me a lot in this area. However, I still need to run Vista, so hopefully someone out there can help me.

---

### Post by MySeid on 2007-03-01
what you may want to try is to fully install Ubuntu on your whole hard drive, then partition a section of the HD.  Once that is done, you can install vista on that partion.  Once that is installed,  you will have to update grub probally.  I am  pretty sure this can be done in a couple of lines by adding the boot sector to the boot list.  

I haven't tried doing this at all, but its just how I would take a stab at it.

---

### Post by moloth on 2007-03-01
Did you fry vista when doing your resizing? I would set up all your partitions first, then install vista then ubuntu. But I can only vouch for xp doing this.. dont know how vista behaves when having its boot loader changed.

---

### Post by karcin on 2007-03-01
I have exactly the same problem. 

I install Ubuntu last night 
and I can't have Vista now. 

Please someone help, because these Microsoft 
guys are really stupid. Can Ubuntu community 
resolve this problem?

I think it's important to resolve this, also
for the future Vista users that would like to
install Ubuntu in their PC.

---

### Post by silas_irl on 2007-03-01
Well it turns out that good ole MS have changed their default bootloader (boot.ini) to a new bootloader called BCD, that's very unfriendly to work with. Ah don't you just love Microsoft? :)

Have a look here, it also describes how to alter grub to load vista: [http://desktoplinux.com/articles/AT2094892904.html](http://desktoplinux.com/articles/AT2094892904.html)

I assume that should sort you out, if you didn't do any damage in resizing the Vista partition.

---

### Post by BLTicklemonster on 2007-03-01
... "vista won't boot after ubuntu install"...


QUICK, PATENT IT!!!

---

### Post by karcin on 2007-03-02
Thanks silas_irl but it didn't work.
Any other solution?

---

### Post by endtroducing on 2007-03-02
Im not sure how Vindows Wista behaves , but if you can get a recovery console you could use fixboot and fixmbr.

[http://www.apcstart.com/3895/how_vista_screws_dual_booting_nirvana](http://www.apcstart.com/3895/how_vista_screws_dual_booting_nirvana) (**Read the 2nd comment!)**
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

:popcorn:

---

### Post by karcin on 2007-03-03
Thank you endtroducing, I read the 2nd comment 
but when I wrote in a terminal "setup (hd0)",
the answer was: "Error 17: Cannot mount selected partition"

I really don't now what to do.
The first time I install Ubuntu (with XP in the other partition),
I didn't have any problem. Why these MS guys make our lives
so difficult?.. Anyone got an answer?.. ;-)

---

### Post by endtroducing on 2007-03-03
See here: [http://www.cyberciti.biz/tips/howto-fix-dual-boot-windows-vista-linux.html](http://www.cyberciti.biz/tips/howto-fix-dual-boot-windows-vista-linux.html)

If not, you try to get a recovery console and repair the mbr so only vista boots. Im not saying to re-install here... Just run a recovery console and fix the mbr.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Once it's fixed, i'll help you get a proper dual boot.

---

### Post by karcin on 2007-03-03
endtroducing I tried this:
[http://www.cyberciti.biz/tips/howto-...sta-linux.html](http://www.cyberciti.biz/tips/howto-...sta-linux.html)
but didn't work.

As for the recovery console, it was the first thing I 
have tried, but from step3 "Select a language,..."
stop loading. It didn't gave me the ...chance to
go to the recovery mode.

---

### Post by endtroducing on 2007-03-03
:confused:

---

### Post by puccaso on 2007-03-10
but because vista isnt like xp in any respect now in regrads to booting.

there is no boot.ini
and extra's like winload etc..

i heard that if u grub over the mbr,
vista wont boot.
because it requires complete control over its partition (has to be active) and the mbr..


i have been stuck with vista because of this

have you had any luck?

also try
booting up with another cd, like a rescuse cd - ubuntu cd or whatever
see which partitions are active
for experiments sake
make the vista partition active.. 
then boot up with the cd..
and goto the recovery box, or it should give u an option to repair an installtion on the bottom left
go there
find the obtion that says
fixmbr
do that
then reboot
(thats what i would do with xp ne way)
see how it goes.. 

let me know please
if we can resolve this
im gonna install ubuntu 
otherwise we're all screwd.

---

### Post by konungursvia on 2007-03-10
Burn a copy of the live gparted cd, and boot from there, and let it repair your partitions. This may work.

---

### Post by puccaso on 2007-03-10
OK
THIS IS HOW U INSTALL UBUNTU
ON PRE-INSTALLED VISTA SYSTEM.

you have to first re-size the drivers in vista - easyest option here.
so if ur harddrive is 200g, make ur vista 100g, (these figures are just examples)
now with the 100g u have left over:

when you install SELECT F6 - so that you go in expert mode.
more about this later:


now... 
MAKE A SEPERATE BOOT PARTITION... as apposed to ur home/root/swap.
select your BOOT parition to be bootable.


reference to f6::: 
there will come an option after you isntall base system about the GRUB 

rememebr pressing f6 before hand... this allows you to CHOOSE WHETHER TO INSTALL GRUB TO MBR OR NOT.
 YOU SELECT NO
 AND YOU TYPE IN THE YOUR BOOT PARTITION
 IN GRUB LANGUAGE 
 
 SO /dev/sda2 would be (hd0,1) etc.. (work that out for urself - it explains anyway)
 
now when you boot
you should see ur grub
with vista lodare
and i just did it
and it works :)

---

### Post by W@LT on 2007-03-12
I had this problem on a couple of occassions...

To overcome it I loaded the original upgrade / install disk for Vista and tried to reboot from there... It took around 20 attempts before it eventually managed to boot up and then it was a case of carrying out a repair on the Vista Install

It worked a treat... but the main thing is to continue to try booting from the Vista disk and don't give up...It will eventually

W@LT

---

### Post by flue on 2007-03-12
I was having the same problem as most have with Ubuntu/vista dual booting.  Everything says it should work, but it just would not boot vista from hdd or cdrom.  

My work around. (very cude, but works with out a hitch)

1.  Use Gpart to partition drive and install Ubuntu on 1st partition (I made 4 because I am wierd)
(1 and 2 for Ubuntu, 3 for WinXP and 4 for Vista...5 a small fat32 to Xfer files between Ubuntu and M$)

2.  Install WinXP on 3nd partition.

3.  Install Vista on 4th partition.

4.  Use Live-CD to fix grub...I forget how since I know crap about linux, but search for grub fix and you can put grub back on the MBR.

5.  Add Vista entry to Menu.lst (for me it was (hd0,4)) and make active.  Reboot.

ESC at grub and select Vista.  Vistal boot loader will take over and give you WinXP or Vista to load.

Because the Vista over writes XP's mbr (taking a guess here) you will be unable to add XP to the Grub list.  Will get an unknown partition error.  But thats fine.  I wanted a triple boot and managed to stumble onto a solution.

G'luck.

Flue

p.s. I have not tried this install with only Ubuntu and Vista.  since I was failing with just Ubuntu and Vista I opted to add XP since it was working with dual boot.  But for me installing Vista first and then Ubuntu was not an option.

---

### Post by gus sett on 2007-03-15
yes. more :idea: perhaps by searching on HP triple boot
and checking the mdoyle entry. :arrow: 

> **karcin said:**
> I have exactly the same problem. 

I install Ubuntu last night 
and I can't have Vista now. 

Please someone help, because these Microsoft 
guys are really stupid. Can Ubuntu community 
resolve this problem?

I think it's important to resolve this, also
for the future Vista users that would like to
install Ubuntu in their PC.

---

### Post by tyeo098 on 2007-03-25
I have a similar problem, I can get the little vista scroll bar to come up but then everything just locks up(or it takes forever).
Any idears?

---

### Post by Unhindered on 2007-03-27
> **tyeo098 said:**
> I have a similar problem, I can get the little vista scroll bar to come up but then everything just locks up(or it takes forever).
Any idears?

Yes. I had the same problem. The fix? The computer was new (hence the Vista), and I'm having it replaced by the manufacturer. Doesn't seem there's any fix for this, once Ubuntu has been installed this way, Vista is totally inaccessible. Even from the "system restore" CDs/DVDs.

---

### Post by alex_sem on 2007-03-28
I have just got this problem. Very very unpleasant, very very childish. Stupid M$ corporatists :mad:.

---

### Post by unisol on 2007-03-28
you could try this: Dual-Boot Windows Vista and Linux 
After the installation of Windows Vista, you will want to install Linux. DO NOT resize the Vista partition during the installation of the Linux distribution! Due to the change in NTFS versions, no Linux partitioning program, nor standard Windows partitioning programs, can properly alter the partition that Vista is installed to. Also, be sure to specify that GRUB is the bootloader to be installed if this is an option. After installation is completed and you will boot into the Linux operating system that you installed (because GRUB over-wrote the Vista bootloader in the MBR). From here, open up a terminal window (the method of doing so will vary across distrobutions/window managers). After you are at the terminal, all commands that are going to be needed to modify the boot menu will need to be run as 'root' so you will need to know how to accomplish this on your system (su or sudo). The first thing that we will do is backup the current boot menu, which can easily be done by doing this (remember to run this as root): 

Code: 
cp /boot/grub/menu.lst /boot/grub/menu.lst.bak 


Next, we need to edit the file "/boot/grub/menu.lst" in the text editor of your choice. You will now want to add an entry for Windows Vista. To do so, you need to add three lines to the file at the end of the file. Example entries follow: 

Vista is installed to the first partition of the first IDE hard drive: 
Code: 
title         "Windows Vista" 
root         (hd0,0) 
chainloader      +1 


Vista is installed to the first partition of the first SATA/SCSI hard drive: 
Code: 
title         "Windows Vista" 
root         (sd0,0) 
chainloader      +1 


If your setup is not the same as either of the examples above, you will need to modify one to match your current setup. The only area that should need modification is the line that starts with "root". The item that will likely need modification is the drive and partition information. For editing the drive that Windows Vista is installed on, you will have to change the first '0' to the number of the drive. If it is the primary or first drive, it will be a '0', the secondary or second drive would be '1', and so on. The same numbering scheme is followed for the partition information, which is the second '0'. First partition on the device is '0', second partition is '1' and so on. If you do not know what drive/partition you should put into the list, you can find this out with a disk or partition management program that may be installed with the system. If you know the device that Vista is installed on, you can also translate that to the GRUB menu. For instance, if Windows Vista is installed to "/dev/hda3" then the "root" entry would be "(hd0,2)" and if the device was "/dev/sdc5" the "root" entry would be "(sd2,4)". A general note here as well, if you have Windows Vista installed to a logical partition within an extended partition, the extended partition counts as a partition. Because of this, what would be thought of as the "second" partition, if it is logical, would actually be the third, as the whole extended partition counts as '1'. If you do not know what the entry should look like, please ask as the only stupid question is the one not asked. It will likely save time and frustration on your part. After you have the file modified, save it and now restart the system to test it out. 

Multi-Boot Windows XP, Windows Vista, and Linux 
The "triple-boot" scenario is actually not difficult, although one might suspect otherwise. The installation sequence is specific though for an easy setup. The installation procedure will be, first, install Windows XP as you normally would. After setup has finished and you are done setting things up the way you want them to be, you will want to install Windows Vista. This will alter the bootloader, and will have the Vista bootloader with an entry for Vista and Legacy OSes (XP and earlier). Once you are done with installing and configuring Windows Vista, you need to install the Linux distribution of your choice. During testing, Ubuntu 6.06 was used, and the GRUB boot menu was properly edited during installation to include an entry for Windows. Although the entry was labelled "Windows XP Professional", when this entry was selected during boot, it would bring up the Windows Vista bootloader and you could then boot either Windows Vista or a legacy operating system. There is a chance however that the installation of Linux will not automatically add an entry for Windows Vista/XP. In such a situation, one should follow the first section about adding an entry for Windows to the GRUB boot menu. 

Installation of Linux before Windows Vista 
While this situation is not the ideal situation, it is not hard to fix. This should just involve re-installing GRUB. This can be done by using the following directions. First, open up the terminal and run the following command as 'root': 
Code: 
grub 

This will bring up the GRUB shell, which will allow you to re-install GRUB. From here, you will need to specify the drive and partition that GRUB is going to be installed (or reinstalled) to. We can do that by using the following command: 
Code: 
root (hd0,1) 

There may be a few changes that need made here depending upon the current setup. First, you need to make sure the drive type is correct. If GRUB is going to be installed to an IDE hard drive, then 'hd', as shown in the example, is going to be used. Otherwise, it will be 'sd', for a SATA or SCSI hard drive. The next item, the '0', is the drive number. Zero (0) specifies that it is the first hard drive in the sequence. If it is the second hard drive, this would be changed to '1' (one) and so on. Keep in mind that numbering starts at '0' so you would take the drive number and decrease it by one for the number used here. The last number, '1' in the example, is the partition where GRUB is to be installed. This partition should be the one that contains the '/boot' directory, and again, numbering of partitions starts at '0', so the above example is installing to the 2nd partition on the physical disk. The last step would be to install GRUB to the MBR, which can be done with the last command: 
Code: 
setup (hd0) 

Which could also require editing, depending on the setup. The drive type would need changed as described above along with the disk number. Since we are installing to the MBR, you will want to specify the drive that currently contains the boot information that is used by Windows Vista. 

From here, we are now done installing GRUB to the MBR and we can exit the GRUB shell by typing: 
Code: 
quit 

After exiting the shell, we can restart the computer and test out to see if the reinstallation of GRUB was successful. If you do not have any entries for Windows, you will need to follow the instructions above in the section on dual-booting as this describes the process of adding Windows Vista/XP to th

---

### Post by Unhindered on 2007-03-28
The problem, of course, is that this isn't a fix for the problem, but a different way to start from the beginning. More of a "told you so" than a help at this point.

It seems that anyone who already partitioned using the Ubuntu install has now permanently destroyed their capability to dual-boot.

---

### Post by rstevesat on 2007-04-02
> **Unhindered said:**
> The problem, of course, is that this isn't a fix for the problem, but a different way to start from the beginning. More of a "told you so" than a help at this point.

It seems that anyone who already partitioned using the Ubuntu install has now permanently destroyed their capability to dual-boot.

Hi Everybody,
                     I have Vista installed on my laptop. Now i want to dual boot with Ubuntu. I burned up  a CD with the Ubuntu.iso as the OS. Now from all the below posts , i am in a confusion that whether it works or not. Can anyone just again repeat the steps pertainnig to my situation so that i can enjoy the UBUNTU freedom. I am a beginner in this field of dual boot. I have a SATA hard drive with 160 Gb capability but My Computer shows two partions HP 6 GB for all the on disk recovery stored and 142 Gb C:\ drive .
Thanks

---

### Post by Titch on 2007-04-17
**Before I begin. I am no expert when it comes to Linux, so am not really the best person to give detailed instructions, but I have had my fair share of experiance with Windows.**

Have you tried using an old XP disk (use this as it is more likely to work initially) you may have lying around to Fix the Master Boot Record (boot from install CD then it asks if you want to install or **Repair a current installation of Windows** next you will get a DOS style screen from the command line type FixMBR) then try following it up with a Vista repair. Then finally you maybe able to either reinstall GRUB and set up to dual boot or try completely starting again with Ubuntu.

**Full details of my senario......**

I installed Ubuntu on a second HDD (HDD 2).
All my documents, and family photos (all irreplaceable) were on a second partition on the same drive as Vista (HDD 1) and this drive was completely inaccessible accept when I logged into ubuntu when the files were read only, but I was able to rescue all these precious files by putting them onto an external USB HDD. 

It was at this point I felt it was safe to scrub the vista HDD, remove Ubuntu and all associated partitions on HDD 2 and start all over again. After doing this I still couldn’t load Vista installation while HDD 2 was still connected, so what I did was to try an old XP disk and run Fixmbr with HDD2 connected only. 

That was it, I was now free to reinstall Vista. And everything so far is going ok, I still need to reinstall Ubuntu which I will put on HDD 1 with Vista.

Fixmbr is non destructive normally but should be used with caution. In my case HDD 2 was 500Gb with all my music and videos on so was running a risk of loosing the lot but all partitions were left intact and only the Master Boot Record was altered.

I do believe if I had run Fixmbr before wiping HDD 1 I would still have the original install of Vista working with all documents intact but starting again was a good thing as now I will install Vista and Ubuntu on one drive keeping both OS’s separate from all personal documents, photos and media files.

After everything I still do not see why anyone would choose Linux over Windows for day to day computing.  Don't get me wrong I ain't give up on it and I am going to reinstall it and endevor to get it working

---

### Post by Titch on 2007-04-17
Sorry mistakingly posted same thing twice

---

### Post by zencoder on 2007-04-17
I've done a lot of background skimming articles and Googling, after following this thread.  I've got a few links that should help folks in anyone of the three states I've seen described (1. installed linux, Vista mbr is fubar; 2. installed XP/Vista, trying to work out how to use grub/BCD/boot.ini; 3. considering dualboot, fearing the Wrath f Gates for daring to put some free socialist open-source crap on the same system as his shiny new Vista :P)

***Caveat Haxor*** -- I have not yet evaluated ANY of these programs.  The whole BCD thing throws a big effing munki-wrentch into the multi-boot system, and Microsoft doesn't give a flying crap if your Linux boots or not.  I would HIGHLY suggest anyone planning on doing this backup ALL NECESSARY DATA OFFLINE before doing ANYTHING.  Vista could make your XP or Linux OSs easily inaccessible, if you don't do things just right.

Vista BootPRO - [http://www.vistabootpro.org/](http://www.vistabootpro.org/) - "101 best freebie" award winning BCD editor (!) (Windows Vista app)

Easy BCD - [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) - (Windows Vista app)

How to fix MBR in Vista - [http://forums.whirlpool.net.au/forum-replies-archive.cfm/722827.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/722827.html) - Not a lot of detail, but a few crucial statements are made in this thread.  You SHOULD be able to boot from the DVD to a recovery console, and run the bootsect.exe command from there.  (Another user said they kept hanging during the 'green bars loading' screen, from hdd or DVD...are you *certain* you were actually booting from the dvd? Did you force it to boot from the DVD-drive?  I've seen this mistake made before.)

From everything I've seen, you should be able to recover the botsect from the Vista DVD.  If your problem is like mine, it's not recovering the boot sector, but something else equally screwy, like Vista being the active partition but putting the boot files on anther drive/partition. :P

Good luck!

---

### Post by zencoder on 2007-04-17
More info on moving the boot folder and files:
[http://help.wugnet.com/vista/move-boot-loader-files-ftopict44655.html](http://help.wugnet.com/vista/move-boot-loader-files-ftopict44655.html)

---

### Post by eatingorange on 2007-04-18
I know this sounds like an odd solution but it has worked for me each time I've done it. I had the same problem. Installed Ubuntu 6.10 on a working Vista system only to find that Vista would not boot.

This solution requires that you have an XP CD, since Vista CD/DVD will not boot the system either. Go figure.

Boot from the XP CD and choose the system repair option (not the recovery console). It will scan your disk and ask you which installation you want to repair. Choose 1 since it will probably be the only option. It will prompt you for the administrator password for the account. Type in anything as it will certainly fail anyway. Enter the password three times. This will force the XP installer to make a write attempt to the NFTS partition. At this point, the system is as good as fixed.

Next, reboot, choose your Vista installation from Grub. Do the safe mode with command prompt option. The system will load a bunch of drivers and stop at crcdisk.sys. Leave it here for a minute. The drive should light up for a couple of minutes then the system will reboot. Choose Vista again and do a normal boot from the Vista boot menu.

All fixed! Of course, ymmv. But this has worked for me several times. Only gotcha is that you do need an XP CD.

---

### Post by Kenetack on 2007-04-18
This article was very helpful in making my Vista/Ubuntu system boot without errors.  

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

These guys are great.  They take you step by step with screen shots.

---

### Post by Amalthea on 2007-04-24
> **eatingorange said:**
> I know this sounds like an odd solution but it has worked for me each time I've done it. I had the same problem. Installed Ubuntu 6.10 on a working Vista system only to find that Vista would not boot.

This solution requires that you have an XP CD, since Vista CD/DVD will not boot the system either. Go figure.

Boot from the XP CD and choose the system repair option (not the recovery console). It will scan your disk and ask you which installation you want to repair. Choose 1 since it will probably be the only option. It will prompt you for the administrator password for the account. Type in anything as it will certainly fail anyway. Enter the password three times. This will force the XP installer to make a write attempt to the NFTS partition. At this point, the system is as good as fixed.

Next, reboot, choose your Vista installation from Grub. Do the safe mode with command prompt option. The system will load a bunch of drivers and stop at crcdisk.sys. Leave it here for a minute. The drive should light up for a couple of minutes then the system will reboot. Choose Vista again and do a normal boot from the Vista boot menu.

All fixed! Of course, ymmv. But this has worked for me several times. Only gotcha is that you do need an XP CD.

Hi, I am new to this forum (and also to ubuntu). I had the same problem. I tried thousands methods but it seems that yours is the only one that works! I admit that I thought it was strange and probably useless, but I tried and I was wrong  (and at this point I am happy I was wrong) :)
The only negative point is that you must have an xp cd.
However, since I saw this problem unsolved in a lot of forums, I recommend that you tell this method to everyone. Nice done!

---

### Post by Kangming on 2007-04-25
Using an Xp cd worked like a charm--thanks, eatingorange!

---

### Post by robbydek on 2007-04-27
> **eatingorange said:**
> Boot from the XP CD and choose the system repair option (not the recovery console). It will scan your disk and ask you which installation you want to repair. Choose 1 since it will probably be the only option. It will prompt you for the administrator password for the account. Type in anything as it will certainly fail anyway. Enter the password three times. This will force the XP installer to make a write attempt to the NFTS partition. At this point, the system is as good as fixed.

Next, reboot, choose your Vista installation from Grub. Do the safe mode with command prompt option. The system will load a bunch of drivers and stop at crcdisk.sys. Leave it here for a minute. The drive should light up for a couple of minutes then the system will reboot. Choose Vista again and do a normal boot from the Vista boot menu.


Other than the fact that to Repair Windows is to use the Recovery Console and that I didn't have to boot into safe mode to get this to work.  It's a great solution.  Microsoft told me to use my upgrade DVD and that it would fix the problem, but of coarse it's Microsoft and that didn't work.

---

### Post by eap1935 on 2007-04-30
I really want to like Ubuntu, I really do, but the community on these forums doesn't help much. To my regret, I installed Ubuntu on a machine already running Windows 2000, thinking the dual boot bugs would have been worked out by now. So after installing, I select Windows from the grub menu, Windows starts loading and then throws an inaccessible boot device blue screen at me. The only changes I made to the partition table were the ones the Ubuntu installer made when I selected a pre-existing swap partition and a pre-existing ext3 partition for /. 

So I come here for help, and I see you fricking idiots blaming Microsoft and suggesting moronic things like get rid of Windows. This is not an option in the real world, sorry, I need it for work. (You know, to make money so I don't have to live in my parents' basement writing stupid irresponsible crap about how Linux rules and Windows sucks.) This is not a Microsoft problem, this is a serious problem with the Ubuntu installer that basically blows away an existing operating system.

One of the threads that comes up when you search the forums for "inaccessible" is on how to reply to people who say Linux isn't ready for the desktop. You know what would help? Make an installer that actually lets you dual boot and doesn't fry other OSs.

Ubuntu has come a long way in the past couple of years, and I might even try it again next time around. Till then, forum-morons, keep jacking in your parents' basement.

---

### Post by hayim on 2007-07-26
Thanks eatingorange!! I dunno about this dude above me, but orange you must be the smartest forum-moron alive.

I dunno how you came up with that ridiculous solution, but it worked. I stupidly let Dapper LiveCD fumble around with my Vista partition, and that new NTFS had a meltdown. And *why* exactly should this prevent the Vista DVD from booting properly?? Who knows..

Just to reiterate: Orange's solution worked for me!!

Thx! :D

---

### Post by ebrahim01 on 2007-12-04
Hi guys,

I have the same problem, Vista does not boot after I installed Ubuntu.

I tried what orange said above, but he said to only choose the 'system repair' option, not the 'recovery console' option. Theres only 3 options for me, to install XP, to repair with recovery console, or to exit install. Do i just use recovery console?

Please help guys. I really need to get back into Vista to get my files back. Some important files I need for work tomorrow.

Any help would be greatly appreciated. 

Thanks people

---

### Post by ebrahim01 on 2007-12-05
Someone please help!

In desperate need of Help here..

I tried recovery console last night but this command prompt window came up and did not know what to type in so just typed exit. 

Can someone please help?

---

### Post by skydog2004 on 2007-12-30
I found a solution that worked great for me. I just installed gutsy on a new vaio vgn-nr160e laptop, and when I tried to reboot into vista it hung up at crcdisk.sys. (safe boot mode). 
 
After a bit of cursing at the boys in redmond, a bit of googling, more cursing...

I rebooted back  into linux and downloaded ntfsprogs and ran ntfsfix on vista partition. It resets journal and forces a file system check next time windows boots. 
no problems since. 
I can hibernate in both OS's and life is good...

---

### Post by athianos on 2008-07-18
> **skydog2004 said:**
> I found a solution that worked great for me. I just installed gutsy on a new vaio vgn-nr160e laptop, and when I tried to reboot into vista it hung up at crcdisk.sys. (safe boot mode). 
 
After a bit of cursing at the boys in redmond, a bit of googling, more cursing...

I rebooted back  into linux and downloaded ntfsprogs and ran ntfsfix on vista partition. It resets journal and forces a file system check next time windows boots. 
no problems since. 
I can hibernate in both OS's and life is good...
skydog2004 - You have made my life complete.

sudo apt-get install ntfsprogs
sudo umount /dev/sda2 (or whatever your vista drive is - if your not sure use gparted to bring up a graphical image of your drive partitions and then close)
sudo ntfsfix /dev/sda2

reboot selecting the recovery partition at the Grub stage (mine was the first windows option on the list)
Allow windows to attempt to fix itself
After a few minutes the program will ask you to reboot (or will do so automatically)
Reboot Vista (using the normal windows option)

And there you go. Proof for all your friends that it is possible to dual boot. Now you can leave the Vista partition alone and get on with your linux life!

Nice one skydog2004!

---

### Post by greenfrog on 2008-07-18
You have to install Ubuntu with the loader in the superblock, do not use grub to boot your computer.

Grub does not understand the new Vista loader.

Then you install Vista and its loader will load Ubuntu.

That is the only way I way able to dual boot with Vista and Ubuntu.

---

### Post by athianos on 2008-07-19
> **greenfrog said:**
> You have to install Ubuntu with the loader in the superblock, do not use grub to boot your computer.

Grub does not understand the new Vista loader.

Then you install Vista and its loader will load Ubuntu.

That is the only way I way able to dual boot with Vista and Ubuntu.

I think I got Grub and superblock mixed up!

When the computer boots I have a number of options available to me. One of which is my ubuntu kernal. Two are for Vista. I selected each one in turn to figure out what they did!

Thanks for the correction.

---

