---
title: "Ubuntu thinks my HDD is allocated"
date: 2008-07-28
forum: Hardware
---

### Post by Liopleurodon on 2008-07-28
Hello,
some months agon I installed Ubuntu without any problems. A time after that, I formatted my HDD, installed Vista again and then when I boot from Ubuntu (to install it), I open the partition manager and it shows that my whole HDD has no partitions, but is has 3! When I try to install it, then says it still that I have no partitions. Back booted into my Vista and everything went fine like before. Again booted into Ubuntu CD and the same problem was there. Can please someone help me?

---

### Post by Liopleurodon on 2008-07-30
Hello,
I mistyped: it has to be UNallocated in place of allocated. I booted form my Ubuntu cd and the problem is still the same.

---

### Post by prshah on 2008-07-30
> **Liopleurodon said:**
> 
I open the partition manager and it shows that my whole HDD has no partitions, but is has 3!


Can you boot off the CD, open a terminal [Applications-Accessories-Terminal] and then post the output of the following commands```
sudo fdisk -l
lshw -C disk
```

EDIT: This is not a fix, it will only give us the extra information that is needed.

---

### Post by Liopleurodon on 2008-07-31
Ok, I'll try that out.

---

### Post by Liopleurodon on 2008-08-02
Hello, here is the log:

```
fdisk: invalid option -- 1



Usage: fdisk [-b SSZ] [-u] DISK     Change partition table

       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)

       fdisk -s PARTITION           Give partition size(s) in blocks

       fdisk -v                     Give fdisk version

Here DISK is something like /dev/hdb or /dev/sda

and PARTITION is something like /dev/hda7

-u: give Start and End in sector (instead of cylinder) units

-b 2048: (for certain MO disks) use 2048-byte sectors




Hardware Lister (lshw) - B.02.12.01

usage: lshw [-format] [-options ...]

       lshw -version



	-version        print program version (B.02.12.01)



format can be

	-html           output hardware tree as HTML

	-xml            output hardware tree as XML

	-short          output hardware paths

	-businfo        output bus information



options can be

	-class CLASS    only show a certain class of hardware

	-C CLASS        same as '-class CLASS'

	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )

	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

	-quiet          don't display status

	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)





```

I've forgotten to say, but when I boot from my Ubuntu CD, I can browse trough my partitions in it. But when I launch partition manager, my whole disk is still unallocated.

---

### Post by prshah on 2008-08-02
> **Liopleurodon said:**
> Hello, here is the log:

```
fdisk: invalid option -- 1

```


Please, in this one case, copy/paste the commands. for fdisk, the option is "-l" (hyphen lowercase letter "L"). You've put "1" (the numeral "one") I don't know what you've typed for lshw, but that is wrong as well.

in linux, case (UPPER, lower, MiXed) is important. If you can't copy/paste, make careful note of the commands.

---

