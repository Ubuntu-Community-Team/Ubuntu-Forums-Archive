---
title: "Installing GRUB on a separate partition?"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by Pipps on 2009-11-09
I would like to install Ubuntu 9.10 for a friend. 

They already have Windose. I would like to create a new partition for all of the Ubuntu files, with the mount-point as '/', and then for GRUB to be installed within its own separate 50MB partition.

Would this be possible?

How would I request this within the standard installation steps?

What should be the stated mount-point for the GRUB files within the GRUB partition?

Thank you.

---

### Post by Herman on 2009-11-09
You could make yourself a 'Separate Boot' partition, or at least that's what I call it.
A 'Separate Boot' partition means you have /boot in it's own partition, which will be part of the operating system and will house your Linux kernel and iitrd.img files as well as GRUB files. A 'Separate Boot' partition will be listed in your /etc/fstab file as /boot.

The other kind of GRUB partition is called a 'Dedicated GRUB' Partition, a term coined (as far as I know) by a Mr. Steve Litt, who wrote a website titled [Making a Dedicated Grub Partition]("http://www.troubleshooters.com/linux/grub/grubpartition.htm"). ('Legacy' GRUB).
A 'Dedicated GRUB' Partition contains only GRUB files and not the Linux kernel and is not mentioned in /etc/fstab and is 'operating system independant', (GRUB will still function the same even after the operating system has been deleted, so you can add or remove hard disks and operating systems as you please). 

Since you're saying you want to make it during installation I think you mean a 'Separate Boot' partition. 
You need to select 'manual partitioning', when you get the the partitioning phase of the installation. 
I usually make mine about 250 to 500 MiB to be on the safe side, in case it ends up with quite a few Linux kernels and their matching initrd.img files in it. 
It should be mounted as /boot.
Your /boot partition may be formatted with any file system supported by GRUB. Many people suggest using ext2 without knowing why, I'm only guessing but I think maybe the reason was to minimize file system overhead to save disk space in very small hard disks  or USB flash memory sticks, (a habit from the old days when hard disks were very small and expensive). If you're using a normal sized modern hard drive or even a USB flash memory stick of a decent size then you can probably afford to use ext4. ReiserFS is also good for GRUB, with even smaller file system overhead than ext2 if you're squeezed for disk space. Ext4 would be my favorite all purpose file system now though.
Your main Ubuntu partition will be mounted as /, and again I now prefer ext4.
Most people also make a Linux 'Swap area', of around 500 MiB to 1 GiB.
Some people like a 'separate /home' partition too, where all their personal files and settings will be stored. It's then possible to re-install the operating system if that ever becomes necessary, (it shouldn't), however, you should always have a backup of your personal files on some other media anyway. Ext4 for that too, unless you need to share files with an older Ubuntu or some other Linux that doesn't support ext4 yet. Personally, I don't like having a 'Separate /home', but that's a matter for personal preference.

---

### Post by Pipps on 2009-11-09
Herman!

If you are the same esteemed expert that I am thinking of, then allow me to say that I have spent many hours studying your exemplary GRUB guide. It is a marvel! It helped me install my own Dedicated GRUB Partition on my own desktop machine a long time ago.

Your advice on the Separate Boot Partition protocol is extremely useful. Though it is definitely the Dedicated Grub Partition that I would ideally wish to achieve if possible. That is, a Grub partition which is entirely separate and independent of all other local operating systems files.

However, am I correct in my understanding that the implication of your comments in this respect is that it would be necessary to prepare and create the a Grub partition with Gparted and the necessary GRUB files prior to installing Ubuntu, if a Dedicated Grub Partition is to be achieved?

I agree with you on the separate '/home' partition point. It is surely best practice, but for the purposes of installing machines for friends, surely not necessary, and probably liable to make life slightly less convenient at certain times.

I look forward to your next reply.

Best wishes

Pipps

---

### Post by Herman on 2009-11-10
:D Hello Pipps, thanks for the compliments on my GRUB (Legacy) Page.

You're using Ubuntu 9.10 Karmic Koala so you're using GRUB 1.97. (GRUB 2).
It's very simple and quick to make yourself a 'Dedicated GRUB 2 Partition' when you already have Ubuntu installed. 
If that's what you want you can just install Ubuntu in the normal way first.
After that you may create a new partition or use one that's already there which doesn't have any directory named /boot in it, (or it will be overwritten).

 [How To Make a Dedicated GRUB 2 Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-install") - use grub-install

[LIST=1]
[*]Choose an existing partition or create a new one and format it with a file system, you will need at least about 60 MiB of space in the partition for grub 2 files, but a little more room than that might be advisable.
[*]Format the partition with a file system and optionally give the file system a LABEL, (from the right-click menu in GParted).
[*]Mount the partition - Usually 'Places'-->'Removable Media'-->'FS_LABEL',
[*]Run a grub-install command similar to the one shown below,
[/LIST]
```
sudo grub-install --root-directory=/media/grub2 /dev/sda
```Where: '/media/grub2 is the name of the mount point for the partition where I want to make a new /boot/grub directory and fill it with GRUB files.
Where: '/dev/sda' is the hard disk in which I want to write the stage1 code to MBR in.

You can relax the file permissions for easier editing now that it's not part of an operating system,
```
sudo chmod 777 -R /media/grub2
```Next, let GRUB in Ubuntu make your new grub.cfg file automatically for you in your Dedicated GRUB Partition,
```
sudo grub-mkconfig -o /media/grub2/boot/grub/grub.cfg
```After that command has run, you can use your Dedicated GRUB as it is if it suits you or you can customize it in any way you like. In an installed GRUB you're not supposed to edit /boot/grub/grub.cfg, but in an 'operating independant Dedicated GRUB Partition you can edit the grub.cfg in any way you like. 

Thanks for the compliments about my web site's GRUB pages.
Regards, Herman :)

---

### Post by Pipps on 2009-11-10
Herman

It is a pleasure to make your acquaintance!

I agree with your earlier comments about the use of a separate '/home' directory. It is probably logically best practice, but in reality unlikely to ever be necessary. For an installation on a semi-casual user's laptop, I think I will avoid the urge to make the task any more difficult than I am already.

Thank you so much for your incredibly kind instructions on setting-up a Dedicated GRUB2 partition. I am going to memorise your prescribed commands and then bust them out in front of my friend during installation next week. I may earn some extra nerd points! I will of course be indebted to you! :)

I have only one further question regarding the GRUB install: Would it be advisable to perform it before installing Ubuntu 9.10 in a separate adjacent partition? 

My reason for asking, is that doing the two tasks in this order would allow me to then install Ubuntu using the 'Advanced' option of not installing 'a bootloader', as it describes it, during the Live CD installation procedure.

If this would indeed be the best approach, then would it be possible to perform the GRUB installation using GRUB files contained on a LIVE CD, whilst booted in Live CD mode, in the first instance, and then performing the separate Ubuntu install from the same Live CD subsequently?

Best wishes

Pipps

---

