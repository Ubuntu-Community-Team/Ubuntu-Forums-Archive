---
title: "Ubuntu on HP ENVY dv6t-7200"
date: 2013-02-27
forum: Hardware
---

### Post by demercel on 2013-02-27
I have intention to buy new laptop. I am old ubuntu user (and even older linux user) and I am toying with the idea of buying HP ENVY dv6t-7200
15.6" 1080p Quad HYBRID Series, 3rd Gen Intel Core i7 Ivy Bridge GDDR5 Nvidia GeForce GT 650M. Has someone tried to install ubuntu on such beast? 
(I have searched the forum for this laptop but nothing came out)
It comes with Windows 8. 
Will I have any problems with UEFI and stuff?
Will the nvidia card work?
Will the wireless card work?
If you have some experience, advises, comments, please reply.

---

### Post by Robbobden on 2013-03-09
My PC arrived from China yesterday.  I spent a couple hours with it, first making a backup DVD set (6 DVDs), then activating Windows 8 and getting MS updates to it.   BTW, this is the HP Envy DV6t-7300 Quad Edition.  I think it's fairly new.  Maybe just marketed this year.   The attached .png shows how it's optioned.   In BIOS, it shows Legacy Support (disabled), and Secure Boot (enabled).   BIOS is InsydeH20 F.22.  It's partitioned thus:  400MB Recovery, 260MB EFI System Partition, 672GB NTFS (C:), 26GB NTFS Recovery OEM Partition.  That's Disk 0.   There's a Disk 1 of 8GB which I haven't got a clue where it is or what it's used for.  And a CD-ROM 0.   The 32GBSSD doesn't show up anywhere in any screen but it's used as a start-up cache.   There's a BIOS entry where you can disable it.   So, today, I tried running two Ubuntu LiveCD/DVDs.   I have the 12.04.2 64-bit iso (on CD) and 12.10 64-bit iso (on DVD).   They're both supposed to be UEFI compliant or capable.   Neither will run.  Both present a Grub menu where you can select try, install or check disc for defects.   The 12.10 has one additional Grub entry.   It's OEM install for manufacturers.  What's that ?   When I select try Ubuntu on 12.04.2, the error: couldn't read file, you need to load the kernel first appears.   When I select try Ubuntu on 12.10, error: failure reading sector 0x5b500 comes up.   When I enable Legacy Support in BIOS (which automatically disables Secure Boot), both Live CD/DVDs boot up ok.   Wireless on this PC works right away on both.   Zipped around the Internet like you wouldn't think you were using a Live CD/DVD !    Beats Audio seems ok; I briefly watched and listened to a YouTube video.  I haven't checked anything else yet.   If I didn't need a Windows OS for a couple things, I'd wipe the HDD, change the BIOS setting for Legacy Support and load up Ubuntu.   I might try to get Ubuntu on a USB and see how things work that way first.   If anyone knows a way to run an Ubuntu LiveCD without having to tweak the BIOS, I'd appreciate a note here.   Oh, and I'm thinking maybe I could run Ubuntu within VirtualBox on Windows 8.  

RDL

---

### Post by Robbobden on 2013-03-11
I used this forum thread as a starting point:   [http://ubuntuforums.org/showthread.php?t=2041457](http://ubuntuforums.org/showthread.php?t=2041457)

No problems with the wireless after suspend.   The wireless button (F12) worked.  You can set up your router access and then just press this key to enable/disable wireless connection.  Beats audio is good without making any changes.  Keyboard backlighting works, as does ability to change screen brightness using the keys F2/F3.  Sound volume good using F9/F10.   The PC speakers are pretty wimpy but plugging into the earphone jack gives you excellent sound.  I don't know how to properly check the discrete NVIDIA 650M yet.   I'll google some more.   

I want to use Ubuntu as the default OS, so I'll need some form of boot menu, not how it works now using F9 at PC power up.   Comments welcome on how this might be done.   Thanks !

RDL

---

### Post by Robbobden on 2013-03-11
I think I'm going to solve all the problems by purchasing a full OEM version of Windows 7 Home from the local PC Land here, about $100.    I should be able to dual-boot or maybe run Windows 7 within VirtualBox installed on Ubuntu.   More to follow this evening.


RDL

---

### Post by GrouchyGaijin on 2013-03-11
Thanks for the play by play description - it is really interesting.

---

### Post by Robbobden on 2013-03-11
You're Welcome !   I just ran into a show-stopper though.   I'll talk about that after I do this.   I deleted all partitions using Parted Magic, then in terminal got rid of any GPT labels/data or whatever by running this command set:  I think that may have been the reason for the blivit mentioned in an above thread having to do with GPT.

parted /dev/sda
mklabel msdos
quit

Then booted up the Ubuntu 12.04.2 64-bit LTS.  Grub appeared and I selected Install.  Here's how the partitions are set up:

    - sda1 ext4   500MB   /boot
    - sda2 ext4   20GB     /root
    - sda3 ext4   50GB     /home
    - sda4 ext4   50GB     /data
    - sda5 ext4   8GB       /swap
    - sda6 fat32  50MB     /boot efi
    - unallocated 578.92GB
 
Yep, and this is a GPT table also.  I was never bothered by primary/logical partitions.  I didn't do anything special, it just happened like this.  I initially left the 50MB /boot efi partition out (I didn't know anything about it) whereupon Ubuntu told me I'd better not if I wanted a workable system.   So, I backed up and created one of those.   So, I appear to have a clean install of Ubuntu 12.04.2.   I bought that full OEM Windows 7 from PC Land which I wanted to run in VirtualBox from Ubuntu.   Guess not !

