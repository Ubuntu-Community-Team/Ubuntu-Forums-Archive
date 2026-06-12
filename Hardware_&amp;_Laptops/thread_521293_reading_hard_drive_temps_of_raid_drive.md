---
title: "reading hard drive temps of raid drive"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by crhumber on 2007-08-09
I have two sata hard drives connected in a raid 0 setup and I'm trying to get hddtemp set up to read the temps.  Does anyone know if hddtemp can read the temperature correctly?  Currently I'm getting an error saying that there is no sensor present.  I've also tried reading the temp using the temp3 from lm-sensors output, but I'm getting a reading around 124 C.  Is temp3 from lm-sensors necessarily a hard drive temp or is there something else it can be??  Any help is appreciated

---

### Post by kidders on 2007-08-10
Hi there,

Every drive is different, I'm afraid. The numbers reported by sensors & similar hardware tend to be completely arbitrary, because every manufacturer has its own ways of doing things.

**hddtemp**
This tool works by reading SMART information (which is essentially a meaningless list of numbers that normally conforms to no established standard) off your hard drives. To make any kind of sense of them, you should ...[LIST]
[*]Check whether hddtemp already knows about your particular devices.
[*]See if someone else in the world has already figured out which numeric fields correspond to drive temperatures.
[*]Find out if your hardware manufacturers have published details of their SMART implementations.
[*]Take a look at hddtemp's debug information and see if you can figure out what's what on your own.[/LIST]**lmsensors**
> **crhumber said:**
> I've also tried reading the temp using the temp3 from lm-sensors output, but I'm getting a reading around 124 C.There's no way for anyone to know what's going on here except you, really. Similar to hddtemp, lmsensors simply regurgitates values reported by your hardware, but for them to make sense, you'll need some additional information...[LIST]
[*]Which sensor fields contain real information, and which don't. For instance, your hardware may not be capable of reporting all the information supported by lmsensors.
[*]What the baseline values of each sensor field are. For instance, a CPU temperature of 0 degrees C may well be reported as -123 by your hardware.
[*]What multipliers to apply. For instance, if "-123" is 0C, does that really mean "-113" is 10C?[/LIST]Just like hddtemp, lmsensors' config files may already be equipped to handle your hardware ... then again, maybe not ... so you might have to do some digging to turn reported data into useful information.



The short answer to your questions is ...[INDENT][SIZE=3][COLOR=SeaGreen]*shrug*[/COLOR][/SIZE]
[/INDENT]... but I thought you might appreciate a little explanation as to *why* it's hard to help people in your position. Whenever I buy new hardware, one of the first things I do is dredge the web for details on my new sensors. After I figure out the answers to questions like "What does temp3 refer to?" once, I put the configuration files aside somewhere safe (along with things like my xorg.conf), so I never have to do it again.

---

### Post by crhumber on 2007-08-10
Thanks for the reply.  I appreciate the information...I guess I'll have to look into my hardware a little more!

---

### Post by kidders on 2007-08-10
Yeah, it's kinda irritating. Web searches are great ways of tracking down work done by other owners of your hardware. When searching, try to be specific. For instance, on my box...
```
# hddtemp -D /dev/sda

================= hddtemp 0.3-beta15 ==================
Model: ST3500841AS

field(1)         = 0
field(3)         = 0
field(4)         = 135
...
...
```... the "ST3500841AS" is exactly what I'd need to find what I wanted. For lmsensors, motherboard model numbers often lead you to the information you're after.

**Edit:** Incidentally, there's no harm in posting your vendor/model information here ... someone may just happen to have exactly what you want sitting in their /etc directory!

---

### Post by crhumber on 2007-08-11
My raid disk is setup in the bios.  Ubuntu and any other OS recognize it as "External Disk 0" since it is a raid set.  Its a RAID 0 consisting of two Western Digital Caviar SATA 160 gb hard drives, model number "WD1600YS".  I'm not sure if the model number even matters here though since it won't be recognized as such.  The motherboard is an ASUS P5B Deluxe and I'm using the EZ RAID feature.  If anyone sees this and knows how to make lm-sensors see my hard drive sensor let me know!! thanks

