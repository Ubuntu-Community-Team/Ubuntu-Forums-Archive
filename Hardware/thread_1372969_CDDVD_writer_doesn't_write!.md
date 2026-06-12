---
title: "CD/DVD writer doesn't write!"
date: 2010-01-05
forum: Hardware
---

### Post by Janneman27 on 2010-01-05
I have Ubuntu 9.10 on an Acer Travelmate 5620 notebook with a TSSTCorp TS-L632D CD/DVD Writer.

I'm using Linux kernel 2.6.32 with GNOME 2.28.1

I've been trying to write an .iso file to a CD-RW but during the process, the progress bar just stays at 0% and nothing gets written to the disc.

What can/should I do?

---

### Post by mjitkop on 2010-01-05
What is the file size of the ISO file?

What application are you using to try to write the ISO to disc?

Have you been able to write to the same type of disc before?

---

### Post by Janneman27 on 2010-01-05
The iso is 600MB and is basically an mp3 CD.

I'm using the standard writing program that comes with ubuntu.

This was the first time I tried writing a disk, but the drive works perfectly with Win Vista (which I have on a dual-boot on a separate partition on the same notebook)

---

### Post by Black Sun on 2010-01-05
I have same kind of problem and in my case it simply dosen't matter what kind of image or of what size I try to write it always fails. I use Brasero and I have Acer Aspire 5920 with Ubuntu 9.04 installed.

---

### Post by alwayshere on 2010-01-05
sounds like writers block lol;

Hey try just right clicking on the iso and choose "write to disk"

if that doesnt work you got a problem for sure

---

### Post by 1branchonthevine on 2010-01-05
I have to use K3B burner, with "force unsafe operations" enabled, in order to use my cd drive. Burner and disks work like a charm every time. For me, all other burners report my drive is unable to write to media. Bug in the discount drive's firmware. Windows has the same problem, but at least I can use it in linux now!

sudo apt-get install k3b

Go to **k3b** settings > Configure k3b > advanced > check the "**Force** **unsafe****operation**" box.

---

### Post by Janneman27 on 2010-01-05
> **alwayshere said:**
> sounds like writers block lol;

Hey try just right clicking on the iso and choose "write to disk"

if that doesnt work you got a problem for sure

That's what I did initially...then only I tried alternative ways...eitherway, it doesn't work. This is my fstab file:

[I]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=77e0938a-0ef2-49dd-98fb-79f035f3b752 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=09c2bd5f-7fc5-497c-9d85-6861d4b6770f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/I]

---

### Post by Janneman27 on 2010-01-07
I can't seem to use any program to write anything to a CD or DVD!

It's like the writer thinks it's a reader!

---