Here's the show stopper.   The wireless F12 button is inop.  The little amber light doesn't change to green when you press it.   The wireless icon drop-down shows wireless is disabled by hardware switch (no kidding !).  In terminal,   rfkill list all     shows:   hardware block: yes.   Now, this didn't happen when I had Windows 8 installed and Ubuntu was installed along side.   That F12 button worked perfectly.   All the other special keys like backlit keybd, screen brightness and sound work ok.  Must be instructions in EFI/GPT partition installed by Windows 8 (which aren't there now - I don't exactly know what I'm talking about here) for that switch.   Can't use this PC without a wireless interface.   Oh boy !   Ok, now I'm going to install Windows 7, then verify F12 works, then install Ubuntu.  Try a dual-boot.   And check wireless again.

RDL

---

### Post by Robbobden on 2013-03-11
About the wireless button (F12).  There's actually a driver set for this  PC available on the HP support center web site.  It's for  keyboard, mouse and wireless button.  So, no driver, no wireless  button.    More bad news.  HP drivers for this PC are for Windows 8.   When you hit the drop-down menu on the driver pages, there's no  selection for Windows 7.   Man, this is a nice ! PC, but there's no  flexibility here to do anything but use Windows 8.  I'm going to give  these Windows 8 drivers a shot on Windows 7 and see what happens.

RDL

---

### Post by Robbobden on 2013-03-12
Got all the Windows 8 drivers for this PC:  chipset, audio, graphics, network, cardreader, wireless button.   During the wireless button driver install a message popped up telling me:  The operating system (Windows 7 Home Premium) is not adequate for running HP wireless button driver.   That does it !   Going to put this beast back to factory default with the 6-DVD set.   Tomorrow I'll be better.   Right now I'm insane.

RDL

---

### Post by GrouchyGaijin on 2013-03-12
Oh man, after all that, it's a no go?
That truly does suck.
Just guessing here, but are you sure that you can't use an open source driver to get the wi-fi to work and then just control it though network settings as opposed to using the keyboard button?
I have a button on my keyboard too and I've never touched it.  I just leave the wi-fi turned on.

---

### Post by oldfred on 2013-03-12
This sounds like an UltraBook.

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

This was a Dell but the Intel SRT is the same for all vendors

  HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
      
 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)

           
 HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

Ultrabook uses RAID which causes issues.
      
 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.




If you want to dual boot, you have to install Ubuntu in UEFI mode.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

Many UltraBooks also have dual video and also need bumblebee.
      
 Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
