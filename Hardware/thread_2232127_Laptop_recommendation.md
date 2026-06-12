---
title: "Laptop recommendation?"
date: 2014-06-30
forum: Hardware
---

### Post by oygle on 2014-06-30
Have used Ubuntu now for about 9 years now, using 13.10 with Kubuntu at present. I have always had a desktop, and basically no major problems. The desktops have ASUS motherboards in them.

I'm needing a Laptop and there are so many mentioned in the 'Laptop Compatibility List". Is there a list of 'most recommended laptops' or 'pre-installed', so that I can narrow the searching down a bit. As the laptop will replace the desktop, I need it to run Ubuntu/Kubuntu "out of the box" please.

So, if there are any recommendation please ?

Also, can I simply reformat the HDD on a laptop, create 2 partitions, and run Kubuntu on the primary and Windows on the secondary (This is what I do now on one desktop).

Oygle

---

### Post by SeijiSensei on 2014-06-30
We've had good success with Lenovos.

As for dual-booting, yes you can reformat the drive as you describe.  Make sure you install Windows first.

I prefer choosing one operating system that I usually work in (Ubuntu in my case) and install the other OS in a virtual machine using [VirtualBox]("http://www.virtualbox.org/").  This machine has a Win7 VM inside a Kubuntu 14.04 host.  I don't use Windows very often so that's a good arrangement for me.  If you want to play games, you'll probably be happier with a dual-boot arrangement as many demanding games need to talk directly to the video hardware and won't install in a VM (Final Fantasy XIV is the latest culprit for me).

---

### Post by oygle on 2014-06-30
> **SeijiSensei said:**
> We've had good success with Lenovos.

Okay thanks, that's 2 recommendations now for Lenovos. I didn't know they were IBM.


> **SeijiSensei said:**
> As for dual-booting, yes you can reformat the drive as you describe.  Make sure you install Windows first.

As I use Kubuntu the most, I'd want that to boot as default. is there a way to setup grub so that Kubuntu is the default and then I press a function key at boot to bring up the menu, to then select Windows ?

> **SeijiSensei said:**
> I prefer choosing one operating system that I usually work in (Ubuntu in my case) and install the other OS in a virtual machine using [VirtualBox]("http://www.virtualbox.org/").  This machine has a Win7 VM inside a Kubuntu 14.04 host.  I don't use Windows very often so that's a good arrangement for me.  If you want to play games, you'll probably be happier with a dual-boot arrangement as many demanding games need to talk directly to the video hardware and won't install in a VM (Final Fantasy XIV is the latest culprit for me).

I have no need of games, but will look at Virtual Box. I have never used that.

Thanks,

Oygle

---

### Post by SeijiSensei on 2014-07-01
> **oygle said:**
> Okay thanks, that's 2 recommendations now for Lenovos. I didn't know they were IBM.
They were IBM's laptop manufacturer, but IBM spun off Lenovo when it got out of selling hardware.  It's now an independent company based in China.

> As I use Kubuntu the most, I'd want that to boot as default. is there a way to setup grub so that Kubuntu is the default and then I press a function key at boot to bring up the menu, to then select Windows?

Yes, you can tell grub which OS to boot by default.  It's set in /etc/default/grub.  On a multi-boot system you should see a menu of choices when the machine first boots.  If that doesn't appear, you can force it by holding down the Shift key during boot.

---

### Post by oygle on 2014-07-02
> **SeijiSensei said:**
> 
As for dual-booting, yes you can reformat the drive as you describe.  Make sure you install Windows first.


Do I _have_ to install Windows first ?

I wanted Kubuntu on the primary partition and Windows on the secondary, if possible.

Also, is it better to buy a laptop with a NVidea or AMD card (dedicated 2 GB).

Thanks,

Oygle

---

### Post by oygle on 2014-07-02
Also, in regards to purchasing a Laptop with Windows 7 pro or Windows 8, is there any BIOS restrictions that would force installing the OS in the primary partition ?

Can't remember where I read something like that. Or, I guess is there anything in M$ Windows products that force installing to primary partition ?

Thanks,

Oygle

---

### Post by SeijiSensei on 2014-07-02
Windows does not play well with others.  There may be methods to install it after Ubuntu, but the reverse is always much easier.  The order on the hard drive does not determine the order of booting.  As I said, that is controlled by the grub boot loader that Ubuntu will install and configured with entries in /etc/default/grub. 

