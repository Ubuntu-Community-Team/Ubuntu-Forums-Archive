---
title: "n00b help"
date: 2008-08-26
forum: General Help
---

### Post by Fauntix on 2008-08-26
I have kubuntu KDE4 and I need some help finding my external hard drive. Its been too long since I used a linux box so I forgot all the commands:lolflag:

---

### Post by Inane_Asylum on 2008-08-26
Is your hard drive not listed in the file manager?

---

### Post by Fauntix on 2008-08-26
i looked in home, network, and the root in my dolphin file thing and i couldnt find it... its a firewire ExHDD if that means anything to you.

---

### Post by Inane_Asylum on 2008-08-26
go to a terminal and post the output of:

```
sudo fdisk -l
```

---

### Post by jerome1232 on 2008-08-26
The output of mount would be helpful too, just to make sure it's not mounted anywhere
```
mount
```

---

### Post by Fauntix on 2008-08-26
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

---

### Post by Fauntix on 2008-08-26
> **jerome1232 said:**
> The output of mount would be helpful too, just to make sure it's not mounted anywhere
```
mount
```

```
fauntix@paso-kun:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

```

---

### Post by jerome1232 on 2008-08-26
> **Fauntix said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

I don't see a second disk, is the firewire even being recognized? The output of lspci ought to tell us.

```
lspci
```

---

### Post by Fauntix on 2008-08-26
> **jerome1232 said:**
> I don't see a second disk, is the firewire even being recognized? The output of lspci ought to tell us.

```
lspci
```

I dont see a firewire pci unless its called something weird and different.

```
fauntix@paso-kun:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

```

like the USB 2 EHCI controller?

---

### Post by jerome1232 on 2008-08-26
> **Fauntix said:**
> I dont see a firewire pci unless its called something weird and different.

```
fauntix@paso-kun:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
[COLOR="Red"]**08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller**[/COLOR]
08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

```

like the USB 2 EHCI controller?

Bold and red is the firewire port looks like it's seen, at this point I'm not sure what to look at next.

---

### Post by Inane_Asylum on 2008-08-26
Is there any other computer you can test the HDD on, just to make sure it's not a problem with the HDD instead of Kubuntu?

---

### Post by Fauntix on 2008-08-26
the HDD is working fine i just cant access it

---

### Post by Inane_Asylum on 2008-08-27
Okay...next thought...do you have any other devices that connect with FireWire?  Mebbe it just doesn't like your HDD?  I know I'm having trouble connecting my digital camera.  Ubuntu apparently just doesn't like it.:confused:

---

### Post by Fauntix on 2008-08-27
no its the only firefire i own.... I really...well i could buy an enclosure USB format for the HDD and change it but since its a wall powered ExHDD I dont know if I can.

---

### Post by Inane_Asylum on 2008-08-27
Try running another distro or two (I know...herasy, right?:p) on liveCD, and see if it's recognized.

---

### Post by bankg3 on 2008-08-27
Does the drive have a valid partition on it?

---

### Post by Fauntix on 2008-08-27
it is just a storage drive... it is an operating ExHDD everything works on windows.

---

### Post by BLTicklemonster on 2008-08-28
Fauntix, I'm not much of a kde user, nor have I ever tried firewire, but this is the only place I have found that appeared to have a resolution to your problem. Sorry it took me so long, and I hope that it helps you. Let us know, and we'll keep looking if not.

