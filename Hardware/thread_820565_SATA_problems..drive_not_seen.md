---
title: "SATA problems..drive not seen"
date: 2008-06-06
forum: Hardware
---

### Post by drifter0000 on 2008-06-06
This is a little complicated.
onboard Via ata and achi/Sata 4 port controller

Hard drive western digital ata 80gb...any type of linux install no problem.
Everything works great.
Installed my first SATA HDD...Seagate Barracuda 500gb sata 3.0

Bios:  ata 80gb 1st primary, pioneer cd/dvd burner 2nd primary, Seagate Sata 3rd primary
I set seagate as SATA in Bios and leave all other settings automatic

I want to do fresh install of hardy 8.04 to make sure it loads newer SATA driver and I get full benefit from my new sata drive.

Erase ata 80gb drive with Zeros after deleting all partions.  To save time i loaded old dvd image of win xp pro sp3 onto new sata drive.  Boots and runs fine...device manager in windows listed sata drive only as udma6.

Did some drive testing and achieved 82mb throughput...after googling a lot it seemed like this is what I could expect from SATA drive in windows, so im satisfied.

Try netbootin install of Hardy 8.04 64 bit...dosnt see my SATA drive
Try netbootin install of Mandriva 2008...during install it stops to insall Via ACHI/SATA 4 port controller...thats correct driver for my motherboard..after this driver install it informs me that I have no hdd installed
Try live cd open suse 11rc1...says I have no hdd installed
Try dvd install open suse 11rc1....says no hadd installed
Try Mint 4.0 live cd install...installs and runs perfectly

Do a lot of research....Then change Bios southbridge from SATA to ACHI with SATA installed from rom

Try all installs except mint (at this point mint is still installed) still say i dont have a SATA hdd

Remove ata 80gb from system...now bios lists SATA drive as 1st primary

Remove Mint from SATA drive....Try all install again....all say i do not have a hdd installed.

Try Mint 4.0 live CD install and works perfectly...something must have changed after I changed bios to ACHI enable rom SATA because now Mint boots up very quickly

I check Mint hardware listings for driver it used for my SATA.
It shows correct drivers and all hardware correctly except it does not list any hard drive at all....it does show the correct Via ACHI/SATA 4 port driver installed but does not list a device.

Gparted in Mint correctly displays model number for SATA drive and lets me preform all operations on SATA drive....Mint runs great, no problems.

Any help would be appreciated....thanks for your patience

Adding pci=nomsi to the boot options under install mode from Hardy 8.04 CD allowed the installer to recognize my SATA drive right away
Installed with no problems.....Boote from SATA no problems....Hardy running great....even on a SEAGATE SATA drive.

Thanks for everyones help

---

### Post by johnlvs2run on 2008-06-07
I set up my biostar system on the motherboard box this morning and am very impressed with the biostar.

Both PCLinux and Ubuntu run well as liveCD, but neither of them see or install on the sata Seagate harddrive.  Likewise, GParted does not see the Seagate harddrive.

Unfortunately, small print on the Seagate says to format with windows 2000 or xp.  I ran emachines xp disks all the way through, and still the Seagate was invisible to PCLinux, GParted, and Ubuntu.  Apparently the Seagate only works when formatted first by windows, if at all.  Otherwise, if anyone knows how to get the Seagate to accept installation of Linux, let me know.

---

### Post by drifter0000 on 2008-06-07
Thanks for your post.  The anserw is clearly in Mint 4.0 live cd install because it works on the seagate SATA everytime.

I just dont know enough about it to try and figure it out.

---

### Post by johnlvs2run on 2008-06-07
Are you running from the liveCD, or installing the program on the harddrive?

Mine run the liveCD, but they don't install on the seagate harddrive.

---

