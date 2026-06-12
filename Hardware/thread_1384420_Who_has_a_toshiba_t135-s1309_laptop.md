---
title: "Who has a toshiba t135-s1309 laptop?"
date: 2010-01-18
forum: Hardware
---

### Post by AlexZaim on 2010-01-18
Hello, i am thinking on buying that laptop and i read some reviews that it's bios doesn't have an option for booting from a usb device. And even an other review said that toshiba tech support affirmed that it can't boot from a usb device. But then later he stated that he actualy managed to boot suse from a flash drive.

So the q is: Does anyone else tried to boot linux with this laptop? Please write about your experience with it!!


> 
Sucess was able to boot T135-S1309 from USB flash drive but not external USB CDR

01-13-2010 05:30 PM

I am partially correct. I am unable to boot for an external connected USB DVD/CDROM drive. The system does not see it during boot up nor in the boot menu by pressing F12. In the bios there is no provision for choosing an external DVD/CDROM drive.

HOWEVER the system will see a bootable USB Flash drive. It needs to be installed in the computers USB port, any one of there 3 at boot time. When you press F12 during the initial boot process the USB flash drive does show up. I was able to boot openSuSE Linux 11.2 this way today and installed it. Now the little Toshiba dual boots using GRUB so I can choose either Windows 7 32 bit or OpenSuSE 11.2 64 bit OS on boot up and both run pretty fast. I am happier than I was when I wrote the previous messages.

 Apparently Toshiba has taken the liberty of hiding within the bios the various bootable accessories. So one will not know until you connect it, then try the F12 boot menu at first power / boot up. Their description of a previous bios update Bios 1.06
# Updated the boot menu: 1. Hid the USB empty slot in the setup menu boot page and pop-up boot menu. 2. Hid the CDROM empty slot in the setup menu boot page and pop-up boot menu. 3. Adjusted the highlight bar UI dynamically for the setup engine. 4. Updated the USB Memory type string definition and algorithm.

There is a restore provision pressing the number 0 during boot up, there is no choice for an external drive so far as I followed that process which was not beyond the first screen.

I'd think an external DVD/CDROM would be the way to boot an .iso but it worked fine from the USB flash drive. I used a windows program to make the bootable .iso. Not sure if it will do anything beyond making a bootable Linux USB flash drive but its worth a try Google for Win32DiskImager worked great for me and was fast doing a Live CD image. Inputting *.iso even when .iso was not a choice worked as it found the .iso I was wanting to install on the USB drive.

[link]("http://laptopforums.toshiba.com/t5/General-Technology/Unable-to-boot-from-external-CDR/m-p/81265;jsessionid=96C25F93A322BE2092DB92923F438D58") to the forum that has the upper quote.

[EDIT]
It can boot from USB wihtout a problem!
Linux related solutions for this laptop may be found [here]("https://launchpad.net/~toshiba-t100-series")!

---

### Post by dgtl_rebellion on 2010-01-18
I just bought a t135 series laptop and it boots from usb just fine. Just make sure the usb drive is plugged in okay and then hit f12 while it's booting up (during the bios screen that says toshiba). you should see 3 options (Hard Drive, Network, USB) and you can select whichever one you want.

---

### Post by AlexZaim on 2010-01-19
Thank you very much! This is a relief for me.

---

### Post by Speshio on 2010-01-19
dgtl_rebellion

Thanks for your input. I've just purchased this nifty little machine from Best Buy, and I see that the BIOS has been upgraded at least twice. 

Can you tell us what BIOS version your machine is using?

I ask because the revision history shows that certain USB booting options were hidden between the initial release BIOS (1.30) and version 1.60. I suspect perhaps you've purchased a machine with the original release BIOS of 1.30 before certain USB booting options were hidden. Current version is 1.90.

My new machine has BIOS version V1.70 as reported by the Phoenix SecureCore Setup Utility 
F12 at Toshiba screen presents choice to boot from hd or lan, or enter set-up. In the Boot section of Set-up, choices are:
HDD/SSD
FDD
LAN

In other words, my Toshiba Satellite T135-S1309 running BIOS v1.70 has no listed option for booting from any USB device.

I don't consider this issue solved for all BIOS iterations of this machine. Thanks everyone for your input on this very interesting issue.

