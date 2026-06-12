---
title: "I'm basically f***ked with Ubuntu and I didn't realize it"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by Rhizome21 on 2005-11-25
In reminiscence to the thread started about how a person misrepresented Linux, I too have some trouble with it. The only thing I give thanks to Ubuntu is that it has withdrawn my computer game addiction lol--- because I couldn't figure out how to play games on ubuntu.

Anyways I have had major problems with Ubuntu over the past months. I just wanted to post this thread to see if anyone is willing to help me. A while back, this linux-minded person told me to update my ubuntu to harty (or warty) or whatever it was.... and I ended up messing up Ubuntu. When I turned on the computer the screen wouldn't show up... it just had numbers all over the place.

So, I had to re-install Ubuntu on the computer (this was like 4 months ago). And I haven't 'updated' it since. The basic computer needs are fufilled. I mean, my gaim is working, my printer is working, etc... I still use Openoffice 1.0 on it :rolleyes: My cd-rom doesn't work when I try to play music cds etc..

I'm stuck with Linux, because I can't install my windows back. It's get frozen whenever I try to install windows back.


So what should I do :(? Is there any other user-friendly linuxs? :(

---

### Post by aysiu on 2005-11-25
[QUOTE=Rhizome21]
So what should I do :(? Is there any other user-friendly linuxs? :([/QUOTE] Well, you could try Mepis or SuSE.

If you really want Windows on your computer, though, you could try wiping the entire hard drive clean first and then installing it again. Microsoft feels your plight and has actually set up a page on [How to Remove Linux and Install Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;314458).

If you want to give Ubuntu another chance, though, I would install Windows and configure a dual boot with the newest version of Ubuntu (Breezy). This guide will walk you through it step by step:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Whatever you try, I wish you the best. Let us know if you need more suggestions or guidance.

---

### Post by kirmonkey on 2005-11-25
I think there are a couple of options:

1. Work through the problems you have with ubuntu one by one to get an effective and powerful system up and running (I have done this) I found this guide both clear and through for hoary:

[http://www.frankandjacq.com/ubuntuguide/5.04/]("http://www.frankandjacq.com/ubuntuguide/5.04/")

2. Try another distribution, they are free and easy to get and may work better 'out of the box' on your system

There is no reason to have a crippled system if you throw a little time at it.

Post back if you have any more questions

Hope this helps!

---

### Post by Rhizome21 on 2005-11-25
well i'm interested in dual-booting with windows and linux...

The windows instructions are a bit complicated -_-

When it says to start off with the linux setup floppy disk? does this mean the Ubuntu CD installation? and where  do i type fdisk..... i don't want to seriously **** this up again lol

1.	Remove the native, swap, and boot partitions used by Linux:
a. 	Start your computer with the Linux Setup floppy disk, type fdisk at the command prompt, and then press ENTER.

NOTE: For help with using the Fdisk tool, type m at the command prompt, and then press ENTER.
b. 	Type p at the command prompt, and then press ENTER to display partition information. The first item listed is hard disk 1, partition 1 information, and the second item listed is hard disk 1, partition 2 information.
c. 	Type d at the command prompt, and then press ENTER. You are then prompted for the partition number that you want to delete. Type 1, and then press ENTER to delete partition number 1. Repeat this step until all the partitions have been deleted.
d. 	Type w, and then press ENTER to write this information to the partition table. Some error messages may be generated (because information is written to the partition table), but they should not be significant at this point because the next step is to restart the computer and then install the new operating system.
e. 	Type q at the command prompt, and then press ENTER to quit the Fdisk tool.
f. 	Insert either a bootable floppy disk or the bootable Windows XP CD-ROM, and then press CTRL+ALT+DELETE to restart your computer.
2.	Follow the instructions on the screen to install Windows XP.

The installation process assists you in creating the appropriate partitions on your computer.

---

### Post by poptones on 2005-11-25
Let's consider the facts: 

Your system did not respond well to an "upgrade," it doesn't work as it should after doing a "regular" install, and it won't install windows at all...

I am willing to bet you your system is experiencing a hardware failure - likely the hard drive or controller, although for all we know right now it could be a motherboard issue and/or a power supply issue. Why don't you post some more information about your system?

Just saw your last post... if you are willing to reinstall everything from scratch, how about running a few tests first?

---

### Post by aysiu on 2005-11-25
Of course, before you do anything, you should back up all your important files.

I'd say the easiest way to delete all your Linux partitions and start from scratch with Windows is to use a live CD like Knoppix and run the program called QTParted. Use it to erase all your partitions and create an NTFS partition (for Windows XP, NT, 2000) or a FAT32 partition (for Windows ME, 98, 95).

Then, Windows can install itself there.

---

### Post by Quinn52 on 2005-11-25
I am sort of in the same boat.  I was told I could install Ubuntu and my windows would remain intact.  However, I was told the same thing about another Linux download about 8 months ago and it totally knocked out anything I had on windows out of my computer.  I just want to be sure I can maintains windows, while I study and learn ubuntu.  I can not study ubuntu at my leisure if it is my only operating system.  I must have the windows XP until I feel ready to switch.

Any comments, I will try it if I can be assured I can keep windows, but how.

---

### Post by aysiu on 2005-11-25
I don't think dual boot setup instructions get any clearer than this:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

And always back up your work. Always back up.

---

### Post by Rhizome21 on 2005-11-25
Well, apparently a while ago I was talking to this linux expert about why my music cds wouldn't play any sound and he said that the cd-rom may not be recognized in ubuntu for some strange reason. I mean all other CDs do work... like those that have files, images, mp3s etc..


uhhh... i just realized that I might not want to install windows... because I can't find the cds to install my printer and shit lol :(




here is my system specs:

Alienware desktop
AMD Athlon 1900 xp+
Geforce 4 ti4600
512 DDR ram
DVD rom 16 x
Plexwriter 24/10/40A
In-board etherenet (some geforce shit)
Soundblaster (don't know which one...)

---

### Post by Rhizome21 on 2005-11-25
I just ordered the Ubuntu 5.10 (breezy). I hope it works .

---

### Post by poptones on 2005-11-25
> Well, apparently a while ago I was talking to this linux expert about why my music cds wouldn't play any sound and he said that the cd-rom may not be recognized in ubuntu for some strange reason. I mean all other CDs do work... like those that have files, images, mp3s etc..

This is extremely unusual and sounds like a hardware problem. If you would actually post some info about your hardware I might be able to help... sorry, what I mean is really more like when you bought it, and where you live (apartment, city/rural, etc).  Was it working fine (and playing CDs) in windows? Does it read other (non music) cds?

People have become so accustomed to windows flakiness they are willing to live with almost any sort of odd behavior from their systems. It seems very likely your system has hardware problems that need to be addressed - until you do this it will never be right no matter what operating system you manage to get installed on it.

---

### Post by Rhizome21 on 2005-11-25
[QUOTE=poptones]This is extremely unusual and sounds like a hardware problem. If you would actually post some info about your hardware I might be able to help... sorry, what I mean is really more like when you bought it, and where you live (apartment, city/rural, etc).  Was it working fine (and playing CDs) in windows? Does it read other (non music) cds?

People have become so accustomed to windows flakiness they are willing to live with almost any sort of odd behavior from their systems. It seems very likely your system has hardware problems that need to be addressed - until you do this it will never be right no matter what operating system you manage to get installed on it.[/QUOTE]

1. I bought it in early February of 2002.

2. I live in a city -- downtown. In a Victorian old house type

3. It was working fine in Windows --- originally what drove me to install Linux was that I was having problems with WIndows. The windows explorer would keep refreshing whenever i started the computer, and I couldn't open "my computer" because I think the explorer got fucked by too many add-ons . I don't know. But the cds did work normally.

4. Right in Ubuntu it does read non music cds. In other words, those that contain files, images, mp3s files.

---

### Post by teaker1s on 2005-11-25
sounds like a hardware fault if it's not then you will need a dos boot disk and copy of fdisk which can be found by googling fdisk.
basically you need to boot computer from floppy then run fdisk and delete all partitions and possibly format disk as well then windows will reinstall-trust me I've done it when I tried redhat

---

### Post by poptones on 2005-11-25
Yeah it's a pretty old system, you live in a victorian house (that probly has ancient wiring) and it sounds as if it was already flaking out by the time you lost windows.

Don't fdisk or any of that stuff yet it's not going to do a damn thing but waste time and effort. First step is to find out what's got the system crippled THEN you can 
worry about fdisking it and reloading it.

type this in a cli: 

grep 'ide' /var/log/messages

and post any output.

---

### Post by Littleweseth on 2005-11-25
you mean the age of the wiring in the house actually affects the lifespan of a computer? You'd think this is the kind of thing where you'd just put a $20 AUD (10-15$ US?) surge prtector or something inbetween yor computer and the wall.

Where I live, though, is true computer hell : in the tropics, at the beach. The combination of salt and moisture rusts or corrodes ANYTHING in very short order - for example, my video card is very flaky right now and displays artifacts everywhere. Gotta get aircon.

---

### Post by Rhizome21 on 2005-11-25
this is what came out of that comman i typed:

```
Sep 17 10:06:51 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Sep 17 10:06:51 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Sep 17 10:06:51 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Sep 17 23:17:05 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Sep 17 23:17:05 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Sep 17 23:17:05 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Sep 17 23:17:05 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Sep 17 23:17:05 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Sep 17 23:17:05 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Sep 17 23:17:05 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Sep 18 17:21:54 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Sep 18 17:21:54 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Sep 18 17:21:54 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Sep 18 17:21:54 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Sep 18 17:21:54 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Sep 18 17:21:54 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Sep 18 17:21:54 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Sep 19 10:15:39 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Sep 19 10:15:39 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Sep 19 10:15:39 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Sep 19 10:15:39 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Sep 19 10:15:39 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Sep 19 10:15:39 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Sep 19 10:15:39 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Sep 20 09:58:34 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Sep 20 09:58:35 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Sep 20 09:58:35 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Sep 20 09:58:35 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Sep 20 09:58:35 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Sep 20 09:58:35 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Sep 20 09:58:35 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Sep 22 21:29:06 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Sep 22 21:29:06 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Sep 22 21:29:06 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Sep 22 21:29:06 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Sep 22 21:29:06 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Sep 22 21:29:06 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Sep 22 21:29:06 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Sep 23 21:50:05 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Sep 23 21:50:05 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Sep 23 21:50:05 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Sep 23 21:50:05 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Sep 23 21:50:05 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Sep 23 21:50:05 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Sep 23 21:50:05 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Sep 24 12:09:28 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Sep 24 12:09:28 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Sep 24 12:09:28 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Sep 24 12:09:28 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Sep 24 12:09:28 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Sep 24 12:09:28 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Sep 24 12:09:28 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Sep 24 19:00:49 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Sep 24 19:00:49 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Sep 24 19:00:49 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Sep 24 19:00:49 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Sep 24 19:00:49 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Sep 24 19:00:49 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Sep 24 19:00:49 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 7 19:49:23 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 7 19:49:23 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 7 19:49:23 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 7 19:49:23 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 7 19:49:23 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 7 19:49:23 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 7 19:49:23 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 7 21:18:26 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 7 21:18:26 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 7 21:18:26 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 7 21:18:26 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 7 21:18:26 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 7 21:18:26 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 7 21:18:26 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 8 14:28:45 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 8 14:28:45 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 8 14:28:45 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 8 14:28:45 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 8 14:28:45 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 8 14:28:45 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 8 14:28:45 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 8 22:16:40 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 8 22:16:40 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 8 22:16:40 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 8 22:16:40 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 8 22:16:40 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 8 22:16:40 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 8 22:16:40 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 9 12:22:58 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 9 12:22:58 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 9 12:22:58 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 9 12:22:58 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 9 12:22:58 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 9 12:22:58 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 9 12:22:58 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 9 13:25:41 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 9 13:25:41 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 9 13:25:41 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 9 13:25:41 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 9 13:25:41 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 9 13:25:41 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 9 13:25:41 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 9 16:18:49 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 9 16:18:49 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 9 16:18:49 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 9 16:18:49 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 9 16:18:49 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 9 16:18:49 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 9 16:18:49 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 9 20:27:38 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 9 20:27:38 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 9 20:27:38 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 9 20:27:38 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 9 20:27:38 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 9 20:27:38 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 9 20:27:38 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 14 22:57:16 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 14 22:57:16 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 14 22:57:16 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 14 22:57:16 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 14 22:57:16 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 14 22:57:16 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 14 22:57:16 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 15 13:52:27 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 15 13:52:27 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 15 13:52:27 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 15 13:52:27 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 15 13:52:27 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 15 13:52:27 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 15 13:52:27 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 15 20:39:06 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 15 20:39:06 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 15 20:39:06 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 15 20:39:06 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 15 20:39:06 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 15 20:39:06 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 15 20:39:06 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 16 14:52:25 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 16 14:52:25 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 16 14:52:25 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 16 14:52:25 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 16 14:52:25 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 16 14:52:25 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 16 14:52:25 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 16 20:32:19 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 16 20:32:19 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 16 20:32:19 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 16 20:32:19 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 16 20:32:19 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 16 20:32:19 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 16 20:32:19 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 22 13:14:57 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 22 13:14:57 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 22 13:14:57 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 22 13:14:57 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 22 13:14:57 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 22 13:14:57 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 22 13:14:57 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 28 22:25:48 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 28 22:25:48 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 28 22:25:48 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 28 22:25:48 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 28 22:25:48 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 28 22:25:48 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 28 22:25:48 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 29 13:37:00 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 29 13:37:00 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 29 13:37:00 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 29 13:37:00 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 29 13:37:00 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 29 13:37:00 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 29 13:37:00 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 29 21:43:46 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 29 21:43:46 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 29 21:43:46 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 29 21:43:46 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 29 21:43:46 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 29 21:43:46 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 29 21:43:46 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 30 12:37:13 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 30 12:37:13 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 30 12:37:13 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 30 12:37:13 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 30 12:37:13 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 30 12:37:13 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 30 12:37:13 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 30 19:52:20 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 30 19:52:20 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 30 19:52:20 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 30 19:52:20 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 30 19:52:20 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 30 19:52:20 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 30 19:52:20 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Oct 30 21:33:31 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Oct 30 21:33:31 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Oct 30 21:33:31 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Oct 30 21:33:31 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Oct 30 21:33:31 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Oct 30 21:33:31 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Oct 30 21:33:31 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 5 12:14:12 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 5 12:14:12 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 5 12:14:12 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 5 12:14:12 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 5 12:14:12 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 5 12:14:12 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 5 12:14:12 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 6 10:05:06 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 6 10:05:06 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 6 10:05:06 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 6 10:05:06 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 6 10:05:06 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 6 10:05:06 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 6 10:05:06 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 6 16:09:50 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 6 16:09:50 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 6 16:09:50 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 6 16:09:50 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 6 16:09:50 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 6 16:09:50 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 6 16:09:50 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 6 16:12:14 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 6 16:12:14 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 6 16:12:14 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 6 16:12:14 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 6 16:12:14 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 6 16:12:14 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 6 16:12:14 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 6 21:38:59 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 6 21:38:59 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 6 21:38:59 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 6 21:38:59 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 6 21:38:59 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 6 21:38:59 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 6 21:38:59 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 10 19:08:29 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 10 19:08:29 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 10 19:08:29 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 10 19:08:29 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 10 19:08:29 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 10 19:08:29 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 10 19:08:29 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 11 18:44:15 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 11 18:44:15 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 11 18:44:15 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 11 18:44:15 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 11 18:44:15 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 11 18:44:15 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 11 18:44:15 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 12 15:43:33 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 12 15:43:33 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 12 15:43:33 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 12 15:43:33 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 12 15:43:33 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 12 15:43:33 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 12 15:43:33 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 12 18:07:35 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 12 18:07:35 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 12 18:07:35 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 12 18:07:35 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 12 18:07:35 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 12 18:07:35 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 12 18:07:35 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 13 09:58:22 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 13 09:58:22 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 13 09:58:22 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 13 09:58:22 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 13 09:58:22 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 13 09:58:22 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 13 09:58:22 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 21 15:10:44 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 21 15:10:44 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 21 15:10:44 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 21 15:10:44 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 21 15:10:44 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 21 15:10:44 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 21 15:10:44 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 23 18:42:33 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 23 18:42:33 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 23 18:42:33 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 23 18:42:33 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 23 18:42:33 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 23 18:42:33 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 23 18:42:33 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 24 14:22:58 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 24 14:22:58 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 24 14:22:58 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 24 14:22:58 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 24 14:22:58 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 24 14:22:58 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 24 14:22:58 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 24 14:36:11 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 24 14:36:11 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 24 14:36:11 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 24 14:36:11 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 24 14:36:11 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 24 14:36:11 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 24 14:36:11 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 24 21:44:16 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 24 21:44:16 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 24 21:44:16 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 24 21:44:16 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 24 21:44:16 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 24 21:44:16 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 24 21:44:16 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 25 14:50:36 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 25 14:50:36 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 25 14:50:36 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 25 14:50:36 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 25 14:50:36 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 25 14:50:36 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 25 14:50:36 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

Nov 25 16:28:43 dsl081-050-234 kernel: BIOS-provided physical RAM map:

Nov 25 16:28:43 dsl081-050-234 kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Nov 25 16:28:43 dsl081-050-234 kernel: ide0: BM-DMA at 0xe000-0xe007, BIOS s ettings: hda:DMA, hdb:pio

Nov 25 16:28:43 dsl081-050-234 kernel: ide1: BM-DMA at 0xe008-0xe00f, BIOS s ettings: hdc:DMA, hdd:DMA

Nov 25 16:28:43 dsl081-050-234 kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Nov 25 16:28:43 dsl081-050-234 kernel: /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >

Nov 25 16:28:43 dsl081-050-234 kernel: ide1 at 0x170-0x177,0x376 on irq 15

root@dsl081-050-234:/home/alvaro #
```

---

### Post by aysiu on 2005-11-25
Just some forum stuff:

1. You originally linked to [a separate HTML page with the output of a command](http://www.angelfire.com/ak5/hitman47/shit.html). I've edited your post so that it contains the output in an easy-to-read format. Please take a look at your post and see what code I used to do this.

2. I moved this from Community Chat to the appropriate support forum. This has quickly turned into a real support issue, not just discussion.

---

### Post by poptones on 2005-11-26
rhizome, do you have a live cd? 

Earlier in the discussion it sounded as if you were prepared to wipe everything out and start over. If you have everything backed up and are prepared to do that it would be worth your while to do some diagnostics on your hard drive before proceeding. 

Littlesweth, it's not the age of the wiring in itself, but the way things tend to age. for example, an old breaker box can have corroded ground connections which allow the neutral to "float." This can result in surges on the line that no 20 dollar surge supressor can remove. 

Yes, salt air plays hell with everything - it's not just the corrosion but salt is also conductive. Of course, in the northern climates the stuff spewed into the air by kerosene heaters can also work over electronics.

---

### Post by Rhizome21 on 2005-11-26
i requested the ubuntu breeze 5.10 live cd. I guess that will take weeks to arrive. :P

---

### Post by poptones on 2005-11-26
OK... well, if you get a live cd between now and then, post here and we'll see if we can get your system healthy.

Is your machine plugged into a surge supressor? If so, where did you get it and how much did it cost?

---

### Post by Rhizome21 on 2005-11-26
my system is not plugged to a surge protector.

---

### Post by teaker1s on 2005-11-26
the joys of no surge protection I lost a pc to that because of thunder that also killed a few other things in the house.
if you of your friend have internet access just go to ubuntu webpage and download and burn a copy yourself of live cd.

---

### Post by poptones on 2005-11-26
In an old house a surge supressor is a wise investment - but not one of those $4 wal-mart surge supressors. Get a real surge supressor that comes with a warranty for your equipment, like a good Belkin. 

My system lives on a UPS I purchased from computer geeks for twenty five bucks. The battery is pretty much dead, but it still helps keep the pc healthy.

---

### Post by gbond13 on 2006-04-23
I have a slightly different problem, not as severe but still a problem. I run a dual-boot system -- Ubuntu and XP Media Center Edition. This works fine for a couple of months then the system-boot selector (GRUB) gets flakey. I really don't want to go back to a Windows-only home office. The only long-term solution is looking like setting up a Linux-only computer and cutting it into my network. Talk about space waste.

---

### Post by A2A on 2006-08-19
Rhizome21: Have you tried PCLinuxOS?  D/load the Junior Version of 0.93a and run the live CD.  I'm pretty sure you will like it enough to install it :-)
Here is a link to their website: [http://www.pclinuxos.com/news.php](http://www.pclinuxos.com/news.php)

It's a relatively new distro, and not that well known either.  I installed it on my mom's notebook after she lost her XP serial.  She can barely tell the difference she says!  

My personal experience with it is that it runs faster and smoother.  We had no issues with it at all.  I loaded the Live CD and looked around, then just hit "Install" and took it from there.

Regards,

---