### Post by drifter0000 on 2008-06-07
The install that works is Mint 4.0.  This is a live cd that I use to install mint or to work on partions with.  It finds my SATA drive everytime, even when I have my ata 133 drive in the system.  Mint install asks me which drive I want to install to..It always finds my SATA as a SCSI but I have done some research and it seems that a lot of linux installers do that with SATA.  The other installs that didnt work were just as in my post, unetbootin or live CD or DVD install.  Since the post I have put my ata drive back in and unplugged my SATA just to test system.  I used Burned DVD to install open suse 11rc1, no problems, I used it for a while last night to make sure install was ok.  This morning I did unetbootin install of Hardy 8.04 64 bit from the suse install and I am using it now.  Its my OS of choice right now.  This all began because i wanted to put hardy on a bigger and faster drive.  

So their is something in the Mint 4.0 live cd that can see the SATA that all the other listed installs lack.  And this is not especially a hdd driver problem, because when I used unetbootin to install Mandriva, the install halted to install my via SATA 4 port drivers.  I checked the driver number and its the same as listed in my motherboard book.  After it installed the CORRECT driver for my system it informed me that I had no hdd installed.  So it is something else on the Mint live CD that I dont know enough about to investigate, but it works on my Seagate SATA everytime

---

### Post by johnlvs2run on 2008-06-07
So you've found that none of the other linux distros work with sata?

In that case, if I exchange this HD for a western digital, then it still won't allow linux to install.

Any suggestions for getting either Ubuntu or PCLinux on the harddrive, without using msw?

---

### Post by kyphi on 2008-06-07
While I do not have a solution for you, I would like to mention that I have only SATA drives on my machine.  Two SATA II hard drives by Western Digital and two SATA optical drives (CD/DVD burners).
All function perfectly in Hardy Heron and have done so since Dapper Drake (2006).

Your solution might lie with the SATA controllers on your motherboard or the mountpoint of your drives.  What is the readout for your drives in the BIOS?

I would advise you not to mix SATA with PATA drives nor older and slower SATA with faster SATA - keep all hard drives to the same type.

---

### Post by johnlvs2run on 2008-06-07
> **kyphi said:**
> While I do not have a solution for you, I would like to mention that I have only SATA drives on my machine.  Two SATA II hard drives by Western Digital and two SATA optical drives (CD/DVD burners).
All function perfectly in Hardy Heron and have done so since Dapper Drake (2006).

Your solution might lie with the SATA controllers on your motherboard or the mountpoint of your drives.  What is the readout for your drives in the BIOS?

I would advise you not to mix SATA with PATA drives nor older and slower SATA with faster SATA - keep all hard drives to the same type.

Thanks much for this great information.  The Biostar TF8200 motherboard manual has the following:
"The motherboard has a PCI to SATA Controller with 6 channels SATA interface.
It satisfies the _SATA 2.0 spec_ and with transfer rate of 3.0Gb/s."

The BIOS has the following:
Main - IDE Controller
on chip pata controller - enabled
on chip sata controller - enabled
sata mode select - sata mode
primary IDE master - atari cdrom
primary ide slave - not detected
sata 1 device - hard disk*
sata 2 device - not detected
sata 3 device - not detected
sata 4 device - not detected
Main - hard drive* - _SATA 1_
vendor - ST3250410as
250gb
lba mode - supported
bluh? mode - 16 sectors
pro mode - 4

Does this mean the MB is Sata 2.0 and the HD Sata 1?

Were you able to install Linux on your HD's without Windows?

Maybe what I need then is a Sata 2.0 harddrive.

---

### Post by drifter0000 on 2008-06-08
After doing a lot of looking around on google, it seems most SATA problem with linux are related to seagate drives.
I have reinstalled Mint 4.0 on my SATA drive for now.

---

### Post by kyphi on 2008-06-08
The partition editor "should" identify your hard drives - try the button in the top right corner of the editor that lists one of your drives.

No, you do not need Windows to partition or format - Ubuntu can do all of that (and more).

I have XP on one hard drive and Hardy Heron on the other.  XP cannot see Hardy but Hardy reads all of XP.

One thing that may be worth trying is to adjust your BIOS settings to IDE rather than SATA.

I know of Seagate SATA II drives working perfectly with Ubuntu. so brand is not the problem.

---