I have used both NVIDIA and AMD/ATI adapters and would definitely choose the first of these.  AMD has a nasty habit of dropping Linux support after a few years.

I'm using a Lenovo with a "hybrid" Intel/NVIDIA architecture.  One of the nice features of this machine is that you can select the adapter using a simple toggle switch on the front of the machine.  Life isn't nearly as easy on an HP machine I have with an Intel and an AMD adapter.

---

### Post by oygle on 2014-07-02
Okay thanks, I won't worry about Windows being installed then, better to leave it "as is" and just get GParted to add a partition for Kubuntu. Will only go for a NVIDIA video card also.

Thanks very much for your help.   :)

Oygle

---

### Post by sudodus on 2014-07-02
Please remember to ***backup*** you original Windows system (the whole drive or at least make a recovery disk) before starting to edit the partitions.

It is recommended to use a Windows tool to shrink the Windows partition, C: with NTFS. So do it from inside Windows. And after that you can use gparted to prepare for Kubuntu.

If you buy a new computer it is probably delivered with Windows 8 installed in UEFI mode, and UEFI makes it harder to install linux (dual boot) compared to old style BIOS. A large part of the support at the Ubuntu Forums today is helping people to dual boot in UEFI mode. See these links

[UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295")                 
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The following links do not describe exactly what you need, but it might contain useful tips, how to make things work.
[URL="http://ubuntuforums.org/showthread.php?t=2213631"]
[/URL][Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by oygle on 2014-07-02
Yes [sudodus]("http://ubuntuforums.org/member.php?u=1499021"), the laptop I will buy will have either Windows 7 pro or Windows 8.x pre-installed. Some very helpful information in those links.

Thanks heaps,  :D

Oygle

---

### Post by squakie on 2014-07-03
About 4 months ago I purchased a new Toshiba C55D series laptop.  Ubuntu installed to it with no problem for dual boot.  Do keep this in mind whatever you do:

Don't use gparted to shrink the Windows partition to make room for Ubuntu.  Instead, you need to do the following:

- boot Windows
- BACKUPS
- defrag the hard drive  twice - even if it says it doesn't need to be defragmented.
- use Windows disk management to shrink an existing partition to make room for Ubuntu
- reboot Windows until it boots cleanly with no checking of the file system

NOW you can go on with installing Ubuntu.  Remember to read the links that sudodus and research your BIOS settings before attempting the install - knowing if your BIOS is in legacy mode or EFI/UEFI mode is VERY important.

---

### Post by oygle on 2014-07-03
Thanks [squakie]("http://ubuntuforums.org/member.php?u=1741485")  :)

---

### Post by oygle on 2014-07-04
My choice was either Lenovo or Dell. I couldn't get the Lenovo online chat to work, and the Dell seemed slightly better, in terms of hardware.

Decided on a Dell Inspiron Laptop 3000 series - [http://www.dell.com/au/p/inspiron-15-3542-laptop/pd?oc=x520403au&model_id=inspiron-15-3542-laptop](http://www.dell.com/au/p/inspiron-15-3542-laptop/pd?oc=x520403au&model_id=inspiron-15-3542-laptop)

Certification at [http://www.ubuntu.com/certification/hardware/201402-14684/](http://www.ubuntu.com/certification/hardware/201402-14684/)

---

### Post by mastablasta on 2014-07-04
porblem with ubuntu Linux on laptops is that even if they are certified, they might not work with next version. depends how much is that important to you.

---

### Post by SeijiSensei on 2014-07-04
I've owned a number of Dell laptops.  I've never had problems installing Linux on any of them, unlike HPs which are a pain in the butt.

One problem you may encounter is if all four primary hard drive partitions are already allocated (HP does that).  Then you'll need to do some fancy footwork to repartition the drive and create an expanded partition so you'll have space for Ubuntu.

---

### Post by AllenGG on 2014-07-04
Hi oygle!   you've been around for a long time so your question is a surprise.

I have 2 laptops,  old one is an Acer, works fine, but not capable of handling 14.04
My ASUS Zenbook  UX31 with an SSD drive is an i5 and very fast, handles everything.  Not a touchscreen.
It integrates well with my Galaxy S4. 
Note > you will find better support in Ubuntu Forums for these laptops than ASUS provides. note UEFI help.
Refurbished from Amazon is the best deal.
Personally I got rid of Windows 2 weeks after.

This is a 1.5kg machine, very sturdy. Great resolution, nice sound when attached to Logitech USB speakers.
And , it takes the SDxc 64gig card.  Scary fast.
....8-)

...Allen

---

### Post by squakie on 2014-07-05
> **SeijiSensei said:**
> I've owned a number of Dell laptops.  I've never had problems installing Linux on any of them, unlike HPs which are a pain in the butt.

One problem you may encounter is if all four primary hard drive partitions are already allocated (HP does that).  Then you'll need to do some fancy footwork to repartition the drive and create an expanded partition so you'll have space for Ubuntu.

+1.  That's pretty important - but also remember if it's Windows 8 it will be running UEFI, and *if* I remember correctly the disk will be gpt, and I don't think that 4 partition limit applies anymore.  In watching the forum before I got my last desktop, it does appear as if people are having a hard time with something with the new(er?) HP laptops - I seem to remember it being something like it doesn't actually "allow" or something with grub, so you can't get back into Ubuntu even after boot-repair.  I am by far NO EXPERT on any of this - just things I've tried to pick up on in the forums so I wouldn't hose up my own laptop too bad ;)

---

### Post by oygle on 2014-07-10
> **mastablasta said:**
> porblem with ubuntu Linux on laptops is that even if they are certified, they might not work with next version. depends how much is that important to you.

The laptop I got is certified to 12.04. I have the Kubuntu 14.04 ISO, so I'm taking a risk I suppose, especially when I use Kubuntu , and hardly use Windows.

> **SeijiSensei said:**
> I've owned a number of Dell laptops.  I've never had problems installing Linux on any of them, unlike HPs which are a pain in the butt.

One problem you may encounter is if all four primary hard drive partitions are already allocated (HP does that).  Then you'll need to do some fancy footwork to repartition the drive and create an expanded partition so you'll have space for Ubuntu.

I have noticed when I go into Disk Management with Win 8.1, it shows an additional 4 partitions. Don't know what they are used for, must be for the OS. Maybe I would have less problems if Kubuntu was on a separate HDD.

> **AllenGG said:**
> Hi oygle!   you've been around for a long time so your question is a surprise.

I have only ever owned a desktop, and always made Ubuntu the primary boot, and if I needed windows, make it a separate drive. So no problems. But I have to have a laptop now, as we are off grid, the desktop would use about 130 watts average, and this laptop is only 13 watts with battery fully charged. So even with an overcast day, I can use the laptop. I'm eager to get Kubuntu going on it.

> **AllenGG said:**
> I have 2 laptops,  old one is an Acer, works fine, but not capable of handling 14.04
My ASUS Zenbook  UX31 with an SSD drive is an i5 and very fast, handles everything.  Not a touchscreen.
It integrates well with my Galaxy S4. 
Note > you will find better support in Ubuntu Forums for these laptops than ASUS provides. note UEFI help.
Refurbished from Amazon is the best deal.
Personally I got rid of Windows 2 weeks after.

This is a 1.5kg machine, very sturdy. Great resolution, nice sound when attached to Logitech USB speakers.
And , it takes the SDxc 64gig card.  Scary fast.

Is that a 64Gb video card, wow. The one I have is dedicated but only 2Gb.The CPU is i7 and it was quite fast initially but seems after windows update and installing zonealarm, it is now a lot slower. Touch pad goes to sleep (resources under win), so I use the keyboard where possible. Thanks for the tips about getting help. I will need help on UEFI I think. I'm looking forward to trying Kubuntu.

I downloaded the Kubuntu 14.04 ISO for 64 bit using windows 8.1. Burnt it to a DVD. Changed BIOS to make secure boot disabled, then at boot pressed F12 to boot from the DVD. This is what was displayed

> Boot mode is set to: UEFI with Legacy OPROM:  Secureboot: OFF
LEGACY OPTIONS:   CD/DVD/CR-RW Device

so pressed enter on that option, and got this message ...

> 
PXE-E61: Media test failure, check cable
PXE-M0F:  Exiting PXE ROM
Reboot and Select proper Boot device
or insert Boot Media in selected Boot device and press a key


I can see the ISO correctly in windows explorer , but cannot browse it, as windows thinks it is a media player file. Will check the MD5 sums on it, and see about redoing the iso to DVD.

Thanks everyone,

Oygle

---

### Post by oygle on 2014-07-10
Installed Cygwin on windows, downloaded the ISO again, burnt it to DVD using Cyberlink ISO viewer, then just disabled Secure Boot in the BIOS, rebooted to the DVD, and was able to "Try" Kubuntu. Worked fine, although some things were disabled.

Now for the dual boot, I will read up on thosee links provided.

I wonder if it would be easier having a separate HDD for Kubuntu ? That said, this HDD is 1Tb, and windows only uses a little bit; there is 876 Gb for Kubuntu.

Oygle

---

### Post by sudodus on 2014-07-10
It will be easier to have two separate HDDs. Then you can do the installation without the other drive (disconnect it), which is safer. When Kubuntu is running, you can shutdown and connect the Windows drive, reboot into Kubuntu and run

```
sudo update-grub
```

After another reboot, you should have Windows as a boot option. Otherwise try Boot Repair according to these links

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oygle on 2014-07-10
Thanks [sudodus]("http://ubuntuforums.org/member.php?u=1499021"). I remember in other posts in this thread, that in the case of one HDD, I should not be concerned about having Kubuntu as the second partition.

In the case of 2 HDD's, can I now have Kubuntu as the primary HDD, and Windows 8.1 as the secondary ?

I do not have the media for windows 8.1, so I would have to do a complete "mirror" to backup up windows. I'm not keeping any data on win 8.1, only the OS. Kubuntu is used for all my data needs.

Because the single drive now is 1 TB, I'd like to be considering to just get a (say) 250Gb HDD for windows 8.1, and install it as the second HDD.

Thanks,

Oygle

---

### Post by sudodus on 2014-07-11
With two HDDs and one OS on each drive, you still have to point the boot to one of the drives (in UEFI/BIOS). I suggest that you point it to the drive with Kubuntu and let grub give a menu to select either Kubuntu or Windows.

If you want to 'mirror' Windows, alias clone it, you will probably have problems trying to squeeze it into a smaller drive. One option might be to shrink the main Windows partition (do it from within Windows), and use the unallocated space for a new partition, a ***data*** partition. If you want the data files (documents, photos, videoclips ...) to be available from both Kubuntu and Windows, use the ***NTFS*** file system. Otherwise ***ext4*** is better (if you intend to use the data partition only from Kubuntu).

---

### Post by oygle on 2014-07-13
Thanks [sudodus]("http://ubuntuforums.org/member.php?u=1499021") for your help. I only just found out that the laptop can only take one HDD, so I may have to have Windows/Kubuntu on the one HDD.

I may "wipe" the Windows 8.1, as I assume if the BIOS is set to legacy, then that gets around the UEFI issue/s. I will only use win 8.1 once every few months, so all the hassles of having dual book windows 8.1/Kubuntu are possibly not justified. I'm thinking of running [WINE]("http://ubuntuforums.org/forumdisplay.php?f=313") to run [this software]("http://www.selectronic.com.au/sppro/splink.htm"). If that works fine, I have no need of win 8.1 at all.

Thanks,

Oygle

---

### Post by sudodus on 2014-07-13
Good luck!

And please share your results :-)

---

### Post by oygle on 2015-01-02
> **sudodus said:**
> And please share your results :-)