> Couldn't mount external hard drive at boot I added my external hard drive to /etc/fstab and from the command line, I could mount it no problem with a mount -a. The fstab entry doesn't have noauto in it but every time I'd boot, the "Mounting external filesystems" line would fail. Turns out the necessary modules aren't installed by the time the boot process tries to mount the drive. The general fix is to a) mount it manually b) do a lsmod and see what modules are used by the device (in my case, sd_mod, ieee1394, scsi_mod and a couple others - I'll check at home tonight) c) add these modules to /etc/modules. Works like a charm.

From:

[http://ubuntuforums.org/showthread.php?t=155459](http://ubuntuforums.org/showthread.php?t=155459)

---

### Post by Fauntix on 2008-08-28
im sorry i need a walk through please use one of my instant messenger to talk me through this.

---

### Post by BLTicklemonster on 2008-08-28
Unfortunately, I think that this is based on the person having the ability to access his external drive, but not having it mount at boot. I think your problem is that you can't get it to show up at all.

I'll keep digging.

In the mean time, with the external drive connected, try installing gparted 

sudo aptitude install gparted

then run it

sudo gparted

In the window that opens, look to the top right, where you see something like /dev/sda1 (partition size GIB), and to the right of that is a drop down menu. Click the triangle, and see if there's anything other than /dev/sda showing up. If so, it's your external drive. If so, it can give you information useful to getting it going. Post results if any...

But it probably won't show up. But this is worth a try anyway.

So it shows up in windows... what format is it? fat32, ntfs? Was it plugged in when you installed kubuntu? Did you do a dual boot, or are you running Ubuntu from within windows?

---

### Post by BLTicklemonster on 2008-08-28
I just found this:

> Why doesn’t the drive power-up when connected to my FireWire port?
Computers (usually older models) with a 4 pin FireWire connection do not provide
power through the port. The standard FireWire port uses 6 pins and does supply power
through the port (Note: a 4 pin FireWire connector is visibly smaller than a 6 pin
connector). If your computer has a 4 pin connection you can supply power to the disk
drive in one of two ways:
    1. Use the USB/PS2/DC Power Cable to supply the necessary power from the
        computer’s PS2 keyboard port or an open USB port.
    2. Use the optional Fortress external power supply.

Could it be that any of this applies in your situation?

---

### Post by Fauntix on 2008-08-29
i used the gparted and found the ExHDD at /dev/sdb1 but i unplugged it (by the data cord) to see if it was looking at the right HDD and apparently it was. So I plugged the data cord back into my computer, hit refresh, and it couldn't see it. I tried waiting and hit refresh and replugged it in multiple times, nothing worked. I tried reloading the gparted. I thought I lost the only glimmer of hope. but then I realized that HDDs hate being unplugged by the data cord so, I made sure the cord was in and turned off the power switch to the ExHDD and turned it back on. My "Recently Plugged Devices" widget popped up saying "Hey I found a HDD want to open it?". So now I can get into my ExHDD no problem... Now I am going to shut everything down and reboot, to see if I can access it again. You know, to make sure its permently fixed. I will post again with the results. Oh by the way, I am a Math teacher not and english teacher so, I know I can't spell right.

---

### Post by Fauntix on 2008-08-29
Okay everything is working fine... Now I just have to remember to start my ExHDD after the computer has fully booted up.

Now I simple problem... the Taskbar where all the windows are shown is gone and how do I get java so I can watch radar ([www.noaa.gov](www.noaa.gov)) and youtube?

---

### Post by BLTicklemonster on 2008-08-29
Excellent! It's great to see a problem like this worked out.

As far as flash is concerned, if you have a 32 bit system, try this:

[http://ubuntuforums.org/showthread.php?t=642816](http://ubuntuforums.org/showthread.php?t=642816)

If you have a 64 bit system, try this:

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

I say try because flash SUX.

I'm guessing you are in the States?

If so, here's a couple of radar links you should like:

[http://radar.weather.gov/Conus/full_loop.php](http://radar.weather.gov/Conus/full_loop.php)

[http://media.myfoxtampabay.com/myfoxhurricane/](http://media.myfoxtampabay.com/myfoxhurricane/)

---

### Post by jerome1232 on 2008-08-29
It's easiest to just install it from the repos, haven't had a problem with 32 or 64 bit that way.

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Fauntix on 2008-08-30
ok the gparted wont find it anymore.... i have ubuntu 8.0.4 now

---

### Post by Fauntix on 2008-08-30
never mind i updated ubuntu and now it auto runs

---

### Post by BLTicklemonster on 2008-08-30
Sweet. Hang in there, you're doing well with your attitude and the effort you are putting in to using Ubuntu!

---

### Post by Fauntix on 2008-08-30
well i bought the Ubuntu Unleashed 2008 Edition that came with a CD... IT SO AWESOME!!!! I will soon be a true part of the community

---

