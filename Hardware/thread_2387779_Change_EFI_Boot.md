---
title: "Change EFI Boot"
date: 2018-03-23
forum: Hardware
---

### Post by mabari99 on 2018-03-23
I have an HP Pavilion Touchsmart 14 Sleekbook. I have 3 OSes on it. 1. Mageia 6  2. Windows 10  3. Ubuntu 17.10 (running kubuntu Plasma). When I boot up I get the Mageia 6 Grub2 graphical menu. From there I can choose which OS I bring up. For some reason this has begun screwing up. When I try Mageia or Windows I am getting an error: Grub EFI_ALLOCATE_MAX_PAGES not found. or something like this. When I press the Ubuntu option, I get the Ubuntu Grub 2 menu with the different options on it. All of them work from the Ubuntu menu. My question is: How do I change the Boot order so that I get the Ubuntu Grub 2 menu NOT the Mageia Grub 2 menu. I'm not a deeply experienced Linux user but I know enough to be dangerous. Any and all help greatly appreciated. Thx

---

### Post by oldfred on 2018-03-23
Post this:
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/
[/URL] 

Probably just need to change boot order with efibootmgr.
see
man efibootmgr

       Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
sudo efibootmgr -o 2,1

---

### Post by yancek on 2018-03-23
Running sudo efibootmgr suggested above will give you boot order output including which entries you have with a 4digit code for each.  Use the -o option suggested above with sudo efibootmgr.  You can try one digit or use all four.

---

### Post by mabari99 on 2018-03-26
Changed the order as per your comment. Checked with -v option to ensure it was changed. Rebooted. Got the same Mageia Grub 2 menu, not the Ubuntu Grub 2 menu. Chose Ubuntu. Checked the boot order to see if it still held my changes. Nope. Reverted back to original. Rebooted back into Mageia. Tried to change it there, but Mageia does not have efibootmgr. Currently I'm looking to see if I can load efibootmgr or an equivalent into Mageia. Any help greatly appreciated. Thx.

---

### Post by oldfred on 2018-03-26
HP UEFI violates UEFI standard which says NOT to use description as part of boot.
And only valid description is "Windows Boot Manager".

But the fallback or hard drive entry often works.
That is /EFI/Boot/bootx64.efi and usually is just a copy of Windows .efi boot file.

Boot-Repair now copies shimx64.efi to be bootx64.efi. Before Boot-Repair created that option, many manually copied/renamed files.
If you have run Boot-Repair, can you boot hard drive entry?

 Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186) 


 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 
      
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by mabari99 on 2018-03-26
Thx for detailed reply. Here's a copy of my current EFI Boot Manager