Thanks. I did go down the path of trying to obtain instructions from the Dell Forum. There is a sub-forum for Linux. Quite a few months ago, I posted there, but still no reply. I don't think that forum is very active. Anyway, here is one 'tip" I found from [TimeSmall]("http://en.community.dell.com/members/timsmall")

> Old question, but this still comes up via Google - so since I've now got it working, here's how...

There are two solutions do this:

1. Run the Windows .exe under 'wine' under Linux, and pass it the -writehdrfile command line option e.g.

tim@ermintrude:~/Downloads$ wine O760-A16.exe -writehdrfile
tim@ermintrude:~/Downloads$ ls -al O760-A16.hdr
-rw-r--r-- 1 tim tim 3017988 Oct 7 09:21 O760-A16.hdr

n.b. if the windows executable is unable to write the file (e.g. permissions), you get an unhelpful "check command line arguments" error message.

The other is to use the extract_hdr utility as detailed here:

[http://linux.dell.com/files/libsmbios/main/bios_hdr.html](http://linux.dell.com/files/libsmbios/main/bios_hdr.html) 

I want to wipe Windows 8 on the laptop, and install Kubuntu 14.04. One reply I did get from another forum at Dell, was to buy a 64Gb USB, and use the Dell Backup/Recovery tool to back everything up first.

The laptop is a Dell Inspiron 15 Series 3000, 3542

This is an interesting read and may be all I need ??  [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

---

### Post by sudodus on 2015-01-02
> **oygle said:**
> ...
I want to wipe Windows 8 on the laptop, and install Kubuntu 14.04. One reply I did get from another forum at Dell, was to buy a 64Gb USB, and use the Dell Backup/Recovery tool to back everything up first.

The laptop is a Dell Inspiron 15 Series 3000, 3542

This is an interesting read and may be all I need ??  [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

Installing an operating system is risky, so it is a very good idea to ***backup*** the current system and your personal files (pictures, documents ...) before starting. But I would prefer an external hard disk drive, which is more reliable than a pendrive.

That link may be all you need, but there are also other tips at
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295").

---

### Post by oygle on 2015-01-02
Thanks [sudodus]("http://ubuntuforums.org/member.php?u=1499021"), for the tips and links to articles. I do have an external drive, so I will use that for the backup.

I have tried Kubuntu on the Dell laptop. All I had to do was to disable Secure Boot in the BIOS. If that is any indication, I shouldn't have _too_ many problems.  :)

Oygle

---

### Post by sudodus on 2015-01-02
Good luck :-)

---

### Post by weatherman2 on 2015-01-02
I often simply remove a new laptop's hard drive before I even boot Windows the first time.  (Assuming the laptop's hard drive is easy to get to - sometimes it is.)  Having a few spare hard drives for testing is really helpful!  I also usually clone the original laptop drive's Windows to an image file using Clonezilla (save the large image file/directory to a USB/external drive), then test the clone by restoring it to the test hard drive I've swapped in.  If I can boot the cloned Windows from the test hard drive, then I know I'll always be able to revert the original drive to factory settings if I ever need to, worst case.

A USB hard drive adapter or enclosure is also a handy tool to have around - often $10 USD or less for a generic one.

I was able to install Ubuntu 12.04.2 (when that was the newest) on my Acer netbook dual booting with Windows 8, leaving UEFI on.  It was a bit of trial and error, but it still works, and although I only rarely boot Windows on it it's still nice to have when I need to (to test something out).  I still boot the OS of choice not using Grub but using the F12 key to get a boot menu.  Having a Ubuntu live boot USB that includes boot repair is also helpful to have around.  Maybe as of Ubuntu 14.04 things are easier now with secure boot/Windows co-existence.

---

### Post by oygle on 2015-01-02
Thanks [weatherman2]("http://ubuntuforums.org/member.php?u=1931279"). Your comments on using external drive or USB got me thinking. For me, having Win 8 is a bit of a waste. All I really need it for is the [Selectronic SP pro software]("http://www.selectronic.com.au/sppro/splink.htm"). It only runs on Win platforms. Yes, I have considered using WINE and run it under that, but the same software is used to configure our inverter. We sure don't want to be without power.

1. All 'data' files are on a desktop, running Kubuntu 14.04
2. The laptop is only used for the Selectronic software I have no use of runing anything else on a M$ platform.

So, I can now ponder/consider ..

A.  Use Clonezilla on windows 8 laptop, and write it to a USB drive (say 64 Gb)
B.  Also copy it to an external drive.
C.  Wipe the Win 8 on the Dell laptop
D.  Install Kubuntu 14.04 on the laptop. Allow Kubuntu to take up the complete HDD.
E.  Use Kubuntu on the laptop for a month or two, just in case there are any "gotchas"

F.  Backup all 'data' fiiles from desktop to external drive
G.  Restore files from "F" to the Dell laptop (there may be some install issues with some Kubuntu apps, no worries, I have done a few 'clean' *Ubuntu installs).
H.  When I need to run the Selectronic software, just plugin the USB drive and boot from that.

The only problem I see is keeping the USB drive 'up to date' with MS updates. The HUGE/BIG _plus_ though, is having the Dell laptop **ONLY** for Kubuntu.

---

### Post by sudodus on 2015-01-02
Windows does not boot from USB. That is a big problem! A backup of Windows is good, but you would have to restore Windows to an internal drive (SATA drive), or just keep Windows on its original drive and insert it when needed (swap which drive to use as the internal drive).

---

### Post by weatherman2 on 2015-01-02
I may have mislead you with the word "clone."  Image backups made by Clonezilla aren't themselves bootable from USB.  They are just backup files.  They can be restored to another internal HDD device.  But you can't actually boot a working Windows OS from USB (at least, not in any clean way).  The best you can do via USB is boot a Windows boot disk (to install Windows on an internal HDD).

So you can forget about trying to boot Windows occasionally from USB.

An alternative is to install Windows in a virtual machine within Kubuntu (that's what I do even though I also can boot Windows 8 - a virtual machine is still easier than re-booting).  But I've never done this with Windows 8.1, and I'm not sure you can using the Windows version that came with your laptop, because MS no longer provides product keys for OEM versions of Windows 8 pre-installed on computers.  If you don't care what version of Windows you use, if you have access to a legal Windows 7 product key, I'd probably go with that.  Legal downloads of Windows 7 boot disks (which you can boot from USB to install in a virtual machine) can be downloaded via DigitalRiver, last I checked, but need a product key to activate.

I wouldn't give up on doing a dual boot of Windows / Kubuntu though.  Give it a try.  It may go easier than you expect.  Once you've made your initial backup, what do you have to lose?  You can shrink your Windows partition down to about 100GB (even less if you think you won't use it much) and use the rest for Kubuntu.  If it doesn't work out after a little effort, you can always give up, wipe the disk, and install Kubuntu on whole disk in legacy mode.

---

### Post by oygle on 2015-01-02
Thanks for clarifying in regards to "clone". I guess the Dell backup/recover may be also just backup files, but does backup the OS. There doesn't seem to be any indication that you can boot from a media containing the Dell backup/recover.

> **weatherman2 said:**
> 
So you can forget about trying to boot Windows occasionally from USB.

Okay.

> **weatherman2 said:**
> 
An alternative is to install Windows in a virtual machine within Kubuntu (that's what I do even though I also can boot Windows 8 - a virtual machine is still easier than re-booting).  But I've never done this with Windows 8.1, and I'm not sure you can using the Windows version that came with your laptop, .....

Okay, so a may not be able to do it with a VM. I'm using Win 8.1 , and yes it is OEM. I have had discussions with Dell support in the pasr about buying the MS CD's containing Win 8.1. Their reply was that it is not availabe online, but I can get it by calling some number and mentioning the product number. It will cost $55 ; must cheaper than $149 if I buy from the shop where I purchased the laptop.

I do have a 'legal' XP pro, but would rather use the latest win 8.1 

> **weatherman2 said:**
> 
I wouldn't give up on doing a dual boot of Windows / Kubuntu though.  Give it a try.  It may go easier than you expect.  Once you've made your initial backup, what do you have to lose?  You can shrink your Windows partition down to about 100GB (even less if you think you won't use it much) and use the rest for Kubuntu.  If it doesn't work out after a little effort, you can always give up, wipe the disk, and install Kubuntu on whole disk in legacy mode.

In the last few hours, I have come across so many articles on "how to" do it. Choosing which article to follow is the difficult part. I used to have a dual boot Ubuntu/Win XP, and that was so easy. That said they were on seperate drives.

The only "alarm bells" I'm hearing is the ever so slight chance of windows clobbering any data on the Kubuntu partition.

---

### Post by sudodus on 2015-01-03
> **oygle said:**
> ...
The only "alarm bells" I'm hearing is the ever so slight chance of windows clobbering any data on the Kubuntu partition.

Windows does not even read linux ext4 partitions, so if you avoid editing or formatting partitions, you should be fine. But you need a good backup anyway, because your hardware can fail, there can be a power outage, which destroys the file system ...

---

### Post by oygle on 2015-01-05
I may need to edit the Kubuntu partition at some point. I wouldn't want to be touching the Windows partition though; only once to shrink it before installing Kubuntu. Have found a step by step guide at [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) . The author used a Dell Inspiron, same type of laptop.   :)

---

