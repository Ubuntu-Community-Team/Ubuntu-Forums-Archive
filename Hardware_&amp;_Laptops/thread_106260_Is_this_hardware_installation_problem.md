---
title: "Is this hardware installation problem?"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by janlin1975 on 2005-12-20
Hi

I would appreciate any help on this matter.

It really is an installation matter problem but I suspect that it has an incompatible hardware firmware component to this.

I have posted to the installation forum and nobody seems to know what to do.

The reason I suspect this is because I have been successful at installing on my P2 system but not my P3. thinking that this is a filing problem I have used my HD from the P2 on P3 and no success.

My configurations are

P3,256MB RAM, 4.3 GB two of them, award bios (disabled virus protection n video shadow)

I will paste a copy of the error codes I have received.

Also is there an ubuntu manual that would detail the installation process /troubleshoot? i have used the Debian GNU/Linux installation guide but cannot find any more details into my problem. Direction would be much appreciated.


The system hangs during Installing packages after rebooting.

It doesn't matter at what stage the installation is.it could be 49%, 78% or 99%.Usually the later stages.

[1359.146994} EXT-fs error (device hda1): ext3_free_blocks_sb: bit already cleared for block 1425853

[1359.1477171] Remounting filesystem read-only


Uncompressing linux... Ok, booting the kernel.
[4294667.296000] ACPI: unable to locate RSDP

Loading please wait...

FATAL: Error inserting fan (/lib/modules/2.6.12-9-386/kernel/drivers/acpi/fan.ko): No such device

FATAL: Error inserting thermal (/lib/modules/2.6.12-9-386/kernel/drivers/acpi/thermal.ko): No such device

/contains a file system with errors, check forced.

Deleted inode 82601 has zero dtime. FIXED

Duplicate or bad block in use!

Multiply-claimed block(S) in inode 117268: 256189

Multiply-claimed block(s) in inode 117406: 256189

(There are 2 inodes containing multiply-claimed blocks.)

File /usr/share/man/man/man8/dmesg.8.gz (inode #117268, mod time Tue Sep 17:43:35 2005

has 1 multioly-claimed block(s), shared with 1 file(s):

/usr/share/doc/tar (inode #117406, mod time Mon Dec 19 12:29:59 2005)

UNEXPECTED INCONSISTENCY; Run fsck MANUALLY.

(ie without -a or -p options)

fsck failed. Please repair manually and reboot. Please noe that the root file system is currently mounted read-only. to remount it read-write:

# mount -n -o remount,rw /

CONTROL-D will exite from this shell ans reboot the system.

bash: lesspipe: command not found

bash: dircolors: command not found

thanks in anticipation.

-jan

---

### Post by schdefan on 2005-12-20
Looks like something went wrong during your installation.And ACPI is not supported in your hardware. To repair the harddisc error
log in as root at the prompt and run
```
#fsck /dev/hda
```
or 
> #e2fsck -b 8193 /dev/hda1

schdefan

---

### Post by janlin1975 on 2005-12-20
I have tried installing it to a new 80Gb HD and also swapped the HD which had a successful install on my P2.

Will give it a try nonetheless.

Ta will let you know the result.
-jan

---

### Post by janlin1975 on 2005-12-21
Did the above.No joy.

It was checking my system and repairing it.

I did not jot down the error messages.I am still quite new at this.Reinstalling this  for the n th time now.

I am just trying to install it in different options with the partitioning.( do I have to do this all the time?)

What I fail to understand is what is the systematic error that keeps recurring but I cannot identify where it is?

File corruption on a newly installed sysem?Things that can cause this, is errors in the cd rom image (md5sum check okay and has been successfully installed in a separate system P2), the physical hard drive.(the successful hard disk used to install on the P2 was used for this) or the software and the remaining hardware that is involved.

I will reinstall and try to get the error codes and report.

-jan

---

### Post by janlin1975 on 2005-12-21
I have used fsck and files are fixed.

Prompted to use 

      dpkg --configure -a

and the error out is 

      unable to access dpkg status area: read-only.

-jan

---

### Post by janlin1975 on 2005-12-21
I have this problem too.

[http://paste.ubuntu-nl.org/1327](http://paste.ubuntu-nl.org/1327)

---

