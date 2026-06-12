---
title: "disk map changing"
date: 2008-05-28
forum: Hardware
---

### Post by loko11 on 2008-05-28
Hi Gurus,
I have 2 disk on my laptop. First is integrated in laptop and second is external disk connected via FireWire.
When I have external disk unplugged and boot ubuntu hardy, the inetgrated sata disk is /dev/SDA - this is right....
When I connect the external firewire disk and boot to linux, the FireWire is SDA and integrated SATA is /dev/SDB. This is not good for me, because I need to have integrated disk allways as SDA and external as SDB. 
(I know, in fstab, I have mapped folder by GUID of disk and it works, but for some applications, i need to have it like I describe (internal as SDA, external as SDB)

Thank you very much...

Lukas

---

### Post by logos34 on 2008-05-28
Good question.

> **loko11 said:**
> (I know, in fstab, I have mapped folder by GUID of disk and it works, but for some applications, i need to have it like I describe (internal as SDA, external as SDB)


you could use [drive labels]("http://www.linux.com/base/ldp/howto/Partition/labels.html#volumelabels") as a workaround.

---

### Post by loko11 on 2008-06-28
Thank you... this is a way too.
But, hm, there is really no way to change mapping of /dev/sdX ?


you could use [drive labels]("http://www.linux.com/base/ldp/howto/Partition/labels.html#volumelabels") as a workaround.[/QUOTE]

---

### Post by plonka2000 on 2008-09-15
I'm trying to find a solution to this same issue.
I'm setting up my new server and I've run into a bit of a wall when it comes to setting up my RAID array (which I plan to expand in future.

I'm booting off a USB disk, for my OS and using internal drives for the RAID.

Problem is my USB was mapped as **/dev/sda** while setting up the system. Now the system is done and I've plugged the drives in, my USB system drive is changed to **/dev/sdd**.

Does anyone know a workaround for this to force a device to a particular /dev mapping?

Thanks all.

[i]Edit:
The reason this is such an issue for me is that I plan to add more drives to my RAID array in future.
So I can see that when I plug more drives in my system drive will become **/dev/sde** then **/dev/sdf** etc...[/i]

---

### Post by plonka2000 on 2008-09-15
> **logos34 said:**
> Good question.



you could use [drive labels]("http://www.linux.com/base/ldp/howto/Partition/labels.html#volumelabels") as a workaround.

Thanks for that link btw.
From that page you have linked it seemed that this indeed wouldnt be much good. However, I re-read it and picked-up one gem of info that might well help:

> 6.2. Device Labels

devlabel is a script which creates symbolic links to devices. For example,

```
devlabel -d /dev/hdb1 -s /dev/home
```

will create a link from /dev/hdb1 to /dev/home. Crucially, it stores a unique identifier for the hardware that was on /dev/hdb1 and stores that identifier along with the link name that you specified in /etc/sysconfig/devlabel. **_If the hardware is later moved to /dev/hdc1, its unique identifier will be queried (using /usr/bin/partition_uuid), matched to its entry in /etc/sysconfig/devlabel, and again linked to /dev/home._** 

I've **bolded** and _underlined_ the part that I think will save the bacon here. So if I'm thinking of this clearly, I could make a link from my current **/dev/sdd** to ( for example) **/dev/systemroot**? And if in future **/dev/sdd** does indeed become **/dev/sde** and subsequently **/dev/sdf** then I'm still good because all static device mappings can be made directly to **/dev/systemroot**?

Could anyone verify this would be correct?

Thanks again.

---

