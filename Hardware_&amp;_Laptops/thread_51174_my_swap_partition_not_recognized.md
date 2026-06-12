---
title: "my swap partition not recognized"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by matthew on 2005-07-22
When I installed Hoary I didn't make a swap partition because with 1Gb of RAM I didn't think it would be necessary. Now I want one so I can try to get hibernate to work. I created a swap partition, but when I run the free command this is what it shows:
>              total       used       free     shared    buffers     cached
Mem:       1035992     519776     516216          0      36152     198960
-/+ buffers/cache:     284664     751328
Swap:            0          0          0

I would guess this means the partition is not formatted properly or is at least not being used. What should I do now?

More info...here's my disk partition setup:
>  Size: 80 Gb Hdd, currently dual booting Ubuntu with Win XP

Partitions:
Name/type/size/mountpoint

hda1 ntfs 15.3 Gb WinXP *mounts read-only as /media/windows in ubuntu
hda2 ext3 10 Gb /
hda3 ext3 30.5 Gb /home
hda4 extended, includes hda5 & hda6
hda5 fat32 19.4 Gb /home/matt/music
hda6 linux-swap 1 Gb

hda5 and 6 used to be part of hda1's ntfs partition. As I am using XP less and less I decided to remove space from its partition and make a shared space accessible from both. Since I am now using XP for almost nothing, hda5 holds my mp3s and almost nothing else.

---

### Post by jasmuz on 2005-07-22
You must tell the machine that you have a swap partition now.

on the command line you can type swapon /dev/hda6 

And make your entry into /etc/fstab, like this.

/dev/hda6       none            swap    sw              0       0

That does it. :)

---

### Post by matthew on 2005-07-22
Thanks for the reply. 

For the command - swapon /dev/hda6 - here is the output:
> swapon: /dev/hda6: Operation not permitted

I took a look and this was already in my /etc/fstab:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda5	/home/matt/music	vfat    iocharset=utf8,umask=000   0       3
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

What should I check next?

---

### Post by GTvulse on 2005-07-22
[QUOTE=matthew]Thanks for the reply. 

For the command - swapon /dev/hda6 - here is the output:


I took a look and this was already in my /etc/fstab:


What should I check next?[/QUOTE]

```

sudo swapon /dev/hda6

```

does the trick. Reboot and your done.

---

### Post by matthew on 2005-07-22
Nope. Here's the output. BTW, it didn't matter if I used "sudo swapon /dev/hda6" or "sudo swapon -a"

> swapon: /dev/hda6: Invalid argument

---

### Post by matthew on 2005-07-22
I found the answer!!

I couldn't turn the swap on because it had never officially been made. Here's the code:

> sudo mkswap /dev/hda6 

Then I could do this and have it work:

> sudo swapon -a 

To be certain I typed "free" and this is what was output:

>              total       used       free     shared    buffers     cached
Mem:       1035992     466208     569784          0      33588     184764
-/+ buffers/cache:     247856     788136
Swap:      1060248          0    1060248 

Thanks to all who helped put me on the right track!

---

### Post by Firetech on 2005-07-29
Strange. I experienced the same thing (and the solution here solved it).
The thing that makes me confused is that I'm sure the swap partition worked earlier...
It might be the fact that I have my swap partition on LVM an that I shrinked another logical volume last night... It might also be that I tried the acpi hibernation.sh script earlier, and that didn't work (just did a "bad" shutdown...).
But as I said, the solution here ("mkswap [device]" and then "swapon -a") solved it.

---

### Post by matthew on 2005-07-29
Very cool. Glad that helped you out. I would guess that the swap file was deactivated when you resized and as you discovered just needed to be reactivated.

---

### Post by art on 2005-07-29
Hi guys
Since we are talking about swap and hibernation, let me ask a question... I have a swap 512 Mb, and since my hibernation is not working, I thought maybe it's because of swap being too small. Anyone knows how can I resize the swap partition, make it bigger?
Thanks a lot.

---

### Post by matthew on 2005-07-29
You can use the install disk to do this. Boot from it and get to the partitioner. Resize as you want and then stop the installation before it goes further. You need to do this because you cannot resize an active partition. If you don't want to do it from the installer, I believe gparted or qparted is included on the live cd and I know qparted is included on the Knoppix cd.

Your swap partition will need space next to it if you are to enlarge it. See what partitions are adjacent first and if any of them may be resized slightly to give room for the increase.

Read this for a little more detailed info.

[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

---

### Post by mike41 on 2006-10-26
I would just like to add that it most definitely has something to do with hybernation. I just upgraded to Edgy and I thought maybe hybernation would be fixed, so I tried to hybernate, but of course my computer just turned off. The when I rebooted, it just so happened that I was at my 30th mount of the root partition, so I got a look at the terminal output of my boot while the partition was being checked, and I noticed that "mount swap" FAILED. Id never noticed that before, and seeing this thread (which fixed my problem), and this thread ([http://www.ubuntuforums.org/showthread.php?t=182074&highlight=swap+problem+unknown+gparted](http://www.ubuntuforums.org/showthread.php?t=182074&highlight=swap+problem+unknown+gparted)) makes me quite confident that hybernating messes up the swap.

---

### Post by dc. on 2006-10-26
Same problem here!
Everything else works.
I also tried to hibernate and got the 30th mount message.

in /etc/fstab there is a comment #converted during update to edgy and the normal device names like hda1 or hda3 are replaced by very long and funny looking ID-Strings, huh?


swapon -a doesn't work either.

---

### Post by mike41 on 2006-10-27
as far as I know, edgy's fstab is using a new naming facility to refer to drives, because it will be more powerful (eventually). BUT it seems to be buggy. Edit your fstab so that the swap entry looks like this:

/dev/hdaX       none            swap    sw              0       0

where /dev/hdaX is whatever your swap partition is.

then go to a terminal and do:

sudo swapoff -a
sudo mkswap /dev/hdaX
sudo swapon -a
sudo swapon -s

if the final command gave you output, then your swap should now work. 

(note that this issue may have been fixed since i played around with mine)

---

### Post by haricharan on 2006-11-07
hey thank you its working now......:) ..but i have another question...i have both FC6 and Ubuntu 6.10. Can i use the same swap partition for both the kernels?

---

### Post by anaconda on 2006-11-07
> **haricharan said:**
> hey thank you its working now......:) ..but i have another question...i have both FC6 and Ubuntu 6.10. Can i use the same swap partition for both the kernels?

Yes you can!

---

