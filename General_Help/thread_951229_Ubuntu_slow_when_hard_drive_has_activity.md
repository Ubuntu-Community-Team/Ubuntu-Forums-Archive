---
title: "Ubuntu slow when hard drive has activity"
date: 2008-10-17
forum: General Help
---

### Post by milasch on 2008-10-17
Strangely Ubuntu's performance is extremely slow when copying large files from a folder to another or from different partitions.

I did some googling but wasn't able to find any tips. I suspect it's something to do with Nforce chipset (I also suspect linux kernels don't support nforce chipsets for suspend/hibernation).

Also, I want to check if DMA is ON in my /dev/sda, how can I do that?

And finally, what really made me post this message is that when I have 2 virtual machines on, both with 1.5GB memory (I have 3GB physical memory), the system freezes completely, and the hard drive LED stays on for a long time. I've waited for more than 30 minutes, and it did nothing, even the mouse, if I moved it, its cursor wouldn't move at all. I have a 4GB swap disk partition that is never used when I'm not loading virtual machines.

Can someone lead me to some articles or give me some opinion on what can be happening?

```

sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   6268 MB in  2.00 seconds = 3136.02 MB/sec
 Timing buffered disk reads:  234 MB in  3.01 seconds =  77.76 MB/sec

lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:01.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:02.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:03.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
09:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:01.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:02.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:03.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
09:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

cat /etc/hdparm.conf 
## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -s Turn on/off power on in standby mode
#poweron_standby = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode
# --security-freeze Freeze the drive's security status
# security_freeze
# --security-unlock Unlock the drive's security
# security_unlock = PWD
# --security-set-pass Set security password
# security_pass = password
# --security-disable Disable drive locking
# security_disable
# --user-master Select password to use
# user-master = u
# --security-mode Set the security mode
# security_mode = h

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

```

---

### Post by milasch on 2008-10-17
```

sudo hdparm -i /dev/sda

/dev/sda:

 Model=ST3500830AS                             , FwRev=3.AAE   , SerialNo=            6QG0FQR2
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?1?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```

According to this command, udma6 is enabled, so I guess I can discard the possibility of Ultra DMA mode being off.

Anyone?

---

### Post by MaxIBoy on 2008-10-17
The reply is quite simple. ANY operating system slows down during hard drive activity, because hard drives are MUCH slower than memory, by a factor of thousands..

Running two seperate machines with 1.5 gigs of RAM devoted to each means that a LOT of stuff will have to use swap for ALL their memory, and since the swap partition is on the hard drive... I think you're probably seeing the picture.

Don't run VMs you don't have the RAM for.

---

### Post by milasch on 2008-10-18
> **MaxIBoy said:**
> The reply is quite simple. ANY operating system slows down during hard drive activity, because hard drives are MUCH slower than memory, by a factor of thousands..

Running two seperate machines with 1.5 gigs of RAM devoted to each means that a LOT of stuff will have to use swap for ALL their memory, and since the swap partition is on the hard drive... I think you're probably seeing the picture.

Don't run VMs you don't have the RAM for.

I understand what you are saying. But try copying a 5GB file from a folder to another with Ubuntu and open firefox or other programs like OO Writer, and then boot a M$ XP or Vista, do the same.

In my case, Ubuntu almost freezes, even the mouse cursor gets very laggy. This doesn't happen with Windows, looks like it is managing the disk activity in a better way. And I believe firing up 2 VMs with all the memory you have, I would experience a LOT worse performance, BUT not a total freeze due to what I suspect to be a lack of management of disk activity between the 2 processes and swap memory. I waited 1 hour and half and finally could open a terminal window so I could kill Virtual Box. This is ridiculous.

---

### Post by OzzyFrank on 2009-08-10
I'm having similar issues with my 4Gb Swap - which was rarely ever used at all - now being used 100% after browsing a few web pages!!! It slows the system down gradually till I cannot even move my mouse. Getting the terminal up can take MANY minutes... even doing a Ctrl+Alt+F4 takes about 5 mins before anything happens!

---

### Post by motyR on 2009-08-10
Hi,
try changing the cpu scheduler to noop by adding "elevator=noop" to the kernel opions, something like that:
"kernel /boot/vmlinuz-2.6.31-020631rc4-generic root=UUID=92d45c9a-c3eb-4a0f-b534-d71b3266f6bd ro quiet splash elevator=noop"

hope it helps :)

EDIT: @OzzyFrank by any chance do u have intel driver and compiz enabled?

---

### Post by humphreybc on 2009-09-08
I seem to get this problem too with large file transfers, although not to the extent where my cursor lags.

The reason why your computer stops working when you run two virtual terminals with 1.5GB each is simple.

1.5 + 1.5 = 3GB. Your computer has 3GB of RAM, but really, only about 2.9GB. So for a start, the virtual computers are requesting MORE ram than you physically have. 
And remember Ubuntu ITSELF requires 700mb or so of RAM to run on idle, so basically the virtual computers use up all of your physical ram plus some more, and then your host system, Ubuntu, is left to run entirely off swap (hard drive) memory - which is thousands of times slower! This also explains the HDD activity light.

