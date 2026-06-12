---
title: "Problem with GPT drive on Ubuntu GNOME Remix 12.10"
date: 2012-12-23
forum: Hardware
---

### Post by quantenmetz on 2012-12-23
Hello all,

I have persistent problems getting my new 3TB HDD (Seagate Barracuda ST3000DM001) running on my Windows 7 64bit Professional / ubuntu GNOME Remix 12.10 64 bit dual boot system. These are all the details, even though I am pretty sure the problem is not distribution-specific.

This is what is going on: I started out partitioning the drive using Ubuntu's gparted. I created a GPT partition table, a big NTFS and a smaller ext4 partition. Everything worked fine and I could use the drive straight away - no surprises there.
However, booting Windows to check, I found the drive missing. The Windows partitioning tool told me the drive was "unitiliazed" - it asked me to create a MBR or GPT table. 
So I let Windows do its work, getting the drive running straight away. Booting Ubuntu again, now parted reported the drive as "unallocated space". I checked gdisk, and it tells me that there is an MBR present but no GPT info, even though Windows created a GPT table and a 3TB NTFS partition. 
Since then I spent hours of switching back and forth, I used gdisk to --zap remaining GPT and MBR info, I created partition tables by hand. Once I got an invalid setup where the drive could be read from Windows AND Linux at the same time, however reporting different partition layouts. 
WHAT IS GOING ON? Right now I have the drive usable in Windows, configured with just one 3TB NTFS partition and performing like it should - but still showing as "unallocated" space in parted and listed as an MBR drive in gdisk. I have 2 other HDDs and a SSD running, all sharing NTFS and ext partitions and all of them running fine under both systems.

I am stuck now... Please help.


Cheers

Q.

---

### Post by oldfred on 2012-12-23
Windows only boots from gpt drives with UEFI. Is your computer new enough to have UEFI not just BIOS?
Windows 7 will read gpt data partitons, but XP cannot even see a gpt drive.

I have my old XP on a MBR drive and use gpt on several other (smaller) drives with out issue. My Ubuntu can see the XP, but XP never saw Linux parititons any way so that did not matter to me.

Windows often does nasty things to gpt drives. When it installs it converts to MBR, but leaves the backup gpt partition table at the end of the drive. Then Linux tools see both MBR & gpt and get confused. Usually gdisk or fixparts required to repair.
Windows also may convert a large drive to MBR but then it is only 2.2GB not your 3GB.

If you want Windows and only have BIOS, probably best just to have another smaller drive. I prefer systems on different drives.

---

### Post by quantenmetz on 2012-12-23
Hey oldfred,

Thanks for the reply. I don't want to boot from the drive. My OS's are installed on the SSD. I just want to use it as data drive, but somehow Linux and Windows don't understand each other's definition of a GPT table.

The drive is now definitely defined by a GPT table, I have a working (under Windows) 3TB partition on it. What does confuse gdisk to think it sees a MBR drive? Why do I see "unallocated space" in parted?

Cheers

Q.

---

### Post by oldfred on 2012-12-23
If you formatted with Windows, does it see the entire 3TB?

With the new rounding for SSDs & 4K drives there often is 1MB unallocated shown at various places. Before the rounding was such that it was under 1MB and space was there, just not shown as it only shows larger spaces.

Post this. If you do not have gdisk download from repository or rodbooks site. Change to sdb or sdc as appropriate.

       sudo parted /dev/sda unit s print
sudo gdisk -l /dev/sda

    
       GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by quantenmetz on 2012-12-23
Hello again oldfred,

```
sudo parted /dev/sdd unit s print
Error: /dev/sdd: unrecognised disk label
```

and

```
sudo gdisk -l /dev/sdd
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sdd: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): C568D91E-09F2-4B37-85B2-419A8A72CE38
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 5860533101 sectors (2.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name

```

Windows thinks the drive has a GPT table (it created it itself...) and uses it flawlessly with one 3TB NTFS partition...


Cheers

Q.

---

