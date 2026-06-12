---
title: "No recogniction of harddrive"
date: 2008-06-06
forum: Hardware
---

### Post by reyn8414 on 2008-06-06
Hey folks.
Ive used ubuntu for a while, and now i have an issue.

My hard drive wont be recognized by anything but linux.
including Disk erasing software.

My laptop is an Extensta 4620z.

I need to wipe the drive to Absolute nothing.
for i am donating the computer.

I can post more information as needed.

---

### Post by Rocket2DMn on 2008-06-06
Windows computers will probably not see the drive if it is not formatted as NTFS or FAT32.
The easiest way to delete everything off the hard drive is to use the LiveCD or GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

If you are on the Ubuntu LiveCD, go to System->Administration->Partition Editor, select the partitions on the drive and delete each of them.

If you are worried about security, like somebody attempting to read data sensitive data off the hard drive after you donate it (even though the partitions have been deleted), you can use killdisk - [http://www.killdisk.com/](http://www.killdisk.com/) or dban (darick's boot and nuke) - [http://dban.sourceforge.net/](http://dban.sourceforge.net/) .  That will go through your hard drive and overwrite all the bits, but it can take hours and hours depending on the size of your drive.

---

### Post by AndyCee on 2008-06-06
Try this:

1) Boot from a Ubuntu LiveCD
2) Run the partition editor (administration -> Partition editor)
3) Delete your hard disk's partition (or reformat to fat32/ntfs/ext3 or whatever)

If you REALLY want to clear every trace of anything, and have lots of free time to do it, the following will clear traces of data on your RAM and hard disk:

4) Connect to the internet and run:

```
$ sudo apt-get install secure-delete
$ sfill
$ smem <your harddisk's mountpoint>
```

Details of using the package are at [http://www.techthrob.com/tech/securedelete.php](http://www.techthrob.com/tech/securedelete.php)

---

### Post by reyn8414 on 2008-06-06
Having tinkered with this for a little bit, I used gparted, and reset he partitions. With no success.

I have tried DBAN and it says it succeeded with no fatal errors. But the drive isnt wiped to zero.

And i haven't tried killdisk, Will it make it so even if the drive is low leved, or any sort of recovery, should be very difficult, if not impossible, this was my personal/business laptop.

Im trying the secure delete

---

### Post by Rocket2DMn on 2008-06-06
What do you mean it isn't wiped to zero?  Are you still able to boot into an operating system?  Using a program like killdisk or dban will make it impossible for anybody to recover information from the drive since it goes through and either writes 0s to every bit on the drive or overwrites every bit of the drive with random data.

Please explain how the drive is still not clean yet.  How are you arriving at this conclusion?

---

### Post by AndyCee on 2008-06-06
Just to clarify - "no success" with Gparted means you couldn't clear the data or you couldn't delete the partitions?

---

### Post by reyn8414 on 2008-06-06
Yes the OS boots ( im still trying secure delete) 
And Gparted always partitions, but it wont wipe the information.

---

### Post by AndyCee on 2008-06-06
Again, to clarify:
You're booting from Ubuntu installed on the computer?

If this is the case, it won't work because you're deleting partitions while they're in use.And you would need a LiveCD to boot from.

The tools in secure-delete will very very securely delete free space, I imagine the same as killdisk. It will take ages though, and I don't know if there's a progress check. You can decrease the time and security by using the flags, as by default it does 30-something passes.

---

### Post by reyn8414 on 2008-06-06
Yes i can boot off a live CD.
I acutlly tired Gpparted with the Gparted LiveCD

---

### Post by Rocket2DMn on 2008-06-06
In GParted, you have to select the partition from the list, click the Delete icon, then click Apply.  Note you can select between different hard drives in the upper right of the window.  It then prompts you with something like "Are you sure?", then you click Apply again and it will remove the partition.  If you are using killdisk or dban, you need to make sure you run it on the correct drive.

---

### Post by reyn8414 on 2008-06-06
i may not have done DBAN correctly,
" E: Could'nt find package secure-delete"

---

### Post by Rocket2DMn on 2008-06-06
Have you enabled the universe and multiverse repositories from System->Administration->Software Sources?
I have never used any of these programs myself, but you can't wipe the disk while you are booted in to the operating system.  That's why we use the LiveCD or something else like a floppy or bootable flash drive.

---

### Post by reyn8414 on 2008-06-06
Maybe.
Let me reboot. with teh live CD and try that way.
I have tired with Acers Partion software and it cant detect the harddrive.
Now i know that it is there, I havent unplugged anything. Nothing windows based can recognize the drive. And some of the linux utilitys cannot either. 
If anything, if i could get Vista on there. I can send it in and just get it replaced under warrenty. ( Im nto a vista fan, lets clear that up, haha)

---

### Post by reyn8414 on 2008-06-07
Still nothing.
Anyone help?

---

### Post by AndyCee on 2008-06-07
Assuming you've booted with a liveCD:

To help with GParted, we need more info about the error. It sounds like you may have already reformatted it - what format does GParted say the hard drive is? NTFS? ext3? raw/unformatted? And just for interest, how big does GParted say it is?

For installing secure-delete or dban, do you have internet access? Try getting the tool through synaptic. Secure-delete is in the 'universe' repository.

---

### Post by reyn8414 on 2008-06-08
I would have to find my disk again, im kinda messy with them, But i believe about 149.X Gigs.

And its NTFS

---

### Post by AndyCee on 2008-06-13
Sorry about the lack of follow up, it's just that the solution Rocket2DMn and I provided is the 'standard' one to your problem. Without meaning to patronise, I'll go over the solution one time in painful detail. Tell me where things go wrong.

_Explanation:_
[LIST]
[*]Booting from the liveCD means you can do what you want to the hard disk.

[*]The GParted is to remove the OS.

[*]The tools we suggested is to wipe the HD of data.
[/LIST]

_Instructions:_
All of the following must be done from a LiveCD boot (Gparted or *Buntu) without a restart before the end.

Since you obviously can't delete the OS while you're using the drive it's stored on, you need to boot from another device (ie. a LiveCD), connect to the net and install the tools suggested and run them. This all happens in a 'live environment', so the installation will disappear after reboot.

Run GParted, click on the drive you want and delete the partition. Format again as ext3 (One thought has occurred, perhaps the linux tools don't work on ntfs). Apply the change, or it won't happen. Pay attention/write down the name of the partition as written in the list below (should be sda1, or similar).

Connect to the net. You may have to manually configure your connection. If you can't connect from the LiveCD environment, you can't download the tools.

In terminal, run the commands I gave you before:

```

$ sudo apt-get install secure-delete
$ sfill
$ smem /dev/sda1

```
The last location may be different - replace the "sda1" with whatever you had in GParted. If you can't find "secure-delete", for some reason, there's one here:

[http://mirror.aarnet.edu.au/pub/ubuntu/archive/pool/universe/s/secure-delete/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/pool/universe/s/secure-delete/)

Download the one that fits your architecture (likely secure-delete_3.1-4_i386.deb ) and double-click to install.
The tools take a LONG time to finish. Once they do, the job is done and all data is (as far as I know) irretrievable.

If something doesn't work, report exactly what error you get. If someone gives a different working solution, post it here so I can learn something new.

That's all I've got. Sorry mate, and good luck.
-AndyCee

---

