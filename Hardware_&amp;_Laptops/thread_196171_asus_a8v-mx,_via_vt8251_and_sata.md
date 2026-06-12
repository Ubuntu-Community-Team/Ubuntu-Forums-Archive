---
title: "asus a8v-mx, via vt8251 and sata"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by jamuir on 2006-06-13
Hello,

First, let me say how impressed I was with the new Kubuntu release.  The live CD looks great, and combining the installer with it was a great idea.

I wanted to report on a problem particular to my hardware since I know that there are a number of others like me trying to cope with via's new vt8251 southbridge (see [here]("http://forums.viaarena.com/messageview.aspx?catid=28&threadid=71754&enterthread=y"))

My problem is that I have an sata hard drive which is not detected.  My motherboard is an asus a8v-mx which has a vt8251.  It's because of the vt8251 that my sata drive isn't detected.

The kernel shipped with Dapper is 2.6.15-23.39 (i.e. 2.6.15 + Ubuntu patches).  To support the vt8251, there is a source patch for 2.6.15 which modifies the file drivers/scsi/ahci.c.  This patch is actually part of the Ubuntu patches.  If you look at the 2.6.15-23.39 source, the file ahci.c contains

```
/* START: patch code for VIA VT8251 ahci controller */

static int via_ahci_softreset(struct ata_port *ap)
{
        void __iomem *port_mmio = (void __iomem *) ap->ioaddr.cmd_addr;
        struct ahci_port_priv *pp = ap->private_data;
        u32 tmp,i,j,via_opts[]={0x00000505,0x00000005};


<snip>

```

Despite the inclusion of this patch, Dapper is not able to see the sata hard drive.  During the boot process, the kernel pauses for about 40 seconds while it tries to communicate with the sata controller:

```
Jun 10 09:35:21 james-desktop kernel: [   39.356927] ahci 0000:00:0f.0: AHCI 0001.0000 32 slots 4 ports 3 Gbps 0xf impl IDE mode
Jun 10 09:35:21 james-desktop kernel: [   39.356933] ahci 0000:00:0f.0: flags: 64bit ncq pm led clo pmp pio slum part
Jun 10 09:35:21 james-desktop kernel: [   39.356997] ata1: SATA max UDMA/133 cmd 0xFFFFC20000062D00 ctl 0x0 bmdma 0x0 irq 201
Jun 10 09:35:21 james-desktop kernel: [   39.357021] ata2: SATA max UDMA/133 cmd 0xFFFFC20000062D80 ctl 0x0 bmdma 0x0 irq 201
Jun 10 09:35:21 james-desktop kernel: [   39.357045] ata3: SATA max UDMA/133 cmd 0xFFFFC20000062E00 ctl 0x0 bmdma 0x0 irq 201
Jun 10 09:35:21 james-desktop kernel: [   39.357069] ata4: SATA max UDMA/133 cmd 0xFFFFC20000062E80 ctl 0x0 bmdma 0x0 irq 201
Jun 10 09:35:21 james-desktop kernel: [   82.390808] TimeOut for Wait Command complete
Jun 10 09:35:21 james-desktop kernel: [   82.390811] softreset failed
Jun 10 09:35:21 james-desktop kernel: [   82.390813] scsi0 : ahci
Jun 10 09:35:21 james-desktop kernel: [   82.591498] ata2: no device found (phy stat 00000000)
Jun 10 09:35:21 james-desktop kernel: [   82.591501] scsi1 : ahci
Jun 10 09:35:21 james-desktop kernel: [   82.792184] ata3: no device found (phy stat 00000000)
Jun 10 09:35:21 james-desktop kernel: [   82.792187] scsi2 : ahci
Jun 10 09:35:21 james-desktop kernel: [   82.992871] ata4: no device found (phy stat 00000000)
Jun 10 09:35:21 james-desktop kernel: [   82.992874] scsi3 : ahci
Jun 10 09:35:21 james-desktop kernel: [   83.016051] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
Jun 10 09:35:21 james-desktop kernel: [   83.016072] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 0
Jun 10 09:35:21 james-desktop kernel: [   83.016098] VP_IDE: chipset revision 7
Jun 10 09:35:21 james-desktop kernel: [   83.016100] VP_IDE: not 100%% native mode: will probe irqs later
Jun 10 09:35:21 james-desktop kernel: [   83.016112] VP_IDE: VIA vt8251 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
Jun 10 09:35:21 james-desktop kernel: [   83.016120]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
Jun 10 09:35:21 james-desktop kernel: [   83.016134]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio

```

