---
title: "Recommendations sought for salvaging hard drives"
date: 2020-07-02
forum: Hardware
---

### Post by Sour Mash on 2020-07-02
Hi, I find myself with a handful of big old SATA drives (1 and 2 TB) that all seem to be in some way misbehaving. Some have data on them that I'd like salvage, nothing I want to spend money on salvaging but stuff that would be missed if it were gone for good.
I'm never one to throw away anything that is useful so I was wondering if I could get some suggestions as to what tools I would need to test, fix, salvage data from these old drives. Errors include being recognises when lugged in but unable to mount, not showing up at all when plugged in but the drive is spinning, doing absolutely nothing when plugged in (that one's probably a lost cause). So, before I throw them out, what should I try and in what order please?
I've got access to Ubuntu 20.04 and Windows 10 machines.

Thanks

J

---

### Post by Autodave on 2020-07-02
The only trick that I have found that works maybe 5% of the time is to refrigerate them for a few hours and then try to mount them and copy anything that is available on them.

---

### Post by oldfred on 2020-07-02
If not seen in UEFI/BIOS, no system can repair or recovery it.

So first is drive seen in BIOS?
If not check all connections, try different cables, ports, then maybe Autodave's suggestion. Also see if drive not spinning tap with rubber hammer or something to see if you can get to start rotating. But those suggestions are often a one time start of drive. Or get whatever you can as it may not ever work again.

if drive comes up, is it shown in Disks?
 In upper right corner of Disks is Smart Status. All I know is good/bad that it reports but others understand some of the details. 
[https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1](https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1)
[https://ubuntuforums.org/showthread.php?t=2445397&page=2&p=13965854#post13965854](https://ubuntuforums.org/showthread.php?t=2445397&page=2&p=13965854#post13965854)

The standard suggestion if you can get it to mount, is to copy drive to another drive and work on the image.
Full image backup
GNU ddrescue (packaged as gddrescue, though once installed the command is "ddrescue") 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://ubuntuforums.org/showthread.php?t=2305215&p=13401824#post13401824](http://ubuntuforums.org/showthread.php?t=2305215&p=13401824#post13401824)

---

### Post by Sour Mash on 2020-07-02
Thanks for your thoughts guys.
I've got one up and running, it was a permissions things with that one, funny though it was the least likely to be a runner as it came out of a NAS box that got dropped down the stairs! That one will live again I think, I'm running it now to see if it will fall over or not :-)

On to the next one, this is a 2TB Seagate that was OK until I had a dodgy 20.04 installation experience - system kept turning itself off like a power failure, ran fine off a live CD. The drive now powers up and you can hear it running, sounds fine, but doesn't show up in Disks - what else can I use to probe for life?

---

### Post by Sour Mash on 2020-07-02
Hang on, No2 has just sparked into life. It was making read/write sounds then popped up in Disks, I literally did noting but let it sit there for a few minutes. Now I can see the partitions and I am salvaging files. This is too easy, it can't last. The next one, No 3 is an unknown, a Western Digital 1TB drive. This one is pretty much dead I think.

---

### Post by &amp;wP*!) on 2020-07-02
dd might be helpful as well.

---

### Post by Sour Mash on 2020-07-02
> **pencuse said:**
> dd might be helpful as well.

DD? Sorry, what's that please?

