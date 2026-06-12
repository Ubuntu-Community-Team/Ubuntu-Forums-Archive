---
title: "Why won't GRUB/BURG load when external drive is connected?"
date: 2013-11-22
forum: Hardware
---

### Post by donotspamme532 on 2013-11-22
Hi everyone,

I'm not sure if this actually belongs here in the Hardware section, or if it would be more appropriate in the general help section or something.  Sorry if this is in the wrong place.  But this relates to a piece of hardware, even though I suspect it is mostly a GRUB/BURG issue.  I've searched the forums and the internet but search results keep turning up issues with booting from a usb device as opposed to booting from an internal drive while a usb drive is attached.

Here's the situation.  I have Ubuntu 12.04 LTS installed.  I have previously had GRUB for my bootloader and working perfectly well (with the exception of the external drive issue).  Currently I have BURG installed instead of GRUB, but it uses mostly the same GRUB code as I understand it, and when it first loads up it displays a message "GRUB is loading" just like GRUB does.  BURG is also working perfectly well, again with the exception of the external drive issue.  In addition to all of that I have an external USB hard drive.  It is a Seagate FreeAgent GoFlex 1.5TB USB 3.0 drive.  I have not formatted it, so it has the Seagate drive utilities programs on it.  Now then, when I boot my computer with the drive connected, neither GRUB nor BURG will load.  I get the "GRUB is loading" message, and then nothing but a blank screen.  The boot menu itself will not load.  If I disconnect the drive while at the blank screen, GRUB/BURG will still not load, and I have to do a hard shutdown.  If I boot the system when the external drive is *not* connected, then both GRUB and BURG work perfectly normally.  This behaves the same whether I have the drive connected to a USB 3.0 port or to a USB 2.0 port.

I'd really like to be able to boot my system without having to remember disconnect my external drive each time.  I'm running dual-boot with Windows 7, and I still use Windows fairly frequently, so I do restarts all the time and disconnecting the external drive each time is tedious and annoying.  Could someone please explain why GRUB and BURG have such an issue with external drives?  I remember having the same problem with a previous version of Ubuntu on another system (version 10.10 it might have been), and with a different external hard drive (a USB 2.0 drive).  I'd appreciate some help, or even just some more information to educate me as to why this is happening.

Thanks,
Drake

---

### Post by oldfred on 2013-11-22
All BIOS based systems require BIOS to enumerate drives and report those to the operating system for use.

Do you have internal hard drive set as first in boot order in BIOS? If it tries to boot from external it should normally fail and then boot internal, but perhaps something about your external is interfering?
How does BIOS show external?

Not sure if burg adds any complexity to the issue?

---

### Post by Bashing-om on 2013-11-22
donotspamme532; Hi 

Adding to oldfred's explanation;
> 
Here's an abbreviated version of what happens when you turn the power on after the machine has been shut down for a while:

First, code in the BIOS chip on the motherboard gets loaded into memory automatically and begins running. Next, the Power-On Self Test (POST) code checks all of the hardware to make certain it's working. In the process it clears all of the RAM space except the very small part it's using to run the POST.