I tried recompiling the Dapper kernel with sata and ahci support built-in but had no luck.  I was able to see the sata drive after compiling a 2.6.16 kernel with patches applied to drivers/scsi/ahci.c and drivers/scsi/ahci.c (see [here]("http://forums.viaarena.com/messageview.aspx?catid=28&threadid=71754&enterthread=y")) . For comparison, here is the corresponding part of the system log when I boot my custom 2.6.16 kernel:

```
Jun 11 22:01:18 james-desktop kernel: [   45.280686] ahci 0000:00:0f.0: AHCI 0001.0000 32 slots 4 ports 3 Gbps 0xf impl RAID mode
Jun 11 22:01:18 james-desktop kernel: [   45.280691] ahci 0000:00:0f.0: flags: 64bit ncq pm led clo pmp pio slum part
Jun 11 22:01:18 james-desktop kernel: [   45.280746] ata1: SATA max UDMA/133 cmd 0xFFFFC20000004D00 ctl 0x0 bmdma 0x0 irq 201
Jun 11 22:01:18 james-desktop kernel: [   45.280769] ata2: SATA max UDMA/133 cmd 0xFFFFC20000004D80 ctl 0x0 bmdma 0x0 irq 201
Jun 11 22:01:18 james-desktop kernel: [   45.280791] ata3: SATA max UDMA/133 cmd 0xFFFFC20000004E00 ctl 0x0 bmdma 0x0 irq 201
Jun 11 22:01:18 james-desktop kernel: [   45.280813] ata4: SATA max UDMA/133 cmd 0xFFFFC20000004E80 ctl 0x0 bmdma 0x0 irq 201
Jun 11 22:01:18 james-desktop kernel: [   46.601817] ata1: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4673 85:7c69 86:3e01 87:4663 88:007f
Jun 11 22:01:18 james-desktop kernel: [   46.601821] ata1: dev 0 ATA-7, max UDMA/133, 398297088 sectors: LBA48
Jun 11 22:01:18 james-desktop kernel: [   46.601827] ata1: dev 0 configured for UDMA/133
Jun 11 22:01:18 james-desktop kernel: [   46.601830] scsi0 : ahci
Jun 11 22:01:18 james-desktop kernel: [   46.803302] ata2: no device found (phy stat 00000000)
Jun 11 22:01:18 james-desktop kernel: [   46.803304] scsi1 : ahci
Jun 11 22:01:18 james-desktop kernel: [   47.003988] ata3: no device found (phy stat 00000000)
Jun 11 22:01:18 james-desktop kernel: [   47.003991] scsi2 : ahci
Jun 11 22:01:18 james-desktop kernel: [   47.204675] ata4: no device found (phy stat 00000000)
Jun 11 22:01:18 james-desktop kernel: [   47.204677] scsi3 : ahci
Jun 11 22:01:18 james-desktop kernel: [   47.204774]   Vendor: ATA       Model: Maxtor 6L200S0    Rev: BANC
Jun 11 22:01:18 james-desktop kernel: [   47.204783]   Type:   Direct-Access                      ANSI SCSI revision: 05
Jun 11 22:01:18 james-desktop kernel: [   47.204970] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
Jun 11 22:01:18 james-desktop kernel: [   47.204980] sda: Write Protect is off
Jun 11 22:01:18 james-desktop kernel: [   47.204982] sda: Mode Sense: 00 3a 00 00
Jun 11 22:01:18 james-desktop kernel: [   47.204995] SCSI device sda: drive cache: write back
Jun 11 22:01:18 james-desktop kernel: [   47.205058] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
Jun 11 22:01:18 james-desktop kernel: [   47.205066] sda: Write Protect is off
Jun 11 22:01:18 james-desktop kernel: [   47.205068] sda: Mode Sense: 00 3a 00 00
Jun 11 22:01:18 james-desktop kernel: [   47.205081] SCSI device sda: drive cache: write back
Jun 11 22:01:18 james-desktop kernel: [   47.205085]  sda: sda1
Jun 11 22:01:18 james-desktop kernel: [   47.227671] sd 0:0:0:0: Attached scsi disk sda

```