UPDATE: link to Toshiba support on this issue: [http://laptopforums.toshiba.com/t5/General-Technology/Unable-to-boot-from-external-CDR/m-p/81265#M17614](http://laptopforums.toshiba.com/t5/General-Technology/Unable-to-boot-from-external-CDR/m-p/81265#M17614)

---

### Post by AlexZaim on 2010-01-19
Have you tried to follow exact instrucitons? Is your usb drive connected to the pc before you start it,then hit f12?

I'm asking this because my desktop acts in this similar way: it dowsn't show boot option for usb if you don't install/plug in the device first, then turn on the machine.
But it's a desktop... and has nothing toshiba in it,after all. But just curious.

update: btw, i fount this [link]("https://launchpad.net/~toshiba-t100-series") that says "T*100/T115/T135 series laptop owners and/or developers interested in getting it to work 100% under Linux.*" . Which means people actually manage to install linux on them.

---

### Post by Speshio on 2010-01-19
Thanks Alex, 

I haven't got that far yet. 

First question is to decide whether or not to purchase external CD/DVD drive because of this issue. The guy from the Toshiba forums was able to get his to boot from a USB stick, but not from an external USB CD/DVD drive. 

BIOS version 1.30 is still available on the Toshiba site, so it might be possible to downgrade to v1.30 and be able to boot from an external CD/DVD. 

I hope we can hear back from dgtl_rebellion to learn which BIOS version he has that allowed him to boot from external CD/DVD drive.

steve

---

### Post by AlexZaim on 2010-01-19
No i didn't mean to install it via CD. I was talking about the flash drive)
did you:
1. Connected the usb stick to the computer.
2. Turned it on.
3. Pressed f12.
4. And ,optionaly, have you used these instructions:*1. Hid the USB empty slot in the setup menu boot page and pop-up boot menu. 2. Hid the CDROM empty slot in the setup menu boot page and pop-up boot menu. 3. Adjusted the highlight bar UI dynamically for the setup engine. 4. Updated the USB Memory type string definition and algorithm.*

Some times the usb stick isn't visible if you turn the comp on, then insert the drive.

---

### Post by Speshio on 2010-01-19
Thanks again, Alex, I understand the points you are making, but as I say, I haven't gotten that far yet because I have no readily available bootable usb stick at hand at the moment. 

I don't doubt gfiber's method with a bootable usb stick, but it is the CD/DVD boot issue which interests me most right now. Of course, we really need to know gfiber's BIOS version too, and I have left a question for him on that issue at the Toshiba forum.

Your #4 is not instructions, but rather the version comments of the programmer who upgraded the BIOS -- what changes he made. And that's the point. Apparently, the ability for the little Toshiba to boot from CD/DVD was removed from (or hidden in) the BIOS from v1.60 onward.

We can verify this if dgtl_rebellion returns to tell us his BIOS version, which I suspect is v1.30, the initial release BIOS, but v1.40 and/or v1.50 might well be out there too, so I'd very much like to get this info from dgtl_rebellion, as well as where and when he purchased the t135-s1309.

Cheers

---

### Post by AlexZaim on 2010-01-19
Oh, i see. I'm sorry for missunderstanding you! I thought you wanted to boot from a usb stick too. Why do you want to boot from a CD drive, anyway? I understood you don't even have it right know,yes? Please correct me if i'm wrong.

I appreciate your comments.

edit: oh, please include a link to the 1.30 version of bios you said to have found.

---

### Post by Speshio on 2010-01-19
Alex

I love this little machine - it's truly beautiful, but I think it's pretty important to be able to boot from CD/DVD, not only for testing live cd and/or installing ubuntu, but also in the case where the operating system must be re-installed, or you want to install a bigger HDD.

Here's current direct link to Toshiba's d/l page for the t135-s1309.

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=2439365&rpn=PST3AU&modelFilter=&selCategory=3&selFamily=1073768663](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=2439365&rpn=PST3AU&modelFilter=&selCategory=3&selFamily=1073768663)

There are currently three BIOS versions available for the T135-S1309: v1.30, v1.60, and v1.90. 

As I mentioned, my t135-s1309 came with BIOS  v1.70

I doubt this link above will last. It's no doubt better to simply head over to support.toshiba.com, click on download, and use the interface to select the Satellite T135-S1309 download page.

steve

---

### Post by AlexZaim on 2010-01-19
you know , your posts are very insightful. It gives me a lesson in a certain way... but back to ower topic.

You say about reinstalling the os.. do you mean Windows/others? Because linux goes fine with the usb stick, and it's faster from the flash than from cd.

Then, about the HDD upgrade... you need a CD-ROM for a HDD upgrade? Please explain to me how these come together. I'm a bit confused.

BTW, i've been there, on that toshiba support site, but i couldn't find the 1.30 version, i see only 1.6 and 1.9. I'm sure: i've triple-checked it. Could you point it to me more specificly, please?

---

### Post by Speshio on 2010-01-19
Thanks for your kind words Alex.

To get the v1.30 driver:

On the Toshiba download page for the T135, at the 12-21-2009 entry, click the gray box with the plus (+) symbol next to the ACPI flash BIOS version 1.60. That action will open an additional line with the v1.30 BIOS download.

If windows dies, or must be re-installed, then we should have a recovery disk. Toshiba says to make one with an external cd-writer, but if there's no way to boot from such an external drive, what good is the recovery disk? 

Also, if you want to replace the 320GB drive for more capacity, or in case of a failure, how do we boot windows on the new drive once the old one with the os has been pulled?

Just for booting into Linux, the flash stick would be OK, but with this machine, I'd also like to have an XP partition. Some processors have hardware virtualization so you can run XP from within Win 7, but the dual-core processor in the Toshiba T135-S1309 is the SU4100 which does not support hardware virtualization. 

Also, with Linux, I think the live cd option is very appealing to try out a flavor of the operating system (os) without committing to repartition and installing an os which may not like your wireless card, or something else.

I have to decide within 12 days to keep this machine or return it.

ADDED: Also I should add that I am hoping to be able to install Ubuntu along with Win 7 And Win XP on this laptop. If I can't have all three, then Win 7 probably will be dropped. I already returned a Vista laptop previously because it wouldn't run my legacy applications, which are mostly all several years old, but which work perfectly under XP. 

This little Satellite is amazingly small and light, but with a usable keyboard and very nice display. It has a close-to-perfect form-factor, adequate power, and jaw-dropping battery life. I also got a very good price. This little box takes computing into a new realm - at least for me - so I want to get as much precise data as possible before proceeding, because going forward means laying out more $.

ALSO: I missed it first time around, but the t135-s1309 that Gary (on the Toshiba forum) was able to boot from USB stick is running BIOS v1.90


steve

---

### Post by AlexZaim on 2010-01-20
thanks, i found the version.

Hm... concerning the recover disc, isn't it possible to
```
sudo umount /dev/cdrom
dd if=/dev/cdrom of=file.iso bs=1024 
```
 and make a .iso image of the disk

then use the "USB start-up disc creator" to install the image on the drive? 
And use the content as if it was on a CD/DVD.

Btw, there are good buck-up products out there,free, that allows to copy your whole OS bit by bit.After that you can write it, bit to bit to the new HDD ([help]("http://www.mydellmini.com/forum/windows-xp/226-backup-whole-system.html")). I'm not sure about this last one. Sounds risky for me, and i have not tried it. But other than this, is there something else i'm missing?

---

