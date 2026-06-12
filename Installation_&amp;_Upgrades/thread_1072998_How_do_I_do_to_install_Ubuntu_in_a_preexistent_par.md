---
title: "How do I do to install Ubuntu in a preexistent partition?"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by mnellie on 2009-02-17
Hi all.

I've been using Windows Vista in my computer and after using Ubuntu in other computers I decided to install it on my own.

I'll explain the issue I'm experiencing very clearly because I really need it to be solved and sorry if this post is gonna be huge. In the other hand I think (and hope) the issue is very simple and easy to solve.

I have a 320 GB HD, with 3 partitions:

Partition C &#8594; 223 GB &#8594; it's dedicated to Windows Vista

Partition D &#8594; 6,40 GB &#8594; this one is dedicated the factory image files, I mean, files that will be necessary to recover the system and return it to the state it was when it came from the HP factory.

Partition J &#8594; 70 GB &#8594; this partition is empty and this is where I want to install Ubuntu.

All the other drives are removable medias. 






The problem:

After booting from the Ubuntu install disk and selecting the “English” language as default to my system and also after selecting my city, I'm directed to a “Partitioning Menu” that gives me three options:

1)to create a new partition on my HD so I can install Ubuntu
2)to install Ubuntu without creating any partition (what probably would make me loose all my files in partitions C and D)
3)to manually manage partitions.

I don't want the 1st and 2nd options, that's for sure.

When I choose the 3rd option, these three partitions I mentioned above are shown. So I choose to install Ubuntu in the Partition J.

Then I got an error message saying Ubuntu can not be installed because it was not found system root file or something.





So I have no idea of how can I choose to install Ubuntu in the Partition J.

I know I could use the Ubuntu Installation Partitioning Menu to create a partition dedicated to Ubuntu, but I don't think it's safe since many people have been reporting lost of files.

So all I want to do is to install Ubuntu in this Partition J that I've previously created for this goal.


Also, I know this issue is not caused by any failure on the Ubuntu installation disk I'm using, since it works fine in other computers I had installed it myself.

So I know the issue is related to the partitioning thing.

As you can see, I'm not an expert in computers. When I'm installing Windows XP in a computer, the installation menu gives me the option to choose what partition I want to install to. So I thought it would be the same for installing Ubuntu, and now I know it's not. That's the reason of this post and I hope it's not as stupid as I fear it to be. 


Help needed.

---

### Post by TheBig3 on 2009-02-17
Okay... Do you want to install ubuntu in windows? If that's the case just install it from the disc in windows using the wubi installer.

If you want to install ubuntu to the 70GB partition, you are probably going to have to move the windows partition so the GRUB bootloader will work. I'd start by booting from the CD with Try without any changes.  When Ubuntu is done loading use Alt+F2 to bring up the run application dialogue box. Type "sudo gparted" and either select run or press enter. Select the ntfs partition and the click the Resize/Move button. You should be able to drag the partition to the end of the drive. Right now I wouldn't try to adjust the size of the partition, just leave it the same size. You want to have the empty partition at the front of the drive. You're going to need a swap partition, I usually make mine 2GB (2096 MB). The rest of the empty partition format as ext3 and set the mount point to / (the root directory).  After moving the windows partition(this took about 4-5 hours for me with 200 GB) and formating the new partitions everything should install fine. When the system restarts you should see the GRUB bootloader to select you OS. I did this with my system just yesterday. GRUB wouldn't load because it wasn't within 137 GB of the beggining of the drive.

Hope this helps and good luck.
P.S. DO NOT FORMAT the NTFS partition that is your windows partition

---

### Post by jocko on 2009-02-18
You have to make a new partition. Ubuntu can't be installed on a ntfs partition.
Do NOT attempt to move the windows partition as described by TheBig3 above, it's absolutely NOT necessary and will very likely just create problems, as windows needs to be on the first partition of the drive.
When you get to the partitioning part of the install, choose the manual partition setup.
Select your empty partition (the one windows sees as J:\), and **delete** it.
Make two new partitions in the empty space left after removing the "J\" partition;
A small one (2-4 Gb, or at least the size of your ram).
-Set it to be used as swap.
And a large one which takes up the rest of the empty space of the drive.
-Set the file system to ext3.
-Set the mount point to "/" (that's the root file system).
That should be it.
Note that if you have any data on the ("J:\") partition before you start this, it will be lost, so move it to another partition.

---

### Post by TheBig3 on 2009-02-18
> **jocko said:**
> 
Do NOT attempt to move the windows partition as described by TheBig3 above, it's absolutely NOT necessary and will very likely just create problems, as windows needs to be on the first partition of the drive.

[IMG]http://www.geocities.com/thebig3_99/UbuWin.jpg[/IMG]
Windows does NOT need to be the first partition. My windows is running fine as the last partition, and in fact ubuntu would not start with ubuntu being last. I spent the whole day going through this, so this is from hands-on experience, not incoherent rambling. Most likely you'll get a GRUB error 18, like I did, if you do it jocko's way. If his way does work, So much the better for both of you, but that was my experience.

---

### Post by jocko on 2009-02-18
> **TheBig3 said:**
> 
Windows does NOT need to be the first partition. My windows is running fine as the last partition, and in fact ubuntu would not start with ubuntu being last. I spent the whole day going through this, so this is from hands-on experience, not incoherent rambling. Most likely you'll get a GRUB error 18, like I did, if you do it jocko's way. If his way does work, So much the better for both of you, but that was my experience.

As long as grub is installed in the mbr of the drive (which it always is by default), Ubuntu has no problem whatsoever being on the last partition (I have a small ubuntu partition on the last 10 Gb on a 120 Gb drive for testing development snapshots, and it boots just fine).
I was absolutely convinced that windows always needs to be on the first (visible) partition of the drive (or rather the windows boot loader, ntldr, needs to be on the root of the first partition).
Looks like I was wrong on that point... But still: Ubuntu does **not** need to be on the first partition.

---

### Post by TheBig3 on 2009-02-19
The problem I was having was with the /boot with the grub files being more than 137 GB from the start of the dive and it seemed to be a common problem resulting in a GRUB error 18 when I rebooted.  Using the Windows XP install disc FIXMBR removed GRUB from the MBR so Windows could boot again (one OS is better than no OS). When booting from the live cd, I could still see the GRUB boot files in the Ubuntu partition. So, in therory, any drive under 137 GB wouldn't have the GRUB error 18 problem. I've since found out the boot limitations can vary by BIOS, mine being 137 GB even after updating. I apologize if I've been rude, but I know what I said can, and in my case did, work. And yes I was a little afraid that moving the partition would mess up my windows install. Fortunately it didn't, and now both OSes work perfectly fine.

---