[FONT=monospace][COLOR=#000000]BootCurrent: 0000[/COLOR]
Timeout: 0 seconds
BootOrder: 3000,3001,3005,2001,2002,2003
Boot0000* Windows Boot Manager  HD(2,GPT,b30f85d1-eba9-4351-b677-fed70cc959c6,0xc8800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0001* Ubuntu        HD(2,GPT,b30f85d1-eba9-4351-b677-fed70cc959c6,0xc8800,0x82000)/File(\EFI\ubuntu\grubx64.efi)RC                                                   
Boot0005* Windows Boot Manager  HD(2,GPT,b30f85d1-eba9-4351-b677-fed70cc959c6,0xc8800,0x82000)/File(\EFI\mageia\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.
d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...6................                                                                              
Boot0010* USB Hard Drive (UEFI) - SanDisk Cruzer Glide  PciRoot(0x0)/Pci(0x1a,0x0)/USB(0,0)/USB(1,0)/HD(1,MBR,0x631ff,0x800,0x773cd00)RC                                 
Boot0014* Windows Boot Manager  HD(2,GPT,b30f85d1-eba9-4351-b677-fed70cc959c6,0xc8800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC                                  
Boot0015* Notebook Hard Drive   BBS(HD,&#9618;&#65533;,0x500)................-.`.......`.A.`........................................                                                  
Boot0016* Windows Boot Manager  HD(2,GPT,b30f85d1-eba9-4351-b677-fed70cc959c6,0xc8800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC                                  
Boot2001* USB Drive (UEFI)      RC                                                                                                                                       
Boot3000* Internal Hard Disk or Solid State Disk        RC                                                                                                               
Boot3001* Internal Hard Disk or Solid State Disk        RC                                                                                                               
Boot3005* Internal Hard Disk or Solid State Disk        RC 

Things to Note:
If I change the boot order to make Ubuntu the first option, not Windows, if I run efibootmgr -v option it shows the change of order, but when I reboot it does not run Ubuntu, it runs from the /dev/sda6 partition which has Mageia on it. And yet, as you can see from the above boot order there is absolutely no mention of Mageia anywhere.

I used to get round this by copying the EFI\mageia\grubx64.efi file to the EFI\Microsoft\Boot\bootmgfw.efi and this would give me the Mageia Grub 2 menu on boot from which I could choose my options. As the mageia Grub2 menu no longer works, I still have the option to do this as I can get into Mageia by way of Ubuntu Grub 2 which I can currently do this by copying the EFI\ubuntu\grubx64.efi [/FONT][FONT=monospace]file to the EFI\Microsoft\Boot\bootmgfw.efi.

Still, it doesn't explain how the system boots from the /dev/sda6 (Mageia) partition.

Any ideas?[/FONT]

---

### Post by oldfred on 2018-03-26
Need to see Boot-Repair summary report.
Post link.

We stopped suggesting the copy to the Windows .efi boot file, as Windows updates will overwrite it. 
Usually the other work arounds then are preferred.

You have several Windows UEFI entries that are duplicates. 0000, 0014, 0016
But the "Windows" entry 0005 is your mangeia.
HP only default boots Windows, but with multiple entries, not sure what it does.

---

### Post by mabari99 on 2018-03-26
The Boot summary file is:

[http://paste.ubuntu.com/p/W4kq3rXxDD/](http://paste.ubuntu.com/p/W4kq3rXxDD/)

Also, even though I did not run the repair disk option, the boot repair system changed my efibootmgr to

[FONT=monospace][COLOR=#000000]BootCurrent: 0001[/COLOR]
Timeout: 0 seconds
BootOrder: 3005,3001,2001,2002,2003
Boot0001* Ubuntu        HD(2,GPT,b30f85d1-eba9-4351-b677-fed70cc959c6,0xc8800,0x82000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0005* Windows Boot Manager  HD(2,GPT,b30f85d1-eba9-4351-b677-fed70cc959c6,0xc8800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C
.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...6................                                                                     
Boot0010* USB Hard Drive (UEFI) - SanDisk Cruzer Glide  PciRoot(0x0)/Pci(0x1a,0x0)/USB(0,0)/USB(1,0)/HD(1,MBR,0x631ff,0x800,0x773cd00)RC                                 
Boot0014* Windows Boot Manager  HD(2,GPT,b30f85d1-eba9-4351-b677-fed70cc959c6,0xc8800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC                                  
Boot0015* Notebook Hard Drive   BBS(HD,&#9618;&#65533;,0x500)................-.`.......`.A.`........................................                                                  
Boot0016* Windows Boot Manager  HD(2,GPT,b30f85d1-eba9-4351-b677-fed70cc959c6,0xc8800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC                                  
Boot2001* USB Drive (UEFI)      RC                                                                                                                                       
Boot3001* Internal Hard Disk or Solid State Disk        RC                                                                                                               
Boot3005* Internal Hard Disk or Solid State Disk        RC  


No mention of Mageia. I can still get to Mageia from the Ubuntu Grub menu. Only problem, I have to invoke Ubuntu by pressing the F9 Boot Option Change on boot to stop Windows booting.

So I guess my problem is down to booting to the Ubuntu Grub as opposed to windows.[/FONT]

---

### Post by oldfred on 2018-03-26
Your fstab in sda6 Mageia, has a mount of sdb1, but that UUID does not exist. That often causes issues.

You still have 3 Windows UEFI entries. Best to only have one.

Ubuntu is trying to directly boot Mageia, but its boot stanza looks a lot different than the boot stanza in Mageia's grub.
I might try copying one to Ubuntu's grub's 40_custom.
Or do a chainload like the Windows boot stanza to chain to the ESP /efi/mageia folder. You show both of these in ESP, is only one correct?
 /EFI/mageia/grubx64.efi 
/EFI/mageia5/grubx64.efi 

You can add an UEFI entry, but HP may not let you boot it except as you now are booting manually thru UEFI boot menu.
      
 sudo efibootmgr -c -g -w -L "Mageia" -l '\EFI\mageia\grub64.efi'  -d /dev/sda -p 2  :or mageia5? or both?

Does hard drive entry 3001 or 3005 boot Ubuntu? Do not know if UEFI or BIOS entry or both, but it looks like Boot-Repair copied a grub to bootx64.efi. Not sure which grub?

test hard drive UEFI entries, remove duplicate Windows UEFI boot entries and consider simiplifing grub menus.
I prefer to turn off os-prober as it adds too many entries and copy or create my own entries in 40_custom for the grub I use to boot. Details:

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by mabari99 on 2018-03-26
Thx for quick reply. Unfortunately, you have flown above my head with some of this reply. Let me go thru it.

"Your fstab in sda6 Mageia, has a mount of sdb1, but that UUID does not exist. That often causes issues."

I vied the fstab on /dev/sd6 Mageia. It is

# Entry for /dev/sda6 :
UUID=25bac288-0a11-4c73-ba01-38e1c80836e5 / ext4noatime,acl1 1
# Entry for /dev/sda2 :
UUID=46D2-794A /boot/EFI vfatumask=000,iocharset=utf80 0
# Entry for /dev/sda10 :
UUID=c39c27d0-9586-4000-80f9-767491677892 /home ext4noatime,acl1 2
# Entry for /dev/sda4 :
UUID=CA3E6BFC3E6BE045 /media/windows ntfs-3g defaults,nofail,umask=0000 0
# Entry for /dev/sdb1 :
UUID=1CE6-3D49 /mnt/hd vfatumask=000,users,iocharset=utf8,noauto,exec,nofail 0 0
none /proc procdefaults0 0

You're right I don't see an entry for /dev/sdb1. I'm assuming that it is the last 1 on the line for /dev/sd6 that tells it to mount on sdb1. Is that correct? If so, why can't I just change it to 2? Would this work?

---

### Post by mabari99 on 2018-03-26
I don't actually need to run Mageia Grub on boot, in fact now I don't want to. I want to run the Ubuntu Grub on boot, not Windows or Mageia Grub. The Ubuntu Grub menu has options for both Windows and Mageia and they both work. I also deleted the extra Windows boot entries, so now, on boot, if I press the F9 Change Boot Options I get the choice of Windows or Ubuntu. So if I boot and want to run Windows, I do nothing and it boots Windows. If I want to run Ubuntu or Mageia, I press F9 and choose Ubuntu which gets me the Ubuntu Grub menu and I choose which one I want. I guess I can live with this, but it would be very nice to just get the Ubuntu Grub menu on boot, not automatic Windows.

---

### Post by oldfred on 2018-03-26
With fstab, it is not the entry with the # as that is just a comment. And that can change.
But the next line as the UUID and that UUID is not shown. It may be some flash drive or other removeable device. But then best not to mount with fstab.

Did you try booting the hard drive entries?
HP may let you set one of them as default boot, but you may need to do that from within UEFI, not with efibootmgr.

---

### Post by mabari99 on 2018-03-29
First of all thank you oldfred for all your help. Unfortunately I have tried everything that you suggested to no avail. Damn Windows keeps booting. So I turned off the Secure Boot on my laptop and ran the Disk Repair option again with the Secure Boot option disabled. After that, I still had to press F9 Change Boot Options when I re-booted to run Ubuntu, and the Grub 2 menu was filled with all kinds of options. I ran the Grub Optimizer program and cleaned it all up so that it offered only Ubuntu, Windows and Mageia. Then I went into the /EFI/Microsoft/Boot directly and over wrote the bootmgfw.efi file with the Ubuntu grubx64.efi file. I ten had to change (through Grub Optimizer) the code behind the Windows option which ran bootmgwf.efi and of couse, brought the ubuntu grub menu up againnot Windows. I changed it to run bottmgwfprev.efi which is a copy of the bootmgwf.efi file and which then ran Windows.

I know that this option is not recommended by you as Windows overwrites it on updates, but honestly, I use Windows so rarely (what a ****** OS) that I don't mind doing what I have always done, change it back after Windows updates. This whole thing started because my laptop was going to the Mageia /EFI/Microsoft/Boot menu but something blew it up and I started getting those alloc errors about max pages. What the Boot Repair did was cause the boot to go to the Ubuntu /EFI/Microsoft/Boot not the Mageia one. Which is great. I also changed my ubuntu to kubuntu running Plasma and this actually is as good as the Mageia 6 and of course, Ubuntu has much better resources and support from guys like yourself.

So I'm considering dropping Mageia from the computer and turning the space over to Ubuntu. Though I still really like Mageia and feel that they deserve support for their efforts.

By the way I noticed that if I turn Secure Boot back on again it tells me that there is no OS and won't boot. Is there a downside to running without Secure Boot, or is that just part of the great scam to force Windows on eberybody?

I guess this thread is solved now sort of, what do I do next? Once again, many thanks for your help.

---

### Post by oldfred on 2018-03-29
Torvalds clarifies Linux's Windows 8 Secure Boot position
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security 

Sometime in the future we may need UEFI Secure Boot.

But if you are a company that continuously has press releases about virus and scams, what better than to have "Secure Boot". Even though not related to almost all virus out there.
The main boot virus was years ago from Sony and trying to implement DRM music rights management on everyone's system.

---