### Post by Yellow Pasque on 2008-06-08
You could also try jumpering the draive to SATA 150 speed. VIA chipsets (especially the VT8237 South Bridge) are infamous for issues with SATA 300 drives.

---

### Post by johnlvs2run on 2008-06-08
> **kyphi said:**
> The partition editor "should" identify your hard drives - try the button in the top right corner of the editor that lists one of your drives.

Partition editor = GParted?  The Seagate is invisible to it.

> No, you do not need Windows to partition or format - Ubuntu can do all of that (and more).

But, you have Western Digital.  

> I have XP on one hard drive and Hardy Heron on the other.  XP cannot see Hardy but Hardy reads all of XP.

Unrelated question, can Hardy make changes to XP registry?

> One thing that may be worth trying is to adjust your BIOS settings to IDE rather than SATA.

I know of Seagate SATA II drives working perfectly with Ubuntu. so brand is not the problem.

I will try adjusting the Bios to IDE.  

Perhaps this drive is not Sata II.  I don't see that info in the specs.

---

### Post by johnlvs2run on 2008-06-08
> **Temüjin said:**
> You could also try jumpering the draive to SATA 150 speed. VIA chipsets (especially the VT8237 South Bridge) are infamous for issues with SATA 300 drives.

It came with the jumper.  I've tried it both ways.

By the way, the CD drive is on PATA (I think, i.e. the wide cable).  Could that be an issue?

---

### Post by kyphi on 2008-06-08
Yes, the wide ribbon cable is PATA (IDE).

My BIOS are set this way under Advanced/Drive configuration:

Configure SATA as IDE
ATA/IDE Mode = Native

The other choices besides Native are Legacy and AHCI (Vista needs AHCI).

As mentioned before, all my drives (hard and optical) are SATA and run fine (and fast enough).

As to your question about the Windows Registry being accessible from Hardy - I do not know the answer since I have never tried to do so.

---

### Post by johnlvs2run on 2008-06-08
> **kyphi said:**
> Yes, the wide ribbon cable is PATA (IDE).

My BIOS are set this way under Advanced/Drive configuration:

Configure SATA as IDE
ATA/IDE Mode = Native
Thank you for your responses.  

The Bios picks up the Seagate drive as Sata, and there's no way to change that under drives.
Also, the Seagate HD only has Sata connections, no connections for Pata.

The Bios choices are Auto, or Disabled, and nothing for Native.
Bios Mode choices are Sata, Raid, or Ahci.  When I click Ahci, then Sata disappears.  

> As mentioned before, all my drives (hard and optical) are SATA and run fine (and fast enough).
If this doesn't get working, I plan to return the Seagate and get Western Digital.

Maybe I'm missing something with the Bios.  All ideas and suggestions are much appreciated.

---

### Post by johnlvs2run on 2008-06-09
A friend found this pci=nomsi boot parameter that might be a remedy.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573)

Update: Ubuntu is installed!
Hopefully now all will be well with the hard drive.
Here's a helpful link with clear illustrations of the steps.
[http://www.ubuntu1501.com/2007/01/installing-ubuntu-on-your-dell-1501.html](http://www.ubuntu1501.com/2007/01/installing-ubuntu-on-your-dell-1501.html)

---

### Post by kyphi on 2008-06-09
Congratulations johnlvs2run. Your difficulties regarding SATA are over.

What about drifter0000 who started this post?

---

### Post by drifter0000 on 2008-06-10
I made a live CD for hardy 64 8.04 and added pci=nomsi to the boot options under the install mode.  

It saw my seagate SATA right away and had perfect install.
Thanks very much.:):)

---

### Post by drifter0000 on 2008-06-10
Thank you very much for everyones help.

I made a live CD of hardy and under the boot options for install I added

pci=nomsi

According to the people in the thread that were very helpfull, this is an option that allows intallers to see SATA drives....even a seagate drive.

My install went perfectly.  Rebooted and grub works just fine.

No problems at all with installation
:popcorn:

---

### Post by celem on 2008-09-18
Booting with option pci=nomsi will make it work.

---

