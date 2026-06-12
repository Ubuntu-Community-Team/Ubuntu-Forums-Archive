---
title: "Hard freeze on Installing for x86_64-efi platform"
date: 2016-07-16
forum: Hardware
---

### Post by nhathaway on 2016-07-16
I get a hard lock-up when doing 'apt dist-upgrade' when grub is being updated.

The last lines before the freeze are as follows:

Setting up grub-common (2.02~beta2-36ubuntu3.1) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up grub2-common (2.02~beta2-36ubuntu3.1) ...
Setting up grub-efi-amd64-bin (2.02~beta2-36ubuntu3.1) ...
Setting up grub-efi-amd64 (2.02~beta2-36ubuntu3.1) ...
Installing for x86_64-efi platform.

At this point the PC is frozen totally - no response to the keyboard, not even pressing numlock to change the numlock LED on the keyboard does anything. You have to do a power cycle or hard reset to get back control.

When you do this, the system fails to boot and you just get the 'grub>' prompt. You can type in manual grub commands to boot. Having booted, I ran boot-repair, and this is its log: [http://paste2.org/4vEb92jb](http://paste2.org/4vEb92jb)

This is Ubuntu Mate 16.04.

Has anyone else seen this? Is there a permanent solution/work-around?

---

### Post by oldfred on 2016-07-16
Is this an Asrock motherboard, I see mention of Asrock in video?
I do not see anything in Summary Report that looks out of place?

        Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode](http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode)
