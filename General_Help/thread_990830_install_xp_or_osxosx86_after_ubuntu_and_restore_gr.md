---
title: "install xp or osx/osx86 after ubuntu and restore grub"
date: 2008-11-23
forum: General Help
---

### Post by EnGorDiaz on 2008-11-23
Legal stuff.
> 
**Warning: breaking the eula of apple or windows with or without legitamite licence is purely illegal.**

Sorry guys but first i need to put out the legal stuff this thread will not go against the code of conduct on the forum.

[http://www.apple.com/legal/sla/](http://www.apple.com/legal/sla/)

[http://www.microsoft.com/windowsxp/eula/home.mspx](http://www.microsoft.com/windowsxp/eula/home.mspx)


**Now lets get started.**

This topic is for those who have installed ubuntu first and want to install xp or osx after ubuntu.

Thing's youll need for this.

```

**USB.**
[LIST]
[*]Youll need the link to this page store it on the usb youll need it.
[/LIST]

**Ubuntu 8.04 or .10 disk.**
[LIST]
[*]Youll need this to create 3 seperate partition's, using the partition tool Gparted
[/LIST]

**Windows XP OEM Disk.**
[LIST]
[*]Youll need this to install the operating system.
[*]Youll also need this to fix the bootloader if you have any problem's.
[/LIST]

**OSX86/Apple Leopard 10.5.5 Install Disk.**
[LIST]
[*]Youll need this to install osx on a partition.
[*]youll need this to reinstall the darwin bootloader.
[/LIST]
```


Im going to put this in list order. Its easier to read out you wont make many mistakes, But you can always fix them.:)

[CENTER]**Step 1.**[/CENTER]


Take your **Ubuntu 8.04 Install Disk.** 
[LIST]
[*]Boot into the **Ubuntu** disk(under try before install option).
[*]Now once your logged in goto ** System>Administration>Gparted/Partition Editor**
[*]Now youll see a partition which is marked as **EXT3**
[*]If you have this partition taking up the whole **Hard Drive, Then right click>Resize/Move** Resize it enough for 2 partition's.
[*]Now create 2 Partition's.
[*]The first **NTFS** you will install **Windows XP** on this Partition.
[*]The second partition will be **FAT32**. You will install **OSX** on this partition. as you cant make **HFS** by default.
[*]Click **Apply** after its finished your done. Log out of the disk.
[/LIST]

[CENTER]**Step 2.**[/CENTER]
[LIST]
[*]Take your **Window's XP OEM Disk.**
[*]Boot into it.
[*]Now when you agree to the eula youll see the partition tool come up. now press enter on the one with **NTFS** and **Quick Format** it to **NTFS** or **Keep the current file system** option in the format menu.
[*]Now let it install all the file's when its finished press enter at the restart prompt
[/LIST]

**Quick note:** You will notice when you reboot an error will come up and it will restart dont panic the resolution comes next. 

[CENTER]**Step 3.**[/CENTER]  
[LIST]
[*]Take your **Ubuntu Disk.**
[*]Boot into it now start the **Terminal.** in **Application's> Accessories**
[*]Now put in the following commands.
[*]**sudo grub** (wait for it to probe your **BIOS**)
[*]Then **find /boot/grub/stage1** press enter if it comes up with [hd0,0] then your set. :)
[*]Now put in **root (hd0,0)**.
[*]And put in now put in **setup (hd0)**
[*]Now to save everything you have done put in **quit** press enter.
[/LIST]


Now you should boot into **Ubuntu** this what is supposed to happen.

> The next step is abit more complex but not to hard.

Example of grub list located in /boot/grub/menu.lst

title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=de36de4b-554a-4a0a-b69c-9b3ad10279a1 ro quiet splash
initrd /boot/initrd.img-2.6.24-21-generic
quiet

title Windows Xp
rootnoverify (hd0,2)
chainloader +1
makeactive

title MacOSX
root (hd0,1)
chainloader --force +1

Your wondering why am i showing this well if you notice there is after rootnoverify(recommended for **Windows XP** bootloader issue's) or root there is a (hd0,#) when your in **gparted** you will notice that there is /dev/sda1/ now **Ubuntu** is located on this one but you will notice (hd0,0)

so if sda1 it = (hd0,0) after root 


[CENTER]**Step 4.**[/CENTER] 
[LIST]
[*]Download **Gparted** on your normal **Ubuntu 8.04** installation in **Synaptic**. 
[*]Then goto **System>Administration>** then youll see **Partition Editor**(Gparted) see the sda number for your **Windows XP** install. (Now remember the method above.)
[*]Now open **Terminal** and put in the following command **gksudo nautilus**(This will open **Nautilus** in root.)
[*]Now goto **File System** youll see a folder called **boot** open it then youll see a folder called **grub** open that then look for the file **menu.lst** double click on it and it will open it in root.
[*]Next you will have to edit the list to boot into **Windows XP** and finish the installation remember the method with sda1 = hd0,0
```

title Windows Xp
rootnoverify (hd0,#)(Remember the method cut this text out.)
chainloader +1
makeactive
```
Paste that into the end of the file edit it to fit with the **gparted** list remember **NTFS**.(Save the file and reboot)
[/LIST]


[CENTER]**Step 5.**[/CENTER]
[LIST]
[*]Boot into **Windows XP** on the installation disk.
[*]hold down the key R to go into the **Recovery Console**.
[*]Now put in the following commands **fixboot** and then **fixmbr**.
[*]Reboot and see if **Windows XP** starts up.
[/LIST]

**Note:** Dont panic because **grub** wont show where about to restore **grub** right now. :)