[http://ubuntuforums.org/showthread.php?t=2121707&p=12540889#post12540889](http://ubuntuforums.org/showthread.php?t=2121707&p=12540889#post12540889)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

### Post by Robbobden on 2013-03-12
If you look at thread #10 above in this post, I had the dual boot working.  The wireless button, F12, was working also.   Just no proper boot menu.   Check this blog:   

[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)    

If I had maybe installed EasyBCD, I might have been able to boot Windows 8 and Ubuntu from there.     I didn't mention that I flashed the BIOS from F.22 to F.24.  That and the factory reload somehow screwed up the 8G partition on the 32G mSSD.   When I looked in disk management afterwards, I found the disk 1 8G partition was unallocated.  I get the feeling the wireless driver was in that partition as part of the Intel RST acceleration.  From that point on, the wireless didn't work any time I booted into Ubuntu or used the LiveCD/DVD.   

I have factory defaults loaded again but the 32G mSSD is still not formatted.   I don't know how to do this and HP tech support wouldn't even attempt to help me through it on a live keyboard chat.   They want the PC in for repair now (under warranty).   But I'm giving up because if I send it in for repair, I'm then outside the 21 day RMA window and won't be able to ever return it.   It's going to be hard to find a PC with all these great options for the same cash.   But, I'm going to go ahead and return it.

RDL

---

### Post by Robbobden on 2013-03-13
Yo, I'm back once again working on this project.   Rather than return the HP Envy dv6t-7300 to HP repair (for them to simply reformat the mSSD !!!!), I got them to take it back on an RMA.   Then I replaced it with the same PC (almost - a Pavilion vs an Envy) loaded with Windows 7 for a few dollars less too.   It's now being built in China and will ship around Mar 21st.   In the meantime, I want to understand the Intel SRT better.  Here's a brief YouTube video describing  how HP uses the Intel SRT SSD cache acceration.  [http://www.youtube.com/watch?v=7Djml3gktoc](http://www.youtube.com/watch?v=7Djml3gktoc)  And I'll be talking to the guy who wrote this article:  [http://www.linuxbsdos.com/2012/11/05...uefi-hardware/]("http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/")   He's supposedly working on another ariticle where he's trying to dual boot Ubuntu on a PC with Windows 8 pre-installed.   


RDL

---

### Post by Robbobden on 2013-03-21
Well, my new PC is enroute to me.  It's presently in Anchorage, Al.  I hope FEDEX flys a little closer to me here in Virginia before they put it on one of their trucks !   HP has a consumer support forum that I wish I had used to post my issues with the mSSD acceleration cache.   The support folks seem very knowledgeable and responsive.   Here:  [http://h30434.www3.hp.com/t5/Notebook-Hardware-e-g-Windows-8/bd-p/Hardware](http://h30434.www3.hp.com/t5/Notebook-Hardware-e-g-Windows-8/bd-p/Hardware)

---

### Post by oldfred on 2013-03-21
Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

I do not think computer brand makes much difference as it is an Intel Standard. The size of the SSD seems to be the main difference by brand.
      
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)


 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by Robbobden on 2013-03-25
It came today.  This is also a nice ! PC.  Looks identical to the Envy dv6t-7300.   The hardware complement is the same as was in the Envy I had a couple weeks ago except for the HDD speed.  7200 in the Envy, 5400 in this Pavilion.  But with Windows 7, the BIOS is set up differently.   BIOS ver.  F.22 also, but it comes from the factory with Legacy Support enabled.  Secure Boot is disabled and greyed out.   There's one entry where you can enable or disable Rapid Storage Technology.   There's an entry to clear secure boot keys and one to load factory default keys, both not applicable with Legacy Support enabled.   If you leave it in Legacy Support, you see separate entries for UEFI and Legacy boot order.   You're informed that when Legacy Support is enabled, UEFI and Legacy boot order are both available but that UEFI boot has higher priority.   If you disable Legacy Support, Legacy boot order is not available.   MBR not GPT.   All 4 primary partitions in use:

1. System 199MB  NTFS
2. C:  676.67GB NTFS
3. Recovery  21.66GB NTFS
4. HP Tools 108MB Fat32

I don't notice any difference in boot up times to the Desktop with RST enabled and disabled.   About 15 seconds to the login screen and maybe 3 more from there to the Desktop.   No complaints there.  With the Envy I had couple weeks ago, it would get up to the login screen in about 7 seconds.   I'd like to know how to measure the benefit of using RST some other way other than boot up times.   Maybe some bench mark test ?   In the RST menu, everything looks normal and acceleration is enabled.   It appears to be using most of the 32G for this as opposed to only 8G in the Envy.   Also, in the Envy, disk 1 with 8G showed up in Disk Management.   In this Pavilion, there is no such entry.   Unless you look at the RST GUI application, you wouldn't know there was SSD cache on this PC.

Ubuntu 12.04 LiveCD booted up ok without any problem, wireless button F12 worked as it should.   But, when I just take a look at how I might set up Ubuntu in installation mode, Ubuntu doesn't find the HDD.   It does see the 32G SSD and labels it as /dev/sdb.  Since I'm an Ubuntu user for 5 years, I don't plan to use Windows 7 for much.   Not having the SSD cache wouldn't bother me at all.   Maybe I could install Ubuntu in the SSD and put GRUB on the HDD MBR.      Someone recommended this link:  [http://forum.notebookreview.com/hp-pavilion-notebooks/676213-definitive-guide-clean-install-os-mssd-cache-equipped-laptop-dv6t-7000-dv7t-7000-envy17-3200-a.html](http://forum.notebookreview.com/hp-pavilion-notebooks/676213-definitive-guide-clean-install-os-mssd-cache-equipped-laptop-dv6t-7000-dv7t-7000-envy17-3200-a.html)   I'll check it out....thanks !

RDL

---

### Post by Robbobden on 2013-03-26
Nope !   No way to follow that procedure.   Seems like an ok guy but a step-by-step like that without explanations can fall apart quickly.   In my case, after I did step 3, disable acceleration, I then did not find the 'make available' option in the same tab.   The idea is to disassemble the raid 0 scheme I guess.   I'll keep looking ....   In the meantime, I installed Ubuntu 12.04 on a 16G USB drive.   Put GRUB in that drive, not the MBR.   Success, it booted up ok after I changed the Legacy boot order in BIOS !   Wireless button still working ok.   Wouldn't want to run Ubuntu like that, though.   Not too cool !

RDL

---

### Post by Robbobden on 2013-03-26
In BIOS, I disabled Rapid Storage Technology.  Then opened the Rapid Storage Technology GUI in Win7 and disabled acceleration.  Using Parted Magic on a LiveCD, I gave the 32G SSD a new standard partition table.   Back in Windows Disk Management, the 32G SSD now shows up as Disk 1 32G unallocated.  Also, Ubuntu installer sees the HDD and all 4 partitions.   I started setting up partitions on the SSD (dev/sdb) for Ubuntu and the last thing you do is tell it where to put GRUB right ?   Well, although I can see all the HDD partitions, I can't put GRUB on the HDD boot sector (dev/sda).   Not an option.   Why not ?  It'll let me put GRUB anywhere on the SSD though.   Crap.   I want the GRUB boot menu.  Ok, I want to see how much time it takes Win7 to boot up to the login screen now.   I have a feeling that previously when I timed boot up first with RST enabled and then disabled, I wasn't really disassociating the SSD and HDD.   Times were the same either way, 15 seconds.   

RDL

---

### Post by Robbobden on 2013-03-26
Yep, it consistently takes 30 seconds to get to the Win7 login screen now.   It doesn't bother me because I only use Windows to manage my iPAD2 (with iTunes).   I'm going to mess around with a different combination of sda/sdb for Ubuntu.   Maybe delete the HP Tools partition (4th partition) and put Ubuntu /boot there, the rest on sdb.   Will that give me the option to load GRUB on sda then ?  Dunno.  I bought the HP Recovery DVD set with drivers so I can get back if needed.

RDL

---

### Post by Robbobden on 2013-03-26
Ok, I lopped off the 3rd/4th partition, Recover and HP Tools.   Put Ubuntu /boot in sda3, Root, Home and Swap on sdb.   Got GRUB in sda boot sector now.   Will this work ?   About half way through the install now.
RDL

---

### Post by Robbobden on 2013-03-26
Success !   Both OS now bootable from GRUB menu.   Wireless button still working ok in Ubuntu.    I guess I could have saved myself some grief by not ordering the 32G SSD for this PC, but I think I'll like the increased speed with Ubuntu now.  Guess it's time to activate Win7 and pull the protective plastic off the screen.   

RDL

---

### Post by oldfred on 2013-03-26
Did you make the set of recovery DVDs so you can restore system to as purchased, before deleting it?

I would also make the full backup of Windows and a Windows repairCD.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Robbobden on 2013-03-26
Yo, I'm not the OP here; not possible for me to mark as [Solved]...

But, I think I might experiment a little more.   Like install Ubuntu by itself on the HDD, install VirtualBox, then run Win7 in virtual environment from Ubuntu and maybe in seamless mode.   Lots of work getting Win7 drivers installed - I have an OEM version of Win7.

And since I've borked the RST cache on the 32G SSD, I might think about replacing HDD with an SSD.

RDL

---

### Post by oldfred on 2013-03-28
Moved posts by Robbobden on his install to dv6t-7200 to his own thread.
[http://ubuntuforums.org/showthread.php?t=2130132](http://ubuntuforums.org/showthread.php?t=2130132)

---

