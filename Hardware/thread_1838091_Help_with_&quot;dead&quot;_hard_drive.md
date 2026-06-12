---
title: "Help with &quot;dead&quot; hard drive?"
date: 2011-09-03
forum: Hardware
---

### Post by staf0048 on 2011-09-03
This morning I woke up and my desktop would not boot past the HP boot splash.  I have two 500 GB HDD, one with Lucid and the other with Vista.  Unfortunately, the one with Lucid is the one causing the problems.  Grub 2 is on the Vista drive, but will not boot into Vista (even with the Lucid drive removed), it just gives me the "Grub Rescue >" prompt when I remove the Lucid drive.  Nothing happens when the Vista drive is removed.

Tried the rescue disk for Vista to at least get SOMETHING running, but after multiple attempts the software told me it could not fix my issue.  I was not able to get to a command prompt to run 'fix mbr' as I had originally planned - my only option as far as I can tell is graphical, with limited options.

My data is backed up, so I'm not worried about a re-format if need be, but I'm not able to access the Lucid drive what-so-ever and would like to have both drives functional, if possible.  Any thoughts/suggestions?

---

### Post by coffeecat on 2011-09-03
When you say grub2 is on the Vista drive, that means that grub is installed to the mbr of the Vista drive. However, the grub.cfg file and much of the grub code is in your Ubuntu partition on the Lucid drive, which is why you are getting the grub rescue prompt when you remove the Lucid drive.

You are quite right that you need to run fixmbr to re-install Windows booting code to the mbr of the Vista drive. If you are having trouble with the Vista disc, you can use an Ubuntu live CD to install mbr code that does the same job as the Windows mbr. Three alternative methods here:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

Boot into an Ubuntu live CD or USB. You need an Internet connection to install the application. Most people find the first, lilo, method to be satisfactory. Check that your Vista hard drive appears as sda before you run the command.

That, at least, will get you booting into Vista. However, retrieving data from your Lucid drive may be difficult if it is failing. When you are in the live Ubuntu session, open the Disk Utility app and see if SMART data is supported in your Lucid drive and, if so, what the SMART status is. That might tell us how bad a state the drive is in, if indeed it is failing. Your problems with the Lucid drive may have another cause.

---

### Post by Cope57 on 2011-09-03
There are a few solutions for How to revive a hard drive:
[LIST=1]
[*]Freeze it
[*]Drop it
[*]Hit it
[/LIST]

**_Freeze it_**

When the problem is data-read errors off the platters themselves, is to freeze the hard drive overnight (place in freezer bag).  It makes the data more *readable*, but for a one-shot deal.  If this data is critical, and you have a replacement hard drive (which, if it's a drive failure, you probably do), then you can hook up your frozen hard drive and immediately fetch the data off before it warms up.

If the problem is heat related, I would put the drive in the freezer for about 15 minutes to cool it down... sometimes this gets the drive up long enough to copy any critical files...

If this drive isn't spinning up, putting it in the freezer for about an hour will usually get the drive spinning again so you can copy needed files before the drive warms up again. The first thing you want to do is run a disk utility like Norton disk doctor or **wddiag** (if it's a western digital drive) to verify whether the drive is working mechanically or not. If it is a master boot record problem, sometimes running Fdisk/mbr will correct the problem. It could also be a virus, and a program like F-prot will look at the drive as a physical unit.

Metal contracts when it is cold.... so the platters shrink and increase the clearance for the read/write heads.


**_Drop it_**

Of course, there's always the "drop it from 4-8" onto a flat hard surface" or "smack the side of the case with the flat of your hand" approaches. Believe it or not, both techniques have worked. Rumor has it that sometimes the heads "stick" to the platters during parking/cooldown.


**_Hit it_**

As "unscientific" as this sounds, I have found that rapping the drive case a couple of times sometimes allows the drive to come up. I have had several experiences in the past like this. Sometimes the drive is having trouble "spinning up." Obviously, the drive is on its last legs but a rap on the drive case will sometimes free it to spin up. This will allow the system to boot so the data can be backed up before the drive goes into the trash...

----

There are other options...
One can also send the drive into a White Room to have them get the information off the drive, it is costly, but it is the safest way for data recovery.

Does the drive make any sounds, something like clicking or buzzing?  If so, it may indicate physical damage to the drive, and may not be recoverable.

The freezing, dropping, and hitting are last resorts to a drive which will not be used except to remove the required data.  After these techniques, the drive will most likely not work again, so only do this if you have a backup drive to move the data to.

On a freezer topic, I have had a hard drive in my freezer since May.  I have not purchased another drive yet, and I was planning on upgrading to a solid state drive. (more expensive, but no moving parts)

---

### Post by staf0048 on 2011-09-03
> **coffeecat said:**
> If you are having trouble with the Vista disc, you can use an Ubuntu live CD to install mbr code that does the same job as the Windows mbr. Three alternative methods here:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

Boot into an Ubuntu live CD or USB. You need an Internet connection to install the application. Most people find the first, lilo, method to be satisfactory. Check that your Vista hard drive appears as sda before you run the command.


This did exactly what I was looking for.  Thank you very much!

[quote=Cope57]Does the drive make any sounds, something like clicking or buzzing? If so, it may indicate physical damage to the drive, and may not be recoverable.[/quote]

The drive is completely silent, so I'm hopeful I can get it back up and running again.  Not sure what happened to it, but whenever I plug it in it kills the boot process...(?)

---

