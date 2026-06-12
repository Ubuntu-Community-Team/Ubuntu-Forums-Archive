---
title: "Unable to mount WD Passport 1TB (but can access via testdisk). Easy solve?"
date: 2018-03-21
forum: Hardware
---

### Post by drtombrown on 2018-03-21
Hi, my Ubuntu PC lost power while it was connected to my WD Passport 1TB external drive. I am unable to mount the drive successfully again in Ubuntu or Windows and get the following error message window in Ubuntu:

> [I]Error mounting /dev/sdb1 at /media/[redacted]/My Passport1: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/[redacted]/My Passport1"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details[/I]


*Note: I [redacted] my username in the error message above*

**Some more notables:**


[LIST]
[*]I am unable to access the drive in Windows as well however it will show up as a drive letter (H). I get an, "i/o error message" in Windows. 
[*]I attempted chkdsk /f within windows however the drive cannot be accessed due to the "i/o error" fault. 
[*]The drive still spins and there are ***no*** clicking sounds' or other noticeable anomalies I can observe in addition that tells me this is a complete drive failure. 
[*] I tried using another USB cable and still cannot mount the drive. 
[*]I assume that the drive was busy reading/writing when the pc lost power and has become corrupted in some way (?) 
[*]**testdisk: **I can access the contents of the drive within Ubuntu/Terminal using:

[I]sudo testdisk
[/I]
Steps I took in testdisk:[I] Selected the drive from list of drives > Analyse > Quick Search > 'Highlight the partition' > pressed 'P' on keyboard to list the contents of the partition

[/I] 
[*]From the steps above, I was able to copy many files off the drive and back onto my pc. Many files failed to copy over. 
[*]Accessing the drive contents via testdisk tells me that the platters and head are okay. Again, I was able to transfer some data off the drive but had some files fail to copy over (example: 40 of 50 files will copy 'okay' and '10' will fail) 
[*]**MP4 file issues:** I have many mp4 files that now have the extension *".mp4:xdg.origin.url" * 
[*]Many of these mp4's are game videos I downloaded off Xbox Live via xboxdvr.com. Changing the extension back to mp4 does not work. 
[/LIST]

Can anyone assist me further on this issue? Obviously, I'd like to fully recover the data first then salvage the drive (if possible). The fact that I could still access it's contents for the most part gives me some hope. If best case scenario a hardware failure prevents the drive from being mounted, are there alternative methods similar to testdisk where I could access the full contents of the drive? 

Any help would be appreciated!

---

### Post by oldfred on 2018-03-21
Does testdisk show backup PBR or BS boot sector matchs. NTFS has back up.

 If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
Rebuilding An NTFS Boot Sector On An NTFS Partition

---

### Post by drtombrown on 2018-03-21
> **oldfred said:**
> Does testdisk show backup PBR or BS boot sector matchs. NTFS has back up.

 If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
Rebuilding An NTFS Boot Sector On An NTFS Partition

Thanks for the link. I have some hope perhaps.

Could you instruct me on how best to answer your question? I am a total noob when it comes to testdisk. In terminal, I have the following options under testdisk:
[INDENT] 
[Analyse]
[Advanced]
[Geometry]
[Options]
[MBR Code]
[Delete]
[Quit]
[/INDENT]

How to proceed?

---

### Post by oldfred on 2018-03-21
I do not have any NTFS partitions, so do not remember how to drill down to get to this screen.
I thought it was on the details of testdisk's own instructions.

---

### Post by #&amp;thj^% on 2018-03-21
pardon the drive by but select the** [Advanced]**>>> select your NTFS partition, choose Boot, then Repair MFT. TestDisk will compare the MFT and MFT mirror (its backup). If the MFT is damaged, it will try to repair the MFT using the backup. If the MFT backup is damaged, it will use the main MFT.

---

### Post by drtombrown on 2018-03-21
Here's the main contents of the testdisk terminal window under your instructions @1fallen:

> Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121597 255 63
     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS              0  32 33 121597  37 40 1953456128

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

Should I proceed as instructed?

---

### Post by oldfred on 2018-03-21
That says BS are identical, and valid. So unless you modified BS by installing grub twice to boot sector it should be good. We have seen where users install grub to a BS or partition boot sector and damage NTFS partition. But then BS are not identical. Testdisk will show grub in BS as valid.

So no repair of BS should be required.

Thanks, 1fallen for knowing details on getting to Boot Sector screen.

---

### Post by drtombrown on 2018-03-21
> **oldfred said:**
> That says BS are identical, and valid. So unless you modified BS by installing grub twice to boot sector it should be good. We have seen where users install grub to a BS or partition boot sector and damage NTFS partition. But then BS are not identical. Testdisk will show grub in BS as valid.

So no repair of BS should be required.

Thanks, 1fallen for knowing details on getting to Boot Sector screen.

Would it hurt any to do a repair anyway just to see if the drive could be mounted? I am uncertain what the most logical next step is at this point. Suggestions?

---

### Post by #&amp;thj^% on 2018-03-21
I have to strongly agree with oldfred No repair should be necessary.
**Important Note**: At this point i would take it to a certified professional repair shop. (Mother Boards Circuit Boards seemed fragile from power spikes or outages)
If it was a My Book the repairs are a bit easier, I have done this on a handful of My Books, but sadly the Passport's are a different animal.:( I don't even think there are sellers for the My Passport parts)
[https://www.youtube.com/watch?v=PkAMcMA_d3Q](https://www.youtube.com/watch?v=PkAMcMA_d3Q)
[https://www.youtube.com/watch?v=xpwt13uDDZo](https://www.youtube.com/watch?v=xpwt13uDDZo)

---

### Post by oldfred on 2018-03-21
The link says testdisk has a repair MFT button as well as the repair BS. 
And it has suggestions for commercial Windows software (not free) that may work.

I have seen suggestions here for one of the testdisk suggestions, GetDataBack.
Only click on link in testdisk site as there is a similarly named app (without caps) that is a scam.

---

### Post by drtombrown on 2018-03-21
Thank you for all the suggestions!

So it seems like it's a corrupted filestystem and not a full hardware failure (?)

I am attempting to copy over as much files as I can through testdisk and curious if you know if there is another app or method available that can access the passport outside of testdisk?

---

### Post by #&amp;thj^% on 2018-03-21
I have used this as oldfred points out " GetDataBack" found here: [http://www.runtime.org/gdb.htm](http://www.runtime.org/gdb.htm)
You will get to see if the price is worth it for Free but to recover you will have to pay.(Reasonable Pricing)
The others I just don't have first hand experience with to say. 
Best of Luck! ;)

---

### Post by drtombrown on 2018-03-21
Thank you all for the wonderful help. My stress levels have decreased substantially b/c of your assistance! I'll post a follow-up. Meantime, fingers crossed. [-o

---

