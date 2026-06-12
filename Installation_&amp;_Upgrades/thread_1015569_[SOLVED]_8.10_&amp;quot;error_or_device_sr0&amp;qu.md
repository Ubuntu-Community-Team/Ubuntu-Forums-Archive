---
title: "[SOLVED] 8.10 &amp;quot;error or device sr0&amp;quot; and other install errors."
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by slinkey1981 on 2008-12-18
I used deluge to download the iso and ran it through md5sum. The sum from my dowload matched the one listed on the website. 

While installing, it gets to the loading screen, and then falls on it's face.

I get the following error

```
I/O error on device sr0, sector 128.
Buffer I/O error on device sr0, logical block 16
```

and it goes on and on and on, and then drops me to a shell....

[SIZE="4"][FONT="Arial Black"]EDIT: My problem was that I had my hard drive and cdrom on the same IDE cable and both of them set to cable select.

This wasn't a problem in Hardy, but Intrepid didn't like it.

After switching the jumpers to slave and master, it all works fine.[/FONT][/SIZE]

Edit: I just read where someone said to just type "return" and that gives me the following.
```

cp: cannot create '/root/var/log/': No such file or directory
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directoy
mount: mounting /sys on /root/sys failed: No such file or directoy
mount: mounting /proc on /root/proc failed: No such file or directoy
target filesystem doesn't have /sbin/init
no init found. Try passing init= bootarg
```

1. What the holy fricken heck does that error mean?
2. How can I fix this so I can install 8.10?

Thanks a lot everyone!

My problem was that I had my hard drive and cdrom on the same IDE cable and both of them set to cable select.

This wasn't a problem in Hardy, but Intrepid didn't like it.

After switching the jumpers to slave and master, it all works fine.

---

### Post by Partyboi2 on 2008-12-18
Did you check the cd for defects after you burn't it? Also best to burn at x4 or less if you have not already done so to avoid possible data corruption.

---

### Post by slinkey1981 on 2008-12-18
> **Partyboi2 said:**
> Did you check the cd for defects after you burn't it? Also best to burn at x4 or less if you have not already done so to avoid possible data corruption.

Thank you for your response.

I had Ubuntu 8.04 burn the iso and check the disk when it was finished. I've burned at 4x and then at 2x

---

### Post by Partyboi2 on 2008-12-18
If you motherboard supports [FONT=Arial]UDMA2 try changing your cdrom from auto to [/FONT][FONT=Arial]UDMA2 in the bios.
Another thing you could try if you are using a desktop  is if you have a spare cdrom around try changing it over. Otherwise maybe someone else might know.
[/FONT]

---

### Post by slinkey1981 on 2008-12-19
> **Partyboi2 said:**
> If you motherboard supports [FONT=Arial]UDMA2 try changing your cdrom from auto to [/FONT][FONT=Arial]UDMA2 in the bios.
Another thing you could try if you are using a desktop  is if you have a spare cdrom around try changing it over. Otherwise maybe someone else might know.
[/FONT]

I actually have tried 3 separate drives, a Sony DVD, panasonic cd, and a Sony D/L Writer... nothing changes.

I have tried the Live Cd in a (very) old Dell Latitude laptop, and it seems to work, it is very slow, but it works, so I can rule out it being a damaged/corrupt disk image....