I am a bit curious about why the vt8251 patch does not work in the Dapper kernel.    Any suggestions?

If other would-be ubuntu users are battling the vt8251, then my advice is to  connect a pata hard drive, install ubuntu to that, recompile and install a 2.6.16 kernel with the 2 patches, then migrate everything to the sata drive.

-James

---

### Post by alge on 2006-06-16
The via ahci patch was only working during a short ubuntu kernel release window from -19 to -21 or -20, it stopped working when they added more backported libata features (I guess).

I'm currently struggling with this problem, because I got stuck with a 2.6.15-21 kernel on one my servers. I already tried to replace the via ahci code (which was the 2.6.15 version from [http://forums.viaarena.com/messageview.aspx?catid=28&threadid=71754&enterthread=y](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=71754&enterthread=y))
with the 2.6.16 version. no luck. And the 2.6.17 version of the patch doesn't fit at all into the 2.6.15 kernel.

Currently I'm trying to find out what the libata related changes in the ubuntu kernel were when it stopped working with the 2.6.15 via ahci patch ...

Albrecht

---

### Post by josed on 2006-06-16
Jamuir and alge, could you post your .config file from the sources that you have?

---

### Post by jamuir on 2006-06-20
[QUOTE=alge]The via ahci patch was only working during a short ubuntu kernel release window from -19 to -21 or -20, it stopped working when they added more backported libata features (I guess).

I'm currently struggling with this problem, because I got stuck with a 2.6.15-21 kernel on one my servers. I already tried to replace the via ahci code (which was the 2.6.15 version from [http://forums.viaarena.com/messageview.aspx?catid=28&threadid=71754&enterthread=y](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=71754&enterthread=y))
with the 2.6.16 version. no luck. And the 2.6.17 version of the patch doesn't fit at all into the 2.6.15 kernel.

Currently I'm trying to find out what the libata related changes in the ubuntu kernel were when it stopped working with the 2.6.15 via ahci patch ...

Albrecht[/QUOTE]

Hi Albrecht,

I'd be interested to know if you find out what dapper patches break the ahci.c patch in 2.6.15 -- hunting that down sounds challenging O:) 

Is upgrading your server to 2.6.16 not an option?  or is this too risky?