OK, I was premature with the question sorry - [https://opensource.com/article/18/7/how-use-dd-linux ]("https://opensource.com/article/18/7/how-use-dd-linux")

---

### Post by Sour Mash on 2020-07-02
I could do with some pointers on how Linux handles boot discs - I think I have old boot disks trying to all boot together as when I run the system with more than one HD it either doesn't boot at all or takes ages to boot - unplug one and it's fine. Will a format cure that?

---

### Post by TheFu on 2020-07-02
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[LIST]
[*]ddrescue - dd that keeps trying on failed sectors.
[*]testdisk / photorec
[*]badblocks
[*]smartctl - know what your HDDs think of themselves
[/LIST]
are the tools  i use.

Spinrite can be used for 2TB and smaller disks but badblocks can be setup to do the same stuff.

---

### Post by kurt18947 on 2020-07-02
I've had some old hard drives that were no longer useful. I took them apart and salvaged the magnets. They're some strong magnets, mine are kidney shaped and about 2 mm thick. I use some to hold tools and fixtures to machines.

---

### Post by Sour Mash on 2020-07-03
That's interesting, when I run out of luck I'll take one apart. So far I'm doing OK with 2 useable drives out of three I've worked on - there's stuff on this current one I didn't know I had, lots of iot so I am now searching for places to put it! Also found I didn't have any suitable cables to plug these things into the tower case I have, so waiting on Amazon now :-)

---

### Post by Yellow Pasque on 2020-07-03
> **Sour Mash said:**
> The next one is an unknown, a Western Digital 1TB drive. This one is pretty much dead I think.

As oldfred asked, does it show up in the BIOS/EFI?

---

### Post by Sour Mash on 2020-07-03
I'm not entirely sure what you mean?

---

### Post by TheFu on 2020-07-03
If you only have bare HDDs, you can get a USB3 "dock" for about $20-$30 that lets us drop a SATA HDD into a slot and will be seen like any other USB3 HDD. When done, power off the dock and pull the HDD out, then drop in another.  Infinite storage via a single, cheap, dock. I have 1 dual-dock and 2 single docks (3 computers). The Dual-dock can clone a HDD from slot A --> B without any computer connected.

Of course, having HDDs internal will be faster since the SATA protocol is more complete than the USB_storage protocol.  For data recovery needs, SATA connectivity is important, but they do make eSATA+USB3 docks. Of course, you'll need a proper eSATA external port. A case  2-4 plug converter that connects each eSATA plug to interior SATA plugs (1 for 1) is $9.  If the dock is dual, you'll need a special eSATA-pm (port multiplier) card. Those are about $40, but only specific models work with Linux.

---

### Post by mIk3_08 on 2020-07-03
You can also try hdd/ssd sata disk enclosure if you have one. It might help. But you must need to know that the drive shows up in BIOS.

---

### Post by Yellow Pasque on 2020-07-03
> **Sour Mash said:**
> I'm not entirely sure what you mean?

Go into your BIOS/EFI/System Setup. You need to hit a key (often 'Del') when the system starts. Read your mobo/system manual if the POST screen doesn't tell you.
Does the hard disk register as a bootable option?

---

### Post by Sour Mash on 2020-07-04
> **TheFu said:**
> If you only have bare HDDs, you can get a USB3 "dock" for about $20-$30 that lets us drop a SATA HDD into a slot and will be seen like any other USB3 HDD. When done, power off the dock and pull the HDD out, then drop in another.  Infinite storage via a single, cheap, dock. I have 1 dual-dock and 2 single docks (3 computers). The Dual-dock can clone a HDD from slot A --> B without any computer connected.

I've got one of those that I've been using, it seems to be the way forward as I can easily swap out drives. It seems to accept most drives, I bought it a while back when I had to clone some laptops, made life easier.

It didn't come with any instructions and has a big red button on the front, I so want to press it!

---

### Post by Sour Mash on 2020-07-04
Progress so far, all the drives are alive, even the one i thought was dead came to life and is working! Now the data salvaging is proving tricky. I've put the fullest drive in one of my machines and connected it to the motherboard but it gave me all sorts of issues when I booted the machine. Turns out there was a boot flag on a small partition on it. Now fixed but it's slow progress salvaging the files - I get a lot of recompiling errors - what I'm doing is copying the data off the old drives, onto a new drive so I can then format the old one and run a deep scan/repair - fsck and badblocks.
So, all i'm doing at the moment is to 'move to' the new drive but is there a better/faster way? I want something that will move what it can and automatically skip over what what it can's leaving me the troublesome (probably damaged) files so I can figure out what to do with them (most may be replaceable). Mos of this stuff is music, video and picture files.

---

### Post by Sour Mash on 2020-07-05
Well I'm quite amazed, after a few days of messing about, all these drives seem to be working, yes they have the odd bad segment and yes the one that fell down the stairs looks like it's been through the wars but they all seem to have held their own. I did have trouble with permissions on them but now I've figured out how to fix that I can get at the files on them.
I am having some trouble scraping the data off one of them, lots of errors when I try and move files from it onto another known good drive. The errors seem to mainly be the nonsensical "cannot move as directory not empty" and something about files being too big to reassemble - I'm just skipping through them and will see what's left over once I've moved the bulk - will try and capture the exact error messages and post later.
Two of teh drives are now on my Windows machine to serve movies - I may try and make some sort of movie file server with this old machine, might be a good use for all this storage!

---

### Post by Sour Mash on 2020-07-05
I get "error splicing file:Input/output error"

---

