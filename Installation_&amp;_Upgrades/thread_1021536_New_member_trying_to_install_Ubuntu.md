---
title: "New member trying to install Ubuntu"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by Michael Maurice on 2008-12-25
Hi

I'm a new member to the forum and to Linux Ubuntu itself.

I have been interested in Linux for some time but only now that I have a spare computer have I got round to experimenting with it.

But when I try and install it, the computer freezes and has to be switched off before by pressing the power button before it can be restarted.

The computer I'm using is an HP Pavilion loaded with Windows XP home edition.  It has recently been reformatted.

I have two Ububtu CD roms, one had Ubuntu 7, the other came with a magazine and has Ubuntu 8

When I put either CD ROM in and reboot, i get a screen with two icons on it, Examples and Install.

There is also an information bar at the top with Aplications, Places, System, Firefox an envelope and a symbol with a question mark in it.

So I click on Install, and it begins, by asking my language: English.   My location: London.    Keyboard Layout: United Kingdom,   

Then it says starting up the Partitioner and I get to a screen that says:

**Prepare disk space**

How do you want to partition the disk?

Guided - resize SCSI1 (0,0,0,, partition #2 (sda) and use free space

Guided - use entire disk

Guided - use largest continous free space

Manual



As the first option is highlighted I have been using this, it starts to do what it has to do then the computer freezes.

If I try the manual option, I select ntfs media SDA2 but it just says: no root file system is defined.

So where am I going wrong and what do i have to do to correct it?

---

### Post by Partyboi2 on 2008-12-25
hi
Try defraging your windows a couple of times then try again. If you choose to manually  make the partitions create  a ext3 partition with the mount point set to /  then make another partition called swap which should be roughly 1.5 times the amount of ram (max 3 gig) of your onboard ram.
If you choose ntfs media SDA2 then you will end up wiping (unless you are resizing) your ntfs partition which I assume is your windows installation.
Remember to backup your important stuff before working on partitions.

---

### Post by 2hot6ft2 on 2008-12-25
You have to create the file system. By that I mean you have to tell it where root will be. See the attached pic. Use manual partitioning. It's better to see what you're doing.

You create the partitions, 1 for the system (type ext3, mount point /) this will be root and where your system will be. That's the part your missing

2. A swap partition (2 gig is plenty more or less if you want, file type swap)

---

### Post by Michael Maurice on 2008-12-25
Hi, I've followed your advice and tried installing manually but thecomputer still freezes,

A bit more info, the hard drive is patitioned in Windows to a C drive and D drive.

Does this make any difference?

I was thinking of puttinmg a new hard drive in the computer, booting from the CD and installing on the new hard drive, but this meas i wouldn't have windows, and how would i dowload the computer drivers in linux?  surely these are windows based.

---

### Post by Toshibawarrior on 2008-12-25
Linux will take care of the drivers and if you have any "restricted" hardware meaning the drivers are closed-source then most probably they're up in the repositories and will work with no problems.

As for the installation problem, try to make a partition and format it to some fylesystem other than NTFS...Your idea of using a new hard drive is very good. You could install Ubuntu and then install XP...but you can also install VirtualBox inside Ubuntu and run XP from there...Runs pretty much like having a dual-boot, except for some quirks with 3D rendering (inside XP).

Check the installation using a new drive. OR...maybe, just maybe, you have a bad LiveCD and that's why it freezes...try using the "Check Media For Defects" option on the LiveCD's main menu.

Let me know how it goes.

---

### Post by Michael Maurice on 2008-12-25
Thanks Toshibawarrior,

I've actually got two live CD's one with Ubuntu 7 and one with 8, they both freeze at the same point!

How does one make a new partition?  I've never done this before?

Thanks once again

Michael

---

### Post by Toshibawarrior on 2008-12-25
Once you're in the Partitioner of the LiveCD's installer select Manual, and then select one of your existing partitions and click on Edit...then shrink that partition. Once you do that you'll have unallocated space, with which you'll create a partition by selecting New Partition, then use "/" as the mountpoint and ext3 as the filesystem. The do the same for swap. (Select a big partition and shrink it then use the unallocated space for swap.

I'm sorry if I confused you...I've done these steps more than 50 times and I still can't memorize the exact names of the buttons and options...I just do it automatically when I see the partitioner, so it's a little bit hard to actually guide you through  it without actually seeing the partitioner...

Sorry about that. I hope you got what I tried to say.

If not let me know and I'll see what I can do to give you a more detailed instruction.

---

### Post by Michael Maurice on 2008-12-26
I couldn't install on the HP desktop so i tried it on a spare laptop, trouble is i think i've wiped windows which isn't too terrible because all i used it for was my wife's i tunes. but the laptop was connected to the internet using a netgear wirelss card which i cant get the drivers for on linux.

I was only experimenting with linux, unfortunately the main programmes i use are all windows based so i cant use it as a main system.

So my questions:

1) In Linux can i get drivers for the Netgear WG511v2 wireless card

2) Have I lost all my Windows XP files?