---

### Post by kidders on 2007-08-11
Hmm... I never use those BIOS RAID gizmos, so I don't know a huge amount about them. Just to make sure tools like hddtemp will work properly for you, could you run lshw? On my box, for instance...

```
...
...
        *-disk
             description: SCSI Disk
             product: ST3500841AS
             vendor: ATA
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 3PM12DKB
             size: 465GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
...
...
```What I'm hoping is that, somewhere in the pages & pages of output lshw generates, your individual disk drives will be listed, and they'll have sensible "logical names" that hddtemp can use to access them.

I have hddtemp-0.3_beta15 on my box, and its database describes a number of drives that are very similar to yours. In all cases (where a temperature sensor is present), field #194 describes their hard disk temperature, so it's pretty safe to assume that yours is the same.

So, in theory, you should be able to do something like this...[LIST=1]
[*]Identify the /dev node name that directly references one of your disk drives ... not the RAID array. Imagine, for the sake of argument, that it's /dev/sda.
[*]Run **hddtemp -D /dev/sda**
[*]Remark the "Model" line, and the value of field #194.
[*]If both contain sensible values, try to find your hddtemp database. The man page may point you to it ... or you could try **locate hddtemp.db**
[*]Open the file, and add something like the following to the end...[/LIST]```
"WD1600YS" 194 C "My Pretty WD"
```Substitute the correct "Model" string (I just guessed it).

Again, for the sake of example, let's assume that hddtemp now knows how to read the temperatures of all your hard disks, and that they're called things like /dev/sda, dev/sdb...

```
$ hddtemp /dev/sd?
/dev/sda: ST3500841AS: 26 C
/dev/sdb: ST3500841AS: 28 C
/dev/sdc: WD2000JS-22MHB0:  24 C
```That's the theory, at least! If you can manage to get that far, you might think about creating a tarball of irritating config files, and add your hddtemp database to it, so that the next time you find yourself installing Linux (any Linux) on the same hardware, you can reconfigure it instantly with a single command.

In terms of your sensors, there seems to be a good deal of information around regarding similar motherboards, so it looks like you're in luck. :-)

---

### Post by crhumber on 2007-08-11
Here is the output I get from "hddtemp -D /dev/sda":
================= hddtemp 0.3-beta15 ==================
Model: External Disk 0

field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146
field(10)        = 146

This seems odd that field(10) is repeated so many times.  I tried adding the line
"External Disk 0"    194 C  to my hddtemp.db file, but with no luck.  I'll definitely have to look into my motherboard a little more.  I've always thought it odd that my raid is recognized as a external disk.  thanks a bunch for all your help so far

EDIT: One thing I just picked up on in your post is that you said to determine the /dev node for one of the hard disks, but as far as I can tell Ubuntu cannot tell that I actually have two hard drives.  This is probably what is causing the problem.  Hopefully there is a fix, but I don't know.

---

### Post by kidders on 2007-08-12
> **crhumber said:**
> EDIT: One thing I just picked up on in your post is that you said to determine the /dev node for one of the hard disks, but as far as I can tell Ubuntu cannot tell that I actually have two hard drives.  This is probably what is causing the problem.  Hopefully there is a fix, but I don't know.Hmm... If your motherboard won't show your individual RAID components to your operating system, hddtemp can't be used, I'm afraid. Drat.

I was aware of a number of drawbacks to using on-board RAID implementations ... I guess we just found another one. :-(

---

### Post by crhumber on 2007-08-12
I was afraid of that.  Thanks for all the help, though!

---

### Post by kidders on 2007-08-12
No problem. :-) You should have much better luck with lmsensors though.

---

