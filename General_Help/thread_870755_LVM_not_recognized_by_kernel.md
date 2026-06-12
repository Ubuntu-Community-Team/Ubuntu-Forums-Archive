---
title: "LVM not recognized by kernel"
date: 2008-07-26
forum: General Help
---

### Post by agemon on 2008-07-26
hello, I have 2 hdds: one has 160 GB (sda) the other has 320 (sdb). Basically, I want to use 420GB from both of them for day-to-day linux usage and the remainder of 60GB for windows. For that, I have created a small boot partition (sdb1) and an LVM one (sdb2). Then I created a logical volume using sdb2 from my Kubuntu 8.04 installation.

Now comes the problematic part: I installed using debootstrap a small ubuntu system (this is the one I normally use because it runs faster). I also compiled a custom modular kernel (version 2.6.26). I didn't include all of the available features in the kernel, only the ones that I thought would be used. However, it doesn't recognize my LVM partion.

I searched on the internet and I do have dm-mod, dm-crypt, dm-multypath etc installed as modules. Also, fdisk -l detects the type of sdb2 as being LVM (system id 0x8e). Furthermore I have installed libdevmapper but still, on the minimalistic installation, vgscan or pvscan return no volumes whatsoever.

I believe it's a kernel problem because booting the small ubuntu system with the regular 2.6.24-19-generic kernel caused my LV to be detected, but I don't know what other module to include in the 2.6.26 kenrel.


Sorry for the long post, but I wanted to give as much details as I could :)

---

