---
title: "Feisty Fawn on a new HP dv9500t"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by burrodomo on 2007-08-12
Here are my experiences using Feisty Fawn on a new HP Pavilion dv9500t (purchased in early August).  The hardware in these laptops seems to change constantly, and none of the experiences or advice given in the ["official"]("http://ubuntuforums.org/showthread.php?t=431815") dv9000 thread seemed to work for me.  I wanted to collect all of what I've learned in one place, in case there is anyone else out there with the same laptop.  I have an Intel Core2 Duo processor with dual SATA harddrives, an Nvidia GeForce 8400 GS video card, Intel 4965 AGN wireless card, and Intel HDA sound card (Realtek 268 codec).  (I'll include the output of lspci -vvv below, so you can compare exact hardware specs.)

I'm going to write for a user with some experience.  (i.e. I won't list every single command, I expect you to know how to change directories, edit files, etc.)  If you're a complete newcomer to Linux then I don't think this is the laptop for you.

**Booting the LiveCd**

Not a promising start, but the LiveCD would not even boot for me.  I learned the following from [http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control]("http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control") 

At the LiveCD menu, select the "Safe Graphics" option, and press F6 to edit the command line.  Add "break=top" at the end.  This will dump you to a BusyBox prompt early in the boot process (I got dumped here anyway, but the break option is a way to force it.)  Now type "modprobe piix" and then "exit" and the LiveCD should finish booting.  (Note that it will only boot in safe graphics mode - the 8400 GS is not supported by the nv drivers included with Ubuntu.

Quoting the above mentioned post:
"If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shiny Ubuntu system!"

**Nvidia 8400 GS Video Card**

The drivers in the Ubuntu repository for Fiesty are not new enough to support the 8400 GS.  Download envy from [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") .

Install the .deb: sudo dpkg -i envy*.deb

This will probably fail with messages about missing dependencies.  Simply type:

sudo apt-get -f install

... and apt will install the necessaries packages (and the envy .deb).

Run "sudo envy -t" and choose option "1" to install the nvidia drivers.  It will automatically recognize your card and download the latest drivers directly from nvidia (not the Ubuntu repository).  Let it automatically configure your xorg.conf.  Now you should be good to go.

**Intel 4965 AGN Wireless**

Intel 4965 Wireless:

There are drivers for Linux directly from Intel, but I decided to go with ndiswrapper because it didn't require installing the Gutsy kernel.

I followed the instructions at: [https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty]("http://https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty")

Download Intel's XP drivers from: [http://downloadcenter.intel.com/scripts-df-external/Detail_Desc.aspx?agr=N&ProductID=2259&DwnldID=13000&strOSs=44&OSFullName=Windows*%20XP%20Professional&lang=eng]("http://downloadcenter.intel.com/scripts-df-external/Detail_Desc.aspx?agr=N&ProductID=2259&DwnldID=13000&strOSs=44&OSFullName=Windows*%20XP%20Professional&lang=eng")

Download ndiswrapper 1.43 source from: [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.43.tar.gz]("http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.43.tar.gz")


Steps:

First it is recommended to turn off the wireless card using the hardware switch.

sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo apt-get install build-essential linux-headers-$(uname -r)
Put the downloaded files wherever you'd like them, and untar/unzip both:
tar -xzf ndiswrapper-1.43.tar.gz
unzip V11.1.0.0_XP_DRIVERS.ZIP

cd ndiswrapper-1.43

sudo make uninstall  (this removes the ndiswrapper kernel module that comes with Ubuntu)
make
sudo make install
sudo ndiswrapper -i NETw4x32.INF
ndiswrapper -l  (This should show that the driver is installed)
sudo ndiswrapper -m

sudo modprobe ndiswrapper
Unplug any ethernet cord, and turn the wireless card back on.

If it's working, add ndiswrapper to the list of modules to be started at boot:
echo ' ndiswrapper' | sudo tee -a /etc/modules

**Intel HDA Soundcard (Realtek 268 codec)**

This sound card is too new to be supported by the version of ALSA in the Ubuntu repositories.  I found a bug filed here [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326") requesting support.  If you read through the entire bug you can find instructions, but here's a summary of what I did to get it working:

Dowload ALSA latest version from alsa-project.org. This consists of drivers, libraries, utils, and firmware.  (You don't need tools or any others.)

Get the patches from: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104)
(The two you want will be called realtek10.tar.gz and realtek11.tar.gz)

Extract the ALSA source to a convenient location.

Go to the directory (it will be called this wherever you extract it to) ~/alsa-driver-1.0.14/alsa-kernel/pci/hda

There you will find two files with names identical to the ones in the patches. Replace the old patch_realtek.c with the new one. Same with the hda_proc.c You can do this by simply dragging the new version into the correct folder, and you will be asked if you want to replace the file, which you do.

Once you have patched the ALSA driver, you compile as normal. 

Build them in this order: alsa-driver, alsa-lib, alsa-util and alsa-firmware.

For those of you not familiar with building from source, the incantation is:
./configure && make && sudo make install

A note, I needed to apt-get intall ncurses-dev for utils.

Add the line "options snd-hda-intel model=toshiba" to /etc/modprobe.d/alsa-base

**Conclusion**

Those are the main components that I struggled to get working.  Your own mileage may vary.  I haven't even tried secondary things like microphone, webcam or card reader (though I know some people with other dv9000 models have gotten them to work in at least limited circumstances).

**lspci**

00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0427 (rev a1)
02:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

Verbose output for video and sound cards:

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0427 (rev a1) (prog-if 00 [VGA])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at 2000 [size=128]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at f8500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

---

### Post by EXCiD3 on 2007-08-18
Thanks for some of that info on the dv9500. I needed some more info on that series as they are quite new still. Do you mind if I add any of this information to my Howto? Here's a link: [http://ubuntuforums.org/showthread.php?t=512059]("http://ubuntuforums.org/showthread.php?t=512059")

---

### Post by andsmi on 2007-08-20
I've got this problem when I'm trying to build the alsa driver. 
This is what the terminal shows:
andy@zepto-laptop:~/alsa/alsa-driver-1.0.9rc4a$ make
make[1]: Entering directory `/home/andy/alsa/alsa-driver-1.0.9rc4a/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/home/andy/alsa/alsa-driver-1.0.9rc4a/include  -I/lib/modules/2.6.20-16-generic/build/include -I/lib/modules/2.6.20-16-generic/build/include/asm-i386/mach-default -O2 -mpreferred-stack-boundary=2 -march=i586 -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include -DMODVERSIONS -include /lib/modules/2.6.20-16-generic/build/include/linux/modversions.h  -DKBUILD_BASENAME=hpetimer   -c -o hpetimer.o hpetimer.c
cc1: error: /lib/modules/2.6.20-16-generic/build/include/linux/modversions.h: No such file or directory
In file included from hpetimer.c:22:
/home/andy/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:29:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.20-16-generic/build/include/asm/percpu.h:5,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/processor.h:21,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:9,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.20-16-generic/build/include/asm-generic/percpu.h:8: error: ‘CONFIG_NR_CPUS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.20-16-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:9,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:82: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:82: error: requested alignment is not a constant
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h: In function ‘cpuid_count’:
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:269:46: error: division by zero in #if
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_msecs’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:274: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:274: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:274: error: for each function it appears in.)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:280:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_usecs’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:285: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:293:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘msecs_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:298: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:306:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘usecs_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:311: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘timespec_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:330: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:336: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_timespec’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:349: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘timeval_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:371: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:375: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_timeval’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:387: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_clock_t’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:401: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘clock_t_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:412: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_64_to_clock_t’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:432: error: ‘CONFIG_HZ’ undeclared (first use in this function)
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/rcupdate.h:41,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/pid.h:4,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:72,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.20-16-generic/build/include/linux/mmzone.h: At top level:
/lib/modules/2.6.20-16-generic/build/include/linux/mmzone.h:43: error: requested alignment is not a constant
/lib/modules/2.6.20-16-generic/build/include/linux/mmzone.h:85: error: requested alignment is not a constant
/lib/modules/2.6.20-16-generic/build/include/linux/mmzone.h:282: error: requested alignment is not a constant
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/pid.h:4,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:72,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.20-16-generic/build/include/linux/rcupdate.h:71: error: requested alignment is not a constant
/lib/modules/2.6.20-16-generic/build/include/linux/rcupdate.h:74: error: requested alignment is not a constant
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:21,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /home/andy/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.20-16-generic/build/include/asm/module.h:62:2: error: #error unknown processor family
In file included from /lib/modules/2.6.20-16-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.20-16-generic/build/include/linux/irq.h:172: error: requested alignment is not a constant
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.20-16-generic/build/include/asm/hardirq.h:12: error: requested alignment is not a constant
make[1]: *** [hpetimer.o] Error 1
make[1]: Leaving directory `/home/andy/alsa/alsa-driver-1.0.9rc4a/acore'
make: *** [compile] Error 1

How can I fix this?

---

### Post by burrodomo on 2007-08-21
EXCiD3, please do add to your HOWTO.  I should have cross-posted but didn't take the time.

andsmi, it looks like you may not have the linux kernel headers installed.  The first error in your compile was "cc1: error: /lib/modules/2.6.20-16-generic/build/include/linux/modversions.h: No such file or directory".  I didn't specify, but if you don't install everything in the same order I did you won't have the necessary dependencies installed.  You'll need do:
sudo apt-get install linux-headers-$(uname -r)
If you have already done that, then I'm a bit more stumped.  The file modversions.h is actually in .../include/config, not .../include/linux, so I'm not sure why your configure is looking there.  Are you installing the alsa packages in the order I listed?  And have you rebooted since installing the 2.6.20 kernel?

---

### Post by AlokaParyetra on 2007-08-31
burrodomo,

I stumbled across this thread while searching for solutions to my dv9500t problems.

I just want to say thank you for your explanation on how to get sound to work. I've been racking my brain for over a week now since i got my laptop trying to make it work.

On a side note, does the headphone jack work as well?
And, are you having problems accessing your cdrom drive?
And finally, do programs sometimes run slow? I find that compiz-fusion and avant-window-manager sometimes run with a lag.

Once again, thanks.

---

### Post by burrodomo on 2007-08-31
AlokaParyetra, I'm glad it helped.  

I hadn't actually tried the headphones jacks yet, but I just plugged some in and both left and right work for me (though I don't have fancy enough headphones to do stereo).  At the risk of suggesting the obvious, have you unmuted the headphone in alsamixer or Gnome/KDE mixer?  Before I installed my own alsa I spent a lot of time fiddling with those settings, so I'm not sure what you'd get on a fresh system, but I do know that alsa comes with stuff muted by default.

As for the cdrom, I haven't used it extensively.  I did encounter a system freeze when doing "cat /dev/cdrom" to create an ISO, though, and I recall reading about others' problems with the cdrom.

I haven't yet installed compiz or any accelerated window manager, so I can't speak to those.  

I do know that the suspend/resume is marginal on my system.  I can only suspend once, and when I resume from it then my graphics redraw was really slow (not GL stuff, but regular 2D like redrawing windows).  I haven't had time to investigate that either though.

I'm hoping that many of these issues will be improved when Gutsy is released in October.

---

### Post by niC666 on 2007-09-06
Hi

I have a dv9521ei which i am trying to install feisty on with no luck
I've tried just about all the switches at the kernel boot phase, but still get dumped into a busybox shell.

its an intel core II duo T7200 2GHz based system.

if i turn off quiet and splash in the boot options the last messages i see before the busybox shell are

kjournald starting. commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode

repeated over and over again..

any advice? 
I am busy downloading the alternate cd image in case but its gonna take a while on my connection

thanks
niC

---

### Post by burrodomo on 2007-09-06
niC, it's been awhile now since I did it myself, but I seem to recall similar symptoms when I first tried it out.  Did you try the "modprobe piix" (see first section in the original post) at the busybox prompt?  If so, what is the output?  What happens after loading that module and typing "exit"?

And if your hardware is indeed the same as mine, the alternate cd won't help.  I had the same problem with it as with the standard livecd.  So try the modprobe piix with the regular cd and let me know the results.

---

### Post by niC666 on 2007-09-07
Hi buro..

I got a bit lost between all the posts i was reading and completely forgot about the piix thing, in any event i found someone who had an alternate install disc and the install worked, am now working on getting all the rest of the bits to work, will let you know how it goes

thanks
nic

---

### Post by andsmi on 2007-09-16
> **burrodomo said:**
> EXCiD3, please do add to your HOWTO.  I should have cross-posted but didn't take the time.

andsmi, it looks like you may not have the linux kernel headers installed.  The first error in your compile was "cc1: error: /lib/modules/2.6.20-16-generic/build/include/linux/modversions.h: No such file or directory".  I didn't specify, but if you don't install everything in the same order I did you won't have the necessary dependencies installed.  You'll need do:
sudo apt-get install linux-headers-$(uname -r)
If you have already done that, then I'm a bit more stumped.  The file modversions.h is actually in .../include/config, not .../include/linux, so I'm not sure why your configure is looking there.  Are you installing the alsa packages in the order I listed?  And have you rebooted since installing the 2.6.20 kernel?

uhm... is it possible to get a better explanation? I'm a noob in ubuntu... I did exactly what you said in your first post. Managed to get everything else to work... but when I was trying to mount... the problems started. How do I install headers in the linux kernel?

---

### Post by EXCiD3 on 2007-09-16
```
 sudo apt-get install linux-headers-$(uname -r)
``` will install headers for your kernel

---

### Post by Splinter65 on 2007-10-17
I have a DV9504TX and like burrodomo had no luck with the other thread. Everything here that I needed worked for me. Haven't tried the fingerprint reader yet. Thanks for the help.

---

### Post by Splinter65 on 2007-10-20
Well, managed to destroy my Feisty install with the Gutsy Alternate CD.(own fault) So now I have a clean install of Gutsy. No issue with video driver this time default driver was ok and gutsy prompts to install nvidia driver if you want to add the animations to the desktop.

Sound didn't work. Used the Alsa drivers again. These have changed version and I didn't need to use the bug patches (wouldn't work with these). Did need to 'apt-get install build-essential' first before they would compile.

Wireless just worked. Camera worked, Touchpad worked.:)

---

### Post by Jeff_From_VA on 2007-12-08
I am working on a HP dv9500t for my wife.

I tried this guide before several times and failed with the wireless and ndiswrapper. 

I am not 100% sure, but I think the failure was either, latest driver from intel, or the updates that feisty did, or possibly using the latest ndiswrapper.  I know that's a lot of variables and not helpful, but I wanted to try to share what I did to help those in the future.

I was doing the following, install feisty, let it get it's updates over the wire, then following as the guide said but using the latest from ndiswrapper, and using the link this guide provides which gave me a different set of wireless drivers then the original poster of this thread had used, as they are newer now. 

This morning I decided to try to replicate as close as I could what this guide did, at the time it did it.

This time I searched for the same file name for the drivers, found them via google, and used those instead of the current driver from intel. I also used the older version of ndiswrapper that the guide used.  I did not allow feisty to update before doing this either, I built with what came on the cd.  plus  the few packages I had to install to build with.

For the first time I have gotten wireless working under feisty.  Even the light turns blue like it should.

I will report back if I have any other issues.  I am just glad to be making some progress, as this has been a very difficult install so far.

---

### Post by Jeff_From_VA on 2007-12-08
Let feisty update, and it broke again. I suspect due to the new kernel in the update.

I re-compiled ndiswrapper with the new kernel sources, and it works so far.  Not as fast as I would hope, but better then the speed I got from gutsy.  I will play and see if things like opendns and getting rid of ipv6 speed it up.

It's looking like this card does not want to play nice with either the latest ndiswrapper, or the latest intel driver.  Using the older ones seems to work for me.  

When I used the latest of both, it would fail when I did "sudo modprobe ndiswrapper"  It would sometimes lock the whole machine, other times would just hang there but the machine was still usable.

---

### Post by Jeff_From_VA on 2007-12-10
Ran out last night and upgraded my tired old 802.11b router, and got a new wrt300n router.  I can connect at N @130mb, and it flies now. I can no longer notice I am wireless, it feels like a wire. I am very pleased!!!

---

### Post by kvalenza on 2008-03-01
I have a problem with my sound card...just like others have been having.  I have a REALTEK sound card, and I am getting no sound, even though it works fine with Windows.  I have looked at various solutions here, and I have found them difficult to understand, and no matter what I have tried, I still can't get any sound.

Can anyone give me step by step instructions in a simple way as to what I should do?:confused:

---

