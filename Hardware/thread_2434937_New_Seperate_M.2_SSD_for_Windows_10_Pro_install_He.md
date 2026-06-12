---
title: "New Seperate M.2 SSD for Windows 10 Pro install Help"
date: 2020-01-13
forum: Hardware
---

### Post by arcman7 on 2020-01-13
So I've posted in other threads a while ago about my issues with Ubuntu freezing endlessly randomly, so with no solution to this, I've decided to install a new Corsair MP510 M.2 ssd and install Windows 10 Pro from Kinguin. What is the best way to do this dual boot setup. I'm keeping Ubuntu on my older 500gb Samsung EVO ssd and wanting to put Windws 10 on the newer Corsair M.2 drive.  I have yet to install anything yet. I want to make sure I do this right. Thanks for any help you can provide.

---

### Post by CelticWarrior on 2020-01-14
Your Ubuntu was installed in UEFI mode, right? That hardware kinda needs it...

If installed in UEFI mode there's an EFI partition in the first drive, Windows will use it as well. So...

- Install the new drive
- Boot Ubuntu and open GParted, select the new drive, open the Device menu > New partition table... > select GPT. Do not create any partition.
- Shutdown Ubuntu, insert the Windows installer USB stick, boot from the external media...
- Install Windows - when asked make sure to select the unallocated drive as destination, proceed with the installation.

Note: Windows will change the UEFI boot order to itself. After finishing the installation make sure to disable Fast Startup in Windows. Shutdown. Open UEFI settings and change the boot order back to Ubuntu (Grub), confirm and boot Ubuntu. In Ubuntu run ```
sudo update-grub
```. Now Windows is added to the Griub menu and you should be able to boot Windows from Grub.

---

### Post by oldfred on 2020-01-14
See if your UEFI has a setting to turn off a drive. Mine says disabled.
Then Windows will totally install to just the new drive.

Most UEFI autofind Windows when a drive is plugged in or reconnected, but not Ubuntu.
You may have to use live installer and use efibootmgr to update/replace Ubuntu UEFI boot entry. Or re-install grub which will do the same as grub uses efibootmgr as part of its install.
man efibootmgr

More details and some examples of efibootmgr in link in my signature.

---

### Post by arcman7 on 2020-01-14
> **oldfred said:**
> [B]See if your UEFI has a setting to turn off a drive. Mine says disabled.
Then Windows will totally install to just the new drive.
[/B]
Most UEFI autofind Windows when a drive is plugged in or reconnected, but not Ubuntu.
You may have to use live installer and use efibootmgr to update/replace Ubuntu UEFI boot entry. Or re-install grub which will do the same as grub uses efibootmgr as part of its install.
man efibootmgr

More details and some examples of efibootmgr in link in my signature.

You saying this option eliminates the need to disconnect my Samsung EVO SSD while Windows to loads onto new SSD? I'm seeing other tutorials talk of Windos wanting to put something on the the 1st drive that can mess things up. You would do this before putting in usb stick with Windows right?

Yes Ubuntu was installed via UEFI.

---

### Post by oldfred on 2020-01-14
Since it is often difficult to disconnect a drive particularly NVMe drives, you can do it with software.
We have seen a few cases where user could not see drive, and it was not all the usual suspects but a setting in UEFI.

---

### Post by arcman7 on 2020-01-14
> **oldfred said:**
> Since it is often difficult to disconnect a drive particularly NVMe drives, you can do it with software.
We have seen a few cases where user could not see drive, and it was not all the usual suspects but a setting in UEFI.

Ok interesting, is there a step by step guide on how to do this disable drive deal when setting up a separate drive for Windows? Do I restart into UEFI then do the "disable drive" , then restart again? This assumes the new SSD has been installed.

---

### Post by oldfred on 2020-01-14
You need to look at your UEFI and see what drive settings it has.

In my manual is this and my UEFI uses the periphials tab.
> Port 0/1/2/3/4/5
Enables or disables each SATA port. (Default: Enabled)

---

