---
title: "New SATA-2 drive not detected"
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by futz on 2006-03-31
I run Breezy 32-bit on an Asrock 939Dual-SATA2 mainboard with two old SATA Raptor  drives - a 36GB and a 74GB. So I was obviously hurtin for some drive space. They're reasonably fast, but very small.

Today I finally decided to spend the hunnert bucks and buy a new 250GB SATA-2 drive to use on the single SATA-2 port on the mainboard. 

Plugged it all in and the BIOS sees it fine but, much to my extreme disgust, Ubuntu doesn't see it at all. 

This mainboard uses the ULI chipset, so I'm hoping there's some way to get Ubuntu to use this drive properly... Don't make me put windoze on this frickin thing!!! :-D

---

### Post by futz on 2006-03-31
This is kind of interesting: 
[http://lists.debian.org/debian-boot/2006/02/msg00152.html](http://lists.debian.org/debian-boot/2006/02/msg00152.html)

Seems the controller for that SATA-2 port is a JMicron, and not ULI. 
Quoted from [http://www.phoronix.com/scan.php?page=article&item=355&num=2](http://www.phoronix.com/scan.php?page=article&item=355&num=2)
> As the implemented Southbridge does not offer SATA2 with NCQ, JMicron's JMB360 ASIC was called in for support.
And over at linuxquestions.org I found this:
> Looks like there is a patch in 2.6.16 for the jmicron for intel, anybody tried that ? i can only install on the sata but not on sataii.

---

### Post by futz on 2006-04-03
Well, I've had enough. I'm going to replace the Asrock mainboard with a DFI LANPARTY UT nF4 Ultra-D.
[http://us.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3471&CATEGORY_TYPE=LP&SITE=US](http://us.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3471&CATEGORY_TYPE=LP&SITE=US)
I'll build another box with the Asrock in the future. Hope the DFI hardware has decent support in Linux... 

DFI makes awesome mainboards! I built a box for a buddy with a DFI. More settings in the BIOS than you can shake a stick at. You have control of EVERYTHING! Very stable overclockers too. DFI is the board for you if you wanna burn up some hardware, or just like to tweak and overclock stuff. :mrgreen: :mrgreen: :mrgreen:

---

### Post by Jason_25 on 2006-04-03
Great choice on the boards.  I've chosen DFI for my personal systems and will never go back.

---

### Post by reet on 2006-04-05
If the SATA2 port is the source of the problem, then just plug the drive into a SATA1 port.

---

### Post by Paulus on 2006-04-05
i got my new SATA 2 drive yesterday, ubuntu wasn´t detecting it, but then i realised I disabled sata in the BIOS!  Just saying check out your bios settings!

---

### Post by futz on 2006-04-05
[QUOTE=reet]If the SATA2 port is the source of the problem, then just plug the drive into a SATA1 port.[/QUOTE]
This board only has two SATA1 ports and a single SATA2 port. I'm not removing the Raptors, so the mainboard either becomes a windoze machine or waits till Linux has support for it. 

Anyway, I've already bought the new mainboard. Backup of data is proceeding. Rebuild on Saturday? Maybe Friday night...

Major upgrades and changes/rebuilds of computers here in the swamp is no big deal. Happens all the time.

---

### Post by futz on 2006-04-05
[QUOTE=Paulus]i got my new SATA 2 drive yesterday, ubuntu wasn´t detecting it, but then i realised I disabled sata in the BIOS!  Just saying check out your bios settings![/QUOTE]
First thing I checked. Everything is enabled and set correctly. The BIOS sees the drive fine, and it would work fine in windoze. The problem is that there's no support for the Jmicron chip in Linux (yet).

---

### Post by LinuxDev on 2006-04-10
Hi,

I've got a Asrock 939Dual-SATA2 as well, and I'm still waiting for a solution with my SATA2 hdd.

I've got 2 SATA1 in RAID0 and can't install Ubuntu on the RAID0 keeping my XP partitions (I saw the RAID0 FAQ, but it's not working) and a SATA2 drives that is not detected while the Ubuntu setup :(

I really want to install Ubuntu again, this is sad :(

---

### Post by futz on 2006-04-11
New mainboard installed Sunday night. Ubuntu 64 installed tonight and configuring right now. Works awesome so far!

---

### Post by LinuxDev on 2006-05-07
[QUOTE=futz]New mainboard installed Sunday night. Ubuntu 64 installed tonight and configuring right now. Works awesome so far![/QUOTE]


Cool, if the solution is to buy a new mainboard, that's really great ;)

---

### Post by futz on 2006-05-07
Oops, double post.

---

### Post by futz on 2006-05-07
[QUOTE=LinuxDev]Cool, if the solution is to buy a new mainboard, that's really great ;)[/QUOTE]
Hehehe. Works for me. :mrgreen: Bought some very nice new RAM for the new mainboard too, and changed CPU's - upgraded to a Athlon 64 4200+ X2 dual core.

I built a leftovers box with the Asrock board and put Dapper on it. Dapper has almost the latest kernel, so may have support for that jmicron chip. 

The onboard LAN on the Asrock board works now, and it wouldn't in Breezy. I haven't checked if the jmicron SATA2 controller works yet. When I get around to it, I'll report here.

---

### Post by DiGiTY on 2006-05-08
i thought there was no difference between SATA-I and SATA-II? I remember reading somewhere that it was a actually a misunderstanding where people simply mistook the renamed SATA organization name for the next version of SATA and started listing new drives as 3.0 Gb/s... I could be mistaken or just read misunderstood the article myself

---

### Post by futz on 2006-05-08
[QUOTE=DiGiTY]i thought there was no difference between SATA-I and SATA-II?[/QUOTE]
There's plenty of differences. SATA2 drives are hot-pluggable, they have NCQ which is good for some performance improvement in some circumstances, they have twice the data transfer speed available (obviously all used only when bursting from cache, but very nice anyway). I'm not sure if staggered spinup is implemented yet, but if not it's coming. There's probably some other stuff that I don't know about too.

Here's a link explaining the confusion regarding SATA branding and standards. Technically we're not supposed to use SATA2 to describe the SATA 3Gb/s standard, but we do it anyway. At least I do.
[http://www.sata-io.org/namingguidelines.asp](http://www.sata-io.org/namingguidelines.asp)

---

### Post by DiGiTY on 2006-05-09
thanks, that explains it. guess i'll trade in my 500 PATA for a SATA II drive and controller after all (...building a home file/media server)

---

### Post by LinuxDev on 2006-05-10
Hi again,

Some guys succeeded in patching the kernel to make the JB360 chip work, here : [http://www.ussg.iu.edu/hypermail/linux/kernel/0601.3/1665.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0601.3/1665.html) and the whole thread : [http://www.ussg.iu.edu/hypermail/linux/kernel/0601.3/index.html#1665](http://www.ussg.iu.edu/hypermail/linux/kernel/0601.3/index.html#1665)

Can someone explain me how to proceed to patch the kernel to add the JB360 chip ? sorry, I'm a Linux nooooobie and it's been a long time since I didn't installed it. Now I want Ubuntu back and on my SATA II hdd ;)

And here [http://www.ocworkbench.com/ocwb/ultimatebb.php?/topic/30/6437/3.html](http://www.ocworkbench.com/ocwb/ultimatebb.php?/topic/30/6437/3.html) they say : "the JMicron controller works - with 2.6.16 kernels"

Dapper is using kernel 2.6.15, isn't it ?
 

Any advice would be welcome.

Thanks again.

---

### Post by futz on 2006-05-10
[QUOTE=LinuxDev]Dapper is using kernel 2.6.15, isn't it?[/QUOTE]
Yes.

---

### Post by esiotrot on 2006-05-11
I dont know whether this helps or not but I bought a machine with a 120 gig sata drive and could not install any linux system (mandrake , fedora, suse). eventually after reading a confusing bit of information on this subject I tried to install using 'linux noapic' at boot. I dont understand why but this works fine. i'm now on ubuntu breezy.

---

### Post by futz on 2006-05-11
[QUOTE=esiotrot]I dont know whether this helps or not but I bought a machine with a 120 gig sata drive and could not install any linux system (mandrake , fedora, suse). eventually after reading a confusing bit of information on this subject I tried to install using 'linux noapic' at boot. I dont understand why but this works fine. i'm now on ubuntu breezy.[/QUOTE]
Thanks for trying, but no, it doesn't help. What's going on here is that there's no driver in earlier linux kernels for the JMicron SATA2 controller chip on the Asrock 939Dual-SATA2 mainboard. Disabling APIC is not going to help here, and should not be done except as a last resort anyway.

Rumor has it that the newest linux kernel ***does*** have support, but we haven't confirmed it yet. And we don't know whether the Dapper kernel (not quite the newest) has support.

---

### Post by futz on 2006-05-15
[QUOTE=futz]I built a leftovers box with the Asrock board and put Dapper on it. Dapper has almost the latest kernel, so may have support for that jmicron chip. 

The onboard LAN on the Asrock board works now, and it wouldn't in Breezy. I haven't checked if the jmicron SATA2 controller works yet. When I get around to it, I'll report here.[/QUOTE]
Reporting now: Nope, it doesn't work with the latest Dapper kernel (2.6.15.22-386).

Anyway, now that it's a "leftovers" box and has no other sata drives, I just jumpered the new 300gb sata2 drive to sata1 and plugged it into one of the sata1 jacks.

---

### Post by Paulus on 2006-05-23
[quote=futz]Reporting now: Nope, it doesn't work with the latest Dapper kernel (2.6.15.22-386).

Anyway, now that it's a "leftovers" box and has no other sata drives, I just jumpered the new 300gb sata2 drive to sata1 and plugged it into one of the sata1 jacks.[/quote] 
Since we spoke, I have upgraded to the asrock mobo SATA2 (I was trying to remember what was wrong with this mobo but i couldn't remember and went ahead lol) with  and yep... it doesn't work, but does with sata1 under dapper.

doh  #-o

---

### Post by futz on 2006-05-23
[QUOTE=Paulus]Since we spoke, I have upgraded to the asrock mobo SATA2 (I was trying to remember what was wrong with this mobo but i couldn't remember and went ahead lol) with  and yep... it doesn't work, but does with sata1 under dapper.

doh  #-o[/QUOTE]
Ya, SATA1 worked fine in breezy too. It's the driver for that JMicron SATA2 controller chip that's missing.

---

### Post by jinx099 on 2006-06-07
I just installed a fresh install of dapper on a PATA drive on an asrock939 dual sata2 an the sata2 drive is still not recognized.  Is there a fix yet, or do we just have to wait for a kernel update?  BTW, I'm running 2.6.16-23

---

### Post by LinuxDev on 2006-06-22
Hi.

It's strange, people [there](http://www.ocworkbench.com/ocwbcgi/ultimatebb.cgi?ubb=get_topic;f=30;t=006437;p=4) are sure that it's working on :

"
2.6.16
2.6.17-rc*
"

---

### Post by Magadass on 2006-07-05
Yeah I have the DFI motherboard and it wont install, it installs on my other computer though.  I had the problem with it locking up on the install screen during Decompressing and finally reburned with a different burner and it worked but it still wont work on my DFI... I have two SATA drives, the Baracudas...

So yeah not sure what the issue is there, my BIOS is the latest also...whatever!

---

### Post by Fr@nKy on 2006-07-05
I have a similar problem! I have a ASUS A8N-SLI Deluxe Motherboard and a SATA1 Seagate 200GB Hard disk but the controller is SATA 2 so I get this problem! All current Linux distros have the same problem! I'm be waiting for 6.10 and see if I can finally go away from Windows. Tell me when will 6.10 be released?? Will it be on 1 October 2006?? And when will we see Beta versions?? So that I can give a try to the new kernel?

EDIT: Yeah 2.6.17 is still not enough because KNOPPIC 5.0.1 is 2.6.17 (RC) and doesn't work here!

Will 6.10 have the 2.6.18 KERNEL??

---

### Post by LinuxDev on 2006-07-10
Hi all,

Any fresh news on SATA2 with Linux ? I'm still crying cause I can't install any distro... :(

---

### Post by rbannan on 2006-07-15
ASROCK Dual 939 SATA2 mobo, will post my findings - 

After scouring the internet, I found that a man by the name of Jeff Garzik is in charge of the ahci driver updates, heres a snippet from one of his posts on a forum:



This patch, against latest 2.6.16-rc-git, adds support for JMicron and
fixes some code that should be Intel-only, but was being executed for
all vendors.


diff --git a/drivers/scsi/ahci.c b/drivers/scsi/ahci.c
index 19bd346..2fffc7b 100644
--- a/drivers/scsi/ahci.c
+++ b/drivers/scsi/ahci.c
@@ -286,6 +286,8 @@ static const struct pci_device_id ahci_p
board_ahci }, /* ICH8M */
{ PCI_VENDOR_ID_INTEL, 0x282a, PCI_ANY_ID, PCI_ANY_ID, 0, 0,
board_ahci }, /* ICH8M */
+ { 0x197b, 0x2360, PCI_ANY_ID, PCI_ANY_ID, 0, 0,
+ board_ahci }, /* JMicron JMB360 */
{ } /* terminate list */
};

@@ -802,7 +804,6 @@ static int ahci_host_init(struct ata_pro
struct pci_dev *pdev = to_pci_dev(probe_ent->dev);
void __iomem *mmio = probe_ent->mmio_base;
u32 tmp, cap_save;
- u16 tmp16;
unsigned int i, j, using_dac;
int rc;
void __iomem *port_mmio;
@@ -836,9 +837,13 @@ static int ahci_host_init(struct ata_pro
writel(0xf, mmio + HOST_PORTS_IMPL);
(void) readl(mmio + HOST_PORTS_IMPL); /* flush */

- pci_read_config_word(pdev, 0x92, &tmp16);
- tmp16 |= 0xf;
- pci_write_config_word(pdev, 0x92, tmp16);
+ if (pdev->vendor == PCI_VENDOR_ID_INTEL) {
+ u16 tmp16;
+
+ pci_read_config_word(pdev, 0x92, &tmp16);
+ tmp16 |= 0xf;
+ pci_write_config_word(pdev, 0x92, tmp16);
+ }

hpriv->cap = readl(mmio + HOST_CAP);
hpriv->port_map = readl(mmio + HOST_PORTS_IMPL);
@@ -1082,6 +1087,10 @@ static int ahci_init_one (struct pci_dev
if (have_msi)
hpriv->flags |= AHCI_FLAG_MSI;

+ /* JMicron-specific fixup: make sure we're in AHCI mode */
+ if (pdev->vendor == 0x197b)
+ pci_write_config_byte(pdev, 0x41, 0xa1);
+
/* initialize adapter */
rc = ahci_host_init(probe_ent);
if (rc)
- 


I've recompiled my kernel (breezy) to 2.6.17.5, and it appears that this patch is already in ahci.c of this kernel version(I checked), so theoretically this should work being as how he states this is a 'non intel' implementation.  (ASROCK 939 Dual SATA II is amd board, incase you didnt know....)

In device manager it shows an unknown device (0x2360) which has two sub-levels.  One for a SCSI host adapter, and one for the SCSI Device. A.k.a. my SATA HD.  Everything reports as unknown vendor - which tells me this patch isnt working.

Now I'm a novice at this and it took me quite a while to figure out even go about upgrading my kernel, and applying that patch to ahci.c.  It could be possible that I just don't know what the heck I'm doing, and I'll keep looking into this issue.  I remember reading somewhere that in the BIOS you might be able to set the JMB360 to AHCI compat. mode - which I havent found.  I have tried setting the SATA II controller to IDE mode - which doesnt work either.  I'll update this if I find anything that works, please do the same or just send a thanks if this info is helpfull.

--Best of luck. (thanks tseliot for that kernel upgrade tutorial)

---

### Post by sharperguy on 2006-07-15
6.10 will be released on the 26th of october:

[https://wiki.ubuntu.com/EdgyReleaseSchedule](https://wiki.ubuntu.com/EdgyReleaseSchedule)

---

### Post by LinuxDev on 2006-07-19
Hi,

Thank you, rbannan ;)
I hope to install Ubuntu before I change my Asrock Dual SATA2 to an Intel Core duo one :)

---

### Post by Ninnghizidha on 2006-07-19
I got my SATA2-hdd working with DAPPER and Asrock Dual SATA2, completly without patches.

And thats the way i got it working - and it was easy:

* Put the SATA2-Disk on a ordinary SATA-Port.
* Install dapper
* update the kernel. sudo apt-get install linux-image-386 (or other)
* shut down the machine
* plugg off the disk from the SATA port and Put it on the SATA2 port
* start ubuntu with the new kernal (should show on grub)

Thats it ... quite easy, isnt it?


Ninn

---

### Post by blokka on 2006-09-06
> **Ninnghizidha said:**
> I got my SATA2-hdd working with DAPPER and Asrock Dual SATA2, completly without patches.

And thats the way i got it working - and it was easy:

* Put the SATA2-Disk on a ordinary SATA-Port.
* Install dapper
* update the kernel. sudo apt-get install linux-image-386 (or other)
* shut down the machine
* plugg off the disk from the SATA port and Put it on the SATA2 port
* start ubuntu with the new kernal (should show on grub)

Thats it ... quite easy, isnt it?


Ninn
Thanks Ninn,

this was easy and worked perfectly for me with Dapper and 64bit kernel!

Blok

---

### Post by LinuxDev on 2006-09-23
Well, it looks easy, if you have only one hdd but I've got 2 SATA I in RAID0 with Windows XP on it + my SATA II waiting for Linux.
If I do what you said, I don't know how to get the dual boot to be able to boot on XP. I guess it's not that easy with the RAID0.

---

### Post by LinuxDev on 2006-10-26
Is it now fixed, with the new Ubuntu 6.10 'Edgy Eft' ?

---