### Post by vahnx on 2009-11-10
When running the last command, I get 
**grub-mkconfig grub probe error cannot find device for /**

[http://www.google.ca/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=1z4&q=grub-mkconfig+grub+probe+error+cannot+find+device+for+%2F&btnG=Search&meta=&aq=f&oq=](http://www.google.ca/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=1z4&q=grub-mkconfig+grub+probe+error+cannot+find+device+for+%2F&btnG=Search&meta=&aq=f&oq=)

Cannot find working solution.

---

### Post by Herman on 2009-11-11
> grub-mkconfig grub probe error cannot find device for /
Are you trying to do it from a Live CD or something?

Try mounting the file system that contains the GRUB you're trying to install somewhere, and then do,
```
sudo grub-install --root-directory=/media/KARMIC/boot/grub /dev/sda
```
Where: 'media/KARMIC' is the name of the mount point.
Usually the mount point will be named after the file system label if you have set one (recommended).
If you haven't set a file system label you may do so with GParted in the Ubuntu Live CD anytime you like. Just right-click on the partition and select 'Label', and type in a name of your choice. Mine is 'KARMIC', but you may call yours something else. :)

---

### Post by Pipps on 2009-11-11
Hi Herman
> **Pipps said:**
> 
I have only one further question regarding the GRUB install: Would it be advisable to perform it **before **installing Ubuntu 9.10 in a separate adjacent partition? 
...

Sorry to hassle you for an answer(!), but what do you think? :)

Pipps

---

### Post by Herman on 2009-11-12
> Would it be advisable to perform it **before **installing Ubuntu 9.10 in a separate adjacent partition?  It shouldn't matter very much, one of the advantages of having GRUB in a 'Dedicated GRUB Partition' is that it is 'operating system independant', so GRUB will still work regardless of whether there's a GRUB-freindly operating system around or not.
Another nice thing about it is you can make up your own user freindly operating system titles and just have a short list of them. You can use various commands to boot with. 

The non-good thing is if you want your grub.cfg to be up to date and booting the latest Linux kernels, you'll need to keep running grub-mkconfig fairly often manually, as Ubuntu won't automatically update the file as it would if the file was inside Ubuntu.
If you have a customized grub.cfg, it wouldn't be a good idea to run grub-mkconfig unless you get the command to make you a grub.cfg with some other filename so as not to overwrite your present grub.cfg. You could set a configfile command in your customized grub.cfg to have it look at the next configfile. You can have a lot of fun with GRUB in a 'Dedicated GRUB Partition'.

I like to have time to try things out myself before I give advice to others about what's the best thing to do. I have tried setting up a 'Dedicated GRUB2 Partition' with the commands I gave you in the earlier post. The commands worked perfectly for me.
I haven't had time to try running 'sudo grub-install ... ' from a Ubuntu Live CD yet, I'm not sure if it will work. You can try it if you like, but I'm not sure, most people chroot into a hard disk installed OS before running grub-install, so I think you'll find that you'll need to install Ubuntu first.
I found I had to run 'chmod 777' for a second time, on the grub.cfg file in addition to the whole disk as grub.cfg was still un-editable until I ran that command.
My computer has four hard disks, two IDE and two SATA and I had a few problems getting the 'Dedicated GRUB' working properly, to be perfectly honest with you. I ran out of time and rather than persisting with monkeying around with mt new 'Dedicated GRUB I have re-installed my Karmic operating system's GRUB to MBR for the time being as I have some work to do that I need to get on with. 
Maybe sometime soon I'll get back to it though, and find out what I'm doing wrong. I was getting a boot error message when trying to boot Ubuntu with it; 'sparse file not allowed', whatever that means. Since GRUB2 is new I haven't had time to find out about what the error messages mean yet or what to do about them. ... Interesting ... I'll be back with some news later sometime, I'm not sure when, but I'll be back. :)

---

### Post by Herman on 2009-11-12
> I haven't had time to try running 'sudo grub-install ... ' from a Ubuntu Live CD yet, I'm not sure if it will work.  Actually, I think I do remember trying it and it didn't work, at least not with the options I was trying to use. 
I know grub-setup works from a LiveCD, but I don't think grub-install will, maybe I'm wrong. I'd like it if you can prove me wrong about that. :D

---

### Post by mlmaher on 2010-01-02
Hi, I'm looking for a bit more guidance. I want to install ubuntu and Madriva on one drive and also have a dedicated Grub2 partition and a separate Home partition. However with an extended partition housing the linux swap partition created by Ubuntu I have run into the Four primary partition limit. It seems that using an extended partition would be part of the solution. At this point I am open to suggestions. Thanks for any help.

---

### Post by Herman on 2010-01-02
Just resize one of your primary partitions smaller and resize your extended partition larger then so you will have room for a logical partition in it to install GRUB in.
It seems obvious enough and simple unless there's something you haven't explained.  
What difficulties are you having? I or somebody will help you if you can explain what your problem is.

---

### Post by YesWeCan on 2011-05-28
Here's a challenge: It occurs to me that in an ideal world I would want the following,

1) Grub2 in its own partition, independent of any OSs (this has been explained already)

2) Grub2 to be bootable using a standard MBR. So there is no need for a non-standard, Grub MBR; to choose Grub would simply require the boot flag to be set for the Grub partition.

3) After booting into Grub2 have a facility for probing for OS's and thereby updating the OS selection menu. Also being able to manually edit the config files.

Is this achievable?

---

### Post by Herman on 2011-06-03
:D Nice computer! 
The specs in your sig link imply you may be planning to install Ubuntu in your computer which already has some kind of RAID setup. If your computer has some kind of non-standard arrangement,  then I guess you would quite possibly have good reasons for not wanting to install GRUB to MBR. Besides that, I wouldn't imagine touching any of your RAIDed hard disks with any partition editor would be a good idea either unless you know what you're doing. You could destroy whatever operating system your computer has installed in it. You may need to seek expert help locally.

To install Ubuntu in a computer like that would at least require adding another disk of some kind, be it a hard disk, SSD or flash memory stick. In that case you could easily just install GRUB to MBR in the same disk you install Ubuntu in. 
To boot that disk, you would just need to boot with your BIOS boot menu, most computers have a BIOS boot menu which allows you to select a disk to boot. The key you need to press during the early stages of boot-up varies, so consult your motherboard manual or be prepared to invest a little time using the trial and error method to find out which key you need to press for the BIOS boot menu.
Moving the boot flag in a MBR only works for booting primary partitions  within the hard disk you're booting, usually the first hard disk so I can't imagine how that idea would be any help to you at all in your circumstances.

Grub2 already has the built in ability to detect other operating systems and add them to the boot menu, so we don't need to worry about that, but it needs to be part of an operating system to do so because the files it uses to do that are installed in the operating system. You can also use GRUB2 as an operating system itself and detect other operating systems and boot up from GRUB's Command Line Interface quite easily once you get used to it. You can't make persistent changes to the GRUB Menu that way though. Editing the Grub2 boot menu isn't as easy as it was with Legacy GRUB, (the old GRUB). It is possible if you try hard enough, you need to change file permissions and so on, but it's probably not worth the effort. 
If you want a custom GRUB Menu, there's a program I've read you can install called  [Grub Customizer]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183"), why not give that a try? Otherwise you might be interested in trying out [GAG Boot Manager]("http://gag.sourceforge.net/") or [PLOP Boot Manager]("http://www.plop.at/") instead. Once again though, I would not install either of those in your first hard disk MBR either, or any disk that's a member of your RAID array, install them in some other drive instead.  :D

---

### Post by YesWeCan on 2011-06-03
> **Herman said:**
> :D Nice computer! 
Thanks. I upgraded to Sandy Bridge recently and all is well, except temperature sensors which I don't know how to access yet. I have heard that newer kernels support SB better so now I am deliberating about whether to go to 11.04 or not. Tricky.

Thanks for anticipating my needs so carefully. The system in my sig is not the one I have in mind for the hypothetical scheme I propose. What I want to do is make a truly stand-alone bootloader in its own partition, which has been cut-off at one end by not having a dedicated MBR and at the other by not being dependent on any OS to function fully. By function fully I mean being able to probe for OS's (refresh its boot menu) when a system change has been made.

> You can also use GRUB2 as an operating system itself and detect other operating systems and boot up from GRUB's Command Line Interface quite easily once you get used to it. You can't make persistent changes to the GRUB Menu that way though.
What I have in mind is the automated functionality of update-grub/OS-prober that can be run from the Grub menu.

In this hypothetical multiboot scheme, the downside is using a primary partition for the bootloader. The upside is that the MBR can be standard, thus avoiding problems when Windows is reinstalled, and the bootloader is not tied to any particular OS thus avoiding the problem of potentially breaking it when an OS is deleted.

---

### Post by Herman on 2011-06-03
:-k Hmmm, one other (major, it seems to me), downside will be the inconvenience of needing to move the boot flag around each time you want to toggle between booting Windows directly or booting via this proposed boot manager. Maybe you have already thought of an idea how to do that quickly and easily?
Or were you thinking of leaving the boot flag on this boot manager partition all of the time except whenever the Windows installer interferes with it each time Windows needs to be re-installed?

---

### Post by srs5694 on 2011-06-04
> **YesWeCan said:**
> Here's a challenge: It occurs to me that in an ideal world I would want the following,

1) Grub2 in its own partition, independent of any OSs (this has been explained already)

2) Grub2 to be bootable using a standard MBR. So there is no need for a non-standard, Grub MBR; to choose Grub would simply require the boot flag to be set for the Grub partition.

3) After booting into Grub2 have a facility for probing for OS's and thereby updating the OS selection menu. Also being able to manually edit the config files.

Is this achievable?

I note that you're using an [SIZE=1]ASRock P67 Extreme6[/SIZE] motherboard. This board has UEFI firmware, so if you use it in its native UEFI boot mode, your boot loader options are very different than if you use it in its BIOS compatibility boot mode. Among other things, UEFI boot mode:


[list]
[*]Does not use the MBR, or any "unallocated" sectors of the disk, to store boot loader code
[*]Has a primary boot loader built into the firmware
[*]Stores OS-specific boot loaders as files in a special type of partition known as an [EFI System Partition](http://en.wikipedia.org/wiki/EFI_System_partition)
[*]Supports a different set of boot loaders and boot selectors, including [rEFIt,](http://refit.sourceforge.net/) which does at least some of what you want
[/list]


At the moment, Ubuntu's support for native UEFI booting is fair at best (on a scale of abysmal/poor/fair/good/very good/excellent), but that's a question of how the installation scripts set things up. With a bit of research, you can do better. My personal preference is for a combination of rEFIt and [ELILO.](http://elilo.sourceforge.net/cgi-bin/blosxom) The latter is a Linux-only boot loader that's much simpler than GRUB 2 (and therefore much less likely to go badly wrong, which is what GRUB 2 excels at on UEFI systems).

The main thing from your list that you wouldn't achieve with UEFI, rEFIt, and ELILO is automatic probing of different Linux kernels. rEFIt probes for OS boot loader files in the EFI System Partition, so it'll detect new OS installations automatically; but if you change your kernel or want to issue kernel-specific boot options, you'll need them to have been pre-configured by the time you boot.

If you're multibooting with Windows, UEFI has the advantage of using GUID Partition Table (GPT) partitions rather than Master Boot Record (MBR) partitions. Linux can use either under either BIOS or UEFI, so you can use any combination you like; but Windows ties BIOS systems to MBR and UEFI systems to GPT. GPT has several advantages over MBR. The most important in the long run is that MBR has a 2 TiB size limit (assuming 512-byte sectors), but GPT's limit is much higher. The second most important benefit to GPT is that it doesn't use extended or logical partitions; instead, you get up to 128 partitions (by default) with no distinction between types, so you needn't worry about running out of primary partitions. GPT has a number of more minor advantages, such as CRCs and backups of data structures stored on the disk, which should theoretically help reliability.

If you've already set up and are booting your system using the firmware's BIOS compatibility mode, it's possible to change it. This is easiest with Linux, but it's possible even with Windows (or so I've read -- [this document](http://forums.mydigitallife.info/threads/9857-Change-the-booting-style-of-Vista-or-7-x64-versions-from-BIOS-MBR-mode-to-UEFI-GPT) details how). Personally, I think I'd just reinstall Windows. If you've got a spare hard disk, you could try a test installation using UEFI mode and then switch back to your original disk if you don't like it.

---

### Post by YesWeCan on 2011-06-04
> **Herman said:**
> :-k Hmmm, one other (major, it seems to me), downside will be the inconvenience of needing to move the boot flag around each time you want to toggle between booting Windows directly or booting via this proposed boot manager. Maybe you have already thought of an idea how to do that quickly and easily?
Or were you thinking of leaving the boot flag on this boot manager partition all of the time except whenever the Windows installer interferes with it each time Windows needs to be re-installed?
That's a good point. I assumed one would always boot Grub unless Windows had reset the boot flag. It doesn't gain one much to have to run a special program to change the boot flag over having to run a special program to re-install Grub MBR. Can the boot flag be changed easily in Windows...I don't know. However, the benefit of having Grub independent of any OS remains. But the OS probing facility is so convenient that it would need this to be worthwhile, I think.

---

### Post by YesWeCan on 2011-06-04
> **srs5694 said:**
> I note that you're using an [SIZE=1]ASRock P67 Extreme6[/SIZE] motherboard. This board has UEFI firmware, so if you use it in its native UEFI boot mode, your boot loader options are very different than if you use it in its BIOS compatibility boot mode.
Thanks for pointing this out. I have to say I am very happy with this ASRock mobo. It seems to exude quality and it just works. I have yet to RTFM about UEFI so thanks for prompting me to look into this.

I don't have any booting issues at the moment but I know someone who is about to and I have in mind a lot of the problems newbies in this forum encounter with dual boots and trialing OS's. So this is a semi-theoretical proposal.

Should I infer from your post that UEFI can or in future will be able to boot linux without need for a Grub at all? That would be very nice. It makes complete sense to me that the bios manages all the booting intelligently.

---

### Post by srs5694 on 2011-06-04
> **YesWeCan said:**
> Should I infer from your post that UEFI can or in future will be able to boot linux without need for a Grub at all? That would be very nice. It makes complete sense to me that the bios manages all the booting intelligently.

Without a need for GRUB? Yes. Without a need for a Linux-specific boot loader? No, although that may depend on your definitions.

UEFI boots by reading a UEFI boot loader, which is just a UEFI application, from the EFI System Partition (ESP). Typically, that partition has directories for specific OSes, as in:

```

/EFI/
    ubuntu/grub.efi
    suse/elilo.efi
    microsoft/bootx64.efi
    refit/refit.efi

```

Each of those .efi files is a boot loader for the OS in question. You tell the firmware which to boot by default and it does so. Just as in the BIOS world, some boot loaders boot just one OS whereas others give the option of chainloading to another boot loader (another .efi file, in the case of EFI) or even loading multiple OSes directly.

GRUB 2 on EFI can chainload another boot loader, load a Linux kernel, or load certain other OSes' kernels. ELILO can load a Linux kernel. Microsoft's boot loader can load only the Windows kernel, AFAIK. [rEFIt](http://refit.sourceforge.net/) can chainload another .efi file, and maybe directly load an OS X kernel (I'm far from positive of the latter, though).

In theory, you could embed a simple Linux EFI boot loader into the kernel, turning it into an .efi file that you'd put on the ESP. If you did this, then in some sense the firmware would load the Linux kernel directly. AFAIK, though, nobody's done this.

Overall, the EFI boot method is a much saner way of booting the computer than the BIOS method of funneling everything through boot code in the MBR, which is far too small to store anything complex enough, and which tends to be overwritten by the last OS to be installed. To work properly, though, the EFI has to provide a good and user-friendly way to change which OS boots. There seems to be a lot of variability on this score, and I'm not sure that many do a good job of it. I'd hope that the flashy UEFIs used by ASUS and ASRock on their newest boards would provide the necessary options, but I've never used one or even read their manuals, so I don't know how well they actually do it.

---

### Post by Herman on 2011-06-05
If we're just talking about 'most computers', (and not your particular [SIZE=1]ASRock P67 Extreme6[/SIZE] motherboard with your UEFI firmware), then there are a few ways I think you can achieve at least some of the goals you outlined in post #13.

One idea would be to take a look at [Super Grub2 Disk]("http://www.supergrubdisk.org/"). I'm pretty sure we can install Super Grub2 Disk in a partition or in a USB flash memory stick. Super Grub2 Disk is 'operating system independant' and has the ability to scan a PC and detect OSes and offer to boot them. I'm pretty sure it would not be too difficult to make our own changes to Super Grub2 Disk to customize menus in it and tailor it to a person's own wants or needs.

A second idea would be to have a full (normal) Ubuntu installation which boots with GRUB2 in a USB flash memory stick. You can boot the USB's Ubuntu and run 'sudo grub-mkconfig -o /boot/grub/grub.cfg to scan the computer and add a boot option for the USB and all the operating systems in the computer, then reboot and select whichever operating system you want. 
Advantages are then you can use the entire Ubuntu operating system in the USB as an auxilliary operating system, useful for its portability. You will have all of the diagnostic and repair facilities you can image at your disposal, not just boot loader repair tools either. You'll be able to do just about anything you can think of, file system checking, partition resizing, chroot into another Ubuntu and fix things like say a 'broken packages', which can (rarely but is is possible), the operating system unbootable, file recovery for a dying hard disk, and so on and so on ... 
You can even use it to fix stricken Windows machines too, by installing a program called '[chntpw]("http://home.eunet.no/pnordahl/ntpasswd/")', and edit the Windows registry to get a disabled Windows computer working again, (if you know what you're doing).

If you're strapped for space, (which I don't think too many people would be given the very affordable prices of disks and storage now), and you can't find room for a full Ubuntu installation somewhere in a hard drive or flash memory, but still want to be able to use GRUB2/Ubuntu's operating system detection, you could make a minimal Ubuntu installation (command line only), and then strip out all the stuff you don't want and just have GRUB2 and GRUB2's dependencies and not much else. (Just an idea - a silly one maybe).

Finally, I'm not sure if it would be theoretically be possible or not to make up some kind of new operating system detection software for GRUB2 and provide a text editor so it can actually write to its own menus and make the changes persistent. I think you would need a linux kernel to be able to run a text editor so you would actually have something classed as an operating system instead of a boot loader. GRUB2 does indeed have a part called the 'kernel.img', and GRUB2 is already capable of having modules added to enable it to do a lot of interesting things that we would normally only expect an operating system to be able to to. GRUB2 can understand file systems, read text files and display pictures and fancy fonts and so on. Is a text editor module possible? One that would allow GRUB2 to actually write to a file and save the changes?

... I don't know  :popcorn:

---

### Post by oldfred on 2011-06-05
If booting an install with old grub, you just install grub legacy's boot loader to the PBR - partition boot sector and chainload like we did with old grub. Then no updates are required in the grub partition.

If booting Debian based, you can boot the partition directly as a link to the most current kernel is in root. (also link to previous).

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

---

### Post by YesWeCan on 2011-06-07
Those are good ideas, Herman. :)
I think the Grub+OS on a stick is the one I favour, provided one's bios can boot a USB device. It gives all the functionality required and the versatility of a whole OS for other purposes as you've pointed out. For fun I made one on a 2.2GB stick by using Ubuntu 10.04 server without a GUI. I suppose a commonly available 4GB stick would be ample for an OS with Gnome GUI.

Perhaps a nice product for installing Ubuntu would be a bootable USB stick with Grub+Ubuntu + an installer for that version of Ubuntu. Then you could pop it in, install and keep the USB stick for booting off and future reinstalls. The installer would default to not installing Grub.

---

### Post by YesWeCan on 2011-06-07
> **oldfred said:**
> If booting an install with old grub, you just install grub legacy's boot loader to the PBR - partition boot sector and chainload like we did with old grub. Then no updates are required in the grub partition.
Yep.

BTW, do you understand the details of why it is not recommended to install Grub2 to the PBR of the Ubuntu partition?
Based on how Windows does things one might be forgiven for wondering why Ubuntu cannot be booted directly. Why is it that Grub is not just another part of the Ubuntu partition that can be booted directly by an ordinary entry in a standard MBR partition table?

My vague impression is that it is something to do with the ext filesystem and the relative positions of the PBR and the other Grub files being changed by actions like filesystem checks. But it seems like this is an odd issue...odd that it is an issue at all or cannot easily be overcome.

---

### Post by srs5694 on 2011-06-07
> **YesWeCan said:**
> BTW, do you understand the details of why it is not recommended to install Grub2 to the PBR of the Ubuntu partition?
Based on how Windows does things one might be forgiven for wondering why Ubuntu cannot be booted directly. Why is it that Grub is not just another part of the Ubuntu partition that can be booted directly by an ordinary entry in a standard MBR partition table?

I'm not 100% positive of this, but I believe it boils down to the complexity of GRUB and the limited space available in either the MBR or the PBR. This forces GRUB's designers to do one of two things on a BIOS-based computer:


[list]
[*]Install to the MBR and use the (officially unallocated) sectors immediately following the MBR to store enough code for GRUB to interpret a filesystem and read additional files from it. (If using a GPT disk, a BIOS Boot Partition takes the place of these unallocated sectors.)
[*]Install to the PBR, store the extra code referred to earlier as a file in a filesystem, and use a list of raw sector numbers to refer to that code. This is called "block lists," and it's susceptible to problems if the file is updated or moved. This approach is also necessary if there's insufficient space between the MBR and the first partition to store the code or if you're using a GPT disk without a BIOS Boot Partition.
[/list]


I don't know the details of how the Windows boot loader works; however, I do know that Windows is very sensitive to changes in its boot partition. Thus, it's conceivable that the Windows boot loader actually uses block lists, much like GRUB when installed in a PBR. GRUB tries to do things in a more reliable way, but that's not always possible, and it's got its own problems, some of which you're trying to overcome.

All of this is why I'm now interested in the EFI (and UEFI) method of booting. In this system, the firmware has enough "smarts" to read FAT directly, and so can load a boot loader of any plausible size from the filesystem, without worrying about how much functionality you can cram into 446 bytes of code. In theory, this should help make things much more reliable and flexible. In practice, we'll just have to wait and see, since the current crop of EFI boot loaders isn't nearly as mature as the BIOS boot loaders, which have a two-decade head start on the EFI boot loaders.

---

### Post by Herman on 2011-06-08
It looks like AMD is getting ready to start shipping some new products featuring [coreboot]("http://www.coreboot.org/Welcome_to_coreboot").
Links: [the Inquirer]("http://www.theinquirer.net/inquirer/news/2069286/amd-announces-coreboot-llano-fusion-chips") | [AMD]("http://blogs.amd.com/work/2011/05/05/an-update-on-coreboot/") | [AMD]("http://blogs.amd.com/work/2010/12/21/12-days-of-12-core-day-12-the-gift-of-new-cores-in-2011/") | [PC Tech]("http://www.pcauthority.com.au/News/253244,amd-bulldozer-cpus-get-early-motherboard-support.aspx") | [AnandTech]("http://www.anandtech.com/show/4393/computex-2011-amd-bulldozer-llano-trinity-new-vision-branding") 

Cool!  It looks like it has been worth holding off buying new hardware for a while. I think I'm going to like the new AMD products because I like the idea of replacing the BIOS with coreboot. It's open source and uses Linux.

---

### Post by YesWeCan on 2011-06-09
> **srs5694 said:**
> I'm not 100% positive of this, but I believe it boils down to the complexity of GRUB and the limited space available in either the MBR or the PBR.
I'm just curious about the theory. I just don't understand the reason why Ubuntu does not have all the bootloader in its root partition instead of
- creating a non-standard MBR that conflicts with Windows
- stealing sectors in a no-man's land just after the MBR that can cause conflict with other apps that also steal space from this area
- fails to work at all with other MBR types like GPT

This way booting Ubuntu would be independent of MBR and the loader would have copious space. I mean, once the bios transfers control to the 1st sector of the partition you are away. And uninformed users would not get so terribly confused by it: where is Grub located exactly? And this would also make it easy to reliably add Ubuntu to Windows boot loader menu.

So there must be a really good reason that I don't yet understand.

---

### Post by srs5694 on 2011-06-09
> **YesWeCan said:**
> I'm just curious about the theory. I just don't understand the reason why Ubuntu does not have all the bootloader in its root partition instead of
- creating a non-standard MBR that conflicts with Windows
- stealing sectors in a no-man's land just after the MBR that can cause conflict with other apps that also steal space from this area
- fails to work at all with other MBR types like GPT

This way booting Ubuntu would be independent of MBR and the loader would have copious space. I mean, once the bios transfers control to the 1st sector of the partition you are away. And uninformed users would not get so terribly confused by it: where is Grub located exactly? And this would also make it easy to reliably add Ubuntu to Windows boot loader menu.

So there must be a really good reason that I don't yet understand.

Part of the answer is that you're looking at Windows as being the standard. I'm sure many GRUB developers would disagree about that, and a different perspective on the issue renders your concerns about a "non-standard" MBR moot. Likewise for adding GRUB to a Windows boot loader configuration. You might consider this arrogant, but some developers do think like that.

There's also been a long history of boot loaders doing the things that GRUB does -- replacing the boot code in the MBR and placing code in the (officially) unallocated sectors following the MBR. Lots of third-party boot loaders do this, not just GRUB. Thus, GRUB isn't really being a rebel here; it's just following (more-or-less) standard practice for third-party boot loaders.

One advantage of replacing the MBR code is that it enables you to boot Linux from a logical partition. If you relied on a DOS/Windows boot loader in the MBR, Linux would have to occupy at least one primary partition. By putting GRUB there, you can put Linux entirely on logical partitions. This is useful, and even necessary in some configurations -- say if a new computer comes with three occupied primary partitions, as many today do. (Some even have the audacity to consume all four primary partitions!)

It *is* possible to install GRUB to a Linux partition, without touching the MBR. This was fairly common with GRUB Legacy but has become less common with GRUB 2, since GRUB 2 works better when installed to the MBR. In addition to making it impossible to boot Linux from a logical partition (if you're using a standard DOS/Windows MBR boot loader), putting GRUB in the boot partition renders it less reliable because in that placement, it relies on block lists, as described earlier, which are subject to breakage should files change position. This type of damage is a problem with some boot loaders, and a few years ago, when LILO was king of the Linux boot loader hill, there were lots of posts from people who had problems because LILO stopped working for this very reason. (LILO relies on block lists, whether it's installed to the MBR or to the boot partition.)

GRUB *does*, BTW, work with GPT. The DOS/Windows boot loader does not. When installing to GPT, though, GRUB requires a different approach at some of the early boot stages, since it must interpret GPT data rather than MBR data and there's no free space immediately after the MBR (that's where the main GPT data reside).

All of this will become of academic interest only in a couple of years, since the industry is in the process of adopting UEFI, which uses an entirely different boot model. With UEFI, you don't worry about MBR boot code, and probably not even code in the a partition's boot sector. It's all about files, which of course are much more flexible.

---

### Post by YesWeCan on 2011-06-12
> **srs5694 said:**
> Part of the answer is that you're looking at Windows as being the standard. I'm sure many GRUB developers would disagree about that, and a different perspective on the issue renders your concerns about a "non-standard" MBR moot. Likewise for adding GRUB to a Windows boot loader configuration. You might consider this arrogant, but some developers do think like that.
Well, with these pissing contests it is the ordinary user who gets soaked in pee. ;)

> There's also been a long history of boot loaders doing the things that GRUB does -- replacing the boot code in the MBR and placing code in the (officially) unallocated sectors following the MBR. Lots of third-party boot loaders do this, not just GRUB. Thus, GRUB isn't really being a rebel here; it's just following (more-or-less) standard practice for third-party boot loaders.
Ok.

> One advantage of replacing the MBR code is that it enables you to boot Linux from a logical partition. If you relied on a DOS/Windows boot loader in the MBR, Linux would have to occupy at least one primary partition. By putting GRUB there, you can put Linux entirely on logical partitions. This is useful, and even necessary in some configurations -- say if a new computer comes with three occupied primary partitions, as many today do. (Some even have the audacity to consume all four primary partitions!)
The Extended Boot Partition is not Grub specific, though. Grub is not necessary to enable logical partitions.

> It *is* possible to install GRUB to a Linux partition, without touching the MBR. This was fairly common with GRUB Legacy but has become less common with GRUB 2, since GRUB 2 works better when installed to the MBR. In addition to making it impossible to boot Linux from a logical partition (if you're using a standard DOS/Windows MBR boot loader), putting GRUB in the boot partition renders it less reliable because in that placement, it relies on block lists, as described earlier, which are subject to breakage should files change position. This type of damage is a problem with some boot loaders, and a few years ago, when LILO was king of the Linux boot loader hill, there were lots of posts from people who had problems because LILO stopped working for this very reason. (LILO relies on block lists, whether it's installed to the MBR or to the boot partition.)
Interesting. But how hard would it be to have a dedicated Ubuntu boot-loader in root that comes as part of the install that does not suffer this block list problem. Not hard at all. Just a little customization.
I think there is a conflict between the Grub folk who want an independent "universal" loader for everybody and Ubuntu that could really benefit from a customized one.

> GRUB *does*, BTW, work with GPT. The DOS/Windows boot loader does not. When installing to GPT, though, GRUB requires a different approach at some of the early boot stages, since it must interpret GPT data rather than MBR data and there's no free space immediately after the MBR (that's where the main GPT data reside).
You mean it can be crafted to work. In my strict interpretation it doesn't work.

> All of this will become of academic interest only in a couple of years, since the industry is in the process of adopting UEFI, which uses an entirely different boot model. With UEFI, you don't worry about MBR boot code, and probably not even code in the a partition's boot sector. It's all about files, which of course are much more flexible.
Let's hope so.

---

### Post by oldfred on 2011-06-12
I have had no recent issues with grub2, BIOS, and gpt partitions. I have installed to my sdb drive with gpt partitioning and to a 16GB flash drive with gpt. You just have to use one very small gpt partition as bios_grub for core.img. Grub automatically used it on install.

```
sdb1: ____________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  

```

---

### Post by Herman on 2011-06-12
> I'm just curious about the theory. I just don't understand the reason why Ubuntu does not have all the bootloader in its root partition instead of
- creating a non-standard MBR that conflicts with Windows
- stealing sectors in a no-man's land just after the MBR that can cause conflict with other apps that also steal space from this area
- fails to work at all with other MBR types like GPT
Happily for 99.9% of the time, it is possible to set up a dual boot in most PCs quite easily and the GRUB MBR is perfectly compatible with the MBR that happens to be already there.
The GRUB MBR fits easily within the first 446 bytes of the MBR and doesn't harm the partition table or the Disk Identifier (UID), so the MBR remains compatible with the boot loaders for recent versions of Windows which for some reason have decided to make themselves dependant on the so called 'disk signature'. 

I don't know whether there's an agreement or convention about who can use the first track of the hard disk and for what purpose. It might be just an accident that it has traditionally been left empty, and I think it's a carry-over from the days of cylinders, heads and sectors, when partitions had to start and end at the beginning of a track. The fact is that it's an area of the hard disk that's normally left vacant and is wasted. 
I have read that some viruses like to write code to the normally vacant first track so that even if a Windows OS is re-install the virus can keep coming back again and it can load at boot time before the operating system and take control of the security software.
Software that I know about besides GRUB that has written to or occupied parts of the normally empty first track include GAG Boot Manager, various kinds of full disk encryption softwares, 'Disk Manager' (a software for allowing a larger hard disk to be addressed than the BIOS was capable of), Partition Magic used to write a couple of bytes in the first track for some weird reason and I have read that there are a few newer programs Windows users install that use part of the first track. These were able to share the space quite happily with GRUB Legacy and as far as I have read the problems have been sorted out amicably between GRUB2 developers and the developers of the other programs concerned.

The basic problem boils down to human nature. People are selfish and people are lazy.
The reason why I'm saying people are selfish is because most people want to be able to have Ubuntu for free and keep their Windows too.
The reason I say people are lazy is that most people don't want to bother taking the time and effort to research about what they're about to do an plan how they're going to do it or what else they can do next if things don't according to their original plan.
The reason I know is because I'm selfish and lazy and stupid too sometimes.

I don't think Microsoft Windows likes the idea of anybody installing more than one operating system in a computer at all, not even another Windows operating system. Quite obviously they make their money from selling operating systems and other software and they would prefer a world with only one copy of Windows per computer.

I don't imagine Canonical really wants Ubuntu to be installed with Windows either.
The idea of setting up a dual boot is only supposed to be available as an option for use when a Windows user needs time learn how to use Ubuntu and the software that comes with it and to change their files to open source files. Dual booting is kind of like having training wheels on a bicycle, you're supposed to take them off as soon as you start getting confident enough.
Ideally, a person installing Ubuntu should either install it in a new computer made for Ubuntu, or else delete any other operating system that happens to already be there and install Ubuntu in its place.
Ubuntu isn't designed to be a second operating system in a Windows PC, Ubuntu is designed to replace Windows.

Some people are also able to install Ubuntu in MacIntosh computers but I don't think Macs are especially designed to accommodate Ubuntu.

The concept of dual booting is not really supported by any operating system vendor or at least it's not regarded as an ideal situation.

If a person does want to set up a dual boot then I think that GNU GRUB is by far and away without a doubt the world's best boot loader and installing GNU GRUB in the MBR and first track of the hard disk is a beneficial upgrade for any person who wishes to dual boot any operating systems, even if they want more than one Windows.
The GNU movement is all about freedom, and GNU/Linux users aren't bound by the Windows convention of being restricted to one operating system per computer. many GNU/Linux users like to dual and even multi-boot more than one flavour of GNU/Linux and possibly a Windows OS as well. GNU/Linux users are also free to install and delete operating systems and move them around on their hard disks when they want or need to. Therefore, it is advantageous to have a boot loader with code in the first track of the hard disk that is smart enough to be able to read file systems.

I think though, that people (Windows users) should take the time to read and educate themselves a little before they act and start using softwares they don't understand. They should make themselves aware of what they're doing and make sure what they're about to do will be safe and have backups ready in case anything goes wrong. The act of setting up a dual boot between Windows and any other operating system is not dangerous to Windows and to Windows users if they know a little about what they're doing. There are plenty of guides and how-tos available on the internet about how to set up dual boot configurations, and a good site should explain to what people can expect to happen and how to control what happens to their computers. Not all computers are suitable for GNU GRUB to be installed to MBR in. There are plenty of alternatives and work arounds though. The problem is if people know they need to do all that reading and learning first most people wouldn't bother. It ain't gonna happen.

For sure there will always be a few people who get themselves into difficulties, but that can happen doing just about anything. There are also a few good people here in this forum who are willing to give up some of their time to try to help anyone having difficulties. Sometimes it's easy to help and other times nobody knows the solution. Over all I think that there's a silent majority of happy users who are able to install Ubuntu and dual boot with Windows quite successfully.

---

### Post by srs5694 on 2011-06-12
> **YesWeCan said:**
> [quote=srs5694]One advantage of replacing the MBR code is that it enables you to boot  Linux from a logical partition. If you relied on a DOS/Windows boot  loader in the MBR, Linux would have to occupy at least one primary  partition. By putting GRUB there, you can put Linux entirely on logical  partitions.The Extended Boot Partition is not Grub specific, though. Grub is not necessary to enable logical partitions.[/quote]

I'm not sure what you're saying here, since I'm not familiar with the term "Extended Boot Partition." I tried Googling it and got a confused mish-mash of meanings. When I added "GRUB" to the mix, I got a total of three hits: this thread, somebody's bug report, and a false alarm hit.

My point is this: The DOS/Windows MBR boot loader can only, AFAIK, redirect the boot process to a primary partition; it cannot redirect the boot process to a logical partition. Thus, if you install Linux on nothing but logical partitions and want to rely on the DOS/Windows boot loader, it won't work. By putting GRUB in the MBR (and the immediately following sectors), though, you can install Linux in logical partitions.

That said, another boot loader on a primary partition could in principle redirect the boot process to a logical partition. If you're using such a boot loader, that's great; but for greatest flexibility, a boot loader for Linux would have to assume that such a boot loader is not available and at least give the option of installing to the MBR.

> Interesting. But how hard would it be to have a dedicated Ubuntu boot-loader in root that comes as part of the install that does not suffer this block list problem. Not hard at all. Just a little customization.

I don't think you understand the nature of the problem. It's this: There isn't room in the MBR (or in the PBR) to fully implement a filesystem driver. Thus, to read files in the filesystem, you must be able to read a few kilobytes of data (containing code that implements a filesystem driver) from a location that's referenced by sector values. When it uses a combination of the MBR and post-MBR sectors, GRUB does this by using those post-MBR sectors to store a filesystem driver (among other things). When you take those post-MBR sectors out of the equation and force the boot loader to read filesystem files by hard-coding their sector values, you create two problems:


[list]
[*]If the file is heavily fragmented, there won't be enough space in the MBR/PBR to store all the relevant sector values.
[*]If the file is moved or replaced, the MBR/PBR code will have to be written back to disk to update the block lists.
[/list]


There are serious space constraints on both MBR and PBR boot loaders -- 440 bytes for MBR; for PBR it varies from one filesystem to another and I don't happen to know the common values, but I see that on a fresh ext2 filesystem, the first non-0 byte is at byte 1026, so it looks like 1024 bytes maximum. Note that we're talking about *bytes* here, not kilobytes or megabytes. For comparison, this paragraph, in ASCII, is 602 bytes, so the MBR boot loader code must be shorter than this paragraph. Given these size constraints, overcoming these problems is not the trivial issue you seem to believe it is.

> I think there is a conflict between the Grub folk who want an independent "universal" loader for everybody and Ubuntu that could really benefit from a customized one.

I agree with you there. GRUB, and GRUB 2 in particular, tries to do too many things for too many people. It does have the advantage that, with its OS-detection scripts, it *usually* does the right thing for most people. Unfortunately, when it *doesn't* do the right thing, you have to fight those customization scripts to get it to work.

> [quote=srs5694]GRUB *does*, BTW, work with GPT. The DOS/Windows boot loader does not.You mean it can be crafted to work. In my strict interpretation it doesn't work.[/quote]

Please don't tell me what I meant. I meant precisely what I wrote: GRUB (particularly GRUB 2, but also patched versions of GRUB Legacy) works with GPT. If you disagree, please tell me why you disagree -- what sort of problems have you had, or in what sense does it fail to work?

---

### Post by YesWeCan on 2011-06-13
> **oldfred said:**
> I have had no recent issues with grub2, BIOS, and gpt partitions. I have installed to my sdb drive with gpt partitioning and to a 16GB flash drive with gpt. You just have to use one very small gpt partition as bios_grub for core.img. Grub automatically used it on install.

```
sdb1: ____________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  

```
Oh sure. My wording is clumsy. It can be crafted to work by adding a special partition. For instance, I don't believe the Ubuntu installer will do this automatically and so the uninformed user has a problem. In fact, in another thread this week a user has exactly this problem and has so far been unable to Google for how to implement the GPT install. I suggested he drop you a line ;)

---

### Post by YesWeCan on 2011-06-13
> **Herman said:**
> I don't imagine Canonical really wants Ubuntu to be installed with Windows either.
I concur with your whole post; nice summary.
I think this sentence may explain a lot. It seems to me there is an inconsistency between Canonical's aim to "convert" hundreds of millions to Ubuntu, presumably most of whom are currently using Windows, and the obvious (to me anyway) lack of care and attention in Ubuntu's installation process and documentation with regard to happy coexistence of the two. For a transition must be expected to involve a dual boot stage along the way. I suggest a target Windows user is going to be gun-shy of linux and what will improve their confidence of Ubuntu is an assurance that their existing system will not be harmed in any way. So I am surprised that Canaonical are not putting proper efforts in to making this transition as trouble-free as possible.

---

### Post by YesWeCan on 2011-06-13
> **srs5694 said:**
> I'm not sure what you're saying here, since I'm not familiar with the term "Extended Boot Partition."
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

> My point is this: The DOS/Windows MBR boot loader can only, AFAIK, redirect the boot process to a primary partitionWe should double-check this. The extended boot records also have boot flags, so it seems to me that the MBR code ought to be able to.

> That said, another boot loader on a primary partition could in principle redirect the boot process to a logical partition. If you're using such a boot loader, that's great; but for greatest flexibility, a boot loader for Linux would have to assume that such a boot loader is not available and at least give the option of installing to the MBR.I think the DOS MBR (and GPT too, I suspect) are more flexible. This is because they do not rely on files in a no-mans area and an OS partition in order to start any boot-loader. That's why I think Grub (or equivalent) should be only in the OS partition and be started by the standard MBR method.

> I don't think you understand the nature of the problem. It's this: There isn't room in the MBR (or in the PBR) to fully implement a filesystem driver.I agree there isn't room in the MBR because it is restricted to 1 sector (although Grub steals a bunch more from no mans land).  But I don't see this restriction inside an OS partition where there is effectively unlimted space. The PBR is just a nominal 1 sector area that the MBR code loads into RAM and executes, but the the partition is essentially private and Ubuntu could use it however it wants. Eg: the PBR code can load another 1000 sectors and do what the heck it likes. That's my understanding.

The way Ubuntu chooses to organise and manage the space within its partition is completely under the control of Ubuntu.

> I agree with you there. GRUB, and GRUB 2 in particular, tries to do too many things for too many people. It does have the advantage that, with its OS-detection scripts, it *usually* does the right thing for most people. Unfortunately, when it *doesn't* do the right thing, you have to fight those customization scripts to get it to work.I am not expecting perfection. I really like the OS prober facility - really useful.

> Please don't tell me what I meant. I meant precisely what I wrote: GRUB (particularly GRUB 2, but also patched versions of GRUB Legacy) works with GPT. If you disagree, please tell me why you disagree -- what sort of problems have you had, or in what sense does it fail to work?Sorry for the temerity. What you are saying seems to be what I was saying you were saying. :D In my words, special crafting is required - like an extra partition just for Grub. It may be the Ubuntu installer that I am complaining about here rather than Grub itself. Of course to an unskilled user the distinction is unimportant.

---

### Post by oldfred on 2011-06-13
Windows boot loader only boots from primary partitions as that is all the first copy of windows will install into.

We often suggest users install lilo's boot loader to fix windows as it is easy to install from Linux and works the same way as window's boot loader in looking for a partition with a boot flag. But lilo also boots from a logical partition. So lilo can be used to boot XP in a logical partition even though windows will not.

Way to boot windows in extended logical partition with lilo's MBR post#5
[http://ubuntuforums.org/showthread.php?t=1367323](http://ubuntuforums.org/showthread.php?t=1367323)
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)
[http://support.microsoft.com/kb/306559#f1](http://support.microsoft.com/kb/306559#f1)

---

### Post by srs5694 on 2011-06-13
> **YesWeCan said:**
> [quote=srs5694]I'm not sure what you're saying here, since I'm not familiar with the term "Extended Boot Partition."][http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)[/quote]

"Record" != "Partition"

Going back to your original point and replying with a mental substitution of the correct term:

> > **srs5694]One advantage of replacing the MBR code is that it enables you to boot Linux from a logical partition. If you relied on a DOS/Windows boot loader in the MBR, Linux would have to occupy at least one primary partition. By putting GRUB there, you can put Linux entirely on logical partitions.The Extended Boot Partition is not Grub specific, though. Grub is not necessary to enable logical partitions.[/quote]

Partitioning systems and boot loaders are distinct, but interrelated, so of course you're correct that GRUB isn't necessary to use logical partitons said:**
> We should double-check this. The extended boot records also have boot flags, so it seems to me that the MBR code ought to be able to.

The EBR contains boot flags because it uses exactly the same data structures as does an MBR. That doesn't mean those boot flags will do you any good when used with the standard DOS/Windows boot loader; the EBR's boot flag is a sort of vestigial organ. I tried doing some Googling on the issue, but I couldn't come up with a search term that produced an appropriate hit, one way or the other. I do know that my assertion that the DOS/Windows boot loader can't handle logical partitions was extremely common knowledge in the 1990s. It would certainly be possible to test in various ways, but I'm unwilling to put in the time to do that. If you are, go right ahead. In the meantime, as my claim is the one that's commonly accepted (note that oldfred is backing me up on this point), I think the burden of proof is on you.

If you care to do a test, try installing Linux to a primary partition with its boot loader in the partition's boot sector and the DOS/Windows boot loader in the MBR; then change the primary partition into a logical partition using my [FixParts](http://www.rodsbooks.com/fixparts/) utility, ensure that it's still marked as active/bootable, and see if it still boots.

> I think the DOS MBR (and GPT too, I suspect) are more flexible. This is because they do not rely on files in a no-mans area and an OS partition in order to start any boot-loader. That's why I think Grub (or equivalent) should be only in the OS partition and be started by the standard MBR method.

You're confounding boot loaders and partitioning systems. Although "MBR" can be confusing this way because the MBR (in the sense of sector 0 of the hard disk) contains both the MBR partition table and the primary boot loader, "GPT" clearly describes only a partitioning system. It can be used in conjunction with a boot loader (GRUB, Chameleon, etc.) stored in its MBR (sector 0) or without, but precisely what any given boot loader does is undefined by the GPT spec. The same is true of MBR as a partitioning system, except that there's no formal MBR specification; it's just sort of grown and evolved over time.

Booting is defined by the computer's firmware -- typically a BIOS, but UEFI is growing in importance, and there are competing systems (OpenFirmware, etc.). These sometimes require particular partitioning systems, but in the case of BIOS, it just reads the first sector of the hard disk and does whatever the code there tells the computer to do.

The lack of specification in both the BIOS's post-BIOS boot processes and the MBR partitioning system is at the heart of your complaints. DOS did things one way, but various third-party boot loaders (including, but not limited to, GRUB) do things differently, and when users' expectations come into conflict with these differences, debates such as this one ensue.

> I agree there isn't room in the MBR because it is restricted to 1 sector (although Grub steals a bunch more from no mans land).  But I don't see this restriction inside an OS partition where there is effectively unlimted space. The PBR is just a nominal 1 sector area that the MBR code loads into RAM and executes, but the the partition is essentially private and Ubuntu could use it however it wants. Eg: the PBR code can load another 1000 sectors and do what the heck it likes. That's my understanding.

You've now greatly expanded what needs to be changed. In order to give a boot loader enough space in the boot partition to guarantee that its files won't be changed you'd need to set aside some reserved space in the filesystem for the boot loader. To the best of my knowledge, no Linux filesystem does this, although my knowledge of Linux filesystem internals is admittedly limited. Note you can't just say "put it in a file," because files can be changed by ordinary system maintenance actions -- a defragmentation operation could move a file, or a package update might replace it entirely. If LVM is in use, the opportunities for changes become even greater. For the needs of an MBR boot loader, the reserved space must be *fixed* and not changeable by ordinary file operations.

> The way Ubuntu chooses to organise and manage the space within its partition is completely under the control of Ubuntu.

Not really -- at least not in the way that's required to achieve the outcome you want. There are several different programs, and associated individuals or organizations that develop each one:


[list]
[*]GRUB, which is the boot loader
[*]The Linux kernel, which manages filesystems, among other things
[*]Ext2/3/4fs, which is part of the kernel that's developed by particular individuals
[*]ReiserFS, which is another filesystem that's part of the kernel and developed by other individuals
[*]XFS, which is another filesystem that's part of the kernel and developed by still other individuals
[*]And so on for JFS, Btrfs, etc.
[*]LVM is a filesystem container that can run atop partitions (or without them). It's also part of the kernel and is maintained by yet another set of individuals.
[*]Ubuntu, which is merely a packager. Unless they develop something fundamentally new themselves or try to coordinate activity among other developers, all they can do is use what's available from others.
[*]Other Linux distribution developers might need to get in on any big change like this.
[/list]


This is the nature of open source development, and it's one of its weaknesses. If Microsoft wanted to set aside space in its filesystem for a boot loader, a directive from somebody up high enough in its chain of command could cause the change to be implemented fairly easily (although it would necessarily create changes in the filesystem that might cause compatibility problems for users). Doing the same in Linux requires coordination among several different parties, any one of whom could refuse to go along with the proposed changes. This is similar to the difference between a dictatorship and a democracy.

[quote=YesWeCan]Oh sure. My wording is clumsy. It can be crafted to work by adding a special partition. For instance, I don't believe the Ubuntu installer will do this automatically and so the uninformed user has a problem.[/quote]
> Sorry for the temerity. What you are saying seems to be what I was saying you were saying. :D In my words, special crafting is required - like an extra partition just for Grub. It may be the Ubuntu installer that I am complaining about here rather than Grub itself. Of course to an unskilled user the distinction is unimportant.

It's the Ubuntu installer you're complaining about, not GRUB. I said what I meant and I meant what I said. You didn't. GRUB 2 can boot from GPT disks. The fact that it works best with a special partition is part of its design. The fact that the Ubuntu installer doesn't set that partition up by default is an Ubuntu issue, not a GRUB issue. This may seem like hair-splitting, but as a practical matter, if you want something done about the issue, you need to know to whose attention to bring the issue or what bit of code to modify yourself. Searching GRUB for a way to make it "work" with GPT isn't the solution to the problem if, as is the case, the problem is in the Ubuntu installer. Another distribution might do it just fine. (I'm not sure which use GRUB 2 on GPT by default, though; Fedora still uses GRUB Legacy, for instance.)

---

### Post by YesWeCan on 2011-06-13
So the current assumption is that the DOS MBR boot code and PT is incapable of booting an extended partition. Therefore, a partition-based Grub would need to be in a primary partition.

I'd like to clarify the GPT situation.
My understanding is that the first sector is used for the (optional) boot code and subsequent sectors (those that Grub stage 2 would occupy) are used for the GP table itself. This is why Grub needs a separate partition for at least stage 2.

When Grub2 is installed on a GPT type disk, does a version of the Grub stage 1 (MBR boot code) get put in sector 0 or not? Or is it that Grub stages 1 & 2 are both put in the special partition and that partition is set to boot in the GPT?

---

### Post by oldfred on 2011-06-13
It is only windows that will not boot a logical partition officially. Windows defines primary partitions as bootable partitions.

Grub will boot any partition. But it is MBR/msdos partitioning and BIOS that determine how a computer boots. BIOS is designed just to jump to MBR and load that code. A few BIOS (some Intel ) will not boot unless you have a boot flag on a primary partition but that design assumes windows, I guess. I have installed grub2 to a PBR. The MBR just loads the PBR and it does work, just not reliable.

With BIOS and gpt the MBR is still used but the bios_grub partition provides the extra space for grub2's core.img. One other advantage of gpt is all partitions are primary.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on

---

### Post by YesWeCan on 2011-06-13
Presumably it is not necessary for a Grub stage 1 code to overwrite the MBR code in a GPT system. Both the Grub stage 1 and the core.img can exist in the bios_grub partition. This way, if one deletes the associated Ubuntu partition one doesn't lose the ability to boot other OS's normally.


It seems to me that with the DOS-MBR system, the only reason that Grub needs to over-write the MBR code is to avoid consuming one of the 4 primary partitions. Otherwise, one could just use a primary partition in the same way as required for the GPT system.

But as the GPT system allows 128(?) primary partitions and Grub has to use one of them, there seems to be no excuse to over-write the sector 0 MBR at all.

Am I making sense or have I lost the plot?

---

### Post by oldfred on 2011-06-13
It is BIOS that has to jump to the MBR. It does not matter what system you are using. If it is BIOS based it uses the MBR.

While this is Vista & XP it applies to all BIOS, MBR systems. If you do not want all the details it explains just review pictures. I think it mentions Lilo at the end. 

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

If you go back to very old systems with IDE, the BIOS was only able to boot the MBR from the primary master in the IDE chain. And that was set with jumpers on the IDE hard drive.

---

### Post by srs5694 on 2011-06-13
> **YesWeCan said:**
> Presumably it is not necessary for a Grub stage 1 code to overwrite the MBR code in a GPT system. Both the Grub stage 1 and the core.img can exist in the bios_grub partition.

That's incorrect, at least on a BIOS-based computer. On a BIOS-based computer, the MBR gets read by the BIOS, and when GRUB installs to a GPT disk on a BIOS-based system, it overwrites the MBR (meaning sector 0) code.

There is, however, an incorrect assumption in your summary that needs addressing. Through this discussion, your complaint boils down to GRUB overwriting the DOS/Windows MBR boot loader. That boot loader, though, is 100% useless on a GPT disk, and Microsoft has no equivalent for it. That's because Microsoft does not support booting Windows (much less DOS) on GPT disks on BIOS-based computers. The range of GPT-capable boot loaders available for BIOS-based computers is pretty narrow. It includes modified versions of GRUB Legacy, GRUB 2, certain varieties of SYSLINUX, possibly LILO, one or two FreeBSD boot loaders, and various Hackintosh boot loaders. Notably absent from this list is anything from Microsoft. Maybe they've got something in-house, but if so they've certainly never released it publicly.

To boot from a GPT disk, Microsoft *requires* UEFI, not BIOS. UEFI boots in an entirely different way from BIOS. Most notably, the firmware itself includes FAT (and sometimes other) filesystem drivers, and it includes a simple boot loader of sorts that loads OS-specific files from a FAT partition known as an EFI System Partition (ESP). Note that this procedure does *not* require boot code in the MBR or in unallocated sectors anywhere on the disk. Where the design of the BIOS created a potentially destructive battle for which boot loader controls the computer by requiring one and only one to occupy the precious MBR position, the UEFI design enables multiple boot loaders to coexist in the ESP. One can be flagged as the primary boot loader, but that's easily changed, unlike the MBR code position, in which one boot loader *replaces* another's code to take top position.

> This way, if one deletes the associated Ubuntu partition one doesn't lose the ability to boot other OS's normally.

On a BIOS-based computer with a GPT disk, this is also incorrect, at least with the typical method of installing GRUB through Ubuntu or other distributions. In these setups, critical GRUB files still reside in the Linux /boot directory, which is either a separate partition or part of the Linux root (/) partition. (Of course, with either MBR or GPT, you can use a separate /boot partition and then not delete or overwrite it if you delete or replace the original OS. Alternatively, you can create a dedicated GRUB partition and install GRUB there independently of any OS.)

Your statement is mostly correct on a GUID-based computer. In that case, the boot loaders all reside in the ESP, which should not be touched by an OS deletion. The catch is that if GRUB relies on files in another partition (as Ubuntu's GRUB installation on a UEFI computer does), and if that GRUB is configured in the firmware as the primary boot loader, then it'll malfunction if you delete the Linux partition. This is still preferable to the BIOS situation, though, because it's easier to recover from the problem -- you can go into the firmware and tell it to use another boot loader as the default.

> It seems to me that with the DOS-MBR system, the only reason that Grub needs to over-write the MBR code is to avoid consuming one of the 4 primary partitions. Otherwise, one could just use a primary partition in the same way as required for the GPT system.

That's one way of looking at it, aside from the GPT analogy. Certainly there have been boot loaders that consume a primary partition all by themselves. OS/2 had one like that, called Boot Manager. The problem is that this effectively reduces the number of available primary partitions to 2, since you need one for the boot loader and one for the extended partition. With most modern Windows pre-installations chewing up 3 or even 4 primary partitions all by themselves, this sort of design would be a real problem today.

> But as the GPT system allows 128(?) primary partitions and Grub has to use one of them, there seems to be no excuse to over-write the sector 0 MBR at all.

Again, with a BIOS-based computer, *something* has to put code in the MBR or the disk won't be bootable. Microsoft *never* puts a boot loader in a GPT disk's MBR, so your objection to GRUB doing so is irrelevant. On a UEFI-based system, *nothing* puts code in the MBR's code area (unless a utility thinks it's on a BIOS-based computer and does it inappropriately), so the concern is misplaced.

---

### Post by YesWeCan on 2011-06-15
Grub is like a Windows boot-loader that is not contained within the Windows partition. Instead, it replaces the standard MBR code, consumes unallocated sectors immediately afterwards (which sometimes conflicts with other programs) and creates a booting dependency on the Ubuntu partition. This is why if you delete Ubuntu you cannot boot anything. 

Grub basically breaks the MBR system.

I see justification in this only in so far as it allows Grubs files to exist in a non-primary partition. If a primary partition is available, there is no good reason why grub should not be entirely contained within it, just like Windows does, and be MBR compliant. Presumably this is only necessary if you wish to install to a disk that has already used 3 of its 4 primary partitions and you need extended partitions.

Furthermore, I think Grub/Ubuntu ought to be designed to work reliably when Grub is installed to PBR. This way, the user has full flexibility to boot directly or chainload from another loader, such as the Windows boot loader. It would be a lot easier for a lot of users if Ubuntu had the option to add itself to the Windows boot menu and leave the MBR system intact.



With GPT disks you can have any number of primary partitions (Windows chooses a limit of 128 ). So there is no need for Grub to exist outside of a primary partition and I would hope that this is the way a future Ubuntu installer will arrange things by default. This way everything is clean and compliant.

---

### Post by YesWeCan on 2011-06-15
It seems to me that the basic principle of the MBR system is that a partition is bootable via its PBR code.

Why isn't a Ubuntu partition bootable via its PBR code?

Without this limitation, the only potential issue would be how to boot an extended partition. For this, a user could install a custom MBR code that does just that and nothing else. But this would not be called Grub or have to be installed unless needed. I think it would be easier for a novice user to comprehend and it could be used for any primary or extended partitions, not just for Ubuntu's. Of course, this is not an issue with GPT.

---

### Post by HawkFest on 2011-06-22
> **Herman said:**
> The reason why I'm saying people are selfish is because most people want to be able to have Ubuntu for free and keep their Windows too. The concept of dual booting is not really supported by any operating system vendor or at least it's not regarded as an ideal situation.
And that "regard" would be where the "selfishness" you're talking about actually reside (which is *not* on the user's side). I'm sure that you are aware of that one fact : since the advent of Internet, new paradigms are now depicting a "customer-centric" world. Users dictate their needs, not some product marketer or manager pretending to know-it-all for every current usage and beyond while seeking one single "ideal situation" that must fit everyone's needs... In the real world and a Universe expanding in complexity, Universality for a "one-size-fits-all" is not a panacea. Especially when considering power-users, developers, IT integrators and such...

> **Herman said:**
> Ubuntu isn't designed to be a second operating system in a Windows PC, Ubuntu is designed to replace Windows.
Take this issue the other way around : in regards to currents technologies, maybe that Users aren't "designed" upon some pseudo standard so as to rely on one sole operating system?

One example - I personally use Ubuntu for all office works (web, e-mail, spreadsheet, texts and presentations, collaboration tools and Web 2.0, etc.). I prefer the tranquility of mind provided by Linux's ACL and robust security "by design", over Window's holiday resort for viruses backdoors and such. More over, Linux requires much less maintenance than Windows (no need for disk defragmentation; no need to clean some registry database slowing down the system, and potentially ending-up reinstalling the whole Windows system; no need to run a virus scan every week or so; no need to actually acquire an anti-virus!)... However on the other hand, I need Windows for the use of specific applications such as Adobe CS5 and Maya, and my girl friend who's a doctor needs a specific application solely running under Windows (so that she can do her conciliation with the ministry from home - we have a government funded universal health system here, but that's not the issue, it's an example). As well as other software in regards to the market, the client base and most of all the features, not to mention GAMES.. ;)

That's what I NEED, and I'm sure I'm not the only one. As such, that's what I expect OS developers and publishers to facilitate (amongst other things of course). Therefore, I agree with YesWeCan who states the following: > **YesWeCan said:**
> It seems to me there is an inconsistency between Canonical's aim to "convert" hundreds of millions to Ubuntu, presumably most of whom are currently using Windows, and the obvious lack of care and attention in Ubuntu's installation process and documentation with regard to happy coexistence of the two. For a transition must be expected to involve a dual boot stage along the way. I suggest a target Windows user is going to be gun-shy of linux and what will improve their confidence of Ubuntu is an assurance that their existing system will not be harmed in any way. So I am surprised that Canaonical are not putting proper efforts in to making this transition as trouble-free as possible.

> **Herman said:**
> There are also a few good people here in this forum who are willing to give up some of their time to try to help anyone having difficulties.
Hail to them and especially to you!.. :KS

---

