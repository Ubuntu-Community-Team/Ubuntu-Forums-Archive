---
title: "Install externally before dropping HD into system?"
date: 2015-01-22
forum: Hardware
---

### Post by mamamia88 on 2015-01-22
I ordered a few cheap dells that haven't arrived yet without HDS.  I have the HDS and the necessary USB adapters to use them externally.  If I install ubuntu on say /Dev/SDC and make sure grub installs on same disk can I just pop the HD in new system when it arrives?

---

### Post by oldfred on 2015-01-22
Probably.

Just do not install any proprietary drivers for graphics, wireless or other.
And depending on graphics may need nomodeset or other boot parameters.

New systems will probably be UEFI, so can you install in UEFI mode on your current system? And then you would want to manually remove UEFI entry for that install after you remove drive.

You can install in BIOS mode, but if only Ubuntu you can use gpt and boot in BIOS mode or UEFI mode. I then would use gpt partitioning, create both an efi partition at beginning of drive and a bios_grub partition for BIOS boot. Then you can convert to UEFI with Boot-Repair later if you want.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by mamamia88 on 2015-01-22
Oh these are older dells recommissioned from the business sector.  I don't plan on using proprietary graphics. One will have 4gb ram and one with 8 assuming old ram I have works. One has an 80gb sad the other a 160gb 7200 drive.  I'd just prefer to pop in an HD and go.

---

### Post by sudodus on 2015-01-22
If the computers are similar enough, you can configure an OEM system in one of the computers, and later on clone it to the other computers. Remember that you can clone to the same size or larger drives but not to smaller drives.

Maybe that would suit your purpose.

[URL="https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview"]https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview
[/URL]

---

### Post by mamamia88 on 2015-01-22
> **sudodus said:**
> If the computers are similar enough, you can configure an OEM system in one of the computers, and later on clone it to the other computers. Remember that you can clone to the same size or larger drives but not to smaller drives.

Maybe that would suit your purpose.

[URL="https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview"]https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview
[/URL]
Hmm interesting.  I'm setting it up on the ssd now and will worry about the hdd system later.  Didn't really even need 2 systems but I went overboard on ebay

---

### Post by weatherman2 on 2015-01-22
I have done the "install on some other system" approach many times, and it works well most of the time (with caveats mentioned above for proprietary drivers noted).  Ubuntu is extremely forgiving, in general, about being moved from system to system.  I've booted many internal drives later via USB on other computers and vice versa.

You can do one single install, do all the updates, then clone it to the others.  The last step may be to change the /etc/hostname and /etc/hosts files to make unique hostnames so they aren't all the same on your network.  Also, you might want to erase the files /etc/udev/rules.d/70-persistent-net.rules and /etc/udev/rules.d/70-persistent-cd.rules (will be regenerated at next boot) so that your ethernet cards get reset to eth0 on each computer (not really a big deal if it bumps up to eth1 though) and the same for the CD/DVD drive if there is one.

The OEM approach probably makes some sense if you are doing more than a few installs.

---

### Post by sudodus on 2015-01-22
@weatherman2,

Using the OEM boot option is actually quite convenient even for a low number of clones. It does the things you suggest (to make the computers and users unique) automatically. Try it if you haven't done it yet :-)

---

### Post by weatherman2 on 2015-01-22
Thanks, I may try the OEM approach, but I haven't actually needed to do what the OP wants to do.  Instead, I often find I have an already existing install I want to re-use somewhere else but I don't know that ahead of time.

---

### Post by mamamia88 on 2015-01-22
Ok i set it up and installed all the apps i usuually use.  Can i update grub menu to remove the internal laptop drive that i used to set up the install in the first place? The only hd i want to be included in grub is the install i just did

---

### Post by oldfred on 2015-01-22
If you turn off os-prober it does not find other installs. You can later turn it back on if desired.

Several ways:
 In /etc/default/grub I added this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or 
sudo sed -i '$a GRUB_DISABLE_OS_PROBER=true' /etc/default/grub
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

Of course as soon as you plug drive into new system, you can run this and then it will not find any other installs anyway. This also runs os-prober.
sudo update-grub

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by mamamia88 on 2015-01-22
Would sudo update grub work on it's own after booting into system on new machine for first time seeing how it will be the only drive in the machine?

---

### Post by weatherman2 on 2015-01-22
You need Grub whether you have one drive or ten.  The Grub menu comes up only if you have more than one OS installed and detected.  Grub isn't the menu, it's the boot manager - the menu is part of it.

But a simple "sudo update-grub" after moving to the new hardware would do the trick.

---