---

### Post by Toshibawarrior on 2008-12-26
> **Michael Maurice said:**
> I couldn't install on the HP desktop so i tried it on a spare laptop, trouble is i think i've wiped windows which isn't too terrible because all i used it for was my wife's i tunes. but the laptop was connected to the internet using a netgear wirelss card which i cant get the drivers for on linux.

I was only experimenting with linux, unfortunately the main programmes i use are all windows based so i cant use it as a main system.

So my questions:

1) In Linux can i get drivers for the Netgear WG511v2 wireless card

2) Have I lost all my Windows XP files?

1)Read [this]("http://ubuntuforums.org/showthread.php?t=992272&highlight=Netgear+WG511v2") and pray that it works...:(...Apparently that's a very problematic card/router/piece of gear...I've never used NG products so I can't be of much assistance there...

2)Why do you think you wiped windows off your laptop?....Did the windows partition disappear?...If it did your files are gone...It's **_*always a good practice to backup important data *_**before fiddling with Linux or any other OS. Install gparted:

```
sudo apt-get install gparted
```

on a terminal.

And check which partitions are in your HDD.

Come back with the info when you get it.

---

### Post by Michael Maurice on 2008-12-26
Hi Toshiba warrior,

Sorry it took so long to reply.

I dont really understand about gparted, i tried to downloaded this but don't know how to load or use it.

Also if my laptop was now dual booted, how would i be switching from Linux to XP?

I hope i don't appear to stupid, but I'm not that brilliant with windows and Ununtu is a completely different ball game.

BTW, what part of the world do you come from?

Regards

Michael

---

### Post by Toshibawarrior on 2008-12-26
> **Michael Maurice said:**
> Hi Toshiba warrior,

Sorry it took so long to reply.

I dont really understand about gparted, i tried to downloaded this but don't know how to load or use it.

Also if my laptop was now dual booted, how would i be switching from Linux to XP?

I hope i don't appear to stupid, but I'm not that brilliant with windows and Ununtu is a completely different ball game.

BTW, what part of the world do you come from?

Regards

Michael

