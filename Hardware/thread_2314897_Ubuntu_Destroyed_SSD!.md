---
title: "Ubuntu Destroyed SSD!"
date: 2016-02-24
forum: Hardware
---

### Post by firstname on 2016-02-24
hi, 

System:
Win7/Ubuntu
share one "boot" SSD  via dual boot
HDD for data
second SSD  for data and software (now dead).

processor, main board, video card all that good stuff is inside the case.

What:
Copied Files to second SSD while using ubuntu.
Restarted PC used win 7. SSD i just used in Ubuntu is not readable anymore only thing I could do is formatting. Cant even chkdsk.

So... any Ideas what happened?

---

### Post by QIII on 2016-02-24
Did you copy the files to a Windows partition, or do you have a separate data partition?

---

### Post by firstname on 2016-02-24
> **QIII said:**
> Did you copy the files to a Windows partition, or do you have a separate data partition?

What do you mean by windows partition?
The unreadable SSD i talk about was just a drive. No Operating system was installed on it. I only had some software for my windows7 installed on it. 
It was NTFS if you mean that?

---

### Post by QIII on 2016-02-24
Had you hibernated Win or shut down completely?

Had you hibernated Ubuntu or shut down completely?

Did you get a message when starting Windows something to this effect:  "One or more of your disks has errors ..."

---

### Post by firstname on 2016-02-24
> **QIII said:**
> Had you hibernated Win or shut down completely?
Not quite sure what hibernated means.I read a quick explanation on wiki. So i guess NO hibernation.
Anyway, what I did was press "shutdown" in ubuntu. Then on the next Day I started the PC and choose win7. Thats when I saw the SSD became trash.

> **QIII said:**
> Did you get a message when starting Windows something to this effect:  "One or more of your disks has errors ..."
No Errors nothing. 
I just booted win7.

---

### Post by QIII on 2016-02-24
Can you access the disk from Ubuntu after fully shutting down Windows?  You may have to turn FastBoot off in your BIOS/UEFI menu to get a clean shutdown of Windows.

---

### Post by weatherman2 on 2016-02-24
Boot Ubuntu again and run this command in a terminal (Ctrl Alt t to open a terminal window).

```
sudo parted -l
```

and produce the output here.

---

### Post by weatherman2 on 2016-02-24
> **QIII said:**
> Can you access the disk from Ubuntu after fully shutting down Windows?  You may have to turn FastBoot off in your BIOS/UEFI menu to get a clean shutdown of Windows.

"Fastboot" is a Windows 8+ feature.  Windows 7 does have hibernation, and if you hibernate in Windows 7, then boot Ubuntu and write files to a partition, then resume Windows 7, the journal will not have the updated files.  But it seems like the OP did not hibernate.

---

### Post by firstname on 2016-02-24
> **QIII said:**
> Can you access the disk from Ubuntu after fully shutting down Windows?  You may have to turn FastBoot off in your BIOS/UEFI menu to get a clean shutdown of Windows.

I tried this. deactivated UEFI, or only legacy.. well i tried a few combinations 
in any case:
Ubuntu does not show the SSD

---

### Post by firstname on 2016-02-24
> **weatherman2 said:**
> Boot Ubuntu again and run this command in a terminal (Ctrl Alt t to open a terminal window).

```
sudo parted -l
```

and produce the output here.



thats the "dead" ssd

```
Model: ATA Crucial_CT256MX1 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  256GB  256GB  primary  ntfs

```

---

### Post by QIII on 2016-02-24
> **weatherman2 said:**
> "Fastboot" is a Windows 8+ feature.  Windows 7 does have hibernation, and if you hibernate in Windows 7, then boot Ubuntu and write files to a partition, then resume Windows 7, the journal will not have the updated files.  But it seems like the OP did not hibernate.

Quite.  I should have put a space in there:  "Fast Boot", aka "Quick Boot", etc, which are OEM terms for hardware BIOS options that play to Win 8's illusion of booting quickly.

---

### Post by weatherman2 on 2016-02-24
OK, so your HDD is not connected - just the SSD that you can no longer read?  It shows just one NTFS partition, which is normal if you used it in Windows.

