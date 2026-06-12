---
title: "Systemax Desktop Wont Run Live CD"
date: 2014-02-01
forum: Hardware
---

### Post by CeejRab on 2014-02-01
Hello all,

i recently was given a project desktop computer from a friend and im trying to put ubuntu on it....

The specs are as follows:

Ascent Systemax 2004
AMD 64 Athlon
1GB Ram
200GB WD HD

i have a ubuntu 12.04.3 Live CD ive made from a windows xp setup which boots and loads the splash screen, but when the install session should load, my screen goes black and red lines flash allover it as if it cant find my graphic card all of a sudden. Like i said the splash screen shows fine with the ubuntu logo and the loading dots, but when it should show the desktop or installler it goes black with those red lines...

any ideas how i can get this to work so i can install my favorite OS? :) thanks!

-CJ

---

### Post by Bashing-om on 2014-02-02
CeejRab; Hi !

Assuming you have ATI or Nvidia grahics :

Boot the liveCD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets" - if the need should exist .
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
Launcher -> System Settings -> Additional Drivers, install the recommended driver.

If this works in the live environment we can make it work in the install !..

Does this work to boot "try ubuntu" ?

Other: 1 gig of ram may not be enough to run unity well, I often see 2 gigs recommended; else, a lighter desk top.

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by CeejRab on 2014-02-02
@bashing-om, 

Thanks for your reply, I will try this tomorrow morning! I'm having trouble with getting my USB to become bootable at the moment however... I'm running windows xp pro sp3 and trying to make my live USB with lubuntu, Ubuntu, and slax on it via Yumi, but for some inexplicable reason my USB stick keeps saying it can't be made bootable.... I've used it for many other distros before with no issues, and I even tried a low level reformat on the stick to clear the mbr, but no progress so far, all the bootable stick methods I try fail to make it bootable...? 

Anyhow I will try your advice as soon as I can get a live cd environment bootable and running! 

Yes it's an ATI Radeon card I believe, nothing special but it's adequate. 

Asfor the ram, I had an acer aspire one netbook with the intel atom chipset at 1.33 GHZ and 1gb ddr2 ram which ran Ubuntu 12.04 LTS with full gnome and unity quite well, so I don't know if the memory is actually the problem.... We'll see, you may be right, I don't know until I get the live cd to run! 

Thanks again, will get back with my progress as soon as I make some! More advice welcome, especially on the new issue that has come up with my USB sticks not being able to made bootable..... Hmmm

 All The best,

---

### Post by Bucky Ball on 2014-02-02
How are you making them? Try UNetbootin if you aren't already.

---

### Post by CeejRab on 2014-02-02
Hey bucky ball, I've tried YUMI, unetbootin, and others... Nothing seems to be able to make it bootable all of a sudden, they all send an error message saying it couldn't be made bootable and the live cd won't be bootable. 

I tried low level formatting and clearing the mbr, I tried deleting all partitions and making brand new clear mbr with one primary partition fat32, and more. Not sure what the deal is, they all worked fine before. I recall one of the USB sticks did this to me once before but somehow I fixed it... *if only I remembered how.*

---

### Post by CeejRab on 2014-02-04
so i have an update! by going to friend's house and using their 64 bit windows 7 pc, i was able to format and use yumi to make a multiboot drive with ubuntu, xubuntu, and slax on it as well as the live gparted iso. 

ubuntu 12.4.3 and 13 both fail to load the installer, i thought at first that gnome or unity was the cause seeing as my graphics card is a little old, its an ati radeon i believe. so i tried lubuntu, same problem, wont go past the splash screen with the loading dots, it just goes crazy flashing a black screen with my cursor showing as if it cant find my graphic card.

xubuntu is the only thing i could get to install, the installer had bad resolution so it was difficult but once installed to my HD i changed the resolution to 800x600 which is small but at least it fits on my screen! 

any ideas why even lubuntu wouldnt work? and how come xubuntu does? not sure, ive tried different releases to see if the kernel updates would help but no difference, only xubuntu works as far as *buntu distros go.... 

(please do note that slackware based slax runs well, even with a high quality KDE environment with widgets....)

id really like to get ubuntu working on here, cause its my favorite, and i really wont want to use windows xp or 7! i could make do with lubuntu, but i dont prefer xubuntu so any help to get me going with ubuntu would be appreciated.

thank again for all the answers so far!

all the best,

---

### Post by Bucky Ball on 2014-02-04
Why not just install Unity in Xubuntu if it is the desktop environment of Ubuntu you are after. You can then add whatever apps you want from Ubuntu right into Xubuntu. Customise.

Doesn't make much diff which you have installed. They all use the same Ubuntu base kernel. Just mix and match from that point.

---

### Post by Bashing-om on 2014-02-04
CeejRab; Maybe,

I Still think of it as a graphics driver thing. We need to identify the graphics card and look at what diver is being loaded by the different flavors of the operating system.
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

A I noted earlier, many times disabling Kernel Mode Setting in the kernel (nomodeset) forces the use of a frame buffer graphics driver that operates at a lower level and much less functionality, but will many times allow booting the system and permit the installation of higher level drivers.

We can work on getting Lubuntu installed.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by CeejRab on 2014-02-05
Heres the output of the commands you posted:

```
ceejrab@ceejdesktop:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
    Subsystem: Foxconn International, Inc. Device [105b:0c54]
    Kernel modules: sisfb
ceejrab@ceejdesktop:~$ sudo lshw -C display
[sudo] password for ceejrab: 
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:e0000000-e7ffffff memory:ec000000-ec01ffff ioport:d000(size=128)


```

im in a brainlock since its been a few months, but how do i set the no mode set when i first boot from the usb? when it shows the keyboard and stick man, what do i do again? lol sorry im brainlocked its been a while!

(this is the output from terminal in the full install of xubuntu 12 that im running. i still havent been able to try or install lubuntu or ubuntu yet.)

---

### Post by Bashing-om on 2014-02-05
CeejRab; Well, well ;

sis graphics are problematic on linux. From what I have seen can be a real pain to get to working, but it can be done !
See:
[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)
[http://ubuntuforums.org/showthread.php?t=2172375&page=8](http://ubuntuforums.org/showthread.php?t=2172375&page=8)

For some hints on what might be done.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by CeejRab on 2014-02-07
Update:

Im passing the systemax on to a friend with Windows xp on it for them to use, and in turn they're giving me a broken hp pavilion that I'm going to fix and attempt to run Ubuntu and windows xp from. I will likely need help with that system, so I'll keep the thread open until then! 

Thanks for all the help and replies, especially To bashing-om for the very in depth assistance. You guys are great, as always!

all the best,

---

### Post by Bashing-om on 2014-02-07
CeejRab; Hey ;

It is little enough that I can do to help.

As this situation is now concluded, please mark this thread solved. This Aids others seeking a similar solution and helps keep the forum tidy. We have enough to do without hashing over a done deal. 

When you are ready to work the HP Pavilion, open a new thread with an appropriate titile .

and away we will go
[INDENT][INDENT]once more 
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-02-07
> **Bashing-om said:**
> 

When you are ready to work the HP Pavilion, open a new thread with an appropriate titile .


^^^
This. Thanks. Don't continue discussion of the HP here. The thread title and the rest of the thread have nothing to do with it. You will decrease your chances of getting help burying yourself 15+ deep in a thread with an unrelated title and cause confusion.

Post a link to a new thread here when you start one if you wish. 

Good luck.

---

### Post by CeejRab on 2014-02-07
just realized that myself, thread closed and thanks again,

all the best,

---