### Post by arcman7 on 2020-01-14
[ATTACH=CONFIG]284800[/ATTACH]  I appears that I can according to this. I hope this pic is visable. Under "Advanced tab" I have Sata controllers settings and and detection settings for SATA and the M.2's.

---

### Post by arcman7 on 2020-01-14
> **oldfred said:**
> Since it is often difficult to disconnect a drive particularly NVMe drives, you can do it with software.
We have seen a few cases where user could not see drive, and it was not all the usual suspects but a setting in UEFI.

From what I understand its only my present Ubuntu SSD which is not M.2( its Sata) that would need to be disabled/or disconnected. The new SSD I'm putting Windows 10 onto is a M.2 SSD.

---

### Post by mastablasta on 2020-01-16
> **CelticWarrior said:**
> Y
- Boot Ubuntu and open GParted, select the new drive, open the Device menu > New partition table... > select GPT. Do not create any partition.


out of curiosity and for possible future use- what does thi sstep do exactly? change to GPT format. but what happnes to existing data on drive. is this a painless procedure like changing fat32 to ntfs?

---

### Post by rbmorse on 2020-01-16
Converting an MBR storage device to GPT style partitioning will "erase" the device as all of the existing partitions will be removed. 

I put "erase" in quotes because all of the data is still there, but it's going to take heroic efforts to get to it.  For all practical purposes it will be gone. Make a good backup of the device before doing the conversion.  You can restore it when you're done.

---

### Post by arcman7 on 2020-01-16
> **arcman7 said:**
> [ATTACH=CONFIG]284800[/ATTACH]  It appears that I can according to this. I hope this pic is visible. Under "Advanced tab" I have Sata controllers settings and and detection settings for SATA and the M.2's.

It actually looks like my settings has the ability to turn off ALL Sata drives but that wouldn't help me in this scenario I'm trying here. I'm not sure I can just turn off one Sata port the for the Ubuntu drive unless there's' another setting. Anyone else running AsRock boards? Again I would only need to turn off the Ubuntu Samsung Evo SSD while installing Windows to the new Corsair M.2 PCIe SSD.  My only option might be to pull the sata cable on the Ubuntu Samsung SSD.

---

### Post by arcman7 on 2020-01-16
[ATTACH=CONFIG]284811[/ATTACH]This is the only other menu options for storage management I can find but I don't think this will help me here.

---

### Post by him610 on 2020-01-16
> Anyone else running AsRock boards?
Yes, I use an AsRock H270M-ITX/AC. In the User Manual, there is a section titled, "Storage Configuration." First item reads, > SATA Controller(s)
Enable/disable the SATA controllers.
I have learned something new in this thread; glad I stumbled onto it.

---

### Post by arcman7 on 2020-01-16
[ATTACH=CONFIG]284812[/ATTACH]So just installed the Corsair Nvme M.2 SSD , decided to unplug my older Samsung EVO SSD sata cable , inserted usb booted into AsRock UEFI and selected the usb with the Windows 10 ISO file and got this. Apparently I set up the iso file in Rufus wrong???

---

### Post by oldfred on 2020-01-16
How you boot from UEFI boot menu is how it installs for both Windows & Ubuntu.
You need to boot in UEFI boot mode.

You manually select in UEFI boot mode, and that is optional as settings in UEFI for UEFI boot are for the installed systems.

---

### Post by CelticWarrior on 2020-01-17
> **mastablasta said:**
> out of curiosity and for possible future use- what does thi sstep do exactly? change to GPT format. but what happnes to existing data on drive. is this a painless procedure like changing fat32 to ntfs?

It happens exactly as described in #11 but it's a moot point because we're talking about a new **blank **drive.

The step is there just in case the new drive has a "msdos" type partitioning table. The Windows installer can delete existing partitions, create and format new ones but it cannot change the partitioning table to GPT which is required for UEFI installations.

---

### Post by mastablasta on 2020-01-17
> **CelticWarrior said:**
> It happens exactly as described in #11 but it's a moot point because we're talking about a new **blank **drive.