### Post by oldfred on 2012-12-23
I am somewhat surprised if Windows created a gpt partition table that gdisk does not actually see something.

I am not sure sure I would have one very large NTFS partition. How long does chkdsk then take when you have issues?

I follow this poster's logic that every large drive should have an operating system.

       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.
    I now have SSD with main install but still keep working Ubuntu installs on every drive.

---

### Post by quantenmetz on 2012-12-24
> I am somewhat surprised if Windows created a gpt partition table that gdisk does not actually see something.
Well, yes, so am I...
The only "solution" I can think of right now is turn the drive into a MBR disk with 2 <2TB partitions. Can I do that without losing the data?


Cheers

Q.

---

### Post by oldfred on 2012-12-24
You cannot change to MBR and still use the entire 3TB. MBR limits are the total size of a drive cannot be over 2.2TB.

Testdisk works with gpt drives, I am now curious if it shows it correctly or not.

Testdisk is in the repository so you can easily download it.
Choose efi/gpt even if not UEFI to use gpt partitions.

       Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by quantenmetz on 2012-12-25
Hey oldfred,

We had this thing called "Christmas" here, that caused some inevitable delay. I hope your're still following the thread, though.
I installed testdisk and it tells me 

```
Bad GPT partition, invalid signature.
```

Ain't that great?

Then I went on and did the "quick search" and found something very interesting: Apparently, the old setup of one large NTFS and a small Ext4 partition still lingers somewhere on the drive, even though I used gdisk to --zap it:

```
P MS Data                     2048 5438576639 5438574592 [Barracuda]
P MS Data               5438576640 5860532223  421955584 [barracudaExt4]
```

So, what do I do now? I really want to avoid re-installing everything on that disk if this is somehow possible...


Cheers

Felix

---

### Post by oldfred on 2012-12-25
We are having Christmas, I just popped in as I was copying some photos of kids and new grandson to computer.

Does testdisk show old partitions and offer to let you recover any?
Otherwise gdisk is usually the tool for repairing gpt drives.

---

### Post by quantenmetz on 2012-12-25
Hey,

well, I started a "deep scan" with testdisk... It seems to find quite some inconsitencies.
I don't know what is the best way to proceed here. I just want a clean partition table matching the current data layout Windows believes to see (1 3TB NTFS partition) WITHOUT losing the data on the drive.

How do I get there?

Cheers

Q.

---

### Post by oldfred on 2012-12-25
To me all the inconsistencies are scary, I would would backup everything. Any time there are issues there is no guarantee that you will not lose data.

Are you able to know exact sectors of start and end of gpt table? 
One of the repairs procedures on the gdisk site was remove partitions and then reset to correct size. As long as you do not reformat and do not change size, data is still there. But if locations with file tables get overwritten or changed then you lose data, so always some risk.

---

### Post by quantenmetz on 2012-12-25
Ok, thanks... but how exactly would I go on?

Backing up will take ages ofc, but I guess that I can do tomorrow. Can't I somehow back up my partitition table data that I have now to be able to switch back to the broken status quo in case of major catastrophe?

I know that the NTFS partition is supposed to start at block 2048, and the last sector should be the last of the drive I guess. Isn't this information sufficient to get a valid GPT table without thrashing my data?

Cheers

Q.

---