Seriously, if anyone had ANY ideas, throw em out there, and I'll give it a try... I don't care how much you think it might now work (within reason, don't say "reboot" cause that's just silly..............       and I've tried it.)

And just to be a pain in my own a$$
```

shifty-desktop            
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: MS-6540
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       slot: &#65533;PRIMARY IDE
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (07/09/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.53GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.3
          serial: 0000-0F33-0000-0000-0000-0000
          slot: Socket 478
          size: 2533MHz
          capacity: 4GHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts sync_rdtsc pni monitor ds_cpl cid
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
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
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128 module=pata_sis
           *-disk:0
                description: ATA Disk
                product: WDC WD80EB-28CGH
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 24.8
                serial: WD-WMA9NA098696
                size: 7633MiB (8004MB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000d290f
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 0f34d2ec-159d-4e1b-83bd-02378fb43067
                   size: 7632MiB
                   capacity: 7632MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-17 19:09:10 filesystem=ext3 modified=2008-12-18 23:17:26 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-12-18 22:56:10 state=mounted
           *-disk:1
                description: ATA Disk
                product: WDC WD800JB-00JJ
                vendor: Western Digital
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 05.0
                serial: WD-WCAM9R909539
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=47057d04
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 5460c443-bc46-cd42-9246-e921ea826c7a
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-04-26 10:46:02 filesystem=ntfs state=clean
           *-disk:2
                description: ATA Disk
                product: WDC WD400EB-00JE
                vendor: Western Digital
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/sdc
                version: 13.0
                serial: WD-WCAJC1491730
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a20ca20c
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdc1
                   version: 1.0
                   serial: ef1a4910-1f45-4d95-98a1-b476abfa16f6
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-01 14:17:09 filesystem=ext3 modified=2008-12-18 13:47:39 mounted=2008-12-18 08:43:43 state=clean
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW DRU-830A
                vendor: SONY
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SS25
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-network
             description: Ethernet interface
             product: NC100 Network Everywhere Fast Ethernet 10/100
             vendor: ADMtek
             physical id: 6
             bus info: pci@0000:00:06.0
             logical name: eth0
             version: 11
             serial: 
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.0.10 latency=32 maxlatency=128 mingnt=64 module=tulip multicast=yes
        *-display
             description: VGA compatible controller
             product: NV44A [GeForce 6200]
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: driver=nvidia latency=32 maxlatency=1 mingnt=5 module=nvidia
```

---

### Post by Nandro3 on 2008-12-19
I am having the same issue, and it does this with fedora as well.  I had to reinstall vista as it wont even allow me to run the live version either.  I hope someone can point us in the right direction.  If I happen to find an answer elswhere I will post it for you.

---

### Post by slinkey1981 on 2008-12-19
> **Nandro3 said:**
> I am having the same issue, and it does this with fedora as well.  I had to reinstall vista as it wont even allow me to run the live version either.  I hope someone can point us in the right direction.  If I happen to find an answer elswhere I will post it for you.

Yeah, last night I tried the latest Fedora, Arch, and Mint builds, and it just keeps doing this... I am burning off cds for Mandriva and OpenSUSE to see if either of those work.

---

### Post by Nandro3 on 2008-12-19
I highly doubt they will seeing the others don't, but let me know if one of them does please.  I was really hoping someone here would be able to help with this issue and seeing as mine is identical I see no reason to start a new thread.  I will likewise let you know if I have any luck.

---

### Post by thinkinhurtz on 2008-12-24
Same Problem Here. Running M3A78T Asus board. AMD2. Ubuntu 8.10. 
Getting "Buffer I/O on device sr0" Errors when trying to install from the live CD. Any Help?

---

### Post by RobbyV on 2008-12-24
Hello People,


I wanted to give a go @ Linux so I tried downloading and installing Ubuntu.
Got similar probs to the other folks here. Tried installing Ubuntu & Xubuntu (8.10 & 8.04.1).
Bizarre thing is that there always seems to be an error on the disk even though the checksums checks out to be good, burned them on different speeds (even @ 1x on a different pc - zzzzzz) and the integrety check @ boot still shows errors on the disk (3 to be exact). Downloaded the images from the mirror in The Netherlands, Europe, even tried Torrent-version. Already used up 7 discs (it's not the cost, but it's becoming annoying).

I'm really lost here. Anyone any ideas? Really want to try out Linux... I will have a go with OpenSuse now.

---

### Post by Partyboi2 on 2008-12-24
> **RobbyV said:**
> Hello People,


I wanted to give a go @ Linux so I tried downloading and installing Ubuntu.
Got similar probs to the other folks here. Tried installing Ubuntu & Xubuntu (8.10 & 8.04.1).
Bizarre thing is that there always seems to be an error on the disk even though the checksums checks out to be good, burned them on different speeds (even @ 1x on a different pc - zzzzzz) and the integrety check @ boot still shows errors on the disk (3 to be exact). Downloaded the images from the mirror in The Netherlands, Europe, even tried Torrent-version. Already used up 7 discs (it's not the cost, but it's becoming annoying).

I'm really lost here. Anyone any ideas? Really want to try out Linux... I will have a go with OpenSuse now.
Try using a different burn program like [[COLOR=Blue]imgburn[/COLOR]]("http://www.imgburn.com/") and maybe try different brand of cds/dvds.

---

### Post by RobbyV on 2008-12-24
I've already used Nero, PowerISO, InfraRecorder, ...

---

### Post by Nandro3 on 2008-12-24
I have searched all over and only found others with the same issue with no solution.  I am on hold with my linux install till I can find something.  Whats odd is vista installs no problem on the same setup with a burned disk.

---

### Post by bimmer jake on 2008-12-24
Same error word for word on my laptop.  I've had 8.04 on the same laptop in the past so it's not a problem with the hardware.

---

### Post by Nandro3 on 2008-12-24
Is it possible to reinstall 8.03?  Also, with 8.03 can you upgrade to 8.1?

---

### Post by bimmer jake on 2008-12-24
i'm going to give it a try and i'll post the results.  i have the same disk i originally used to install 8.04 on the laptop so i should get the same results.

I'll post my finding as soon as i can.  might be a delay due to Christmas stuff.

---

### Post by Nandro3 on 2008-12-24
Deffinitly dont forget us!  J/K, would just like to know so I can get this crappy M$ off my rig.

---

### Post by BatsotO on 2008-12-24
I had this too, try different cd-rom, different cd, still can't get to live desktop or installation menu. I remember when i replacing ram i can get to installation, but i dont remember if it sr device error or squashfs error. Just give it a shot.

---

### Post by Nandro3 on 2008-12-24
We pretty much tried a bunch of different cd/dvd's as well as different distro's.  I have tried using different HD's as well with no luck.  It has to be something OS related if it works with 8.03 and not 8.10  I cant see it any other way if that's the case.  Just waiting on him to try it unless someone else has had success with a different way.

---

### Post by kelean on 2008-12-25
Are you burning the cd at the slowest speed.  I had that problem and another thing I found out was I had a bad batch of cdrw disks.

---

### Post by slinkey1981 on 2008-12-25
I have an old laptop here, it's a Dell Latitude, runs the live CDs no problem, so this is a problem that has begun with the newest version of SOMETHING in Linux. It doesn't matter what flavor it is. I've fallen back to Ubuntu 8.04 and it installs perfectly fine.

---

### Post by Nandro3 on 2008-12-25
Yes, unless there bad to where speed doesn't matter.  But I have other cd's out of the batch that do work.

---

### Post by rich86 on 2008-12-26
Hi,
I had lots of errors trying to make a live cd and install 8.10 i ended up using unetbootln in the end. It installs to the local disk or to a usb stick, creating a liveUSB. If the liveUSB doesn't work or you don't have a spare one you can even do a net-install.
It installs some things to the boot loader(win or linux) so when you re-boot you get he option of installing over the internet. It took a few hours on my 8Mbit connection so not recommended for anyone with slow inet.

Oh the link is: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

hope that helps someone in installing,

---

### Post by alexinspain on 2008-12-26
Me Too !  I had V7.4 and it worked ok but cant get 8.10 to install and only get ERROR:3  or ERROR 16 when its almost finished loading and it totaly mashed my XP too , so had to do a complete re-install of xp ! the live cd works a treat but can't install with at all ! The only reasn i was up gading from 7/4 to 8.10 was 7.4 didn't like my laptop but was fine on my desktop !  Think i'll get another drive just for Ubuntu and keep trying !!!

---

### Post by kelean on 2008-12-26
Another thought I had.  This has happened to me before.  Is the disk clean.  Free of dust, finger prints, and smudges?  I know it sounds trivial but something to rule out.

Kelean

---

### Post by Nandro3 on 2008-12-26
I cant speak for the others, but I have tried 4 different hard drives, 1 of them was new and all of them work perfectly with vi$ta.  I will try net install of Ubuntu.  I am however surprised that this hasn't got more attention seeing that if I search for it many have it and no one seems to know why.  

Thanks for the link, I shouldn't have an issue with speed.  I have a 15M connection and it usually goes pretty fast.  In any case, I will let it do most of the DL overnight.

---

### Post by bimmer jake on 2008-12-26
> **Nandro3 said:**
> Deffinitly dont forget us!  J/K, would just like to know so I can get this crappy M$ off my rig.

After checking many sources i concluded that my burn was indeed bad, even though it really didn't seem like it at the time.

i just finished installing intrepid on the same laptop but i burned the cd with different settings.

I used K3b this time.  i also changed the image type to "iso" instead of "auto", the writing mode to "DAO", and the write speed to 8x (the slowest k3b will do as far as i know).

everything is working great now and intrepid has native support for my wireless (realtek 8187b) !:)