### Post by lisati on 2010-01-20
I don't know about the t135 but the M200 I have has a hidden option to hold down the "0" (zero) key during boot that lets me boot from the recovery partition. Perhaps there's a similar option somewhere on other models that might be of help. (The A100 I had didn't have this option)

---

### Post by Speshio on 2010-01-20
@Alex

Thanks for your ideas. Currently, I'm downloading the 9.10 iso. Then I'll create the bootable usb stick with the iso image, and see what happens when I boot up with the stick mounted and hit F12.

I'm not very fluent with BASH so I can't exactly decipher your code suggestion, but your accompanying explanation seems feasible, and I may give it a try, depending on the outcome of Plan A, above.

The poster at Toshiba support who succeeded with Plan A is using BIOS v1.90. If Plan A fails with my BIOS v1.70, then I suppose I would upgrade my BIOS to 1.90, and go from there. Prolly, I'd want to upgrade to that BIOS version anyway, or go back to v1.30, which seemingly does support booting from external CD/DVD. Once grub and the desired extra os are installed, then I suppose one could go back to the newer BIOS version.

I think it's worth mentioning that there are a number of posts at support.Toshiba.com concerning Flash BIOS upgrade failures, although none that I saw dealing with this specific Laptop, the t135-s1309.

@lisati

Yes, there's a hidden partition on many Toshiba machines with the recovery data to re-install the original Windows OS. I haven't explored this option yet, but thanks for mentioning it.

---

### Post by Speshio on 2010-01-21
My Toshiba T135-S1309 came with BIOS v1.70 when purchased from BB in Jan 2010. 

After downloading the image, I Used this process to create a bootable USB stick with Ubuntu 9.10:

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

With the usb stick physically mounted
power-on
F12 at Toshiba splash screen
and select your usb stick

After a bit, I reach the Ubuntu desktop.

No wireless card recognized by Ubuntu, but that's a different issue.

The little Toshiba uses the realtek rtl8191se. Several threads here on Networking & Wireless about it. Another adventure awaits.

:popcorn:

Steve

---

### Post by Speshio on 2010-01-22
Well, after a fair amount of thrashing about, I'm here on 9.10 live usb stick using ndiswrapper with the win2k drivers for the onboard realtek RTL8191se wireless on my Toshiba Satellite T135-S1309 running under BIOS v1.70 with which this box shipped.

At this point, my wireless connectivity is highly sensitive to the laptop's location within this local public wifi ntwk, which is hammered pretty hard. I was able to get online only by moving to the corner of my pad closest to the router. 

Trial by error getting the onboard card recognized. There are several threads on this topic. There are native linux drivers from Realtek available for this card, but I have to burrow more deeply into that issue after some more popcorn & coffee.

More later.

---

### Post by chellrose on 2010-01-24
@Alex: I have this laptop, and had no trouble booting Linux from an external CD drive.  No idea what version my BIOS is, though, nor how to find out.

@Speshio: After a fair amount of trial and error, and many forum posts, I found a workable solution: using ndiswrapper with the WinXP driver provided on Realtek's site.  The driver is the rtl8192se version, and I found the instructions here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126)
No luck yet with a native Linux driver, though (not for want of trying!).
I should add that wireless works just fine with non-WEP networks, but I haven't been able to convince it to connect to my parents' WEP-protected network.  So WEP could be a problem if you use ndiswrapper...

---

### Post by AlexZaim on 2010-01-25
Can anyone of you paste the output of the comands:
```
lspci
```
```
lshw -C network
```
?
You may want to try the linux driver for realtek. Instructions [here]("http://rtl-wifi.sourceforge.net/wiki/Installing")

---

### Post by chellrose on 2010-01-26
> **AlexZaim said:**
> Can anyone of you paste the output of the comands:
```
lspci
``````
lshw -C network
```?
You may want to try the linux driver for realtek. Instructions [here]("http://rtl-wifi.sourceforge.net/wiki/Installing")

Thanks for that linux driver link.  I'll have to try it, as I'd really like to get that WEP working.  I've hunted all over for linux drivers but haven't been able to find one for my card.

Output of lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

```

Output of lshw -C network:
```

  *-network               
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: c0
       serial: 00:26:9e:87:35:23
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:c0000000-c003ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 10
       serial: 70:1a:04:65:ef:de
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8192se driverversion=1.55+Realtek Semiconductor Corp. ip=172.16.31.51 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: irq:17 ioport:3000(size=256) memory:c0100000-c0103fff

```

---

### Post by AlexZaim on 2010-01-26
By the way, it says
> NOTE : the rtl-wifi drivers are in recent kernels. rtl8180 is in mainline kernel since 2.6.23 and 2.6.25 is in mainline kernel since 2.6.25, so under these kernels you don't need to compile the driver if you only wants to make your wifi working. 
so you may want to try 
```
uname -r
```
to see your version.

...I've just checked realtek's official site and it says 
> 
Linux driver (driver has built-in the kernel)
uhm, i'm stuck. You may want to open a nother topic in the forum concerning this special issue.

Wait,don't go. :) I found a way better tutorial on how to get the driver installed (even with the latest kernel).I recommend, see [http://forum.novatech.co.uk/showthread.php?p=197789]("http://forum.novatech.co.uk/showthread.php?p=197789")

---

### Post by Speshio on 2010-01-26
Alex & Sissy
Thanks for your input. 

Just quickly for the moment: My suggestion is that we keep issues with this laptop confined to this thread, at least for the time being. Alex's original title will bring all searchers here, where we've already plowed some valuable turf, and more to come I believe. 

@Sissy
When the Toshiba splash screen appears right after power-up, mash on the F2 key to enter the Setup Utility. 

See penultimate line for System BIOS Version

Also: Please make note of your Boot options listed in that section of the Setup Utility before exiting. 

@Alex
More to follow on wireless, please stay tuned.
:popcorn:

---

### Post by Speshio on 2010-01-27
Before using Realtek's native Linux wireless drivers, ndiswrapper must be uninstalled completely. 

There are some issues about completely purging ndiswrapper. I hope to have time to pursue this today and try the native Linux drivers supplied by Realtek. 

As it stands, I'm using Win2K drivers with ndiswrapper. I see Sissy is using the Win XP drivers with her T135. 

I have BIOS v1.70.

---

### Post by chellrose on 2010-01-27
I'm running BIOS v. 1.90.  Boot setup listings (when I have my external CD/DVD drive connected) are:

```

HDD/SSD: TOSHIBA MK3263GSX
CD/DVD: HL-DT-ST DVDRAM GP08NU20
FDD:
LAN: Atheros Boot Agent

```Of course, the CD/DVD option isn't there if it's not connected.  The GP08NU20 is the model number of my CD drive; it's an LG Portable Super Multi Drive, in case that helps.

I'm also still trying to get wireless working with the native Linux driver.  The instructions in the link posted by Alex seemed to work for me until rebooting; I suspect that something wasn't updated and it thought it was still using ndiswrapper (despite my having deleted the drivers, or so I thought).  However, I didn't realize that ndiswrapper had to be uninstalled.  I'll try that and see what happens...

---

### Post by AlexZaim on 2010-01-28
And you say that you can't move the CD/DVD entry upper in order to change the boot sequence? Or what seems not to work when booting from a CD?

Yes, you have to remove ndiswraper.

---

### Post by Speshio on 2010-01-28
Sissy, thanks for that information, which is very interesting.

1. Hmmm. I find it curious that your BIOS v1.90 lets you boot from CD/DVD, because that was the original issue here. Based on the BIOS revision history on the Toshiba site, it looks like the ability to boot from an external CD was removed (or hidden) at the v1.60 upgrade.

**Interim conclusion**: Depending on your BIOS version and external CD/DVD, your Toshiba T135 may or may not support booting from that device.;)

I still don't have external device to test on v1.70 other than usb stick, which works.

2. The critical point about removing ndiswrapper seems to be that it must be **completely purged** from the system.

So, as I understand it, if any file relating to ndiswrapper remains on your system, the native Linux drivers may not work.

Instructions for removing ndiswrapper from sourceforge:

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Uninstall_HowTo](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Uninstall_HowTo)

3. I'm unable to get a stable connection while on the Toshiba and Karmic, although I did once earlier, so this project is inching forward. It's a very big nuisance not being able to paste code directly.
:popcorn:

---

### Post by chellrose on 2010-01-28
Thanks for the information regarding ndiswrapper.  I, naively, did modprobe -r ndiswrapper, deleted the drivers, and purged it using adept.  I still can't connect to wireless though.  I'll try the instructions in the sourceforge link & see what happens...

Apart from the WEP issue, ndiswrapper + XP drivers worked on my machine.  I'd like to get the Linux driver working, though.

@Alex: I can move it up in the boot sequence.  Everything seems to work fine.

I don't have an external device other than my CD drive to test booting, and that worked out of the box.

Curious indeed...

Update: After removing all of the ndiswrapper files and rebooting, I was able to connect to wireless... for a while.  All web pages loaded much more slowly than usual (not quite dialup speed, but close!).  After ~10 min. it disconnected, and I couldn't convince it to reconnect, despite KNetworkManager's claim that the signal was still excellent.
So, the linux driver isn't working for me quite yet.  I'll post more updates as things work (or don't).

---

### Post by Speshio on 2010-02-02
Exec. Summary: I was able to get online again using ndiswrapper.

After looking at the rather dense text at sourceforge's ndiswrapper removal instructions, and groaning, it suddenly dawned on me that I was still running Karmic from the live USB stick. Better to start over, eh, where I know what I'm doing, than fool around removing ndiswrapper, where I don't.:D

And, come to think of it, better to give this incarnation of Karmic with ndiswrappeer and the win2k drivers a full chance before dumping it. I suddenly recalled the ancient and revered zen technique of rebooting a couple times to let the system sort itself out after installing a new os. 

At any rate, in the aftermath of several restarts, including an inadvertant trip or two into Win7, I was able to get a stable connection with Karmic at a public hotspot, and stayed online for a couple hours without any problems.

There are two threads on the wireless issue under the Toshiba T135-s1309 search results, and also several threads on the Realtek RTL8191SE which is the onboard card.

I read most of these threads before following some of the advice given to get the wireless working. I suggest trying the win2k drivers with ndiswrapper if the win xp drivers continue to misbehave.
:popcorn:

---

### Post by Speshio on 2010-02-07
I'm wrapping up initial testing of my Toshiba t135-s1309. So far, very good.

I decided to purchase the matching Toshiba SuperMulti Drive to facilitate s/w installation, to create a system restore disc, and to increase booting options.

With the drive plugged in, power-up leads directly to a boot option menu, and I was able to boot from a live CD. 

With my current v1.70 BIOS, I'm able to boot from either usb stick or usb cd/dvd drive, so this is the ideal arrangement. 

:popcorn:

---

### Post by chellrose on 2010-02-08
Still no joy with wireless.  I'm going to try to re-do ndiswrapper when I can get to a wired connection -- hopefully this week.

I fixed the sound issue.  The solution can be found here: [http://ubuntuforums.org/showthread.php?t=1389855](http://ubuntuforums.org/showthread.php?t=1389855)
but here is a summary.

GNOME: System > Preferences > Sound, click the Output tab, and turn up the slider at the top.

KDE (3.5): Right-click on the volume icon in the tray, choose the mixer option (I think it's called KMixer), and turn up the volume slider there.  On login, the speakers usually just crackle, but the rest of the time, sound seems to work OK.

The only other major issue that I've run into is getting the laptop screen brightness changed.  The Fn F6/F7 keys don't work.  I found a solution here ([http://ubuntuforums.org/showthread.php?t=1321403):](http://ubuntuforums.org/showthread.php?t=1321403):)

> 
all you do is edit /etc/default/grub  You add 'nomodeset acpi_backlight=vendor' to the GRUB_CMDLINE_LINUX_DEFAULT line.


And then, of course, run update-grub.  I can now change screen brightness via Fn keys (or brightness-applet) in GNOME, but KDE seems to be ignoring this change.  Has anyone else had this problem, or discovered a fix?

---

### Post by chellrose on 2010-02-09
Wireless update... I'm doing even worse now, apparently.  I couldn't get the Linux driver to work, so I re-installed ndiswrapper and set it up with the WinXP drivers using the method found here: [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/) (same as I used before).

No error messages when configuring ndiswrapper, but after several reboots, my wireless interface, "wlan0", is not recognized by network manager or iwconfig.  I'm not sure how to get it back.  I tried switching to the Win2K drivers, same problem.

Speshio, can you offer any pointers on how you got yours working?

---

### Post by Speshio on 2010-02-10
My results have been mixed and somewhat erratic.

EDIT: My error; I had installed the native linux drivers after all. 

ADD: Well, it's taken me almost all day to backtrack, but I believe I followed the instructions in this thread to install the native driver

[http://ubuntuforums.org/showthread.php?t=1339877&highlight=rtl8191se&page=2](http://ubuntuforums.org/showthread.php?t=1339877&highlight=rtl8191se&page=2)

System>Admin>Hardware Drivers to see if/what/any drivers are being used.

After too much reading on this issue, I stumbled back onto this thread, **originally referenced in comment # 18 by Sissy13**;
See comment #218:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)

Also, this thread, see #12
[http://ubuntuforums.org/showthread.php?t=1354666&highlight=rtl8191se&page=2](http://ubuntuforums.org/showthread.php?t=1354666&highlight=rtl8191se&page=2)

*I know: spaghetti threads. *

**There's something in Karmic that causes erratic behavior with the Realtek card (rtl8191/2se *aka* 8171/2). It may be fixed in these latest patches. Sissy13's launchpad link is probably the one to watch for the latest and greatest solution to ongoing problems with the onboard 819x cards in Karmic. **
 
:popcorn:

---

### Post by AlexZaim on 2010-02-11
Guys. I've managed to get my wifi working with native linux drivers from realtek. I suggest going to [forum.novatek]("http://forum.novatech.co.uk/showthread.php?p=197789") and follow the installation (don't forget to remove ndiswraper as they said). But use this driver [(rtl8192se_linux_2.6.0014.0115.2010)]("http://launchpadlibrarian.net/38201251/rtl8192se_linux_2.6.0014.0115.2010.tar.gz"). It's the latest, directly from a Realtek consultant that was helping me to get it work.

After installing the driver you will have to do 
```
sudo /place/to/driver/installed/wlan0up
```
if it gives you some error messages: do
```
sudo /place/to/driver/installed/wlan0down
```
and then repeat the first step
For more details read the /place/to/driver/installed/readme.txt file.
It also says that you have to do 
```
ifconfig wlan0 up 
```
after the first step... but I can't see it changing something. *Ifconfig wlan0 down* doesn't do nothing too.

I also managed to get the brightness work properly. But I still have problems getting the microphone working. Installing the gnome-alsamixer and checking the second mic doesn't work. I have to shout really loud to get something out of it(with full volume and max sensitivity).

---

### Post by platypus1000 on 2010-02-12
Have you tried it on battery power?  I have also installed the latest Realtek drivers.  It works well on AC but drops the connection on battery power.
[]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126")

---

### Post by chellrose on 2010-02-15
I'd done all that before, with no success.  But, after trying Alex's suggestions again (with 3 reboots), my computer has finally connected to the wireless network with GNOME's NetworkManager.  The connection takes a rather long time to establish, but once it has been established, it seems to be quasi-stable.  I'm having a problem with the signal dropping from 72% to 10% after several minutes, but I'm not sure whether that's Ubuntu or the wireless network itself.  In either case, re-connecting to the network ups the signal strength again, for a few minutes at least.

The signal strength just increased on its own, so maybe it is the network being flaky.

A few caveats:

1. KDE 3's KNetworkManager still refuses to connect to wireless.  I haven't tried KDE 4.
2. ```
sudo ifup wlan0
``` didn't work either.

Thus, on my machine at least, it seems that GNOME's NetworkManager is the only thing that will get any results.  I'll keep playing with the others, and post if anything useful occurs.

---

### Post by AlexZaim on 2010-02-16
I did not tried it from battery power, and i don't think that this actually means anything. They should not depend from one another. I suggest opening another thread in "network and wireless forum" concerning this.

By the way guys, i use WICD network manager. gnome network-manager crashes sometimes my system. See if it's any better with wicd.

I'm uploading some file scripts so that you can use key shortcuts to load the kernel modules of the driver and unload them.

place them in /usr/bin

ex:  sudo mv /path/to/file/wifi_on /usr/bin

You'll have to edit them for to things:
1. in the first line, insert the directory where the driver's source files are.
2. give a path to the notifier from where to get icon images.

ps: don't forget to asign shortcut  keys (in the keyboard shortcuts utility) for these file, with gksodu. 
ex: gksodu /usr/bin/wifi_on

---

### Post by Speshio on 2010-02-16
Sissy: I've also seen - and read comments about - that rising/falling signal strength business, which in my experience is usually in conjunction with networks I can't access or get a good connection. Meanwhile, there are other networks that I can log onto, and maintain a good connection for at least a couple hours, as at present, and on battery power. 

I'm using the linux drivers extracted from rtl8192_linux_2.6.0010.1116.2009.zip to a folder named realtek sitting on my desktop. 

So, modest success, but I won't consider this issue resolved until wireless performance is as good under Ubuntu with this card as it is with Win7, and that is very good indeed. 

Still some work to do, but making progress.

---

### Post by chellrose on 2010-02-17
FYI, it seems that after doing a kernel update, one must re-install the driver under the new kernel.

The signal strength is still fading in and out.  It drops to 10% every 1-15 minutes (the actual time varies).  I have to ask NetworkManager to reconnect.  I can get a stable signal from this network under Win7, though.

I'll give wicd a try and see if it does any better...

update: Installed wicd, it seems to work great so far.  In GNOME, it kept dropping the signal strength as noted above, but I am now in KDE and have had a stable signal for nearly an hour.  Not sure if it's a GNOME thing, or if the driver finally sorted itself out.

Can I put a signal-strength indicator in the panel like I had for NetworkManager?  According to wicd.sourceforge.net, there is one, but I can't figure out where it is...
Edit: Never mind, it just magically appeared.  Maybe it needed a reboot...

---

### Post by AlexZaim on 2010-02-27
Speshio, the 2009 driver version of the realtek wifi card didn't worked for me either.
use the 2010 version. Follow my instructions in post #33 .

My wifi works great! I get no signal loss nor any disconnects. Everything  works great except the microphone. Also my webcam doesn't get detected after it wakes up from suspend

---

### Post by chellrose on 2010-02-27
My connection is still spotty.  Sometimes it works great, very stable; other times it drops out every few minutes.

I think there is, at least in part, a problem with the card itself, because I also had the signal-dropping problem on Win7 when the laptop was on battery power.  And the lower the battery power dropped, the worse the problem became.  Has anyone else seen a significant difference between battery and AC wireless behavior?

In general, though, the connection behaves quite nicely under Win7.

Maybe _my_ card is going bad, though the machine is only 3 months old...

---

### Post by Speshio on 2010-03-01
@Alex
Thanks for that note and clarification. Good to hear you're doing well with your wireless. I'm down with the flu, but will follow up in a day or two.

@Sissy
That's interesting, but it must be frustrating. More on this issue at that Launchpad link.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)

clark_mi (#232) wrote:

> Re: #225

The issue should be caused by "Leisure power save" state of rtl8192se. Using AC power, rtl8192se doesn't enter "Leisure power save" state, so rtl8192 can maintain a good work state, but using Battery, rtl8192se will enter "Leisure power save" state if rtl8192se is in the idle state, and triggers the issue.

It can be solved by modifying the makefile "HAL/rtl8192/Makefile" to disable "Leisure power save" feature of rtl8192se, and the patch is attached.

I think the bug will be fixed in next rtl8192se driver release.

FWIW, it seems somewhat odd that some users of this card are not experiencing this issue, but it's too much for my flu-addled brain right now.

:redface:

---

### Post by chellrose on 2010-03-01
@Speshio: Thanks; that's interesting.  Guess I didn't read down that far in the Launchpad link.  I'll give it a whirl and see if it helps...

Hope you feel better soon.

---

### Post by AlexZaim on 2010-03-12
Interesting to know about the power thing related to wifi. I don't think i ever tested iton battery power because at university i always take the battery out and plug in the cable if i'm in laboratories, other times i don't use wifi on linux.

By the way, a [new driver]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") is freshly out! Have installed it, and works great with the new kernel image (2.6.31-20). Make sure to start the installation with "sudo su"!

Hope you get better soon, speshio!!

PS: if someone has their mic working please let me know how you did it! (i tried gnome-alsamixer,btw)

---

### Post by chellrose on 2010-03-12
Update... After the most recent failure, I uninstalled, then reinstalled the newest driver, with the patch, and the Launchpad suggestion

>  [Andrea Baudracco]("https://launchpad.net/%7Eandrea-baudracco")             wrote             on 2010-03-11:                                                             [ #253]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126/comments/253")                                   
                       My temporary solution (Toshiba Satellite Pro U500, driver 0014):
 in /etc/acpi/wireless-rtl-ac-dc-power.sh replace RTL8192_BATT_POWER=6 with RTL8192_BATT_POWER=0 (line 15)
 in this manner the wlan card never go in battery mode
 I tested this solution for about 8-9 days (with and without AC cord) and I have no problem .... ;-)
 [for csc: i have tested that if you change CONTROL_RTL_POWER to 0 the wlan card always go in battery mode only (because this is the default mode) and, obviously, don't work correctly ... when the wlan card is in battery mode the ping response is about 1 ms slow than in AC mode, I use this trick for testing the power card state]
 another solution is setting power card state manually:
 "iwpriv wlan0 set_power 0" -> AC mode
"iwpriv wlan0 set_power 6" -> battery mode (the broken state)
 ciao


and it _seems_ to be keeping a stable connection (*crossing fingers*), at least in AC mode, which is a big improvement.  Haven't tested it again on battery yet.

Second time's a charm, perhaps??  Not sure why it worked on the second try, but I'll at least tentatively say that this one has been resolved...

---

### Post by secondstage on 2010-03-14
Thanks AlexZaim for posting that link. I got my Toshiba T135D-S1324 working with that. 


Note: "that link" refers to one of the first you posted. ([http://forum.novatech.co.uk/showthread.php?p=197789](http://forum.novatech.co.uk/showthread.php?p=197789))

---

### Post by avilella on 2010-03-15
Hi,

Has anyone made a DKMS deb package for the latest realtek drivers?
I would point to it in the website ([https://launchpad.net/~toshiba-t100-series](https://launchpad.net/~toshiba-t100-series)) if this exists.

> **AlexZaim said:**
> Interesting to know about the power thing related to wifi. I don't think i ever tested iton battery power because at university i always take the battery out and plug in the cable if i'm in laboratories, other times i don't use wifi on linux.

By the way, a [new driver]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") is freshly out! Have installed it, and works great with the new kernel image (2.6.31-20)

Hope you get better soon, speshio!!

PS: if someone has their mic working please let me know how you did it! (i tried gnome-alsamixer,btw)

---

### Post by fcallaghan on 2010-04-30
Hello,
I just have one problem with the sound left! 
  pluggingin headphones & mic does not take over - only the laptop's 
internal speaker & mic work with skype !?

Any suggestions ?

TIA,
    Frank.

---

### Post by secondstage on 2010-04-30
fcallaghan, I tried to get that to work a month ago, and couldn't muster up anything that would work. At this point, it's either play the waiting game, and hope that eventually the hardware is supported, or go out and buy a cheap $2 USB headphone/microphone jack.

---

### Post by chellrose on 2010-05-03
Headphones work fine for me.  Unfortunately, I haven't the faintest idea what setting, configuration file, etc., to point you to, as it just works.

I haven't tested an external mic or webcam though.

---

### Post by secondstage on 2010-05-03
__Sissy13, are you using the new 10.04 release?

---

### Post by secondstage on 2010-05-03
I just booted into a live usb of Ubuntu 10.04 64bit and got nothing coming out of the headphones. 

@Sissy13
Please copy the contents of   ~/.pulse/default.pa   /etc/pulse/daemon.conf   and  /etc/pulse/system.conf  into a reply so I can try them out myself. Also run the command ```
sudo aplay -l
``` and copy the results also.

---

### Post by chellrose on 2010-05-03
> **secondstage said:**
> I just booted into a live usb of Ubuntu 10.04 64bit and got nothing coming out of the headphones. 

@Sissy13
Please copy the contents of   ~/.pulse/default.pa   /etc/pulse/daemon.conf   and  /etc/pulse/system.conf  into a reply so I can try them out myself. Also run the command ```
sudo aplay -l
``` and copy the results also.

I'm running 9.10, 32 bit.  I was planning to upgrade after the semester is done, but if things are broken, perhaps I'll wait awhile.

I did just notice that when headphones are plugged in, audio comes out of the main speakers as well.  I didn't realize this in the past since I typically have the volume very low when using headphones.  This is a problem if one must be quiet.  However, I do get good sound from the headphones also.

I don't have a default.pa in my ~/.pulse folder.

Contents of /etc/pulse/daemon.conf:
> 
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10


I don't have a /etc/pulse/system.conf file, but I'll post the contents of /etc/pulse/system.pa in case these help:
> 
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

# This startup script is used only if PulseAudio is started in system
# mode.

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Automatically restore the volume of streams and devices
load-module module-stream-restore
load-module module-device-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Enable positioned event sounds
load-module module-position-event-sounds


And finally, the result of sudo aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Hope that helps...

---

### Post by secondstage on 2010-05-03
> **Sissy13 said:**
> I did just notice that when headphones are plugged in, audio comes out of the main speakers as well.  I didn't realize this in the past since I typically have the volume very low when using headphones.  This is a problem if one must be quiet.  However, I do get good sound from the headphones also.

Sadly that is the root of the whole problem. Thanks for responding quickly anyways though.

If I remember tomorrow, I'll check to see if a bug has been filed, and if not, then report it. Maybe someday someone will get around to it. But for now, keep your fingers crossed.

---

### Post by chellrose on 2010-05-03
> Sadly that is the root of the whole problem. Thanks for responding quickly anyways though.

Oh, I misunderstood... thought you weren't getting any sound at all from the headphones.  Your comment about bug reporting, though, reminded me that there is a Launchpad group dedicated to T100,T115,T135 Satellite computers here: [https://launchpad.net/~toshiba-t100-series](https://launchpad.net/~toshiba-t100-series).  A microphone solution has been posted here: [https://lists.launchpad.net/toshiba-t100-series/msg00000.html](https://lists.launchpad.net/toshiba-t100-series/msg00000.html) (I haven't tried it).  It seems that no one in this group has found a solution for the headphones yet, though.

---

### Post by AlexZaim on 2010-05-17
I found this workaround for the earphones problem... not sure if it works, because it's from a nother laptop issue, but seemingly as this.

[link]("http://ubuntuforums.org/showthread.php?t=1460790")

1) SOUND: for mutting the speakers while headphones are plugged, follow this instructions:

gedit main.cpp

# Paste the following inside, save and close.

Code:
```

/* 
 * File:   main.cpp
 * Author: xtr
 *
 * Created on April 26, 2010, 5:26 PM
 */

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <unistd.h>
#include <sys/ioctl.h>
#include <sys/io.h>
#include <sys/types.h>
#include <sys/fcntl.h>
#include <syslog.h>
#include <signal.h>

#include <stdint.h>
typedef uint8_t u8;
typedef uint16_t u16;
typedef uint32_t u32;
typedef uint64_t u64;

#define HDA_VERB(nid,verb,param)    ((nid)<<24 | (verb)<<8 | (param))
#define HDA_IOCTL_VERB_WRITE        _IOWR('H', 0x11, struct hda_verb_ioctl)

struct hda_verb_ioctl {
    u32 verb;    /* HDA_VERB() */
    u32 res;    /* response */
};

void daemonize()
{
    pid_t pid, sid;

    /* Fork off the parent process */
    pid = fork();
    if (pid < 0) {
            exit(EXIT_FAILURE);
    }
    /* If we got a good PID, then
       we can exit the parent process. */
    if (pid > 0) {
            exit(EXIT_SUCCESS);
    }

    /* Change the file mode mask */
    umask(0);

    /* Open any logs here */
    openlog("pinsensed", LOG_PID, LOG_DAEMON);
    /* Create a new SID for the child process */
    sid = setsid();
    if (sid < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }

    /* Change the current working directory */
    if ((chdir("/")) < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }


    /* Close out the standard file descriptors */
    close(STDIN_FILENO);
    close(STDOUT_FILENO);
    close(STDERR_FILENO);

}

bool done = false;

void trpsig(int)
{
    done = true;
}

int main(int argc, char** argv) {
    daemonize();
    signal(SIGTERM, &trpsig);

    int fd, state;
    struct hda_verb_ioctl val;
    syslog(LOG_INFO, "Daemon started.");
    fd = open("/dev/snd/hwC0D0", O_RDWR);
    if (fd < 0) {
        syslog(LOG_ERR, "Failed to open snd device.");
            exit(EXIT_FAILURE);
    }
    val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");
    state = val.res >> 31;
    syslog(LOG_INFO, "Starting input value: %0x", state);
    while(!done)
    {
        sleep(1);
        val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");

        if(state != (val.res >> 31))
        {
            state = (val.res >> 31);
            syslog(LOG_INFO, "New input value: %0x", state);
            if(state == 0x1)
                val.verb = HDA_VERB(0x1f, 0x701, 0x1);
            else
                val.verb = HDA_VERB(0x1f, 0x701, 0x0);
            if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
                syslog(LOG_ERR, "Failed to write hda verb.");
        }
    }
    close(fd);
    syslog(LOG_INFO, "Daemon stopped.");
    exit(EXIT_SUCCESS);
}

```

g++ main.cpp -o pinsensed
sudo cp pinsensed /usr/local/bin/pinsensed
sudo pinsensed
sudo gedit /etc/init.d/rc.local

# Add the following (in red) to line 10 (under ### END INIT INFO)

/usr/local/bin/pinsensed

# That's it. Your speakers should mute when you plug in your headphones (also after a reboot). This is not an "official" solution, but a workaround until things get solved.

---

### Post by chellrose on 2010-05-19
Thanks for the tip.  My speakers do mute now when I plug in my headphones... unfortunately, the headphones mute also.  I'll keep playing with it...

---

### Post by trgreerca on 2010-05-27
Here is the solution for the speakers not shutting off when the headphones are plugged in:

Edit /etc/modprobe.conf/alsa-base.conf and add this line to the bottom of the file:

options snd-hda-intel model="olpc-xo-1_5"

Source: [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/549289](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/549289)

---

### Post by AlexZaim on 2010-05-30
Thanks for dropping by!
firstly, its modprobe.d
other than this it doesn't work on my laptop model (it's different than the one on launchpad). And i'm using an outdated os with a outdated kernel ). 9.10 here.

What about you Sissy13, does it work?
Btw, where is speshio? Last time he was sick. I hope he's ok. I'm kind of starting to miss him.

---

### Post by Speshio on 2010-06-08
Hi Alex,
I recovered, but got behind on everything, and had to set the little laptop aside for awhile, although I've been sporadically monitoring this thread. 

Since I'm still running a probably-not-quite-up-to-date-anymore kernal from a USB stick, I'm idling in wait-and-see mode before getting the latest kernal and going forward.

Thanks for thinking of me & I hope this thread stays alive as a good clearing house for issues with the t135; I know it saves me a lot of backtracking when I'm trying to get back up to speed. 

Can anyone contribute a short synopsis of outstanding & relevant issues with the latest kernal and the t135?

:guitar:

---

### Post by AlexZaim on 2010-06-14
I've upgraded to 10.04, fully updated. Works good! The screen brightness still needed to reconfigure as in previous releases. Wifi driver needs to get installed too. Mic still doesn't work. Other than that, it works!
BTW, sound comes out of speakers even if the headset is inserted. Same for my home desktop.
Good to 'see' you speshio!

---

### Post by AlexZaim on 2010-06-19
All T135 users: please execute ```
sudo lshw
```
and tell me your memory frequencies. The official specs say we have 1066 Mhz,but i get 800Mhz.

```
*-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: 16JSF25664HZ-1G1F1
             vendor: 802C
             physical id: 0
             serial: E636DBFB
             slot: M1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: M471B2873EH1-CF8
             vendor: 80CE
             physical id: 1
             serial: 9379FA70
             slot: M2
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
```

---

### Post by AlexZaim on 2010-06-20
Yeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeees!!!!!!!!!!!!
Goooal :P. I MADE MY MIC TO WORK!!!
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
sudo shutdown -r now
```
```
alsamixer
```
press F4 (to list all capturing devices) or press F5 to list all audio device conf.
Raise up any bar/option you think it's MIC related ("M" will toggle between mute/unmute,just in case you need it too). Play with it a little bit.

Then close and try your mic (or just try your mic)!

It is still low, but hey: better than nothing. Try Preferences>Sound> [amplify your input signal]

s00per. My laptop is now 100% linux proof. Hehe :)

