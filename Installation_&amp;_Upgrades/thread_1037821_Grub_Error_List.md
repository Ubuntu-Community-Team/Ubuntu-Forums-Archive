---
title: "Grub Error List"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by 5BallJuggler on 2009-01-12
This is a list of Grub errors, solutions to follow, any help would be appreciated

# 1 : "Selected item won't fit into memory"

This error is returned if a kernel, module, or raw file load command is either trying to load it's data such that it won't fit into memory or it is simply too big.

# 2 : "Selected disk doesn't exist"

This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

# 3 : "Disk read error"

This error is returned if there is a disk read error when trying to probe or read data from a particular disk.

# 4 : "Disk write error"

This error is returned if there is a disk write error when trying to write to a particular disk. This would generally only occur during an install of set active partition command.

# 5 : "Disk geometry error"

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

# 6 : "Attempt to access block outside partition"

This error is returned if a linear block address is outside of the disk partition. This generally happens because of a corrupt filesystem on the disk or a bug in the code handling it in GRUB (it's a great debugging tool).

# 7 : "Partition table invalid or corrupt"

This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign.

# 8 : "No such partition"

This error is returned if a partition is requested in the device part of a device- or full filename which isn't on the selected disk.

# 9 : "Bad filename (must be absolute pathname or blocklist)"

This error is returned if a filename is requested which doesn't fit the syntax/rules listed in the Filesystem Description.

# 10 : "Bad file or directory type"

This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO.

# 11 : "File not found"

This error is returned if the specified filename cannot be found, but everything else (like the disk/partition info) is OK.

# 12 : "Cannot mount selected partition"

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

# 13 : "Inconsistent filesystem structure"

This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.

# 14 : "Filesystem compatibility error, can\'t read whole file"

Some of the filesystem reading code in GRUB has limits on the length of the files it can read. This error is returned when the user runs into such a limit.

# 15 : "Error while parsing number"

This error is returned if GRUB was expecting to read a numbur and encountered bad data.

# 16 : "Device string unrecognizable"

This error is returned if a device string was expected, and the string encountered didn't fit the syntax/rules listed in the Filesystem Description.

# 17 : "Invalid device requested"

This error is returned if a device string is recognizable but does not fall under the other device errors.

# 18 : "Invalid or unsupported executable format"

This error is returned if the kernel image boing loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).

# 19 : "Loading below 1MB is not supported"

This error is returned if the lowest address in a kernel is below the 1MB boundary. The Linux zImage format is a special case and can be handled since it has a fixed loading address and maximum size.

# 20 : "Unsupported Multiboot features requested"

This error is returned when the Multiboot features word in the Multiboot header requires a feature that is not recognized. The point of this is that the kernel requires special handling which GRUB is likely unable to provide.

# 21 : "Unknown boot failure"

This error is returned if the boot attempt did not succeed for reasons which are unknown.

# 22 : "Must load Multiboot kernel before modules"

This error is returned if the module load command is used before loading a Multiboot kernel. It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of location of such modules to a non-Multiboot-aware kernel.

# 23 : "Must load Linux kernel before initrd"

This error is returned if the initrd command is used before loading a Linux kernel. Similar to the above error, it only makes sense in that case anyway.

# 24 : "Cannot boot without kernel loaded"

This error is returned if GRUB is told to execute the boot sequence without having a kernel to start.

# 25 : "Unrecognized command"

This error is returned if an unrecognized command is entered into the command-line or in a boot sequence section of a config file and that entry is selected.

# 26 : "Bad or incompatible header on compressed file"

This error is returned if the file header for a supposedly compressed file is bad.

# 27 : "Bad or corrupt data while decompressing file"

This error is returned the run-length decompression code gets an internal error. This is usually from a corrupt file.

# 28 : "Bad or corrupt version of stage1/stage2"

This error is returned if the install command is pointed to incompatible or corrupt versions of the stage1 or stage2. It can't detect corruption in general, but this is a sanity check on the version numbers, which should be correct.

this list taken from "http://www.uruk.org/orig-grub/errors.html"

---

### Post by Elfy on 2009-01-12
Not sure what help you need - but this should cover all of those errors

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by kranny on 2009-01-12
Is that a tutorial?:lolflag:

---

### Post by 5BallJuggler on 2009-01-12
Sorry, I should have explained myself better.

I would like this to be a tutorial, I don't need help with a grub error as such, I'd just like peoples knowledge of each fault to be added to the bottom of the list. as it seems a lot of time is wasted looking for solutions that are in different places.

If we could put them all in the same place it would be better....yes?

---

### Post by aeronotix on 2009-01-12
Ooo..thanks.

---