[CENTER]**Step 6.**[/CENTER]
[LIST]
[*]Boot into the **Ubuntu** installation disk. Under the try before install option.
[*]Now put in the following commands.
[*]**sudo grub** (wait for it to probe your **BIOS**)
[*]Then **find /boot/grub/stage1** press enter if it comes up with [hd0,0] then your set. :)
[*]Now put in **root (hd0,0)**.
[*]And put in now put in **setup (hd0)**
[*]Now to save everything you have done put in **quit** press enter.
[/LIST]

Now we can finish the installation of **Windows XP** just start it up from the grub list with the xp disk inside your **CD/DVD** drive and it will finish hurray! you have **Windows XP** installed for what ever purpose.

> The next step this is for users who want to install **OSX/86**

Please refer to the eula at the top of the post i am not giving any links to **osx86** or hacked **osx** install's.

**Note:**_**This is for apple hardware also**_. :)



[CENTER]**Step 7.**[/CENTER]
[LIST]
[*]Boot into your **OSX** install disk
[*]When you have agreed to the **EULA** goto **Utilitys** in the **Global Menu**
[*]Click **Disk Utilitys** You will see the **FAT32** partition. goto **Reformat** and reformat it to **hfs+ Journaled**
[*]Once its done exit the utility.
[*]Now install the operating system. Your done! :).
[/LIST]

**Note:** You will get an error at reboot dont panic where going to sort it out. by reinstalling **grub** and activating partition with **OSX**.

[CENTER]**Step 8.**[/CENTER]
[LIST]
[*]Boot into the **Ubuntu** installation disk. Under the try before install option.
[*]Now put in the following commands.
[*]**sudo grub** (wait for it to probe your **BIOS**)
[*]Then **find /boot/grub/stage1** press enter if it comes up with [hd0,0] then your set. :)
[*]Now put in **root (hd0,0)**.
[*]And put in now put in **setup (hd0)**
[*]Now to save everything you have done put in **quit** press enter.
[/LIST]

**Note:**This next step is vital. Where going to add **OSX** to the **grub menu.lst** file.


[CENTER]**Step 9.**[/CENTER]
[LIST]
[*]Boot into **Ubuntu**.
[*]Now open **Terminal** and put in the following command **gksudo nautilus**(This will open **Nautilus** in root.)
[*]Now goto **File System** youll see a folder called **boot** open it then youll see a folder called **grub** open that then look for the file **menu.lst** double click on it and it will open it in root.
[*]Next you will have to edit the list to boot into **OSX** but thats not the end of it.

Remember when your putting **OSX** in the **menu.lst** file.

To put it in like this.:)

```
title MacOSX
root (hd0,1)(Remember the sda1 = hd0,0 but apply to the **OSX** partition, cut this text out.)
chainloader --force +1
```
[*]Save the file.
[/LIST]

**Note:**This next step is to fix the **Darwin** bootloader.


[CENTER]**Step 10.**[/CENTER]
[LIST]
[*]Boot into the **OSX** install disk.
[*]Goto **Utilitys** and **Terminal**.(Now theres a different method to this one remember this sda1 = hd0,0 well forget that in this step just keep this one in mind flag2 = sda2)
[*]Now put in the following command's **fdisk -e /dev/rdisk0** Press Enter, then **flag#**(remember flag# = sda#) Press Enter, then **Write**, **update**, **quit**, **reboot** 
[/LIST]

Ok if you have a problem with grub loading up just repeat **Step 8.**

You will probably be exhausted after this but guess what you have successfuly installed windows xp and osx after ubuntu. 

Hurray,

Have Fun!

---

### Post by EnGorDiaz on 2008-11-23
Wait theres more if you get sick of both os's then you can simply get rid of them by following these steps

**Note:**back up all data on those partitions like on a dvd or cd :D.

**[CENTER]Step 1.[/CENTER]**
[LIST]
[*]Boot into your **Ubuntu** live cd.
[*]Now once your logged in goto  **System>Administration>Gparted/Partition Editor**.
[*]Right click on the 2 partitions (NTFS and HFS+) and delete the them, click apply.
[*]Then right click your EXT3 partition and click Resize/Move
[*]then resize it to take up your whole drive.
[/LIST]

