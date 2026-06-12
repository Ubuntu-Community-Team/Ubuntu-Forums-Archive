---
title: "Pendrive"
date: 2016-03-30
forum: Hardware
---

### Post by anon_private on 2016-03-30
Hi,

I recently used a pendrive in a Windows machine, and received a message that the pendrive needs a repair. It works well under kubuntu.

My question is: 'Should I allow the Windows machine to repair the pendrive, bearing in mind that I normally use this drive in my kubuntu machine'?

Thanks

---

### Post by kurt18947 on 2016-03-30
If your device works, I would not permit any 'repairs'. I get this message or one very similar if I insert a flash drive formatted to FAT32 using gparted into a Windows session. I ignore it as long as the device performs as expected.

---

### Post by sudodus on 2016-03-30
The general rule is: 'If it ain't broke, don't fix it'

In this case Windows complains about it, and I guess it is a Microsoft file system. Probably there is something wrong. Repairing it is potentially risky, but it might be risky to continue using it without repairing it too.

If there are important files on the drive, I would back them up to another drive, and after that let Windows do the repair it wants to do.

See also these links about keeping pendrives healthy,

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by buzzingrobot on 2016-03-30
What do you think the chances are that a "repair" would include a reformat? ;)

"Repair" seems to mean "make it something Windows understands".

---

### Post by anon_private on 2016-03-30
> **kurt18947 said:**
> If your device works, I would not permit any 'repairs'. I get this message or one very similar if I insert a flash drive formatted to FAT32 using gparted into a Windows session. I ignore it as long as the device performs as expected.

Thanks for responding.

I don't have many investigative tools in kubuntu, but using 'KDE Partition Manager', I note that the pendrive is formatted as fat32.

I wonder if this could account for the Windows repair message since it is likely that the Windows machine I was using is formatted as NTFS (I have not checked this - machine elsewhere).

Best wishes.

---

### Post by X-RED_Tech on 2016-03-30
> **anon_private said:**
> I wonder if this could account for the Windows repair message since it is likely that the Windows machine I was using is formatted as NTFS (I have not checked this - machine elsewhere).

No, completely unrelated. It doesn't matter how other partitions have been formatted. What matters is the file system in the drive/partition giving the error. Having confirmed it's fat32 then it's safe to let Windows 'correct' whatever Windows thinks needs correction. Unless when explicitly mentioned it won't format it. Windows does offer that option ONLY for any unformatted drive or any formatted drive with a file system it doesn't recognize.

PS - Windows is bad but not that bad...

---

### Post by kurt18947 on 2016-03-30
> **buzzingrobot said:**
> What do you think the chances are that a "repair" would include a reformat? ;)

"Repair" seems to mean "make it something Windows understands".

I've permitted Windows to 'fix' devices when it issues that message. There was nothing of consequence on the drive. The 'repair' didn't seem to adversely affect the drive, it did not reformat.

---

