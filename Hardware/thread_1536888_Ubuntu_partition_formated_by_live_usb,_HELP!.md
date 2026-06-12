---
title: "Ubuntu partition formated by live usb, HELP!"
date: 2010-07-22
forum: Hardware
---

### Post by Lrpbpb on 2010-07-22
My partition scheme is/was as follows:
107 gb- Windows partition (primary)
107 gb- Files (extended)
2.1- Swap (primary)
33- Ubuntu (ext4, primary)
The other day I made a live usb through ubuntu (using multiboot), so I could try out the elementary-desktop (I didn't want to install all those packages and figured it would be good to have a live usb). Anyway, in order to install nautilus-elementary, I had to update, so I updated all packages (about 250 mb's). It took all day to download so I just left it there, when I came back all the programs (I had firefox running as well) were greyed out without color (like when they get stuck/crash) and the system didn't respond, so I clicked in the reboot button and removed usb.
When it turned back on I get the grub error: unknown filesystem. :(
Since my "elementary" usb wasn't booting, I then make a new live usb (I feel dumb that I did it though:p. You see my usb doesn't have a metal around it so you can't really know which way to plug it in, I'm pretty sure now that I placed it backwards](*,))  
Anyway, when it boots I get this error that my hard drive might be failing. I click ok and a palimpsest windows says in big red letters: [COLOR=Red]DISK FAILURE IS IMMINENT[COLOR=Black], I have gotten other smart errors before (always when using live usb) but nothing has ever happened, so I didn't take much importance of it. 
Then I see that in the 33gb section where my ubuntu partition was it says "Free". Then I go to computer and the ubuntu partition isn't shown there or in the nautilus sidebar. Then I get REALLY worried.
I first try to reinstall ubuntu, but the utility gets an error that it can't format the 33 gb free partition to ext4. 

Then I decided to just format through gparted, but it never starts, and when it does it says scanning all devices for hours on end but it never continues beyond that.

So then I decide to use palimpsest, but when I try to format the 33gb partition I get this error:
[/COLOR][/COLOR]```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sda, start=216892408320, size=33166941696, type=0x83
Entering MS-DOS parser (offset=0, size=250059350016)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 107372772864, type 0x07)
new part entry
looking at part 1 (offset 107372836352, size 107372773888, type 0x0f)
Entering MS-DOS extended parser (offset=107372836352, size=107372773888)
readfrom = 107372836352
MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 2 (offset 214745610240, size 2146798080, type 0x82)
new part entry
looking at part 3 (offset 216892702720, size 33165410304, type 0x83)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
new partition
Error: Too many primary partitions.
ped_disk_add_partition() failed
```So apparently I have too many primary partitions, then I decided to just erase the swap (and make a swap in the extended) but then I get the following error:
```
Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sda, offset=214745610240
Entering MS-DOS parser (offset=0, size=250059350016)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 107372772864, type 0x07)
new part entry
looking at part 1 (offset 107372836352, size 107372773888, type 0x0f)
Entering MS-DOS extended parser (offset=107372836352, size=107372773888)
readfrom = 107372836352
MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 216892702720, size 33165410304, type 0x83)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
got it
got disk
got partition - part->type=4
refusing to delete a protected partition
```But I don't know what is protecting that partition or how to unlock it.
I REALLY need help, I have tried all my 3 months as a linux user have taught me, but I can't edit my drive's partitions. Also, I have no idea how merely updating a live usb could have screwed my hard drive so badly. PLEASE HEELPP!!!

P.S. Sorry fro the looong post but I really wanted to give as much detail as possible, hoping it will make it easier to find a solution ;).

Edit: After leaving gparted to load for about half an hour it loaded (ok, maybe I exaggerated by sayin hours on end, butI was impatient), now my 2 gb swap says unallocated and my 33gb says unknown. When I tried to partition I got another error (attached), it seems that I can't even partition my hard drive!! PLEASE HELP!

Edit2: I ran sudo fsck /dev/sda4 -a and got the following:
ubuntu@ubuntu:~$ sudo fsck /dev/sda4 -a
fsck from util-linux-ng 2.17.2
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Could this be a zero-length partition?
Any idea on how to fix this?

---