**[CENTER]Step 2.[/CENTER]**
[LIST]
[*]Boot into **Ubuntu** normaly.
[*]Then open up the **Terminal** and do the following commands **gksudo nautilus**.
[*]then navigate to the **File System** then youll see a folder called **boot** goto to it and go into **grub**.
[*]Find the **menu.lst** open it and simple take out the **Windows XP** and the **OSX** entrys out of the list.
[/LIST]

and your done. :)

---

### Post by EnGorDiaz on 2008-11-23
also for gentoo users and others there is a main thread to grub reinstall

[http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

---

### Post by retskrad on 2009-01-04
Is there a way to install MAC OS X LEOPARD on my PC?

---

### Post by EnGorDiaz on 2009-01-21
> **retskrad said:**
> Is there a way to install MAC OS X LEOPARD on my PC?

sorry but i am not aloud to give you detail as to how on this forum

there is a way to and its called osx86 thats the only thing i can tell you

---

### Post by acdc_rulz on 2009-05-08
Hello,
I have an HP NC8000 laptop and came across this site and decided I would give the JAS OSx86 10.5.4 OSx install disc a try. I installed this to my HP that already had Ubuntu 8.10 installed so it seems this configuration was a little bit different from others who have posted in this section. In any case, after booting with the JAS 10.5.4 install disc, I went through the installation and selected the appropriate install options for this PC:

Kernel Packages:
StageXNU
Audio Drivers:
AC97Audio
Device Identification
Atheros Wireless Adapter
Intel ICH and PIIX Controller

However, after rebooting from the OSx install, I cannot get OSx to load and no GRUB boot menu option was created by the JAS install disc. Here is the output of my fdisk (listing partitions and filetypes): (sudo fdisk -l)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sda1 1 2231 17920476 83 Linux
/dev/sda2 * 2232 9729 60227685 5 Extended
/dev/sda5 * 2232 4162 15510694+ af Unknown
/dev/sda6 4163 4445 2273166 82 Linux swap / Solaris
/dev/sda7 4446 9729 42443698+ 83 Linux

/dev/sda5 is the partition that OSx was installed to and it is under the /dev/sda2 Extended partition. Will installing OSx to this partition be a problem? Also, I tried to create another partition (using Gparted Live CD) under /dev/sda1 but no matter what filetype I created this partition in, the JAS OSx86 install disc would not install to this partition).

So now my NC8000 boots Ubuntu without issue but my mac OSx partition is not accessible and will not boot during startup. Any ideas for how to fix this? I have searched around A LOT for users that have installed OS X in this manner but none have had this problem apparently (most likely because they installed OS X on a clean system without WinXP/Vista/Ubuntu.


Also, I did some research and created the following entry in my /boot/grub/menu.lst to create a Mac OS X boot entry in GRUB:

title MacOSX
root (hd0,1)
chainloader --force +1

When I try to select this entry from the GRUB menu, I get a "Loading stage 1...@#$@%" and then the system hangs. When I change the root (hd0,1) to root(hd0,2), I get a lot of hard drive activity and then a "Loading stage 2..." and the system hangs.

Please help!

---

### Post by TheNosh on 2009-05-24
> **retskrad said:**
> Is there a way to install MAC OS X LEOPARD on my PC?

it depends a bit on your hardware, so if you follow the hint you've been given be sure to check hardware compatibility before installing anything

---

### Post by xennon on 2009-07-18
Thanks for your detailed guide, so much work, very much appreciate your sharing the steps. I learned a lot.   For me, the dual boot Ubuntu/XP works, but with OSX install at Step 7, the reformat of the FAT32 partition (convert to hfs+ Journaled) fails:  [quote> **Disk Utilitys** You will see the **FAT32** partition. goto **Reformat** and reformat it to **hfs+ Journaled**[/quote]  The FAT32 partition is greyed out, will not mount, will not, reformat to hfs+ Journaled. Tried various techniques to make the reformat work, others have the same problem: [http://www.insanelymac.com/forum/lofiversion/index.php/t86569.html](http://www.insanelymac.com/forum/lofiversion/index.php/t86569.html)   Nothing there worked for my install though. So I'm stumped -- any suggestions for a way reformat that FAT32 partition for my OSX install?

---

### Post by killians31 on 2009-12-23
Excellent Post!

I do however have a few questions:

Does OSX require a primary partition, or can i use a logical partition?

Should i be installing chameleon as a boot loader, then over writing with GRUB, or don't install chameleon?

This might be a silly question, but is hfs+ journaled file system the same as extended journaled file system?

Will this code work with GRUB 2, or only GRUB Legacy? ```
title MacOSX
root (hd0,1)(Remember the sda1 = hd0,0 but apply to the **OSX** partition, cut this text out.)
chainloader --force +1
```

Thanks!

---