The step is there just in case the new drive has a "msdos" type partitioning table. The Windows installer can delete existing partitions, create and format new ones but it cannot change the partitioning table to GPT which is required for UEFI installations.

oh i get it now. this refers to the new drive where windows will go, not the Ubuntu one. i read that too fast.
i get it all now. pretty much the same as it used to be with with BIOS/MBR, juts a step or two more. it was my first uefi i did 2 weeks ago. and well for now the kid is OK with Linux, but already saving up for windows and a new SSD drive (for gaming). 8-[ so i might need to do dual boot with GRUB in charge. 
but when Steam sales come around again i will introduce proton. so far we do the free games and mostly the old ones in PoL.


I have Kubutnu 18.04 with Windows XP on the other disk and i setup a shortcut that will boot to windows once. they play certain games there (can't get them working in wine) and then on reboot in windows, the system will return to linux. so i would try to do a similar dualboot thing later in windows 10 (if it ever comes to that).

---

### Post by arcman7 on 2020-01-17
> **oldfred said:**
> How you boot from UEFI boot menu is how it installs for both Windows & Ubuntu.
You need to boot in UEFI boot mode.

You manually select in UEFI boot mode, and that is optional as settings in UEFI for UEFI boot are for the installed systems.

OK if I understand you correctly, my Rufus setup was fine but I needed to do another step in UEFI to manually select UEFI boot? Any tips on how to do this. As it stands now I ended up redoing my Windows Iso file and set it up with MBR and NTFS mode, but I haven't yet attempted a reinstall of the Windows 10 Iso file.  Should I be undoing that?

---

### Post by CelticWarrior on 2020-01-17
For UEFI, Windows or Ubuntu, do not select anything that mentions MBR. Always GPT.

---

### Post by arcman7 on 2020-01-17
> **CelticWarrior said:**
> For UEFI, Windows or Ubuntu, do not select anything that mentions MBR. Always GPT.

Okey doke, so back to redoing my Windows iso file. Still not sure as to how to manually run UEFI boot for the usb carrying windows 10 iso.  

Just an FYI , I'm creating my Rufus 3.8 Windows iso file on a Windows 7 Dell laptop then transferring the USB Windows iso to my pc.

Setting up Rufus with the iso file with Partition Scheme as (GPT), Target System (UEFI) , File System (Fat32)

---

### Post by CelticWarrior on 2020-01-17
Windows 7 is out of support, no point in keeping that around, not even worth the time and effort to install it now.


> Still not sure as to how to manually run UEFI boot for the usb carrying windows 10 iso

Open UEFI settings and disable Legacy/CSM. That will assure any external media will boot (and install) in UEFI mode.

---

### Post by arcman7 on 2020-01-17
[ATTACH=CONFIG]284817[/ATTACH]Ok I'm currently in my AsRock UEFI system on my PC and I have 2 options here for the ScanDisk USB stick which has my Windows iso file. My second guess is to choose UEFI: ScanDisk, Partition 1 as I chose the USB: ScanDisk option last time trying to install.

---

### Post by CelticWarrior on 2020-01-17
Yes, that's what typically happens with Legacy/CSM enabled. That's why disabling it makes things easier.

Yes, the one to choose in this situation is always the one with UEFI in its name, same rule for an Ubuntu installer.

---

### Post by arcman7 on 2020-01-17
Ok, so far that last option worked and I'm in to Windows 10 install, Thanks Celtic Warrior. Now to try and set up the dual boot.

---

### Post by arcman7 on 2020-01-17
Ok , Not finding my Samsung EVO SSD after replugging back in an rebooting into UEFI. A tutorial I'm following mentioned checking BBS settings to find the drive that is not showing up, but I dont' see that option showing up anywhere under "Boot" menu. 

Do I need to Enable CSM again possibly??

My options in Boot priority are Windows Boot Manager and UEFI: Built-In-EFI Shell

*Update*

I actually do see the Samsung SSD in "Advanced" tab and under the Storage Configuration detection list. Its there along with the M.2 Corsair. So my Ubuntu drive is detected but not being included in my boot priority options.

---

### Post by oldfred on 2020-01-17
UEFI seems to automatically find Windows in ESP and add that back into boot menu when an internal drive is plugged in.

Do you have a drive boot option, that is also called the fallback and is /EFI/Boot/bootx64.efi. That is the same way external drives are booted.
If so that should boot into Ubuntu and then you can use efibootmgr to create new ubuntu boot entry. Or total reinstall grub which also uses efibootmgr to create UEFI boot entry. You can also use live installer to create UEFI entry or run Boot-Repair to create entry.

To see entries, you may have an old ubuntu entry that does not work.
sudo efibootmgr -v
Details on commands:
man efibootmgr

Some examples of commands:
sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP.
sudo efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/sda -p 1
it defaults to /dev/sda & 1 for sda1 as ESP. You must use correct drive & partition if not sda1.

If NVMe drive thenl, if first drive, nvme0n1 and partition p1.
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

---

### Post by arcman7 on 2020-01-18
> **oldfred said:**
> UEFI seems to automatically find Windows in ESP and add that back into boot menu when an internal drive is plugged in.

Do you have a drive boot option, that is also called the fallback and is /EFI/Boot/bootx64.efi. That is the same way external drives are booted.
If so that should boot into Ubuntu and then you can use efibootmgr to create new ubuntu boot entry. Or total reinstall grub which also uses efibootmgr to create UEFI boot entry. You can also use live installer to create UEFI entry or run Boot-Repair to create entry.

To see entries, you may have an old ubuntu entry that does not work.
sudo efibootmgr -v
Details on commands:
man efibootmgr

Some examples of commands:
sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP.
sudo efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/sda -p 1
it defaults to /dev/sda & 1 for sda1 as ESP. You must use correct drive & partition if not sda1.

If NVMe drive thenl, if first drive, nvme0n1 and partition p1.
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1


My options under "Boot" tab are Boot Priorities 
Boot Option#1 -Windows Boot Manager
Boot Option #2  UEFI : Built in EFI Shell
 
Fast Boot - Disabled
Boot from Onboard Lan- Disabled
Setup Prompt Timeout- 1
Boot Number Lock   - On
Boot Beep    - Disabled
Full Screen Logo- Enabled
AddOn ROM Display - Enabled
Above 4G Encoding- Disabled


CSM(Compatibility Support Module) Turned off.

That is it for my Boot Tab.

Another tab of note is under Advanced Tab/AMD CBS/FCH Common Options/SATA Configuration Options.

Sata Controller
SATA RAS Support
Sata Disabled AHCI Prefetch Funtction
Aggressive SATA Device Sleep Port 0
Agressive SATA Device Sleep Port 1 

All above settings are in Auto.

---

### Post by oldfred on 2020-01-18
Some other Asrock AMD based systems. Note UEFI update my reset to default some of your UEFI settings so keep list and check after update.

ASRock Fatal1ty B450 Gaming K4 - SATA SSD  not seen in NVMe slot 
[https://ubuntuforums.org/showthread.php?t=2433768](https://ubuntuforums.org/showthread.php?t=2433768)
 Asus ROG Strix B450 E motherboard UEFI update worked
[https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679](https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679)

---

### Post by arcman7 on 2020-01-18
> **oldfred said:**
> Some other Asrock AMD based systems. Note UEFI update my reset to default some of your UEFI settings so keep list and check after update.

ASRock Fatal1ty B450 Gaming K4 - SATA SSD  not seen in NVMe slot 
[https://ubuntuforums.org/showthread.php?t=2433768](https://ubuntuforums.org/showthread.php?t=2433768)
 Asus ROG Strix B450 E motherboard UEFI update worked
[https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679](https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679)

Oh ok. Well before all this, last time i tried to update UEFI version, I couldn't boot into Ubuntu at all, had to reload original bios version that came with the board.

---

### Post by oldfred on 2020-01-19
If UEFI update did not work was it because it reset everything to default?
I have multiple settings in my Asus motherboard that I have to redo on every UEFI update.

---