---

### Post by radarlog on 2010-01-31
I have the same problem

---

### Post by charithjperera on 2010-04-10
Same here, I get this problem when transferring large files between partitions, to this machine via SSH or when formatting drives.

So I take it that this happens whenever there is high disk activity.

Any help would be much appreciated.

Thanks

---

### Post by xenosaga456 on 2010-07-15
hey i have this issue but mine happens at anytime i have 4GB of RAM and 3 GhZ AMD 64bit....

but my issue is that it dose it when im not evin on it just at random times???
it will start to hang then it just locks up and i cant do anything?? i have 500GB HDD this should not be a problem i never had this mutch truble with 8.04 on this computer but now this issue is cousing me to loose data that im ether downloading or im doing school work for collage and it just lokes up i wated for 2 hours and it was still locked i had to do a force power off because i thought it was going to catch on fire my CPU was 162F like super hot?



[[IMG]http://brainstorm.ubuntu.com/idea/22551/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22551/)

---

### Post by disciple3d on 2011-05-26
I also have this problem on Ubuntu 10.10.  I have tried lots of things - first of all I thought it was btrfs, so I reinstalled to ext4.  Didn't help.  Then  thought it was the encrypted home partition, so removed that.  Also didn't help.  Finally I found a bug report about an I/O scheduler bug:


I checked the I/O scheduler, and changed to 'deadline' with these commands:

```
cat /sys/block/sda/queue/scheduler
```

(Current shceduler is shown in square brackets):

```
echo "deadline" > /sys/block/sda/queue/scheduler
```

I then put these in /etc/rc.local to keep the setting on reboot:




This made a big difference, it is behaving less slowly, but I still seem to be getting slow downs sometimes, which are so bad that the mouse pointer becomes stuck.  On looking at atop - the disk access is at 100% - but I am not doing anything particularly disk intensive - sometimes it says things like init is using 55% disk time..

```
PRC | sys   2.98s | user   2.98s | #proc    345 | #zombie    0 | #exit      0 |
CPU | sys     28% | user     27% | irq       0% | idle    730% | wait     16% |
cpu | sys      9% | user     10% | irq       0% | idle     80% | cpu001 w  1% |
cpu | sys      9% | user      4% | irq       0% | idle     86% | cpu000 w  0% |
cpu | sys      5% | user      4% | irq       0% | idle     77% | cpu005 w 13% |
cpu | sys      1% | user      0% | irq       0% | idle     99% | cpu003 w  0% |
cpu | sys      1% | user      3% | irq       0% | idle     96% | cpu002 w  0% |
cpu | sys      1% | user      1% | irq       0% | idle     99% | cpu006 w  0% |
cpu | sys      1% | user      2% | irq       0% | idle     96% | cpu004 w  1% |
cpu | sys      0% | user      2% | irq       0% | idle     98% | cpu007 w  0% |
CPL | avg1   0.42 | avg5    0.79 | avg15   1.15 | csw   284916 | intr    8410 |
MEM | tot    3.9G | free  163.2M | cache 288.2M | buff   16.7M | slab  128.8M |
SWP | tot    4.9G | free    4.6G |              | vmcom   6.2G | vmlim   6.8G |
PAG | scan      0 | stall      0 |              | swin       5 | swout      0 |
DSK |         sda | busy     16% | read      16 | write     39 | avio   30 ms |
NET | transport   | tcpi      17 | tcpo      13 | udpi       0 | udpo       2 |
NET | network     | ipi       17 | ipo       15 | ipfrw      0 | deliv     17 |
NET | eth0     0% | pcki      13 | pcko      11 | si    1 Kbps | so    0 Kbps |
NET | lo     ---- | pcki       4 | pcko       4 | si    0 Kbps | so    0 Kbps |

  PID     RDDSK    WRDSK  WRDSK_CANCEL                       DSK CMD     1/5   
14754      460K       0K            0K                       52% gedit
 1049        0K     140K            0K                       16% jbd2/sda7-8
 5532        0K     112K            0K                       13% mysqld.bin
 7120       88K       0K            0K                       10% chrome

```

The well known disk intensive gedit process... 

I am running a Core i7 with 4GB RAM.  It ought to be powerful enough to respond, and the scheduler ought to be doing something to prevent a I/O bound process from slowing down CPU intensive activities, especially on a multi-core machine. 

So I had a look into my hard disk.  I am using a WD20EARS.  I found this:

[http://wdc.custhelp.com/app/answers/detail/a_id/5357](http://wdc.custhelp.com/app/answers/detail/a_id/5357)

When running smartctl --all /dev/sda I see that my load count was over 161000.  Not good.

Also see Flain's post here:

[http://forums.whirlpool.net.au/archive/1462212](http://forums.whirlpool.net.au/archive/1462212)

Basically, I have tried to jumper down the drive to SATA 1.5 as he suggests, and follow the instructions on reducing logging syncs as per the WD instructions.  We shall see what happens...

---

