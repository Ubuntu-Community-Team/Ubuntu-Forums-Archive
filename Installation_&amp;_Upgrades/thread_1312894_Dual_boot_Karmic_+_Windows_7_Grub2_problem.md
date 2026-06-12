---
title: "Dual boot Karmic + Windows 7 Grub2 problem"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by leejkennedy on 2009-11-03
I have spent a couple of days trying to resolve this, and I'm no further forward so I hope someone can help. I have installed Ubuntu 9.10 on to a 2nd partition on the same disk as Windows 7. Grub 2 has overwritten the windows boot loader and I cannot now boot Windows. 

Ideally i'd like to be able to use Grub2 as the boot loader for both the Ubuntu and Windows OS's

I have tried the following:

[LIST=1]
[*]Windows 7 *is* an entry in the grub boot loader list, however when i select it, my PC just reboots and eventually takes me back to the same grub menu list. (FYI I had selected to install Grub to **/dev/sda**)
[*] I have tried re-installing Ubuntu, formatting the partition, to try and get Grub installed to a floppy or a USB stick. However, neither device is recognised during install and I get a 'fatal error' message (both devices are available from the ubuntu desktop once it's installed).
[*]I have forcibly restored the windows boot loader in the hope of using EasyBCD, however there is no support (or limited beta support) for the Grub2 loader and I haven't been able to get that working either.  
[/LIST]

below are the mappings of the drives and output from the parameter files which I hope will help to pin down the issue:

**results of 'sudo blkid'**
[PHP]
/dev/sda1: UUID="1EB0F35FB0F33C39" TYPE="ntfs" 
/dev/sda5: LABEL="ubuntu" UUID="04709c71-7d70-4872-9ea0-1944c0ea5cb6" TYPE="ext4" 
/dev/sda6: TYPE="swap" 
/dev/sdb5: UUID="CE68E8CD68E8B4FD" LABEL="Data + Media" TYPE="ntfs" 
[/PHP]

**results of 'e' on GRUB boot menu:**
[PHP]
recordfail=1
if [ -n ${have_grubenv} ] ; then save_env recordfail; fi
setquiet=1
insmod=ext2
set root = (hd0,5)
search --nofloppy --fs --uuid --set 04709c71-7d70-4872-9ea0-1944c0ea5\cb6
linux /boot/vmlinuz-2.6.31.14 generic root=uuid=04709c71-7d70-48847-9\ea0-1944c0ea5cb6 ro quiet splash
initrd /boot/initrd.img.2.6.31.16-generic
[/PHP]

**results of grub.cfg**
[PHP]
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 04709c71-7d70-4872-9ea0-1944c0ea5cb6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=04709c71-7d70-4872-9ea0-1944c0ea5cb6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 04709c71-7d70-4872-9ea0-1944c0ea5cb6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=04709c71-7d70-4872-9ea0-1944c0ea5cb6 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1eb0f35fb0f33c39
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
[/PHP]

Thanks

Lee

---

### Post by perchrh on 2009-11-04
I've had similar problems (not resolved) with Windows 7 64-bit. It seems that not everyone has this problem. Is your Windows-install 64-bit as well?

---

### Post by leejkennedy on 2009-11-04
Yes, it is the 64 bit install. I've tried both the desktop and alternate install discs but the same symptoms remain.

---

### Post by halj32 on 2009-11-04
Have you tried using the windows boot loader, the easiest way is edit with EasyBCD, just point EasyBCD to your linux partition & save

---

### Post by leejkennedy on 2009-11-04
Yep tried easybcd but ver 1.7 doesn't support grub2 and I couldn't get the v2 beta working as it started to get very technical talking about chainloading. To be honest I'd rather use grub2. Just got to get it working!

I'with going to try wiping ubuntu and installing the 32bit desktop install to see if that works (and confirms a possible bug in the 64 bit versions)

---

### Post by halj32 on 2009-11-04
EasyBCD will use the windows 7 bootloader not Grub, then you dont have to do anything.

---

### Post by leejkennedy on 2009-11-04
Ok... have now tried 32bit Desktop Ubuntu and the same problem: Selecting Windows 7 from the grub menu simply reboots my PC. And to confirm, as i don't think i was clear in my earlier posts, i'm using 64 bit Windows 7.

I have now also tried installing a separate boot partition but that has made no difference. partition layout is:

[LIST]
[*]Windows on SDA1
[*]Boot on SDA5
[*]Swap on SDA6
[*]Ubuntu on SDA7
[/LIST]

Does anyone have any other feedback other than installing easybcd? 
Thanks...

---

### Post by bfoster on 2009-11-04
Not meaning to highjack this thread but the last poster "halj32" advised to use the Windows 7 bootloader. This is exactly what I would prefer.

Currently I have 1 HDD divided into two partitions. The 1st partition has XP and the 2nd has Windows 7. The 2nd HDD has a 50GB partition that I used to install Unbuntu 9.10 to and the rest is NTFS for data storage.

After I installed Ubuntu GRUB2 installed of course and I was able to boot into Ubuntu or Windows 7. It did not see the XP partition for some reason.

At any rate I would prefer to use the Windows 7 boot loader and be able to choose XP, Win 7 or Ubuntu from there. I used EasyBCD 2.0 BETA to reinstall the Win 7 bootloader to the MBR and then I tried to add an enttry for Ubuntu. I am doing something wrong at this stage because if I choose Ubuntu from the boot menu I get the error "BOOTMGR is missing". 

Can someone tell me how I need to set this up with EasyCBD?

Thanks

---

### Post by leejkennedy on 2009-11-04
Sorry, can't help... i tried installing easybcd 2 beta and couldn't get it to work, that's why i've tried to use this post to get some feedback about how to get grub working 

... would suggest that if you're trying to exactly the opposite of me that you set up a new thread ;) ......

---

### Post by JimmieC on 2009-11-04
I'm running Windows 7, 64 bit and Ubuntu 9.10 64 bit on a Asus laptop and I'm having no problems. One hard drive, two partitions. Ubuntu installed first on first partition, then installed Windows 7 on second partition, then re-install grub to MBR. There are many posts on this forum on how to re-install grub.

Good luck,

Jim

---

### Post by leejkennedy on 2009-11-05
I've not only re-installed grub, I have re-installed ubuntu now around 7 times.

I'm pleased you're not having any problems, but the numerous posts on this forum, and elswhere, on how to reinstall grub haven't worked. Perhaps there's an experienced linux user out there who could offer some real advice to help solve this?

---

### Post by artix123 on 2009-11-05
Try putting Windows 7 install disc, startup repair *numerous* times to boot into Windows, then run Ubuntu LiveCD,

I can't find the website I used, this is from memory.

[I]sudo mount /dev/sda1 /mnt
(change sda1 to your boot partition)
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot
grub-install /dev/sda

[/I]edit: I'm not very sure of my steps, try searching for tutorials online?
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

---

### Post by tejas81 on 2009-11-05
I might be able to help some of you here, or atleast let you look in the right places.

My system is a little crazy:
hd0: ubuntu 9.10 + grub2
hd1: Windows XP BUT .. I had previously installed and uninstalled Windows 7 RC, so hd1 has a Windows 7 boot loader loading up XP.

When I earlier had grub-legacy, I had added the following to menu.lst to make XP boot
map (hd0) (hd1)
map (hd1) (hd0)

This is because XP looks at \boot.ini (check this file out if you can) and looks to load from the first hard disk rather than the second. I am guessing Windows 7 does not need the drive mapping.

In grub2, map()() has been replaced by:
drivemap -s hd0 hd1

To try this out, boot into grub2 console, and edit the Windows entry. Right after the line "root (hd1,..)" add the above line.
And try to boot it.

To make it a *permanent* change:
This needs to be part of the relevant entry in /boot/grub/grub.cfg, so I took a look at the shell script that adds it: namely /etc/grub.d/30_os-prober

Sure enough, this script does not add the line for Windows Vista/7 bootloaders, but adds it for everything else. In my case XP needed it, so I modified the script to output this line for every OS. Then ran "sudo update-grub2" to add this line to grub.cfg

And it worked.

---

### Post by Cushie on 2009-11-05
> **leejkennedy said:**
> ..

**results of 'sudo blkid'**
[PHP]

[COLOR="Black"]/dev/sda5: LABEL="ubuntu" [/COLOR]UUID="04709c71-7d70-4872-9ea0-1944c0ea5cb6" TYPE="ext4" 


**results of 'e' on GRUB boot menu:**


set root = (hd0,5)

root=UUID=04709c71-7d70-4872-9ea0-1944c0ea5cb6 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
Lee

Back to your original post, it may be worth checking the partion labels.  Ubu is on sda5 = hd(0,4) but Grub has root on hd(0,5) which seems to me to be an error.  Also check the  same for UUID for the / partition, it seems there may be a mis match to me. (non expert)

Good luck, I'm having a similar problem with Grub 2 on a dual drive but have no solution yet.

---

### Post by tejas81 on 2009-11-05
> **leejkennedy said:**
> I've not only re-installed grub, I have re-installed ubuntu now around 7 times.

I'm pleased you're not having any problems, but the numerous posts on this forum, and elswhere, on how to reinstall grub haven't worked. Perhaps there's an experienced linux user out there who could offer some real advice to help solve this?

My post on this thread reg my own situation may not help you, as mine was a problem with drivemapping while you have only one HDD.

The other thing I can suggest to you is to alter the parameter passed to chainloader. The default "+1" simply tries to load off the first block of the HDD. chainloader can also be used as:
chainloader <bootfilename>

I had tried "chainloader /ntldr" thinking this is the XP bootloader, but it did not work, giving me an "Invalid signature" message. If you can figure out the rightloader for Windows 7 to pass it, it might work. In the grub console, set root to whatever partition Windows is on. You can do a "ls /" to see all the files on that partition.

Give it a try, I wish grub2 documentation was more solid, so we can figure out exactly how to use chainloader.

---

### Post by Hachamacha on 2009-11-06
I installed U910 first (64 bit), on an entire notebook drive, decided it worked well, and then used gparted to squeeze a new NTFS partition in for installing w7 64 bit pro.

Here is the entry I generated, and I just hacked it into menu.cfg of grub2 (so /boot/grub/grub.cfg). I didn't see any sign that using any documented grub2 methods were working correctly (the /etc/grub.d/{10/20/30/40}* stuff). 

menuentry "Windows 7 Pro 64 bit" {
        insmod ntfs
        set root=(hd0,4)
        search --no-floppy --fs-uuid --set D6A06EADA06E9431
        chainloader +1
}

(of course, figure out the block ID using blkid /dev/sdaX (where X is where you installed windows))

That worked fine along with the standard grub2 entry for ubuntu910 64b. 

Keep in mind, of course, that grub2 has a bug(many bugs) that require you to hold down the shift key to see the menu on some installs, or else it's off an running to oblivion.

--

Anyway, first thing I did after installing u910 was to save off the headers of each disk/partition as follows: mkdir prior-to-w7/headers ; dd if=/dev/sda count=1 bs=512 of=sda.bin ; dd if=/dev/sda[1-4]* count=1 bs=512 of=sda[1-4]* ; 

Possibly also put them on a small pen drive. At least you can repair your damage.

Install W7 using custom install and stick on your NTFS partition. This of course overwrites /dev/sda, with the windows bootloader, which is nearly useless for grub2, well useless.

Go back into ubuntu via the install disk, and mount your original partition whatever it is, and restore the /dev/sda first 512 bytes. (dd if=/prior-to-w7/headers/sda count=1 bs=512 of=/dev/sda) and you are back to grub2. Edit the grub.cfg file as I mentioned above. 

(umount the /mnt/{yourExt4driveFromUbuntu910}) and reboot, and hold down the shift key right after POST so you can see the menu. Pick Windows or Ubuntu and they should both work.

Grub2 command line works fine once you figure out how the clauses work. 


--

Now if you are determined to use the windows bootloader, I think it can be done, but BCDEDIT , especially that crazy gui version isn't the best thing. There's a better working non-gui version I've used with success using this type of techique: Figure out where your 910 install really is. It is likely that 910's bootloader (grub2) is the first sector of /dev/hda, so get it on a memstick, and copy it to C:\grub2.bin or some such thing in win 7. 

Bcdedit can only work if the windows boot loader is on /dev/hda, so let bcdedit tell you it needs to restore it and do that, or just use the recovery mode of the w7 boot disk. Then you can't boot linux until you figure this out.

Google up the cmd line options for bcdedit, and create an entry called something like:

"u910 64 bit" C:\grub2.bin 

(I'm forgetting the exact syntax, but you can verbatim use whatever used to work with XP and grub1. 

Save this using bcdedit, and give it a shot. Nothing is guaranteed because both bootloaders are new and unwieldy so far, and 1/2 their functionality is missing or buggy. I can say that I've gotten both ways to work, and I dislike both ways more than the old grub1 and XP bootloaders, but have to keep up with things. AT least grub2 and w7 are "supported" now.

Good luck.

Hashi

---

### Post by Hachamacha on 2009-11-06
Addendum to the last message: I just realized there is a new grub2 update for 910 today, so I installed it, and the menu is now visible via the /etc/default/grub & /etc/grub.d/* setup and it also finds and displays the other OS's without much work. 

It seems a bit more friendly now. I can just boot the laptop, choose from Win 7 or Ubuntu 910 (both 64 bit) and it works.

---

### Post by nepapape on 2009-11-07
Well I ve had the same problems but I finally did it! Its now fully functional.
Here is the full story.

I installed windows 7 and then I installed Ubuntu Karmic in a new partition.
In the bootloader options I checked "Install boot loader over windows boot loader".
Then I rebooted and I found out that even though there was a "windows 7" line between the boot options, when I checked that, it simply refreshed the boot loader page.

Then I inputed the win 7 cd and I "repaired" the system..
But still no change. The windows boot repaid found no problems!

So I opened the command prompt and I typed (while you are on the root directory. Type "cd .." untill you get there.): 
bootrec /FixMbr
and then
bootrec /FixBoot
As stated [here]("http://support.microsoft.com/kb/927392").

But now I didn't had the Ubuntu option at all!

So I installed the easyBCD and tried to fix it.
The problem was that only the beta version supports grub2 which is used by Ubuntu Karmic. 
So you must register in the [site]("http://neosmart.net/forums/showthread.php?t=642") , download easyBCD 2.0 beta and input a new entry for Ubuntu.
Be careful to use the grub2 option.

And now you have a system with dual boot!! :-D

ps: During one Ubuntu Update grub2 was installed again and Windows 7 were once again not functional..
I tried to insert win 7 CD and do the same process but an error message kept appearing.
So I tried a windows vista CD and It worked!!!

---

### Post by leejkennedy on 2009-11-08
Unfortunately none of the suggestions received so far have resolved the issue of the pc rebooting when selecting the windows 7 entry from the grub2 menu. I have since raised this as a bug.

I have confirmed that the windows entry in grub.cfg matches the format expected and is *definitely* pointing to the correct partition where windows is installed: (hd0,1). Grub is correctly installed to /dev/sda so the config *appears* to be as would be expected to successfully boot Windows from the GRUB2 menu.

I can also confirm that if I re-install the windows boot loader, Windows boots without error, 1st time. As the only thing I'm changing each time is the grub2 bootloader, I can therefore conclude that it is the grub2/windows 7 boot loader combo that is the problem on my pc setup.  I believe that other have raised a similar issue with their systems re-booting windows 7 from GRUB2 so i hope the devs eventually figure out what's going on.

BTW i bought a laptop over the weekend which had 32 bit Vista pre-installed. Followed the same steps (resized the Windows partition, installed Ubuntu to the free partition and installed GRUB to /dev/sda (hd0)) and rebooted to see if i could replicate the issue with my desktop, but it worked first time and without any further configuration. So more evidence if any were needed that the issue is the GRUB2 / Windows 7 boot loader. from similar bugs posted the problem may only be with Windows 7 64 bit versions, but I am unable to confirm as i don't have a copy of 32 bit Windows 7.

Following recent responses, I have since tried re-installing EasyBCD V2 Beta and successfully created a chain loader entry to GRUB2. I'm not particularly overjoyed at having to use yet another piece of software to get this config up and running but at least it works I suppose :p

---

### Post by leejkennedy on 2009-11-08
> **artix123 said:**
> Try putting Windows 7 install disc, startup repair *numerous* times to boot into Windows, then run Ubuntu LiveCD,

It isn't necessary to run the Windows 7 MBR repair any more than once:
[LIST]
[*]Boot from the Windows 7 boot disc
[*]Select the region and click next
[*]Select the option to repair the system at the bottom left-hand corner of the screen
[*]Select the option at the bottom of the next screen to get to a command prompt
[LIST]
[*]Type 'bootrec /fixmbr'
[*]Type 'D:\boot\bootsect.exe /nt60 all /force' (where D:\ is your CD\DVD drive) 
[*]Type 'del c:\boot\bcd'
[*]Type 'bootrec /rebuildbcd'
[*]Type 'exit'
[/LIST]
[*]Click restart and the Win7 boot loader should now have been reinstated.
[/LIST]

---

### Post by leejkennedy on 2009-11-08
> **nepapape said:**
> ps: During one Ubuntu Update grub2 was installed again and Windows 7 were once again not functional..
I tried to insert win 7 CD and do the same process but an error message kept appearing.
So I tried a windows vista CD and It worked!!!

nepapape: can you please explain the steps that allowed you to use a Vista boot loader on a windows 7 install as i just get an error saying that the underlying subsystem was not available for this image (or something very similar) when I try to repair the MBR as described above using the Vista repair console.

---

### Post by devi59 on 2009-11-08
Mine is the same but different. Running grub-update EASILY puts the windows 7/vista loader back into the grub menu. I can boot into ubuntu fine doing that. I can even "technically" get into Windows 7. My problem is when the 4 colored balls are coming together on boot to make the windows flag, right before it makes the full flag, it freezes and I see a BSOD but it goes so quick I can't see what the problem with it is. I have been able to quickly hit F8 before it loads and it brings up the menu. It crashes the same way trying to load Safe Mode, Recovery mode doesn't see a proper windows installation and I have set it to not automatically reboot and I see then BSOD with 0x000000007b error which according to google is Invalid Boot. Anyone figured this one out?

---

### Post by corticyte on 2009-11-08
> **tejas81 said:**
>  To make it a *permanent* change:
This needs to be part of the relevant entry in /boot/grub/grub.cfg, so I took a look at the shell script that adds it: namely /etc/grub.d/30_os-prober

Sure enough, this script does not add the line for Windows Vista/7 bootloaders, but adds it for everything else. In my case XP needed it, so I modified the script to output this line for every OS. Then ran &quot;sudo update-grub2&quot; to add this line to grub.cfg

And it worked.

 I think I have a fix: First use the Windows 7 DVD to restore the Windows bootloader to the MBR:

```
bootrec /fixmbr
```then

```
bootrec /FixBoot
```Then reinstall grub2 to a partition other than the one windows 7 is installed on. I haven't figured out how to do this yet. 

Finally, add the line 

```
drivemap -s hd0 hd1
```under the line "root (hd1,..)" in grub.conf (either manually which is not recommended, but I did it anyway, or by the method that tejas81 used)

Reboot and hopefully you should be able to boot into Windows 7 again! Good luck

---

### Post by flamencoguy on 2009-11-08
My experiences as a long time Windows user installing Ubuntu 9.10
I had Windows 7 Ultimate 32 bit installed on my PC.
I had a spare 320 GB Sata2 HD that I wanted to use for other OSes.
Downloaded Ubuntu and made a CD. Booted from CD and created 2 partitions.
The necessity to create 2 partitions threw me off abit. Windows requires only 1 partition and uses a swapfile within the file system whereas Linux requires a separate partition. This is much more complicated for a non-techy. i.e too many decisions about size of each partition and where on the drive to put them (beginning or end )
Install proceeded after answering a few questions about keyboard and timezone.
Everything worked and I was able to boot in Ubuntu. But I wanted Windows to be my primary OS, It should always be the default especially after a Windows Update or an antivirus update that requires an unattended restart. 
Searched for a way to do this. Found many old instructions that a file called
/boot/grub/menu.lst should be edited. I could not find this file. Instead after some poking around I found /boot/grub/grub.cfg. Apparently this is the new file used by Grub2, the sucessor to Grub.  Back to searching on how to edit this file.
I am brand new to Unix/Linux type commands although an experienced Windows user as well as a mainframe programmer. (Yes I am that old).
 
Found that you need to start a terminal session/window. It was fairly easy to do.
then type  
 
      sudo chmod +w /boot/grub/grub.cfg
 
then
 
      sudo nano /boot/grub/grub.cfg
 
The 1st line changes the file attributes to writable from read only.
I was prompted for a password after the 1st command
 
The 2nd line command opens the file in another window using the simple nano file editor.
This is not even as good as Notepad in Windows.
 
After browsing the file and figuring out that there are 5  "menuentry" sections each one for a different boot selection and saw that Windows 7 was the 5th entry but that the offset number should be 4 if the 1st entry is offset 0. Or you can think of it as a relative entry
I changed "default = "0"   to "default="4". Then comes the hard part.
How do I save this file? No SAVE option it in file menu like in Notepad.
 
At the bottom of the Nano screen were what appear to be a menu of key strokes to perform some operations. I figured ^O WriteOut was the equivalent of Save. But what key stroke was ^? Is it the shift 6 key? Heck no. It is the symbol for the CTRL key.
Why could it not be mention somewhere like ^=Ctrl. Better still implement these commands on the Menu bar in drop down menus. I bet this would only be a little more work.  And please Linux/Unix types use Save and not WriteOut. Try to use common language and terminology. 
 
After I figured how to save the file. I restarted the system which then fired up Grub with Windows 7 highlighted. 
 
But apparently the Grub.cfg file could be overwritten in the future 
if Grub is updated. You could just rededit the file again when that happens.
 
Or you could fix the templates mentioned at the beginning of the file.
The DO NOT EDIT THIS FILE warning mentions those files. I have not looked iinto it yet.
 
This is a rather long post but I wanted to write in a clearer and simpler style hopefully and not like the many terse posts in this forum. They assume a certain level of knowledge.
 
I hope to learn more about Ubuntu in the coming months time permitting.
 
Another solution is to use the Windows 7 bootloader to be the boot manager.
the way to do this is via EasyBCD [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
 
This allows you to reinstate/restore the Windows 7 bootloader and let it give you a menu as to which OS to boot up.
 
And finally another solution is to let Acronis OS Selector be your OS menu.
[http://www.acronis.com/homecomputing/products/diskdirector/multibooting.html](http://www.acronis.com/homecomputing/products/diskdirector/multibooting.html)

---

### Post by perchrh on 2009-11-09
One thing we haven't considered is if the partition with Win7 64-bit is marked as active or not (in the partition table). 
The following command shows the partition table and displays a * (star) in column two for active partitions. It would be interesting to see if the systems with working win7-64 boot from grub2 differ from the others in this respect.
```
sudo fdisk -l /dev/sdX
```


EasyBCD 2.0 beta with grub2 support solved my problem too.

---

### Post by krash1220 on 2009-11-10
I was having the same problems as everyone else, with Windows 7 and Grub2. If you don't want to go through all the heartache and  you don't want to install EasyBCD, simply install Grub2 to a USB flash drive. [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

Worked like a charm. I did have to repair Windows 7 bootloader with the commands bootrec /fixmbr and bootrec /FixBoot but then I booted to the USB flash drive and now I can boot to Windows 7 or Ubuntu 9.10. Plus you can edit the grub.cfg files without worry.

---

### Post by tbone7 on 2009-11-11
Today I attempted the dual boot combination of Ubuntu 9.10 and Win7. I installed Win7 first, then Ubuntu afterwards. Both 64-bit and both on the same disk, but on different partitions. I manually configured the partitioning when installing Ubuntu, and made Grub 2 aware of the Win7 bootloader (under 'Advanced' in the installation process). After a while I realized that Grub 2 wasn't able to boot Win7, even though it was an option in the menu (like described by some of you guys earlier in this thread). When I opted for Win7 the screen just went black for a second, before the menu reappeared. Choosing Ubuntu in the menu worked fine.

A couple of hours, one dinner, some bottles of water, and several paragraphs later I have now fixed it. All I can say is that it's fantastic the magnitude of information the Internet holds in 2009. Basically I used a combination of methods described earlier in the thread (and elsewhere I think, can't remember all the sources right now).

The recipe: I booted from the Win7-dvd and navigated through the menu to get to the 'Repair'-section, where I clicked on the command line-option. There I executed 'bootrec /fixmbr' and 'bootrec /fixboot', before rebooting. This will make the Grub 2-menu disappear, and it will boot right into Win 7. At least it did for me. However, concurrently, I magically replaced the Win7-dvd with the Ubuntu 9.10-cd to boot from the Ubuntu Live CD. That is because I couldn't be bothered creating a Grub 2 USB disk as suggested earlier, so instead I followed the procedure detailed [here]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD"). Don't worry, although it's an external link it doesn't include dozens of intricate commands to execute. After entering the Ubuntu Live-system you just need to mount (click on) the disk that holds your installed Ubuntu OS. Then, carry out step 2 and 3 in Herman's excellent guide. After doing that, and rebooting, I had planned to finish the whole procedure by running ['sudo grub-mkconfig -o /boot/grub/grub.cfg']("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig") in the installed Ubuntu. However, I had already done that previously (as a part of my trial & error run). So I decided to try the boot options right away (you guys may (!) have to go through with the previous command to reconfigure Grub 2). Indeed, Grub 2 was visible again, and furthermore, to my great joy, both the Ubuntu Karmic and the Win 7 boot options were functional from the menu :D

To summarize: I can confirm that Ubuntu 9.10 and Windows 7 in dual boot through Grub 2 is possible, even with a full 64-bit system.

---

### Post by phreeky on 2009-11-20
> **tbone7 said:**
> To summarize: I can confirm that Ubuntu 9.10 and Windows 7 in dual boot through Grub 2 is possible, even with a full 64-bit system.

Could you please post the contents of your grub.cfg file.

I have a new PC with a windows7 "restore" disk, not a proper Windows7 disk so cannot follow said procedures. However I did backup my Windows7 MBR, and when I put it back in place Windows7 still boots fine.

---

### Post by darkod on 2009-11-20
Mine experience is entirely positive! And 9.10 is my first touch with Ubuntu. After it was released I have installed it as dual boot with Win7 on both my netbook and desktop. I find it easier when you have only single drive not to touch anything in Advanced (wasn't even aware of those options when I was installing), with a single drive Grub2 will go to the only MBR anyway.
On both the netbook and desktop it picked up Win7 automatically and works perfectly. Also, the netbook has the 100MB win7 boot partition while the desktop doesn't, still working fine.
By reading lots of posts here I am starting to think that people get afraid to let grub2 overwrite the windows MBR and accept suggestion to put it on a partition instead of the MBR, and that only gets them deeper into trouble, especially newbies.
Another situation for problems is if the computer has one or more of those recovery/utility partitions, some of them are created in a weird way it seems. I just helped someone who couldn't boot vista at all after installing Ubuntu. After days of troubleshooting and nothing worked, just deleting a utility FAT32 partition that he was never even using, sorted everything out immediately.
My advice: don't be afraid of grub2 on MBR. Install win7 first, always better option, and always on first partition (or second, if you have recovery/utility, but not beyond that). Don't forget windows doesn't always play nice at the back of the drive, while linux doesn't mind that. Then simply install linux and if you have single drive don't even go into Advanced options, grub2 will sort everything out.
If it doesn't work, it's worth troubleshooting first instead of panicking and reinstalling everything again. Very often things can get sorted out and that's how you learn new things.

All of the above is IMHO. :)

PS. I see people are wondering about 32bit and 64bit too. On the netbook they are both 32bit and on the desktop 64bit.

A HINT ABOUT THE 100MB BOOT PARTITION: About the 100MB boot partition created by the win7 installer. If you have only single hdd and you don't want to "waste" a primary partition for a not needed 100MB boot partition, and plan to dual boot with Ubuntu, you can do this: If you have the option to start with clean installs, do NOT create your first partition for win7 using the win7 installer. In that situation it will give you a message that 100MB boot partition will be created (from what I have seen, still not 100% sure). But it doesn't create it if you already have existing partition for it. So just boot with ubuntu cd, select Try Ubuntu option, use Gparted to create the first ntfs partition with size that you want for your win7 system partition, then boot with win7 dvd and tell the installer to use the existing partition. That way you save one primary partition which is no small thing with dual boot on single drive sometimes. You do not have to create the other partitions in advance, just the one for win7 system to avoid its installer creating the 100MB one. You will create the rest of the partitions when installing Ubuntu at the partitioning screen.

---

### Post by tbone7 on 2009-11-20
> **phreeky said:**
> Could you please post the contents of your grub.cfg file.

I have a new PC with a windows7 "restore" disk, not a proper Windows7 disk so cannot follow said procedures. However I did backup my Windows7 MBR, and when I put it back in place Windows7 still boots fine.

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set a4b6c4a0-9b03-46e6-b8ae-43ed7447abc1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set a4b6c4a0-9b03-46e6-b8ae-43ed7447abc1
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a4b6c4a0-9b03-46e6-b8ae-43ed7447abc1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set a4b6c4a0-9b03-46e6-b8ae-43ed7447abc1
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a4b6c4a0-9b03-46e6-b8ae-43ed7447abc1 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 00b06724b0672000
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

Understand that my grub.cfg file most probably was correct all the time. At least the details for the Win 7 boot option never changed. The important thing is to reactivate your Grub 2 after restoring the Win 7 MBR.

> **darkod said:**
> A HINT ABOUT THE 100MB BOOT PARTITION: About the 100MB boot partition created by the win7 installer. If you have only single hdd and you don't want to "waste" a primary partition for a not needed 100MB boot partition, and plan to dual boot with Ubuntu, you can do this: If you have the option to start with clean installs, do NOT create your first partition for win7 using the win7 installer. In that situation it will give you a message that 100MB boot partition will be created (from what I have seen, still not 100% sure). But it doesn't create it if you already have existing partition for it. So just boot with ubuntu cd, select Try Ubuntu option, use Gparted to create the first ntfs partition with size that you want for your win7 system partition, then boot with win7 dvd and tell the installer to use the existing partition. That way you save one primary partition which is no small thing with dual boot on single drive sometimes. You do not have to create the other partitions in advance, just the one for win7 system to avoid its installer creating the 100MB one. You will create the rest of the partitions when installing Ubuntu at the partitioning screen.
That's a good tip ;-)

---

### Post by spiffwalker on 2009-11-20
I haven't installed Karmic Koala yet, but what people could try is to first install karmic koala.  Then once it's installed,  boot onto a Jaunty live cd.  Once in, delete the current grub directory from within your /boot directory.  Then from the jaunty live cd run the command "grub-install," and specify your Karmic Koala partition. This should install grub1 on your newly installed Karmic Koala, the same old grub you know and love.  Again, I have not yet updated to Karmic, so i have no way to confirm this, but if anyone tries it, please let me know.

---

### Post by Zefal on 2009-11-30
Hi Guys,

Have the same issue (my windows 7 is a RAID volume on Intel ICH9R controller - not sure if this is cause) and Karmic on single drive on same controller.

I gave up trying to use grub2 as I'm new to it and found myself confused trying to configure the new os-prober file. So I then tried removing grub2 and installed grub-legacy. I couldn't get this working either!

The easyBCD workaround works great for me. I put windows 7 in control of boot again and installed easyBCD ( [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) ) Although you need to sign up to forums and get Beta v2 version for Windows 7. I then put Linux GRUB2 option into the Windows 7 boot manager. This worked a treat and can boot into Win7 or Ubuntu that way. Not exactly a fix but a definite work around until someone comes up with solution. :D It should also work for people triple/quad boots as you can boot to pretty much anything with EasyBCD.

Thanks

Paul

---

### Post by frogotronic on 2010-01-21
Does this link help?

[http://www.dedoimedo.com/computers/grub-2.html#mozTocId722095](http://www.dedoimedo.com/computers/grub-2.html#mozTocId722095)

- CH

   :popcorn:

---

### Post by leejkennedy on 2010-01-21
No, sorry, the link to the Grub2 bootloader help doesn't really help me and the problem remains. 
 
To recap, I have followed all instructions but cannot get either either 32bit or 64 bit Ubuntu Grub2 to boot a 64 bit windows 7 installation. Both 32bit + 64bit Ubuntu installations of Grub2 will successfully boot a 32bit windows 7 installation without the need for any additional set up on the windows machine (such as EasyBCD). I have had to create an option to chainload to GRUB2 on boot via the easyBCD bootloader to make my current set up work.
 
Having read some of the other forum posts, I believe there to be a problem with the Grub 2 software and have posted a bug accordingly.

---

### Post by kamabah on 2010-02-14
I had the same problem and I've been able to solve after a long search on different sites. Unfortunately, I don't remember all the things I did. So just let you know, ther is a solution very developped by a contributor. My system works now perfectly well, a HP pavilion dv4-1225dx, with 1 HD, 2 partitions, windows 7 and Ubuntu karmic 9.10;
Good luck

---

### Post by AintJoe on 2010-02-15
> **kamabah said:**
> I had the same problem and I've been able to solve after a long search on different sites. Unfortunately, I don't remember all the things I did. So just let you know, ther is a solution very developped by a contributor. My system works now perfectly well, a HP pavilion dv4-1225dx, with 1 HD, 2 partitions, windows 7 and Ubuntu karmic 9.10;
Good luck

Easily the least helpful post ever. I'm happy that your system works, but mine doesn't. Do you think you could try a little harder to remember what you did? Or where you got it? Or what you searched for?

---

### Post by darkod on 2010-02-15
> **AintJoe said:**
> Easily the least helpful post ever. I'm happy that your system works, but mine doesn't. Do you think you could try a little harder to remember what you did? Or where you got it? Or what you searched for?

This thread is getting old. I understand more people can have same/similar problem but it's often better to open your own thread with more specific info about your exact issues. Sorry if you have them explained here, it's too long to go back now.
I'm not a great expert but create a new thread with your problems or even better post the results.txt content from the Boot Info Script and I'll have a look. So will others probably.

---

### Post by leejkennedy on 2010-02-16
@Darkod: this post may be getting old, but part of the problem is pointless posts by trolls like @kamabah. Yours is the first post in this thread that has offered any suggestion of one-to-one help. Until ubuntuforums offers the functionality to remove troll posts like this, my feelings of frustration with this whole forum help process will only grow as I believe the positive aspects of the forum breaks down when the community allows this to continue.

As an experienced user/poster, I assume from the number of beans you have acquired, I would have thought you would agree with @aintjoe rather than overlooking his comments outing an obvious troll?!

I'll post any information you feel is necessary, above the information I've already provided, if you still wish to help. Some assistance in generating it may be needed...

Thanks.

---

### Post by darkod on 2010-02-16
> **leejkennedy said:**
> @Darkod: this post may be getting old, but part of the problem is pointless posts by trolls like @kamabah. Yours is the first post in this thread that has offered any suggestion of one-to-one help. Until ubuntuforums offers the functionality to remove troll posts like this, my feelings of frustration with this whole forum help process will only grow as I believe the positive aspects of the forum breaks down when the community allows this to continue.

As an experienced user/poster, I assume from the number of beans you have acquired, I would have thought you would agree with @aintjoe rather than overlooking his comments outing an obvious troll?!

I'll post any information you feel is necessary, above the information I've already provided, if you still wish to help. Some assistance in generating it may be needed...

Thanks.

The post you mentioned was definitely not helpful with anything. But I also went through all 4 pages and aintjoe also doesn't have a single post explaining his/her problem. You have to consider the perspective of someone trying to help too, just saying I have the same problem is often not enough. In fact the problem might not be identical even if it looks like that, so the solution might not be the same.
Yes, people should read the forums to find a solution about their problem, but if they don't, or it doesn't work for them, creating their own thread is usually the best way to proceed.
And if you still have any issues, because I thought yours are resolved, please post here or in a new thread the content of the results.txt file created by the boot info script in my signature. You can run it with:

sudo bash ~/Desktop/boot_info_script*.sh (if it's on the desktop)

I'm not a great expert but I'll take a look at it if I can help.

PS. I just read backwards in your posts and it seems you made it work with EasyBCD. I agree it's strange to need to use it at all, but if it worked for you, you might not want to touch the system any more. :)

---

### Post by HarryZontal on 2010-04-12
> **devi59 said:**
> Mine is the same but different. Running grub-update EASILY puts the windows 7/vista loader back into the grub menu. I can boot into ubuntu fine doing that. I can even "technically" get into Windows 7. My problem is when the 4 colored balls are coming together on boot to make the windows flag, right before it makes the full flag, it freezes and I see a BSOD but it goes so quick I can't see what the problem with it is. I have been able to quickly hit F8 before it loads and it brings up the menu. It crashes the same way trying to load Safe Mode, Recovery mode doesn't see a proper windows installation and I have set it to not automatically reboot and I see then BSOD with 0x000000007b error which according to google is Invalid Boot. Anyone figured this one out?

Hi, I'm facing EXACTLY the same issue on HP Pavillion dv7-3133 notebook. Did you manage to fix it?

---

### Post by HarryZontal on 2010-04-14
> **devi59 said:**
> Mine is the same but different. Running grub-update EASILY puts the windows 7/vista loader back into the grub menu. I can boot into ubuntu fine doing that. I can even "technically" get into Windows 7. My problem is when the 4 colored balls are coming together on boot to make the windows flag, right before it makes the full flag, it freezes and I see a BSOD but it goes so quick I can't see what the problem with it is. I have been able to quickly hit F8 before it loads and it brings up the menu. It crashes the same way trying to load Safe Mode, Recovery mode doesn't see a proper windows installation and I have set it to not automatically reboot and I see then BSOD with 0x000000007b error which according to google is Invalid Boot. Anyone figured this one out?

Managed to install dual-boot on HP Pavilion dv7-3133 with latest beta of easyBCD 2.0. Grub2 of course is not in MBR, but on root partition of Ubuntu.

---

### Post by ktechman on 2010-12-29
Anyone who has a fresh copy (non-OEM) of Win 7 needs to elimanate the 100mb partition and set up the size of the partition from Ubuntu or Windows and there will be no need for any other boot loader besides Grub 2. After updating Ubuntu 10.04 and restarting all is good, I also re-installed Grub 2 (both packages) and Windows 7 booted with no problem from the Grub 2 menu. Some are blaming Ubuntu but this is definitly a Windows/OEM problem, end of story.

Ktechman

---