Hopefully this will help.

---

### Post by slinkey1981 on 2009-01-09
My problem was that I had my hard drive and cdrom on the same IDE cable and both of them set to cable select.

This wasn't a problem in Hardy, but Intrepid didn't like it.

After switching the jumpers to slave and master, it all works fine with every distro I downloaded.

I have since installed Intrepid and added the Ubuntu Studio Theme.

I know that this may not be everyone's problem, but since it is mine, I'm going to edit my first post with my fix and mark it solved.

---

### Post by hdjunkie on 2009-02-23
I'm having the same problems.  I installed 8.10 which gave me tons of i/o errors, and broke my win7 installation.
So, I decided to install ubuntu on the entire disk, boot from livecd to create partition, and install win7 that way...but now when I try to boot from live cd I get more of the i/o errors, and it quits to the shell at the same sector every time.
I'm burning my 3rd disk now at 2x speed to see if that helps (I'm not optomistic).

I have no idea what the above poster is trying to say, and I have no idea how I'd fix that w/my laptop.

Am I correct in assuming the 8.04 disk won't have these problems?

---

### Post by hdjunkie on 2009-02-23
Well, I used imgburn instead of win7's built in burner, and switched the burn speed to 2x and I haven't seen any of the errors since.  How odd.
Now, if I can get easybcd working I'll be happy

---

### Post by ludjer on 2009-05-10
hello i am trying to install linux onto my laptop, and it is giving me this error i dont really understand what i am ment to do

thanks
oh ye im using the 
ubuntu-9.04-desktop-i386.iso
really want to use linux instead of M$

---

### Post by Krazzy on 2010-10-01
Hello, I had the same problem and I Disabled "AHCI" mode in Bios and everything ran and worked fine.

Hope this helps someone,
Krazzy.

---

### Post by oviliz on 2011-03-05
> **Krazzy said:**
> Hello, I had the same problem and I Disabled "AHCI" mode in Bios and everything ran and worked fine.

Hope this helps someone,
Krazzy.
Hi,
ok, it's a solution. But it is not the solution! :(

---

### Post by tfaruq on 2011-03-08
Hello slinkey,
Thank you so much! I had the same problem, i was installing it in my old PC when the problem occurred.

Well, successfully run ubuntu but my cdrom is not detected: Secondary hard disk drive 0 not found. I did what you said, cdrom as slave and HD as mater. But this suddenly happened, even i put the secondary device as Auto.

Im still googling it but appreciate if someone can help.

---

