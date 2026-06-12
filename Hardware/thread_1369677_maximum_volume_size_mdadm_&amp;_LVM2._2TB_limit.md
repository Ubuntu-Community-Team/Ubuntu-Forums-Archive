---
title: "maximum volume size mdadm &amp; LVM2. 2TB limit??"
date: 2010-01-01
forum: Hardware
---

### Post by sulla on 2010-01-01
Dear all!

I have a question about the maximum storage volume size that I can use with ubuntu (currently 8.04 LTS, soon 10.04 LTS):

I have several 1TB HDDs each containing one 256MB (/dev/sdX1) and one 0.98TB partitions (/dev/sdX2)

I run a RAID5 on the /dev/sdX2 to create one /dev/mdN array. This array serves as ONE physical volume for LVM2.

Big question: If I add another 1TB drive I will suprass 2TB. Hopefully this will result in an MDADM array /dev/mdN of size >2TB. I would like to use this >2TB blockdevice as the expanded physical volume for my LVM2.

Questions:
* Will MDADM indeed create a 3TB /dev/mdN out of several 1TB partitions /dev/sdX2?
* Will LVM2 accept a 3 TB /dev/mdN PV?

The LVM2 HOWTO on TLDP.org says that the LV limit was 16TB (32bit linux) and 8EB (64bit linux) but it does not specify the maximum size for a PV. Neither did I find information on the maximum raid array size of MDADM.

Hm. I'd like to avoid data loss & frustration when I try to expand my array beyond 2TB...

kind regards,
sulla

---

### Post by richard.scott on 2010-01-02
I don't know if there are limits to the mdadm devices, but see if this helps with regards to creating a physical volume in LVM2:

"The default value for the **physical extent size** can be too low for a large RAID array.  In those cases you'll need to specify the **-s** option with a larger than default physical extent size.  The default is only 4MB as of the version in Fedora Core 5.  The maximum number of physical extents is approximately 65k so take your maximum volume size and divide it by 65k then round it to the next nice round number. For example, to successfully create a 550G RAID let's figure that's approximately 550,000 megabytes and divide by 65,000 which gives you roughly 8.46.  Round it up to the next nice round number and use 16M (for 16 megabytes) as the physical extent size and you'll be fine"

I found it here: [http://www.gagme.com/greg/linux/raid-lvm.php](http://www.gagme.com/greg/linux/raid-lvm.php)

Rich.

---

### Post by sulla on 2010-01-02
Hi Richard!

Thanks for your hint about the maximum PE number! It brought me a step further.

However, this information seems a bit outdated, perhaps it was true for LVM1.
In my LVM2 volumegroup I used the default physical extent (PE) size of 4MB and have 499,875 of them resulting in a size of 1.998 TB of my volumegroup. The largest of my logical volumes inside this VG uses 238,340 PEs resulting in a size of 931.02 GB.
So I don't think 65,535 PEs is an applicable limit any more.

With your hint I googled for "maximum number of PE for LVM2" and I found an IBM article ([http://www.ibm.com/developerworks/library/l-lvm2/](http://www.ibm.com/developerworks/library/l-lvm2/)) claiming that
> with LVM2, there's no limit on the maximum numbers of extents per PV/LV. The default extent size is 4MB, and there's no need to change this for most configurations, because there is no I/O performance penalty for smaller/bigger extent size.
While I don't believe there is *NO* limit, it certainly seems to be high enough for all practical purposes. So it's probably safe to assume that the same limits apply for PE and LE, that would set the limit to 16TB for 32bit OS with a 2.6 kernel according to the TLDP LVM2 howto.

In the meantime I found out that the 32bit i386 ubuntu server kernel comes with LBD enabled:

```
$ cat linux-2.6.24/debian/config/i386/config | grep LBD
CONFIG_LBD=y
```
LBD means large block devices: > "Say Y here if you want to attach large (bigger than 2TB) discs to your machine, or if you want to have a raid or loopback device bigger than 2TB."

So, mdadm should be able to create blockdevices >2TB in size.

I feel confident enough to assume that as long as the kernel has LBD support enabled, the rest (i.e. mdadm, lvm2, ext3) will work fine.

thanx,
sulla

---

### Post by richard.scott on 2010-01-04
Thanks for the feedback.

Did you ever find out if there is a limit to the max size of a mdadm raid device?

Rich

---

### Post by sulla on 2010-01-04
Hi Richard!

Nothing definitive.

I asked on the dm-crypt mailing list whether the LUKS cryptographic system supported blockdevices >2TB and Milan Broz from RedHat answered that
> from the kernel block device point of view, there is no difference between MD, lvm2 or dm-crypt/LUKS.
So, for the moment I would assume that the same limits apply. According to the TLDP's LVM2 Howto the limits for LVs (logical volumes) in LVM2 are
[LIST]
[*]2TB for 2.4 kernels,
[*]16TB for 32-bit CPUs on 2.6 kernels,
[*]8EB for 64-bit CPUs on 2.6 kernels,
[/LIST]
albeit I believe it is not the "bittage" of the CPU but of the OS that counts, i.e. if you run a 32bit i386 kernel on a 64bit CPU I still would assume that the 32bit limits apply...

I thus conjecture these limits also apply to mdadm raid-devices and LVM2 PVs (physical volumes).

Just a note, should you want to partition a >2TB raid blockdevice directly, you can't use fdisk to create an MBR, this is limited to 2TB, you would have to create a GPT (Gnu Partition Table) using parted (Gparted, QTparted...). I'll circumvent GPT and plan to let LVM2 do the trick of "partitioning" a >2TB blockdevice.

---

### Post by richard.scott on 2010-01-05
Ah yes, i'd forgotten about those limits. and yes, I think your right in thinking its the running OS that limits things, rather than the CPU. 

Thanks for the help.

Rich

---