I would like to remaster the the Dapper install CD and put a patched 2.6.16 kernel on there.  I think making such a CD available would really help out the less linux-savy users who just want to install linux on there vt8251 controlled sata drive.  However, there are probably good reasons not to do this as well (e.g. using a custom kernel disqualifies you from Canonical's Dapper support).

-James

---

### Post by jamuir on 2006-06-20
[QUOTE=josed]Jamuir and alge, could you post your .config file from the sources that you have?[/QUOTE]

Josed,

Why do you want someone else's config file?  It is probably better for you to create your own.

If you follow the instructions at [http://www.geocities.com/rajahuroman/main.html]("http://www.geocities.com/rajahuroman/main.html"), it tells you that after you do "make menuconfig" your .config file should contain the following:

```

CONFIG_SCSI_SATA=y
CONFIG_SCSI_SATA_AHCI=y
CONFIG_SCSI_SATA_VIA=y 

```

-James

---

### Post by UNIX4ALL on 2006-06-24
What about remastering the cd with a kernel with support for vt8251 ???

Im trying to install Ubuntu 6.06 Server edition in a server with 2 sata2 hdd on raid0 configuration but it´s impossible.

I really apreciated a remastered 6.06 server iso with an updated kernel.

Regards.

---

### Post by ypout on 2006-06-29
Hi James,
Excuse my lack of acronymolgy but is a PATA drive the same thing as the good old IDE drive that I'm used too, or is it something else.  Also if I get a PC with PATA drive instead of a SATA drive will the VT8251 no longer be an issue? Or does the VT8251 control all drive interfaces.  I appreciate your help.

Thanks

---

### Post by jamuir on 2006-07-02
[QUOTE=ypout]Hi James,
Excuse my lack of acronymolgy but is a PATA drive the same thing as the good old IDE drive that I'm used too, or is it something else.  Also if I get a PC with PATA drive instead of a SATA drive will the VT8251 no longer be an issue? Or does the VT8251 control all drive interfaces.  I appreciate your help.

Thanks[/QUOTE]

A pata (parallel ata) connected hard drive is also called an IDE drive; see the following urls for more info:

[http://en.wikipedia.org/wiki/Advanced_Technology_Attachment]("http://en.wikipedia.org/wiki/Advanced_Technology_Attachment")
[http://www.directron.com/patasata.html]("http://www.directron.com/patasata.html")

The board I have is an Asus a8v-mx which includes the vt8251 southbridge.  I connected an old pata drive to it and was able to install Dapper on it without any problem.

In the VIA forums, I think some people had problems with the vt8251 and pata drives, but I think this was solved by a bios update.  I did not experience any problems though.

-James

---

### Post by jamuir on 2006-07-02
[QUOTE=UNIX4ALL]What about remastering the cd with a kernel with support for vt8251 ???

Im trying to install Ubuntu 6.06 Server edition in a server with 2 sata2 hdd on raid0 configuration but it´s impossible.

I really apreciated a remastered 6.06 server iso with an updated kernel.

Regards.[/QUOTE]

I'm going to give remastering the CD a shot -- I just haven't found the time to do it yet.  My plan is to use the 2.6.17 kernel with bjacques' patch.  I see over at launchpad.net that the next Ubuntu release (Edgy Eft) uses 2.6.17.

I will post back here when I have something that works.

-James

---

### Post by mrazster on 2006-07-02
I don't have a solution for you...I can however confirm the bugg/problem this motherboard have with that particular chipset and SATA drives.

I tried it a while back, with both Breezy 5.10 (not sure wich kernel was jused) suse 10.0, 9.2 and 9.1.. and also fedora Core4.
No matter how I tried linux couldn't find my sata drive...so I just changed mobo and *WOILAAAA* everything was peachy.

---

### Post by ypout on 2006-07-02
Thanks for the info James, I look forward to you finding time to remaster the CD with 2.6.17, good luck, let us know how it goes.

---

### Post by mbos on 2006-07-07
> **jamuir said:**
> I'm going to give remastering the CD a shot -- I just haven't found the time to do it yet.  My plan is to use the 2.6.17 kernel with bjacques' patch.  I see over at launchpad.net that the next Ubuntu release (Edgy Eft) uses 2.6.17.

I will post back here when I have something that works.

-James

Hi,

Have you found some time to remaster te CD? I would be very happy if you have. If so, where can I find an ISO or Torrent or anything downloadable?

Gr. M.Bos

---

### Post by jamuir on 2006-07-07
> **mbos said:**
> Hi,

Have you found some time to remaster te CD? I would be very happy if you have. If so, where can I find an ISO or Torrent or anything downloadable?

Gr. M.Bos

Bos,

I've taken a couple cracks at making a live cd but haven't yet had any luck in producing something that boots.  I will give it another couple of goes.  Be warned, though -- I am approaching my limit on the amount of time I can safely donate to this distraction.

I have a patched 2.6.17.3 kernel and am currently using it to run the amd64 version of Kubuntu from my sata drive. vt8251 support is provided by bjacques' ahci.c patch.  (thank-you bjacques!). Here's what I did:

[LIST=1]
[*]I connected an old pata drive to my box.
[*]I installed Kubuntu to the pata drive using the stock live CD.
[*]I booted from the pata drive and then build a new patched kernel and installed it.
[*]I rebooted to the pata drive using the new kernel
[*]Finally, I copied the system on the pata drive over to the now visible sata drive (I used qtparted to create the partitions).
[/LIST]

Yes, it's just that simple ;) 

As for creating a live cd:  I tried swapping the stock kernel and initial ram disk on the live cd (in the /casper directory) with my custom ones.  Unfortunately, this didn't work: "kernel panic, could not mount VFS".  I have a suspicion about why this isn't working...

Anyway, I might give the scripts at [http://www.linux-live.org/]("http://www.linux-live.org/") a try next...  Unfortunately, there is little documentation for those scripts.

stay tuned...

-James

---

### Post by jamuir on 2006-07-09
**Success!**

I managed to create a modified kubuntu-6.06-amd64 live cd which is able to see my sata hard drive!  **With this CD, users with sata drives controlled by VIA's vt8251 southbridge can install linux on their systems!**

I have an iso file, kubuntu6.06+vt8251.iso, which I want to make available.  Can someone suggest a good way to do so?

-James

---

### Post by mbos on 2006-07-11
> **jamuir said:**
> **Success!**

I managed to create a modified kubuntu-6.06-amd64 live cd which is able to see my sata hard drive!  **With this CD, users with sata drives controlled by VIA's vt8251 southbridge can install linux on their systems!**

I have an iso file, kubuntu6.06+vt8251.iso, which I want to make available.  Can someone suggest a good way to do so?

-James


James you are **Great!**

I have no experience with sharing iso-files, but isn't it possible sharing it via torrent?

Main thing for me is your desciption of the steps you've taken. (patching the 2.17.3 kernel)


But first I'll be gone on a nice holiday in France :mrgreen:  

Thanx M.Bos

---

### Post by jamuir on 2006-07-11
> **mbos said:**
> James you are **Great!**

I have no experience with sharing iso-files, but isn't it possible sharing it via torrent?

Main thing for me is your desciption of the steps you've taken. (patching the 2.17.3 kernel)

But first I'll be gone on a nice holiday in France :mrgreen:  

Thanx M.Bos

Here is a url from which you can download the iso

[http://www.ccsl.carleton.ca/~jamuir/kubuntu]("http://www.ccsl.carleton.ca/~jamuir/kubuntu")

There is a README file in that directory which gives some explanation about what I've done.

If someone who downloads the iso could make it available via BitTorrent, then that would be much appreciated.  I don't have the bandwidth to do that myself.

-James

---

### Post by saido2pac on 2006-07-18
Hi,

I've installed the kubuntu+vt8251 and sound + mouse only works on the live cd.
But when it comes to start up, it gives module errors "????????/dev/modules.dep??" something like that and then it continues booting, but no mouse (usb+ps/2 tried both [-( ) and no sound. but it boots well and the hd is recognized!!
i can login and start kde, and that's it, no login sound nothing.

so, .... what do i have to type in the console?
can't i copy the kernel or configuration or whatever from the livecd?
What are your hints/tips? :confused: 

I've a a8v-mx mobo
sata hard disk 40 gig. (30vfat, 8ext3/2?, 0.5swap)
dvd player
256mb ram
64mb vram nvidia fx5200
sempron 3000+ at 2ghz. (overclockt a bit from 200mhz to 234mhz)

greeds,
Saido2pac

---

### Post by jamuir on 2006-07-19
> **saido2pac said:**
> Hi,

I've installed the kubuntu+vt8251 and sound + mouse only works on the live cd.
But when it comes to start up, it gives module errors "????????/dev/modules.dep??" something like that and then it continues booting, but no mouse (usb+ps/2 tried both [-( ) and no sound. but it boots well and the hd is recognized!!
i can login and start kde, and that's it, no login sound nothing.

so, .... what do i have to type in the console?
can't i copy the kernel or configuration or whatever from the livecd?
What are your hints/tips? :confused: 

<snip>


Give this a try:

```

$ sudo ln --symbolic /lib/modules/2.6.17.3+jm /lib/modules/2.6.17.3jm

```

Other users have report problems with modules not being found.  Creating the symbolic link seems to fix it.

Does this solve your problems?

-James

---

### Post by ramanroom on 2006-07-26
> **jamuir said:**
> **Success!**

I managed to create a modified kubuntu-6.06-amd64 live cd which is able to see my sata hard drive!  **With this CD, users with sata drives controlled by VIA's vt8251 southbridge can install linux on their systems!**

I have an iso file, kubuntu6.06+vt8251.iso, which I want to make available.  Can someone suggest a good way to do so?

-James

Dear Jamuir,
thanks for your efforts. I tried to install ubuntu from your live cd, but the installation stops as an error message appears: "failed to write file system". In addition it seems impossible to mount any partition of the hard disk... I wonder if you have any suggestions...
ramanroom

---

### Post by gdinsdale on 2006-07-28
Hi Guys,

I've also tried the live CD created by jamuir, my motherboard is the Asus A8V-XE which has the VT8251 chipset.

Using the "standard" Ubuntu live CD I couldn't even detect my SATA hard drive. This modified live CD has allowed me to do this, so many thanks jamuir!

I am having exactly the same problem as described by ramanroom, when attempting to install to the drive I get a "Failed to create file system" message. Any suggestions?

---

### Post by gdinsdale on 2006-07-29
Ok, so i've solved my own problem.

Setting the SATA controller mode in the BIOS to AHCI (as opposed to IDE or RAID) allowed the installer to do it's thing. I now have a fully functional Kubuntu install thanks to jamuir.

I did also have the problem described above by saido2pac where the sound and mouse did not work after the install. Executing the line of code as given by jamuir solved this after a reboot.

Thanks for all your work jamuir! Much appreciated. :D :D

---

### Post by csimone on 2006-07-29
I did have the same problem (not being able to install ubuntu 6.06 on an ASUS A8V-MX SATA drives), but resolved installing dapper beta, the one dated 20th of april.

---

### Post by andrenth on 2006-07-29
I've just tried to install my system with Edgy knot-1, which has kernel 2.6.17, and it still couldn't find the SATA HD. Is there any module I need to load manually for it to work?

---

### Post by savimonty on 2006-07-31
what is MOBO???

---

### Post by solva on 2006-07-31
I too initially had a 'failed to create filesystem' message, but on switching to AHCI mode for the SATA controller in the BIOS have got  Kubuntu to install - thanks James!

---

### Post by Pamir on 2006-07-31
Hello experts, I had/have problem installing ubuntu on a brand new HP Proliant server with Adaptec sata raid controler. Can some one help me please?

---

### Post by ramanroom on 2006-08-01
I managed to install keeping SATA in the BIOS options.

I booted from the live cd, and I formatted all the partitions I needed.
Then I rebooted from the live cd, I started the installer, and I chose to do the manual partitioning, without doing anything.

Finally I got the usual problem with mouse and sound. The solution suggested by jamuir worked with the mouse but, misteriously, not with the sound.

In any case now I can start working: big thanks to jamuir and bjacques !

ramanroom

---

### Post by Kayos on 2006-08-09
> **jamuir said:**
> Give this a try:

```

$ sudo ln --symbolic /lib/modules/2.6.17.3+jm /lib/modules/2.6.17.3jm

```

Other users have report problems with modules not being found.  Creating the symbolic link seems to fix it.

Does this solve your problems?

-James

That doesnt work for me. It says the link has been created, but on reboot, mouse still doesnt work ;)

---

### Post by Pierpiero on 2006-08-09
Great job!!! I'm a real newbie, but i got Kubuntu running in few minutes... but (I've yet said that I'm a newbie, isn'tit?) I'm not able to make the network to work... I have an old Proliant DL-360 running SMEserver 7.0, that acts also as DHCP server, but these machine seems to be unable to get network configs...

May some one help me?

P.S. Sorry for the bad english...

---

### Post by blacksun on 2006-08-11
It works for me: I had problems with usb, network etc. This is solved by changing adding this symbolic link. THX jamuir!

does kernel 2.6.17.8 support it already? I want to build a new kernel better suited for my system...


Quote:
download from [http://www.ccsl.carleton.ca/~jamuir/kubuntu/](http://www.ccsl.carleton.ca/~jamuir/kubuntu/)
change this: 
Code:
$ sudo ln --symbolic /lib/modules/2.6.17.3+jm /lib/modules/2.6.17.3jm

---

### Post by mbos on 2006-08-12
> **blacksun said:**
> 
does kernel 2.6.17.8 support it already? I want to build a new kernel better suited for my system...


Thanks for all your work Jamuir! It was a great relieve to see my system could run linux. I'd started creating a live cd with ubuntu (Sorry I like GNOME more), when ubuntu released it's latest update 6.06.1 .

And this one worked great with the via vt8251 chipset. This is good news since there is a LTS for this release.

Thanx again for all your effort,

Greetz M. Bos

---

### Post by flamel2000 on 2006-08-15
HElp!SOS!

I installed the kubuntu patched by jamuir by facing many hardships as i'm a newbie.For me now sound dint work.Not only that certain repositories like skype and amarok 141 dint work.

Kindly help me.

---

### Post by jamuir on 2006-08-15
Hi everyone,

thanks for the positive feedback.  I'm glad that many of you were successful with the custom CD.

I just updated the README file at 

[http://www.ccsl.carleton.ca/~jamuir/kubuntu/README](http://www.ccsl.carleton.ca/~jamuir/kubuntu/README)

**I now recommend that you download the latest Dapper release (6.06.1 released on 10 Aug 2006) as it appears to support the vt8251**.  This was pointed out by mbos and I just confirmed it on my machine today.

So, for those of you still having trouble with my custom CD:  give up ;)   Download the official 6.06.1 iso and give that a try instead.

-James

---

### Post by flamel2000 on 2006-09-02
Jamuir i have a question for you.Does gentoo 06.1 hosting the 2.6.18 kernel works well with our vt8251 chipset in all means?
Please reply to me as quickly as possible.


--->Flamel

---

### Post by jamuir on 2006-09-08
> **flamel2000 said:**
> Jamuir i have a question for you.Does gentoo 06.1 hosting the 2.6.18 kernel works well with our vt8251 chipset in all means?
Please reply to me as quickly as possible.


--->Flamel

Hi Flamel,

I have no experience with Gentoo at all, so I cannot say anything definitive about support for the vt8251 in Gentoo 2006.1.  I suggest you have a look at the kernel source used in that release (with Gentoo patches applied) and check if bjacque's vt8251 patch is being used.  Note that bjacques has said that the vt8251 is supposed to be fully supported in 2.6.18 and onwards; so if 2006.1 uses a 2.6.18 kernel then I would guess it probably works.

There is a Gentoo forum discussion related to this topic here:

[http://forums.gentoo.org/viewtopic-p-3552888.html?sid=b57e7b730b75582bc54830f87f2b96a5](http://forums.gentoo.org/viewtopic-p-3552888.html?sid=b57e7b730b75582bc54830f87f2b96a5)

It is probably better to ask questions about Gentoo support there -- I expect you might get more informed answers ;) 

-James

---

### Post by flamel2000 on 2006-11-03
Hello jamuir.I have kubuntu 6.06 running with certain probs in my system.

But now i would like to freshly install kubuntu 6.10 edgy.

I wanna know wether it will support via vt8251.

Kindly temme.

Pl.

:)

---