You mentioned formatting the SSD.  Did you format it?  (If not - don't format it.)

If not formatted:  Did you try mounting it again in Ubuntu?  Try this from a terminal:

```
sudo mount /dev/sda1 /mnt
```

Then your files would be in the /mnt directory.  In a terminal you would see them by doing:

```
ls /mnt
```

Or you could navigate to them in a Nautilus (file manager) window from "File System" or "computer" - /mnt is in the top of the tree with /usr /home and others.

---

### Post by firstname on 2016-02-24
> **weatherman2 said:**
> OK, so your HDD is not connected - just the SSD that you can no longer read?  It shows just one NTFS partition, which is normal if you used it in Windows.

No I have 2 more hard drives connected (1x ssd for dual boot, 1x hdd for data). But I did not think it would be a good Idea to share that data on the web. After all i had to use my pw to see them o.O



> **weatherman2 said:**
> You mentioned formatting the SSD.  Did you format it?  (If not - don't format it.)

OK

> **weatherman2 said:**
> If not formatted:  Did you try mounting it again in Ubuntu?  Try this from a terminal:

```
sudo mount /dev/sda1 /mnt
```

I tryed that is what happened

```
sudo mount /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```


Then i did dmesg | tail

```
[    4.417355] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[    4.417356] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    4.417358] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    4.417359] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[    4.417360] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[    4.417361] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[    4.997246] [drm:dce6_afmt_write_sad_regs [radeon]] *ERROR* Couldn't read SADs: 0
[    6.119157] r8168: eth0: link up
[  193.317557] usb 3-2: input irq status -75 received
[ 1667.678623] usb 3-2: input irq status -75 received
```





> **weatherman2 said:**
> Then your files would be in the /mnt directory.  In a terminal you would see them by doing:

```
ls /mnt
```


```
ls /mnt
boot-sav
```



Or you could navigate to them in a Nautilus (file manager) window from "File System" or "computer" - /mnt is in the top of the tree with /usr /home and others.

---

### Post by weatherman2 on 2016-02-24
OK, so you won't find anything in /mnt because the partition failed to mount in the previous command.

Yes, I'd guess the partition is corrupted somehow.  Do you have data on that partition you want to try to save?  If so, try searching for "testdisk" which may be able to fix the partition.  That's what I would do, anyway.

If you don't care about the data, try re-formatting the partition.

I'd also check out the S.M.A.R.T. health of the SSD - look at the Attributes using GSmartControl.  Make sure nothing catastrophic happened to the SSD e.g. a failure.

Why did this happen and how can you prevent it from happening again, assuming your SSD is healthy?  Not sure.  I've used lots of NTFS partitions in Ubuntu, and I've got several SSDs running Ubuntu all the time.  Never had issues like this.  What version of Ubuntu are you using?

---

### Post by QIII on 2016-02-24
At this point, with a possible bad superblock, I think that after attempting recovery I would secure erase the SSD to get it back to factory condition before reformatting.  Simply reformatting might not take care of cleaning up the erasure blocks on the SSD, leaving memory cells uncleared.  That would be unusable space.

The ArchLinux wiki gives a pretty good method [here]("https://wiki.archlinux.org/index.php/SSD_memory_cell_clearing").

And I agree that it may be impossible to find out what caused this.  A bad controller could mean that whatever you do you may end up here again.  Power interruptions can do this to SSDs, too.  Hard to say.  But if it is a bad superblock issue, it is unlikely that either Ubuntu or Windows "did" this.

---

### Post by firstname on 2016-02-26
> **weatherman2 said:**
> What version of Ubuntu are you using?

I used 15.04

---

### Post by firstname on 2016-02-26
I guess it will remain a mystery what exactly caused this.

The fact that it happened TWICE exclusively during ubuntu usage remains.. sadly. Yes, it happened before. Back than it seemed like a coincidence. But now that ubuntu killed again.. sigh.
 I would like to switch to a linux OS but stuff like that makes it not only horribly complicated or at least very time intensive but unsafe as well.

At least with windows its more or less safe to assume your files wont be deleted just because you used the hardware.

thanks for your advicee though, I will try to use some of the software you mentioned. but for now I dont realy want to use the ubuntu partition at all.

---

### Post by weatherman2 on 2016-02-26
If you are relatively new to Ubuntu, I would really stick to an LTS version like 14.04, which is likely to be more stable than 15.04.  14.04 LTS is supported for five years from release, until April 2019.  (LTS versions of Ubuntu are released every two years.)  15.04 support has already ended (a few weeks ago) because it is not an LTS release, so to get future updates you will have to upgrade to 15.10 and then eventually to 16.04.  Upgrades can work but can also be very disruptive.   (You won't have to upgrade 14.04 until April 2019.)  Personally, I install a non-LTS release like 15.04 only as a very last resort.

Not that I can say 15.04 has some bug that is corrupting your SSD partition (and to be clear, it's not "destroying the SSD" - it's corrupting the partition on your SSD, which of course is lethal to your data and obviously a problem.)   I would never rely on a system where my data was a risk like you have experienced.  But, as I said above, I have used several SSDs without any issue in Ubuntu including my current laptop Crucial SSD that I use daily - never an issue or hint of corruption.  There may be some specific issue with your SSD and the version of Ubuntu you are using, but there is no general Linux issue with SSDs.

If you have important data on your SSD, you should be backing it up regularly no matter what OS you use.  Devices can fail, even SSDs, and you can get unexpected corruptions even in Windows, including from infections.  (Ever heard of Cryptowall?  Unfortunately, I have.  It's an infection that encrypts your data and holds it for a ransom; you might as well consider the data erased unless you want to pay hundreds or thousands of dollars in ransom.) 

If I were you, beyond making sure I do regular backups of that SSD for data I care about on another device, I'd:
- move to an LTS version of Ubuntu
- check Crucial's website for an updated firmware for your SSD.  Another user recently posted here with a flaky Crucial SSD that was completely fixed with a firmware update.
- check the SSD's  S.M.A.R.T. Attributes to make sure it truly hasn't experienced a hardware failure.

---