### Post by oldfred on 2012-12-25
While gdisk complained, can you use the advanced features of gdisk?

       [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
    
       [http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
    
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)

---

### Post by quantenmetz on 2012-12-28
Hey,

I'm running around in circles. I used gdisk and testdisk extensively, tried all sorts of backup and repair functions. Basically, the partitition table was a mess, the backup was "corrupted", I had "wrong number of bytes per sector" warnings from testdisk flying around ... 

In the end I got bold  and noted down the sectors of the existing partitions and backups, deleted the partitions with gdisk and created a fresh GPT with gdisk. I played around with new partitions.

Now it gets interesting: I created a new GPT partition (Microsoft Basic Data) matching the starting sector of what I noted down from the Windows-readable, but Ubuntu-unusable initial setup. This lead to a **fully readable NTFS partition in Ubuntu with my actual data present**, with gdisk, parted and testdisk reporting a valid structure.

Of course, this is exactly where the joy ended: **The drive is not redable under Windows** anymore, the partitioning tool tells me it is unitialized and wants to create a new GPT table. WARGH!!!!! Now I have the same problem reversed! How can I get a valid setup that even Windows understands? Do I have to create some secret MS-compatible system partition at the beginning of the drive or something? I noticed there are roughly 120 MB of free space (in the partitioning that Windows7 did "for" me)...


Cheers

Q.

---

### Post by oldfred on 2012-12-28
I have not seen a lot of users with 3TB drives but I do not remember anyone else with this type of issue.

Is NTFS partition formatted as NTFS with testdisk? Or is it just created by gdisk and not formatted?

I know testdisk creates XP type NTFS partitions with BIOS and Windows has a different type of NTFS partition for Vista/7. The boot sectors are different as the XP type says to boot with ntldr and Vista/7 says use bootmgr and some other internal details (even if not a boot partition). 
But XP does not even work with gpt so is that part of the issue?

I do not have a NTFS partition in my gpt drives, but can you use testdisk and get to this screen and use the dump command. I had used a Windows 7 repair flash drive to fix my XP install and it created a Windows 7 PBR. I had to scroll to the bottom of the PBR but could see the text ntldr in my backup and bootmgr in the "new" PBR. I then recovered back to XP PBR.

Second screen is top of PBR, but you need to scroll down to bottom to see the text. I did not save that page.

---

### Post by quantenmetz on 2012-12-28
well... I'm giving up.

I spent days on this now and I am at a loss.
[LIST]
[*]Whenever I let Windows 7 64bit 'initialize' the drive, it works under Windows but gdisk reports GPT **not present** and testdisk says **Bad GPT partition, invalid signature**.
[*]When I create the table by hand with gdisk and set the start sector to the correct starting sector of my once-working NTFS partition, I can read the data from Linux but Windows tells me I have to initialize the drive. 
[/LIST]
It's a ******* circle. I did some reading on what Windows expects from a GPT drive, and apparently there HAS TO BE a Microsoft Reserved partition (MSR) of 128 MB present (which perfectly matches the empty space before the NTFS partition, ...). But also creating this by hand does not help Windows to read the damn thing. And in any case, if the GPT information Win7 creates when "initializing"  the drive is NOT EVEN READABLE by any of the tools under Linux, something is foul.

---

### Post by quantenmetz on 2012-12-28
Hmm.... there is one more piece of information that I have been ignoring so far... but I can't make sense of it:

Whenever I use testdisk, regardless of the current state of the GPT table, as soon as I enter the quicksearch utility **it keeps finding a NTFS and a Ext4 partition**, corresponding to my very first partitioning attempt from gparted (and with wrong starting sectors...).

Where does this information come from??? It keeps finding these two partitions , regardless if I delete the GPT info, blank out MBR, --zap the GPT stuff, create new tables ... Could this be the root of all evil?

Cheers

Q.

PS: All the help is very much appreciated, even though my appreciation might be well-hidden under a pile of frustration right now...

---

### Post by oldfred on 2012-12-28
I do not know if that is an issue with Windows. Testdisk finds old deleted partitions to let you recover them, sometimes. Once repartitioned, the deleted partitions should not be seen by any operating system or most partition tools.

I thought the MSR was only required with bootable systems, not just a data partition. 

There are also some new gpt partition internal type IDs.
       New code for NTFS gpt partition
[http://ubuntuforums.org/showthread.php?t=1822452](http://ubuntuforums.org/showthread.php?t=1822452)

    
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by michel30 on 2013-01-15
This looks like similar to this: read and weep :cry:

[http://hardforum.com/showthread.php?t=1632902](http://hardforum.com/showthread.php?t=1632902)

So you might want to update to the latest version of Intel Rapid Storage Technology driver

---