ASRock Z97
[http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6](http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6)
ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
[http://www.asrock.com/mb/Intel/Z77%20Pro3/?cat=Manual](http://www.asrock.com/mb/Intel/Z77%20Pro3/?cat=Manual)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

### Post by nhathaway on 2016-07-17
Thanks for the info.

It's this:

[h=1]ASRock N3700-ITX M-ITX Intel N3700 Braswell 2DDR3 Motherboard[/h]
[https://www.amazon.co.uk/ASRock-N3700-ITX-M-ITX-Braswell-Motherboard/dp/B00YH2I5KO](https://www.amazon.co.uk/ASRock-N3700-ITX-M-ITX-Braswell-Motherboard/dp/B00YH2I5KO)

---

### Post by nhathaway on 2016-07-17
I had a look through the links, and I didn't see anything that related to this problem. It's strange that boot-repair works, but the update using apt freezes the machine.

Some other info:

I bought the machine last November (2015) and installed Ubuntu 15.10. This problem did not occur then. It only started happening when I did an upgrade to 16.04. The upgrade process itself produced an unbootable system, which I had to fix using boot-repair.

When I do 'apt dist-upgrade' I do so via ssh. The machine operates as a server. It has a 'console' in that it has a screen connected via HDMI and a USB keyboard/mouse. When the box locked up, I went to the console and that's when I found it was fully locked up.

I notice that ASRock have issued BIOS updates for this board: [http://www.asrock.com/MB/Intel/N3700-ITX/?cat=Download&os=BIOS](http://www.asrock.com/MB/Intel/N3700-ITX/?cat=Download&os=BIOS)
It says don't update unless there is a problem, so I'm reluctant to update without due cause.

When it is doing an EFI update, does it do more than write files to the FAT32 EFI partition? If not, it seems strange that it should lock up like this. If it contact the BIOS somehow, it seems strange that update should lock the machine, but boot-repair runs OK. Of course, I ran boot-repair from the console.

Any more suggestions?

---

### Post by oldfred on 2016-07-17
Did you have any ppa or proprietary drivers installed before upgrade? That almost always causes issues with an upgrade.
What video are you using? Intel, and what Intel CPU is it then?

Motherboard upgrades write into UEFI NVRAM on motherboard.

Ubuntu is only updating on hard drive and may change boot order in UEFI.

---

### Post by nhathaway on 2016-07-17
In the Additional Drivers tab of Software & Updates, all it has is "Using Processor microcode for Intel CPUs from intel-microcode (proprietary)". There are no PPAs that contain drivers (the PPA's I have are for bubbleupnpserver, java (webupd8team), and boot-repair (yannubuntu))

The video is Intel, and the CPU is the N3700, as I said above. This is the board: [http://www.asrock.com/mb/Intel/N3700-ITX/](http://www.asrock.com/mb/Intel/N3700-ITX/)

Does the line "[COLOR=#000000]Installing for x86_64-efi platform" perform a motherboard upgrade and hence write to NVRAM? Or does this only write to the hard drive (or flash disk in my case)?

I am suspicious that it may depend on whether this is run from the console or whether it is run remotely via ssh.
[/COLOR]

---

### Post by oldfred on 2016-07-17
Ubuntu does not update motherboard UEFI, other than boot order settings. 
Most of UEFI is locked to vendor's updates only, just a few settings can be updated from a system.

Grub2 has two versions for standard Intel/AMD chips. One is CSM/BIOS/Legacy which is grub-pc and the other is for UEFI as grub-efi-amd64 for 64 bit systems.
So system is just saying what version it is installing.

There is a feature in new UEFI standard to allow vendors code to be updated in UEFI from an operating system. 
Most require either Windows and their code, or directly from UEFI reading a vendor file from a FAT32 formatted partition. I have updated my UEFI by downloading vendor's file into my ESP - efi system partition which is FAT32 and then from UEFI read that file to update.

I also have the Intel microcode and Boot-Repair. But even Boot-Repair has to have a new version as ppa's do not get updated when you update a system. Do not know about other ppa, if correct version or may be the issue?

---

### Post by nhathaway on 2016-07-17
Boot-repair is not an issue. It works perfectly.

---

### Post by samslists on 2016-08-19
I just ran into what appears to be this exact same problem, except on an Intel NUC 5PPYH, which has, you guessed it, an N3700 processor.

I was also logged in via ssh (well, mosh), and did an update of packages on the command line, and it also locked up at "Installing for x86_64-efi platform." and now only boots to grub.

This is Ubuntu 14.04, but I believe I might have a later kernel installed (via apt).

Here are the last several lines of the update in case they are useful to anyone:

```
Adding boot menu entry for EFI firmware configuration                                                    
done                                                                                                     
Setting up linux-image-extra-4.2.0-41-generic (4.2.0-41.48~14.04.1) ...                                  
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-41-generic /boot/vmlinuz-4.2.0-41-gene
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-41-generic /boot/vmlinuz-4.2.0-41-gener
update-initramfs: Generating /boot/initrd.img-4.2.0-41-generic                                           
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-41-generic /boot/vmlinuz-4.2.0-41-generic     
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-41-generic /boot/vmlinuz-4.2.0-41-gener
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-41-generic /boot/vmlinuz-4.2.0-41-generi
Generating grub configuration file ...                                                                   
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-42-generic                                                        
Found initrd image: /boot/initrd.img-4.2.0-42-generic                                                    
Found linux image: /boot/vmlinuz-4.2.0-41-generic                                                        
Found initrd image: /boot/initrd.img-4.2.0-41-generic                                                    
Found linux image: /boot/vmlinuz-4.2.0-36-generic                                                        
Found initrd image: /boot/initrd.img-4.2.0-36-generic                                                    
Found linux image: /boot/vmlinuz-3.19.0-65-generic                                                       
Found initrd image: /boot/initrd.img-3.19.0-65-generic                                                   
Adding boot menu entry for EFI firmware configuration                                                    
done                                                                                                     
Setting up linux-signed-image-3.19.0-65-generic (3.19.0-65.73~14.04.1) ...                               
warning: file-aligned section .text extends beyond end of file                                           
warning: checksum areas are greater than image size. Invalid section table?                              
Generating grub configuration file ...                                                                   
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-42-generic                                                        
Found initrd image: /boot/initrd.img-4.2.0-42-generic                                                    
Found linux image: /boot/vmlinuz-4.2.0-41-generic                                                        
Found initrd image: /boot/initrd.img-4.2.0-41-generic                                                    
Found linux image: /boot/vmlinuz-4.2.0-36-generic                                                        
Found initrd image: /boot/initrd.img-4.2.0-36-generic                                                    
Found linux image: /boot/vmlinuz-3.19.0-65-generic                                                       
Found initrd image: /boot/initrd.img-3.19.0-65-generic                                                   
Adding boot menu entry for EFI firmware configuration                                                    
done                                                                                                     
Setting up isc-dhcp-common (4.2.4-7ubuntu12.5) ...                                                       
Setting up isc-dhcp-client (4.2.4-7ubuntu12.5) ...                                                       
Installing new version of config file /etc/apparmor.d/sbin.dhclient ...                                  
Setting up openssh-client (1:6.6p1-2ubuntu2.8) ...                                                       
Setting up openssh-sftp-server (1:6.6p1-2ubuntu2.8) ...                                                  
Setting up openssh-server (1:6.6p1-2ubuntu2.8) ...                                                       
ssh stop/waiting                                                                                         
ssh start/running, process 4423                                                                          
Setting up avahi-autoipd (0.6.31-4ubuntu1.1) ...                                                         
Setting up avahi-daemon (0.6.31-4ubuntu1.1) ...                                                          
avahi-daemon start/running, process 4561                                                                 
Setting up avahi-utils (0.6.31-4ubuntu1.1) ...                                                           
Setting up libdpkg-perl (1.17.5ubuntu5.7) ...                                                            
Setting up dpkg-dev (1.17.5ubuntu5.7) ...                                                                
Setting up firefox (48.0+build2-0ubuntu0.14.04.1) ...                                                    
Please restart all running instances of firefox, or you will experience problems.                        
Setting up firefox-locale-en (48.0+build2-0ubuntu0.14.04.1) ...                                          
Setting up fontconfig (2.11.0-0ubuntu4.2) ...                                                            
Regenerating fonts cache... done.                                                                        
Setting up grub-common (2.02~beta2-9ubuntu1.12) ...                                                      
Installing new version of config file /etc/grub.d/30_uefi-firmware ...                                   
Setting up grub2-common (2.02~beta2-9ubuntu1.12) ...                                                     
Setting up grub-efi-amd64-bin (2.02~beta2-9ubuntu1.12) ...                                               
Setting up grub-efi-amd64 (2.02~beta2-9ubuntu1.12) ...                                                   
Installing for x86_64-efi platform.
```

---

### Post by newan on 2016-11-15
> **samslists said:**
> I just ran into what appears to be this exact same problem, except on an Intel NUC 5PPYH, which has, you guessed it, an N3700 processor.

I was also logged in via ssh (well, mosh), and did an update of packages on the command line, and it also locked up at "Installing for x86_64-efi platform." and now only boots to grub.

This is Ubuntu 14.04, but I believe I might have a later kernel installed (via apt).

Here are the last several lines of the update in case they are useful to anyone:
....


Same here, german:

```

[SIZE=3]Vorbereitung zum Entpacken von .../shim-signed_1.19~16.04.1+0.8-0ubuntu2_amd64.deb ...
Entpacken von shim-signed (1.19~16.04.1+0.8-0ubuntu2) über (1.18~16.04.1+0.8-0ubuntu2) ...
Vorbereitung zum Entpacken von .../tvheadend_4.1-2322~g879d532~xenial_amd64.deb ...
Entpacken von tvheadend (4.1-2322~g879d532~xenial) über (4.1-2308~g203af79~xenial) ...
Trigger für dbus (1.10.6-1ubuntu3.1) werden verarbeitet ...
Trigger für libc-bin (2.23-0ubuntu4) werden verarbeitet ...
Trigger für man-db (2.7.5-1) werden verarbeitet ...
Trigger für ureadahead (0.100.0-19) werden verarbeitet ...
Trigger für systemd (229-4ubuntu12) werden verarbeitet ...
libpam-systemd:amd64 (229-4ubuntu12) wird eingerichtet ...
udev (229-4ubuntu12) wird eingerichtet ...
addgroup: Die Gruppe »input« existiert bereits als Systemgruppe. Programmende.
update-initramfs: deferring update (trigger activated)
libquadmath0:amd64 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
libgomp1:amd64 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
libitm1:amd64 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
libatomic1:amd64 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
libasan2:amd64 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
liblsan0:amd64 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
libtsan0:amd64 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
libubsan0:amd64 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
libcilkrts5:amd64 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
libmpx0:amd64 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
cpp-5 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
libcc1-0:amd64 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
libgcc-5-dev:amd64 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
gcc-5 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
libstdc++-5-dev:amd64 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
g++-5 (5.4.0-6ubuntu1~16.04.4) wird eingerichtet ...
libaccountsservice0:amd64 (0.6.40-2ubuntu11.3) wird eingerichtet ...
accountsservice (0.6.40-2ubuntu11.3) wird eingerichtet ...
linux-libc-dev:amd64 (4.4.0-47.68) wird eingerichtet ...
linux-signed-generic-lts-vivid (4.4.0.47.50) wird eingerichtet ...
shim-signed (1.19~16.04.1+0.8-0ubuntu2) wird eingerichtet ...
Installing for x86_64-efi platform.[/SIZE]

```

After that, only boots to grub. Update over ssh . Motherboard: [http://www.asrock.com/mb/Intel/N3700-ITX/](http://www.asrock.com/mb/Intel/N3700-ITX/)

---

### Post by nhathaway on 2017-01-30
I spotted this Debian bug report from a while back:

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=774138](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=774138)

This also:

[https://bugs.launchpad.net/linuxmint/+bug/1531861](https://bugs.launchpad.net/linuxmint/+bug/1531861)

---

### Post by melogenesis on 2017-03-16
I have same problem on my acer ES-533 and i found somethings about UEFI but still i couldnt figure out :(

---

### Post by oldfred on 2017-03-16
@melgenesis
Best to start your own thread. And post more details on your specific issue and hardware.

---

### Post by psorcerer on 2017-07-15
Same thing here, update via ssh, motherboard: Gigabyte GA-N3150N-D3V, hard freeze, boot to grub afterwards.

[FONT=Courier New]Setting up openssh-server (1:7.2p2-4ubuntu2.2) ...
Setting up snapd (2.25) ...
Removing obsolete conffile /etc/apparmor.d/usr.lib.snapd.snap-confine ...
Setting up ubuntu-core-launcher (2.25) ...
Setting up snap-confine (2.25) ...
Setting up libwhoopsie0:amd64 (0.2.52.3) ...
Setting up whoopsie (0.2.52.3) ...
Setting up grub-common (2.02~beta2-36ubuntu3.11) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up grub2-common (2.02~beta2-36ubuntu3.11) ...
Setting up grub-efi-amd64-bin (2.02~beta2-36ubuntu3.11) ...
Setting up grub-efi-amd64 (2.02~beta2-36ubuntu3.11) ...
Installing for x86_64-efi platform.

Progress: [ 73%] [#####################################################################################################################################.................................................] 
[/FONT]

---