---

### Post by mrebanza on 2010-09-28
Damn this didn't work from me . . . Im on a toshiba t135-s1309 laptop but maby because I am using Ubuntu 10.10 beta?

this sucks . . . I am sickk of carrying around a cheap external mic . . . hopfully this fix will get pushed to me upstream now that I am subscribed to  ppa:ubuntu-audio-dev/ppa
:confused:
> **AlexZaim said:**
> Yeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeees!!!!!!!!!!!!
Goooal :P. I MADE MY MIC TO WORK!!!
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
sudo shutdown -r now
```
```
alsamixer
```
press F4 (to list all capturing devices) or press F5 to list all audio device conf.
Raise up any bar/option you think it's MIC related ("M" will toggle between mute/unmute,just in case you need it too). Play with it a little bit.

Then close and try your mic (or just try your mic)!

It is still low, but hey: better than nothing. Try Preferences>Sound> [amplify your input signal]

s00per. My laptop is now 100% linux proof. Hehe :)

---

### Post by AlexZaim on 2010-09-30
> **mrebanza said:**
> Damn this didn't work from me . . . Im on a toshiba t135-s1309 laptop but maby because I am using Ubuntu 10.10 beta?

this sucks . . . I am sickk of carrying around a cheap external mic . . . hopfully this fix will get pushed to me upstream now that I am subscribed to  ppa:ubuntu-audio-dev/ppa
:confused:

i wanted to say that its still far from "desirable". It works better but definitely not desirable... so i don't use skype with linux, for example. :(
I have to shout in the mic to hear some sound back.

---