When the POST completes, the BIOS code then begins loading the operating system code into memory. This becomes a "chicken-or-egg" situation, since loading the code requires code to already be there and the BIOS chip isn't large enough to hold all of the necessary code. The solution, in most Linux distributions, is to create a pseudo-disk in RAM, and load it with an abbreviated copy of the system that has all the things needed to load the full system, but nothing else (such as a normal user interface or keyboard drivers). That abbreviated copy is the "initrd.img" file, the INITial RamDisk IMaGe. Once it's loaded, control goes over to it, and it begins loading the actual full system from the "vmlinuz" file. While all this is going on, you see only the splash screen (but you can edit GRUB's actions to see play-by-play reports of it all, if you want to).

When the full system is all loaded, control goes to the "init" process, which sets up the console and virtual terminals, loads the window manager and display code, and lets you log in. The init process continues to run in the background until you shut down the machine, allowing the system to do its work more or less invisibly.

You can view the log of all this by firing up a text editor and looking at /var/log/syslog. This file records each significant event -- and gets huge in a hurry.

I hope this helps answer your question, but it will probably prompt many more. Welcome to this wild and wonderful world!


All boils down to what you have set in bios as the boot device as bios is looking there for the boot code.

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by donotspamme532 on 2013-11-22
Thank you both for your responses, and the information you gave.

I just double-checked my BIOS boot order settings.  System is set to boot from primary internal hard drive first (hd0), then will try CD/DVD drive if it fails to find a good boot sector, then it will check the external drive last.  No other devices listed in the BIOS boot order, not even my secondary internal drive (hd1) that linux is installed on.

Also, since I do successfully get through POST and get to the point where GRUB or BURG tries to load (and gives me the message stating that it is loading), and since both load fine when the external drive is not connected, I beleive it is most likely that the drive is interfering with the bootloader during the bootloader's own startup process.  Is it possible that the presence of the external drive is changing the drive mapping, so the bootloader is looking in the wrong place for it's configuration information?  I think that is unlikely.  Since both GRUB2 and BURG use UUID for the root drive, I don't see how connecting the external drive would mess that up.  And since the bootloader loads the boot menu correctly when the external drive is not connected, I have to assume that the UUID that is being used is the correct one.

Nevertheless, I checked where ubuntu has the external drive mapped, and it is located correctly at hd2 and mapped to /dev/sdc.

I went digging through some of the files and did find that /boot/burg/device.map does *not* include an entry for the external drive.  /boot/grub has no device.map file at all (this may be normal, I don't know enough about either GRUB or BURG), and the grub.cfg file has no entry for the external drive.  I'd be very surprised, however, if that is causing any sort of a problem, but again, I don't that much about GRUB or BURG.

I have another hard drive, an internal sata from my old laptop that has been completely formatted.  I may throw that in an external enclosure and connect it up and see if BURG has a problem with it, or if it will load the boot menu without trouble.  If it can load the boot menu without trouble when a blank external drive is connected via USB, then that might suggest it is something on the Seagate specifically that is causing a problem, though I can't think of why or how that would be.

Any other help, suggestions, or information?

Thanks,
Drake

---

### Post by oldfred on 2013-11-22
Grub stopped using device map, but if found will use it. I think it just dynamically maps drives.

So if Ubuntu drive is not in boot order you have grub installed to a different drive and it has to call the second drive?
Some BIOS promote an external drive ahead of internal drives, but grub is supposed to be using UUIDs not devices to boot like /dev/sda unless you modified it or Burg still uses that?
Boot drive from BIOS is always hd0 in grub, then if mapping other drives that can change if using device not UUID.

May be best to see details.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Bashing-om on 2013-11-22
et al: 
Correct me please if my comprehension is in error, but
Does not bios booting go thus
let's say one has this set up for the booting order
1st CD
2nd - 1st Hard Drive
3 External devices

now booting and bios goes by what has been set for the boot order;
looks 1st for a CD. No CD to boot from it goes looking at the 1st hard drive
If then no boot code is found it goes to an external device.

Now if in fact the boot code is found on the 1st hard drive than the external device is never polled.

So, in essence, if I want to boot from the external device, that device must be placed as the 1st boot order choice .

@ donotspamme532 ; Have you set that external hard drive to boot as 1st choice and see what results ?

[INDENT][INDENT]sometimes I wonder, other times I just do not know
[/INDENT][/INDENT]

---

### Post by donotspamme532 on 2013-11-22
> **Bashing-om said:**
> @ donotspamme532 ; Have you set that external hard drive to boot as 1st choice and see what results ?

I have not tried that.  In fact the thought never even occurred to me.


@oldfred:
GRUB and BURG are both installed to sda, but they point back to sdb1 to actually load.  My sda drive is all windows and windows recovery; I have made no changes to its partitions (other than software installations) and they are the HP factory defaults.

You can look at my boot-info output at [http://paste.ubuntu.com/6461446/](http://paste.ubuntu.com/6461446/)

I haven't tried the other drive yet, so I will do that tonight, as well as trying to set my Seagate to boot first to see how that affects things.

I guess we'll go from there :)

Thanks,
Drake

---

### Post by donotspamme532 on 2013-11-22
OK, some new wierdness...  I tried setting boot order to boot from external drive first only to find that my BIOS does not allow me to change the boot order.  I can choose to force it to boot from a different device in the list of devices, but it will not let me change the order it goes through under normal boot.  I told it to boot from the external drive anyway and instead of the bootloader not loading the boot menu I got a grub error:
```
grub error: no such device: 132aa784-645c-4af0-8231-09bf3effd08f
```
I then get a grub-repair prompt.  As you can see from by boot-info output, there is no place where such a uuid is even listed, so I have no idea why it would try to use it.

I also hooked up my other hard drive in an external usb enclosure and connected it in place of the Seagate.  As I mentioned before, this other drive is completely empty.  I tried to boot with the blank drive attached and also failed to get a boot menu.  Again, I received the message GRUB Loading, then just a blank screen.

And one other thing (this may be unrelated).  I can now no longer boot to my normal linux boot image.  It starts the boot process, the plymouth splash screen comes up and progresses, then I get a blank screen and nothing.  I've tried changing to command line mode in case it was only a graphical problem, but that also gets no response from the system.  I can boot to my recovery image, and from the command line I can successfully use both gdm and kdm to log in to a full system with grafical UI (I haven't tried lightdm, but I suspect it also works).  The only thing I have changed today is to install some security updates and to change my KDM and KSplash themes.  I thought that maybe the themes had somehow messed up KDM, so I logged in with GDM and changed the themes back to KDE defaults, but still the system will not boot to the normal mode.  Should I post a new thread for that issue, or do you think it might be related to current problem?

---

### Post by Bashing-om on 2013-11-22
donotspamme532; Hey,

Set in bios (however you can) to boot the drive that has your primary operating system installed onto ;;;;
Now on my box I have 4 operating systems installed on 3 hard drives.
My primary operating system happens to be my 1st hard drive (sda) and I have grub installed to the MBR of each drive.
OK, in bios I have set as my 1st boot option to boot from CD ( I boot up CDs a lot, and leave it 1st rather than changing my bios boot preference)
my 2nd boot option is to boot from 1st hard drive.

I boot my system, no CD in place, bios seeing no boot code, boots the hard drive, On my primary operating system residing on sda is my primary grub from which I can boot any of the other operating systems. In addition, if something happens to my primary operating system I can change my boot order in bios to boot a different hard drive for any of the other operating systems.

You are running Windows and we will have to look at partitioning to see what Window's uses for booting as we do not want to install grub onto that operating system (Windows)  and wiping out the boot code by setting up grub to that MBR .

:::
So in essence install grub to the MBR of each hard drive -but not Windows' yet -
Set in bios to boot the hard drive of your primary operating system and then, to pick up and add all the operating systems to this primary grub; run the terminal command:
```

sudo update-grub

```
The tool "os-prober" within grub-update will pick up every operating system it can see and add them to the grub boot menu. This normally includes Windows ! All that said IF Windows is UEFI , all bets are off .. I have no experience and little knowledge of UEFI booting requirements.

With your last posting I have doubts that grub is installed on the external hard disk in question or maybe that the boot order is set in bios to boot the external hard drive. - and there is the possibility that your bios does not support booting from USB devices (???).

In respect to your last that you can not boot any OS .. All I can suggest is to try various setting for the boot priority in bios and see what happens. You need to boot your primary operating system at the point where you update grub with all the other operating systems.

FYI; Changing the boot order in bios would not have effected the boot code installed onto the hard disk(s). I fully expect the boot code to be fully intact, just a matter of directing bios to look at the correct place.


Am I making any sense to you ?


[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by donotspamme532 on 2013-11-22
OK sorry, but you aren't making sense to me.  I do appreciate you trying to help though.

I'm not sure you're understanding the way things are working for me at the moment.  So let's walk through this in a step-by-step chronological sort of way.  Oh, before that, I should note, I fixed the blank screen after plymouth issue, and can now boot to normal linux as well as to recovery linux or to windows.  So now the chronological thing...

1.  I press my power button.

2.  BIOS loads.  At this point I can enter the BIOS configuration system, but the BIOS that exists on the system does not allow me to change the default boot order, it will only allow me to force the system to try to boot to a specific device first on a one-time-only basis.  Current boot order is primary hard drive (which has windows installed), then CD/DVD, then external drive (if it's connected).

3.  POST runs through, completes without issues, and loads the bootloarder.

4.  GRUB/BURG starts to load and I get a message stating "GRUB Loading".

5.  If my external hard drive is connected (or my other external drive for that matter, either one), then I get a blank screen.  That is to say, GRUB/BURG does not appear to finish loading, and no boot menu is displayed.  On the other hand, if I do *not* have an external drive connected, then GRUB/BURG finishes loading successfully and displays the boot menu (right now that means a themed graphical boot menu in BURG).

6.  If the boot menu has loaded (because I did not have an external drive connected), then I can choose which OS I want to boot.  At this time all of them seem to be working correctly since I fixed the plymouth issue.


Now as to my previous post, I used the BIOS system to try and force the system to boot from the external drive even though there isn't an MBR installed on that drive.  That is when I got the grub error about no such device.  But what confuses me about that error is the UUID of the device given in the error message.  I don't know where grub got that device id from, or why it was trying to use it at all.  But that really isn't important to the current problem, it was just something I tried that didn't work.  And as I've said, I fixed the plymouth issue and can now boot to linux normally again (if I don't have an external drive connected at boot time).


Now as far as I know my BIOS is perfectly capable of booting from USB devices, but I've never tried.  I suppose I could install GRUB and BURG to the external drive (no changes to the internal drives that already have them installed), and see if that makes a difference.  I think I'll try that next.  And as for UEFI, there are no problems with that because I'm not using it... my system is not using UEFI, windows is not using UEFI, and I'm not sure my system is even capable of it.


Thanks,
Drake

---

### Post by oldfred on 2013-11-22
You currently have grub installed to the MBR of all three drives. Not sure if each install works. Boot-Repair is offering to reinstall current grub to every drive. I would not do that as I prefer to have a Windows boot loader on sda and grub on sdb with BIOS set to boot from sdb.
You also do not have a boot flag on any partition on sdb. Grub does not use boot flag, but some BIOS do not work correctly without a boot flag on a primary partition. Use gparted and add a boot flag to sdb1. Click on partition and right click manage flags.

If you now can boot into Ubuntu you can reinstall grub to sdb from there.
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Confirm that you can directly boot from sdb (with or without external) and if so set BIOS to boot sdb first.
Then install a Windows boot loader to sda. That way each drive is independent of the other and should boot without the other. You can use Boot-Repair, uncheck auto and check update MBR and in advanced choose Windows and sda as location.

It may just be boot flag, but I have seen others have install issues with the go-flex drives. They seem to have some proprietary configuration that may contribute to the issue.

---

### Post by donotspamme532 on 2013-11-23
OK, so I did some more digging into my hardware as well as GRUB and BURG installations, and my BIOS.

It turns out that I *CAN* change the default boot order in the BIOS, as well as being able to override that boot order as needed.  However, my secondary internal drive does *NOT* show up in either list.  I changed the drive flags to show that the secondary drive is a bootable drive, but this had no affect on the BIOS.  The BIOS simply does not accept that the secondary drive is a bootable device.  I double-checked in both linux and windows and both OSes see the drive as being a bootable/active device.  It seems that the BIOS code is not designed to accept a second internal drive as a bootable device.  Because of this, I cannot set sdb as the first boot drive.  The BIOS simply will not allow it.

I thought maybe the secondary drive might be set as a slave drive or something, so I checked on that.  It is a master drive, not a slave drive.  This apparently must be a limitation of my BIOS (which I've never liked on this system, but like even less now).

Despite those issues, I installed GRUB and BURG both to sdb and sdc.  Installations returned no errors.  I tried to boot from the external drive now that GRUB and BURG are installed to it, but again the boot menu will not load and display.  I did, however, get the GRUB Loading message, and no grub error this time.

So the issue of not being able to get the GRUB or BURG boot menu to load and display while the external hard drive is connected MUST be an issue with GRUB/BURG itself.  Since this happens even with a blank drive, not just the Seagate FreeAgent GoFlex, then it cannot be an issue of something on the drive itself, but must be an issue with the way GRUB/BURG recognizes and handles (of fails to) an external USB drive.  Since it should be possible to boot from a USB device, I don't understand why GRUB and BURG are having such a problem with this.

I think what I will try next is to install GRUB and BURG to a USB flash drive and see if it can work with that or not.

Any other help and suggestions would be appreciated.

Thanks,
Drake

---

### Post by oldfred on 2013-11-23
Are these internal drives IDE drives with jumpers?
And is one master and one slave or do you have the newer 80 wire cable and have to have jumpers set for cable select?
 I once tried using a never used old cable that came with my CD/DVD player. But it did not work since it was just a 40 conductor cable. I hated jumpers so much that when I built new system and SATA drives were only a little more I immediately chose SATA drives.

 with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by donotspamme532 on 2013-11-25
This is a newer notebook computer.  The drives are SATA, but I don't know how master or slave is handled for SATA drives (or if the serial nature of them means that there is no longer a need for master/slave distinctions).  I haven't had to mess with master vs. slave drive settings since back when I was running IDE with jumpers (I hated them too), and that was at least 10 years ago.  There are definitely no jumpers, and I don't know if there is another way to set an SATA drive as slave other than perhaps drive flags, but if there is a hardware method, such as through the cables, then it is still a possibility that the secondary drive is made a slave through the hardware connection.  I really couldn't say on that score, I simply don't know enough about it.

But I really don't see that as being relevant to my issue.  While the BIOS does not recognize the secondary drive as a bootable device, GRUB and BURG *do* recognize it as having all of the necessary boot files installed, as well as having a bootable OS installed.  So having BURG installed to the sda drive, and set up to boot from the sdb drive, works perfectly fine *if* my external drive is not connected.  It is only when the external drive is connected that I have any problem at all.  This really is an issue of convenience and annoyance.  I dislike having to remember to disconnect my external drive every time I reboot to switch which OS I'm using.  It's just irritating and I'd like to get it working.

I have not yet tried installing GRUB or BURG to a USB flash drive, but I still plan to try that and see what happens, but I may not get around to it for another day or two.

Thanks for all the help and information so far.  I hope you can still help further :)

Drake

---

### Post by oldfred on 2013-11-25
SATA drives have no settings on drive and everything is controlled in BIOS.

Some BIOS settings may make a difference. New systems should use AHCI not IDE nor RAID. But Windows may need drivers for AHCI if not already installed. If no AHCI then large or LBA is preferred.

---

### Post by donotspamme532 on 2013-11-26
OK, so I did some more research into my BIOS.  It actually *does* have many more advanced settings available, but they are not available by default.  Instead, you have to use a keypress during BIOS Setup Utility Load, but before it actually loads, to tell the utility to display advanced settings options.

By accessing the advanced settings options of my BIOS in that way I was able to determine that the BIOS is using AHCI for the hard drives.  I completely forgot to check if it will allow me to set the second internal drive as a bootable drive if using the advanced settings, so I'll check on that.

---

### Post by donotspamme532 on 2013-11-27
OK, more research into my BIOS, as well as USB flash drive...

The advanced settings in my BIOS do *not* allow me to set the the secondary drive as bootable, at least not while the drives are set up for AHCI.  I don't know if I could make it work by making the drives no longer AHCI, but I don't want to try that.

I connected a USB flash drive, installed GRUB to it, and disconnected my external hard drive.  I then shut down the system and tried to boot the system back up with the flash drive connected, but no external hard drive.  Again I received the "GRUB loading." message, but then only a blank screen, no boot menu.  So at this point GRUB and BURG both have failed to load a boot menu when my FreeAgent GoFlex is connected, when a blank formatted external drive is connected, and when a 256MB USB flash drive is connected.  So it seems to me that GRUB and BURG are having problems with the fact that a removable storage device (*any* removable storage device) is connected at the time of bootloader start.

I think this has to be an issue with the GRUB/BURG configuration, but I don't see what could be wrong.

I may end up having to just connect my external drive to my wireless router, but I would be losing some data throughput.  I'd rather get GRUB or BURG working even if the external drive is connected.

Any other suggestions that I can try out?

Thanks,
Drake

---

### Post by oldfred on 2013-11-27
Some old Dells had BIOS that would only boot first drive but not second drive. 

Most new BIOS let you select any drive or even device as bootable. 

But my 6 year old BIOS has many USB boot options and I could not get any of those to work. And flash drive booted on my laptop, so I knew it was ok. 
Then I used one time boot key and under hard drive saw USB flash drive. Even though USB, none of the USB options not even USB-hard drive worked, but it was just another hard drive in list of drives to boot that worked.

---

### Post by bantuvez on 2013-11-28
> **donotspamme532]Is it possible that the presence of the external drive is changing the  drive mapping, so the bootloader is looking in the wrong place for it's  configuration information?[/QUOTE]

Yes. Look [http://moi.vonos.net/linux/Booting_Linux_on_x86_with_Grub2](http://moi.vonos.net/linux/Booting_Linux_on_x86_with_Grub2)

"Before writing to disk, core.img is modified to insert hard-wired values for the disk# and partition# of the filesystem on which /boot/grub exists, ie which it should mount using the linked-in filesystem driver. Hard-wiring these values can be bad if storage devices are added to, or removed from, the system. This hard-wiring can be avoided by linking in the &#8220 said:**
> Nevertheless, I checked where ubuntu has the external drive mapped, and it is located correctly at hd2 and mapped to /dev/sdc.


That's unimportant.It is correct when you boot without the external drive plugged-in. But if you boot with the eternal drive, your drive order is messed up. (Your BIOS screws things up by putting your external ahead of yout 2nd internal.) Read this [https://www.gnu.org/software/grub/manual/html_node/Device-map.html](https://www.gnu.org/software/grub/manual/html_node/Device-map.html)

"The map between BIOS drives and OS devices cannot always be guessed correctly: for example, GRUB will get the order wrong if you exchange the boot sequence between IDE and SCSI in your BIOS."

[QUOTE=donotspamme532]told it to boot from the external drive anyway and instead of the bootloader not loading the boot menu I got a grub error:
     Code:

     grub error: no such device: 132aa784-645c-4af0-8231-09bf3effd08f 
I then get a grub-repair prompt.  As you can see from by boot-info  output, there is no place where such a uuid is even listed, so I have  no idea why it would try to use it.[/QUOTE]

According to your pastebin your external drive did have grub installed into its bootloader:
```
Grub2 (v1.99) is installed in the MBR of /dev/sdc...
```

Did you install it there? Why? The core.img installed into your external HDD must have had an embedded config file with the alien UUID.

So what can you do?

Best solution would be if you could change your BIOS to boot from second drive /dev/sdb. I've never seen a bios which didn't let you do such thing. What bios are you using? What notebook?

2nd best solution is to simply change your internal HDDs in your notebook. 

If you really can't change your BIOS bootorder to boot from your second drive and you can't change your HDDs in your notebook, then you should embed a config file to core.img. See here: [https://www.gnu.org/software/grub/manual/html_node/Embedded-configuration.html](https://www.gnu.org/software/grub/manual/html_node/Embedded-configuration.html) Or maybe this can be solved with a proper device map file? (I don't know)

---

### Post by donotspamme532 on 2013-11-29
@bantuvez:

OK, that's a lot of information that you linked to (which I appreciate greatly), and it is going to take me some time to read through all of it.  But so far, it seems that device mapping could be causing the issue I'm experiencing.  So let's take that as a working theory for present and move forward from there.

There is then the question of how badly messed up the device mapping gets when the external drive is connected.  You suggested that the external drive might be mapped between the primary internal drive and the secondary internal drive, thus making it so that GRUB2 and BURG cannot successfully find /boot/grub and /boot/burg in order to generate and display the boot menu.  That makes sense, and would certainly explain the behavior that I'm seeing.  Is it safe to assume that device mapping for the primary internal drive is *not* affected by this, and make that assumption based on the fact that the initial MBR boot code for GRUB2/BURG appears to load correctly (since I get the "Grub loading." message)?  That also would make sense to me based on the behavior that I'm seeing, but I want to know if I've missed something that would suggest some other possible issue.

Now the information for the device map file is interesting, but while it suggests that I could use the device map file to correctly tell GRUB/BURG where to find or map particular devices, this file is itself located in the /boot/burg directory (or the /boot/grub directory if I were to create the device map file for GRUB2).  So if GRUB2/BURG are failing to even find the /boot directory because it is looking for it on the wrong device, then how would the device map affect this in any way?  Or is the device map file information used by grub-install when generating the core.img?  The page you linked to said that grub-setup uses the file (if present), but it doesn't say how it uses the file.  I guess I'd just like to confirm that the device map file could potentially be used to alter the core.img in such a way that it might make using an embedded config file unnecessary.  But if that is going to be a possibility, then I will need to know how the BIOS is mapping the drives in order to set up the correct device map file.  Is there a way I can tell what device order the BIOS is using when it doesn't even show the secondary internal drive drive?  Or would I have to use some trial and error with the device map file to try and get the right setup?  I'll look through the advanced options in the BIOS setup again to see if there is an indication in there somewhere as to the actual device mapping that the BIOS is using.

Now then, as far as GRUB2 being isntalled to the MBR of /dev/sdc...  I looked more closely at my pastebin and I'm wondering why GRUB 1.97-1.98 is installed to sda and sdb, but 1.99 installed to sdc.  As for it being installed to sdc at that point, that was probably done by boot-repair.  The first thing I tried when the boot menu didn't load was to boot to LiveCD and install and run boot-repair, and I probably told it to install grub to all drives.  It was after that failed that I discovered it was the external hard drive that was preventing the boot menu from loading.  I did, however, then install both grub and burg manually to the external drive, and then tried to boot from the external drive instead of the internal drive.  At that point, I no longer received the grub error with the alien UUID, I simply had the same results as if I had booted from the primary internal drive.  But I don't see why the core.img would have had another UUID embeded.  I certainly haven't done anything to try and do an embedded configuration.

As to your suggestions for possible solutions, the first option is out.  As I noted previously, the BIOS simply will *not* allow me to boot from the second internal drive.  The drive doesn't show up anywhere in any of the boot device or boot order configurations even when the advanced BIOS settings are made available in the BIOS Setup Utility.  The BIOS is InSyde version F.1c using InSydeH2O Setup Utility Rev. 3.5 as the BIOS setup utility.  This is on an HP Pavilion dv7 that is currently just over a year old.  Now, I could certainly swap the internal drives, as you suggested for the second possible course.  I'm a little hesitant about doing that though, as I have no idea how it would affect my windows installation or its drive mapping, and since I use the third partition on the secondary internal drive for windows automatic data backups, I don't like the idea of the drive mapping being changed for windows.  I could use windows Computer Management utility to remap the drive letters if need be, but I'm not thrilled about that prospect.  I will probably try this anyway though, as I can always swap them back again if it presents a problem.  If swapping the drives does not work, or if it presents its own problems, then I'll study up more on making an embedded config file for the core.img and may try that method.  However, if the problem is, in fact, that GRUB2 and BURG are failing to find /boot/grub and /boot/burg (respectively) because of messed up device mapping, then could I copy /boot/grub and /boot/burg to my external hard drive and have it work?  Wouldn't GRUB2 and BURG be able to find their respective *.cfg files to generate the boot menu using UUIDs?  Or would the NTFS file system of the external drive cause issues for that?

Anyway, on another issue, I was upgrading from 12.04 LTS to try and get upgraded all the way to 13.10 and somehow the upgrade step from 12.10 to 13.04 screwed up and I can't get the system to boot to linux right now.  I haven't tried the recovery image, which I'll try next, but I've downloaded the 13.10 iso and burned it to disc and may in the end just format my linux partition and install 13.10.  I don't in the least expect that would solve the issue with the boot menu not loading for GRUB2 or BURG while the external drive is connected, but it does mean that I may not be able to test everything for a bit, as it is a higher priority to me to get a working linux system before worrying about whether or not I have to disconnect my external drive before booting.

Thanks very much for all of the information, bantuvez, I really appreciate it.

Drake

---

### Post by oldfred on 2013-11-29
Are both internal drives SATA drives?
And do you have them in the first two ports on motherboard.

I managed to skip a port when I added drives. Now when I add a flash drive it is sde. But if I reboot, the flash drive is sdb and all my other drives change device letters. But my system shows all drives in BIOS including flash drive and I can & do boot any of them. I default boot is sdd, but it still boots when I have a flash drive plugged in and UUIDs keep everything in order.

---

### Post by donotspamme532 on 2013-11-30
Both drives are SATA.  Both drives are exactly the same make, model, and capacity.  And the mainboard only has the two ports for hard drives.  Remember, this is a notebook/laptop we're talking about.  There's only so much room in there for hardware :)

---

### Post by bantuvez on 2013-11-30
> There is then the question of how badly messed up the device mapping gets when the external drive is connected. ... Is it safe to assume that device mapping for the primary internal  drive is *not* affected by this, and make that assumption based on the  fact that the initial MBR boot code for GRUB2/BURG appears to load  correctly (since I get the "Grub loading." message)?

I think that if your boot order in the bios is:
1. Hard drive
2. External drive

,then there is no way that your external drive will be mapped ahead of your 1st internal drive. If you force your bios to boot from external or put your external into first place in the bootorder, then mapping will be affected, I think. Maybe you could try booting a live USB with different boot orders and see how the drive orderings change (if they do change).

> So if GRUB2/BURG are failing to even find the /boot directory because it  is looking for it on the wrong device, then how would the device map  affect this in any way? Or is the device map file information used by grub-install when generating the core.img? 

I think you are right. I don't know whether the device.map file is used up when generating the core.img, but one of the links which I gave to you suggests that it won't help in your case. 

> This is on an HP Pavilion dv7 that is currently just over a year old

I googled on that machine and it looks like HP machines does have some interesting "problems". There are some reports which confirm that there is no way to change the boot order to the second internal HDD. Another thread reports that even if you swap the drives, the BIOS will boot from the original drive (which was in the 1st bay) You have to completely remove the original drive from the system to make it boot from a different internal drive ([ http://www.eightforums.com/general-support/21033-dual-hard-drive-setup.html]("http://www.eightforums.com/general-support/21033-dual-hard-drive-setup.html") ) Another thread suggested something similar but reverse , that if you remove the first internal drive then the BIOS will boot from the 2nd, and even if you place back the 1st drive it will keep booting from the second. You may try this. (Someone even said that the second bay is only an USB emulating SATA and there is no way to boot from that, but i think that can't be true.) 

> However, if the problem is, in fact, that GRUB2 and BURG are failing  to find /boot/grub and /boot/burg (respectively) because of messed up  device mapping, then could I copy /boot/grub and /boot/burg to my  external hard drive and have it work?  Wouldn't GRUB2 and BURG be able  to find their respective *.cfg files to generate the boot menu using  UUIDs?  Or would the NTFS file system of the external drive cause issues  for that?

As one of the documents say that "The executed core.img code now initialises all the modules that are built into it (linked into core.img); one of these modules will be a filesystem driver capable of reading the filesystem on which directory /boot/grub lives." I think that it will be problematic to "trick" the core.img by  placing /boot/grub to your external drive with NTFS filesystem, because most likely the core.img will only have the filesystem driver for ext4 (or the fs on which you generated the core.img), because when it was generated it was told that the /boot/grub will be on an ext4. But in my opinion if you put a little ext4 partition to your external drive (BEFORE the NTFS parititon, to make it the first parition on the drive) just to hold the /boot/grub directory, then it could work.

 > Anyway, on another issue, I was upgrading from 12.04 LTS to try and get  upgraded all the way to 13.10 and somehow the upgrade step from 12.10 to  13.04 screwed up and I can't get the system to boot to linux right now.

Unfortunately upgrades rarely work (at least for me). Good luck with your system repairing.

---