Ok...Go to Synaptic Package Manager (System>Administration>Synaptic Package Manager and enter your password. Once inside click on the "search" button, and search for "gparted" (without quotes). Once installed go to System>Administration>Partition Editor and enter your password (if prompted to).

If Windows was still alive you're supposed to see it on the GRUB (that neat black and white menu you get right after the BIOS screen when booting up your computer.). If you have Windows still in your hard drive you should be able to see it and the whole list of bootable partitions by pressing the ESC key a few times right after the BIOS menu/screen...

And I'm from the caribbean...Puerto Rico to be exact...why?...:popcorn:

---

### Post by Michael Maurice on 2008-12-26
> **Toshibawarrior said:**
> 

If Windows was still alive you're supposed to see it on the GRUB (that neat black and white menu you get right after the BIOS screen when booting up your computer.). If you have Windows still in your hard drive you should be able to see it and the whole list of bootable partitions by pressing the ESC key a few times right after the BIOS menu/screen...

And I'm from the caribbean...Puerto Rico to be exact...why?...:popcorn:

No you cant see windows when you boot up in the black and white menu, nor can you when you press esc when booting up!

Just wanted to know where people are from.

I presume that because I've lost windows, i cant install my wireless netgear adapter!

Also i presume one cant put in Apple Ipod and itunes either

---

### Post by Toshibawarrior on 2008-12-26
> **Michael Maurice said:**
> No you cant see windows when you boot up in the black and white menu, nor can you when you press esc when booting up!

Just wanted to know where people are from.

I presume that because I've lost windows, i cant install my wireless netgear adapter!

It's not supposed to. Windows partitions stay clear from Linux partitions. So whatever happens in Windows stays in Windows...

Did you read the link I gave you above?...It has tons of information about getting that model working...Try it. Sadly I can't give you exact instruction because I've never used NetGear products...I currently have a Linksys WRT54GS router and an Atheros AR242x card on my laptop and everything works fine.

Try reading that link. Maybe it'll help. If you find something you think  might be useful but don't understand me send me the link to the exact post and I'll try to help. :)

---

### Post by Michael Maurice on 2008-12-26
> **Toshibawarrior said:**
> It's not supposed to. Windows partitions stay clear from Linux partitions. So whatever happens in Windows stays in Windows...



So how do I find windows?  assuming of course that its still there.

---

### Post by Toshibawarrior on 2008-12-26
> **Michael Maurice said:**
> So how do I find windows?  assuming of course that its still there.

Open gparted (like I explained above) and check if there's a partition with a FAT32/FAT16/NTFS filessystem...If there is such a thing then Windows should be alive somewhere. But if you specified in the partitioner of the LiveCD installer to use the entire disk, or you made a new partition table in Manual mode, then Windows is long gone...:(sorry.

Check gparted...and while you do copy the following command into a terminal:

```
sudo fdisk -l
```

Copy that command into a terminal and copy the output here for me to see it. That way I might get a chance to locate Windows if it's still alive.

---

### Post by Michael Maurice on 2008-12-27
What I'm going to do later on is to remove the hard drive from the laptop and connect it to another computer so I can see what files and partitions are on it, what I may then do is to reinstall windows and then ask for help in putting Ubuntu on top of it.

It seems that though Ubuntu is a very good and probably safe OS, one is limited as to what one can do with it.

I could never use it exclusively, too many of my programmes are windows only based and one of them is a DOS programme.  Its old but it works very well.

Many thanks for your replies and help and I look forward to continuing on the site.

Regards

Michael

---

### Post by Partyboi2 on 2008-12-27
If you want to check your hard drive to see if your windows partition is still there you can boot the ubuntu live cd and open a terminal (Applications>Accessories>Terminal) and type
```
sudo fdisk -l
``` this will list your partitions.

---

### Post by Michael Maurice on 2008-12-27
Windows was wiped when I installed Ubuntu, 

I am reinstalling windows XP professional on the laptop and would like to put Ububtu either 8 or Ubuntu 7 as a separate partition so I can play with it.

Can someone kindly explain how I install Ubuntu on a separate partition.

Many thanks

Michael

---

### Post by Partyboi2 on 2008-12-27
You can follow [[COLOR=Blue]this[/COLOR]]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") howto.

---

### Post by BatteriesNotIncluded on 2008-12-27
As a thought you might want to try using Wubi on the install cd. I have a Compaq laptop that flat out refused to dual boot and with Wubi everything works great.

---

### Post by Michael Maurice on 2008-12-27
One more question, would i be better installing Ubantu 7.10 or 8.10? 

I have the disks for both.

---

### Post by Coder543 on 2008-12-27
8.10 would be better.
Look, once it is installed (you sound like you will need ethernet if you don't have the wireless working in ubuntu) go to the Add/Remove... application in the Applications menu (at the bottom) then at the top select All Available Applications then search for Wine. Then install the Wine Windows Program Loader (something like that). Now you can run most of your windows apps in Ubuntu.

---

### Post by Michael Maurice on 2008-12-28
Some progress.

I have installed both Windows XP and Ubuntu 8.10 the partitions are working and i can dual boot.

I have selected and installed the Windows wireless system ndiswrapper

I can go into Windows Wireless Drivers, I've got a disk that came with my Netgear Wireless Card and it works in windows, so how do i install it in Ubuntu?

---

### Post by Toshibawarrior on 2008-12-28
> **Michael Maurice said:**
> Some progress.

I have installed both Windows XP and Ubuntu 8.10 the partitions are working and i can dual boot.

I have selected and installed the Windows wireless system ndiswrapper

I can go into Windows Wireless Drivers, I've got a disk that came with my Netgear Wireless Card and it works in windows, so how do i install it in Ubuntu?

So...what's on the disk?...The drivers?...Utilities?...If you already have ndiswrapper working you shouldn't need anything else. And if it is an utility to access/manage the card, forget about it...Those kinds of programs are a mess in Ubuntu.........:(

---

### Post by Michael Maurice on 2008-12-28
> **Toshibawarrior said:**
> So...what's on the disk?...The drivers?...Utilities?...If you already have ndiswrapper working you shouldn't need anything else. And if it is an utility to access/manage the card, forget about it...Those kinds of programs are a mess in Ubuntu.........:(

So really and truly I can only use Ubuntu in an environment thats either fully wired to the net or which has a built in wireless connection.  Unless of course anyone else has other ideas..........

---

### Post by Toshibawarrior on 2008-12-28
> **Michael Maurice said:**
> So really and truly I can only use Ubuntu in an environment thats either fully wired to the net or which has a built in wireless connection.  Unless of course anyone else has other ideas..........

No.....................Ubuntu can support wireless devices, you just need to fiddle with them a little...don't expect out-of-the-box-high-performance by default...In Linux everything is customizable and "fiddable"....#-o:-k:???:](*,)

---

