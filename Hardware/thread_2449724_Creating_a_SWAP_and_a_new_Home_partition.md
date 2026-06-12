---
title: "Creating a SWAP and a new Home partition"
date: 2020-09-01
forum: Hardware
---

### Post by sabyuntu on 2020-09-01
Hi,

I am trying to create a SWAP and a new home partition in the unallocated space in the hard drive. I have an 12 year old laptop with only 2 GB RAM. I am new to Linux. 

Please see the image to understand the dilemma. 


[https://ibb.co/0jrxm3v](https://ibb.co/0jrxm3v) 

MY problems are: 

1 I am getting the option to create only logical partition  within the exiting one. Not getting the option to create an adjacent partition to the existing one. 

2. If I create a SWAP partition as logical and withing the existing one, will this work as a SWAP? 

3. I want to create a new Home partition. So, will the logical one work? 

4. Please give steps to move the Home folder location after the partition is created.

---

### Post by deadflowr on 2020-09-01
Yes create logical partitions.
It's your only real (easy) choice unless you rebuild from scratch and use the something else option in the installer.

On moving Home: [https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

The system should have a swap file, if not when creating the swap partition you'll need to add it to the fstab:
[https://help.ubuntu.com/community/SwapFaq#How_do_I_add_or_modify_a_swap_partition.3F]("https://help.ubuntu.com/community/SwapFaq#How_do_I_add_or_modify_a_swap_partition.3F")

Good rundowns of doing a fresh install using the something else option:
[https://www.tecmint.com/ubuntu-19-04-installation-on-uefi-firmware/]("https://www.tecmint.com/ubuntu-19-04-installation-on-uefi-firmware/")
[https://ubuntu-mate.community/t/install-ubuntu-mate-using-the-something-else-method/651]("https://ubuntu-mate.community/t/install-ubuntu-mate-using-the-something-else-method/651")

Edit:
Forgot to mention in all cases you should have your data backed up somewhere in case things go awry.

---

### Post by CelticWarrior on 2020-09-01
1. You have what seems to be a UEFI installation in a MBR drive (it works for Linux but not Windows; Windows strictly requires GPT for UEFI mode and MBR for BIOS mode). Due to this and how you installed it you have sda2 as a primary partition extended to use all the remaining space. Inside of that you have sda5, the root file system as a logical partitions and a lot of unallocated space where you can create many more logical partitions. 

2. Both /home and swap work perfectly in logical partitions.

3. Both /home and swap work perfectly in logical partitions.

4. Really? Wouldn't it be better to start from scratch and define your intended partitions during installation? It will be a LOT FASTER, for sure.


If re-installing do your backups first, of course. Then in the live session, prior to installing, open GParted, select the target drive (if more than one), Device menu > New partition table and select "GPT" (this will remove all the existing partitions). Then start the installation as usual. Either let it do the automatic partitioning (one single root partition including /home and swapfile; a separated swap partition is no longer required, the default is a swapfile) or choose something else and carve your intended partitions in the now blank drive. Because now GPT all partitions will be primary and in practice unlimited, unlike with MBR where you can have up to 4 primary partitions hence why one or more created as extended in order to be able to allocate inside many more logical partitions if needed.

---

### Post by sabyuntu on 2020-09-01
Thanks for your inputs. One more thing came to my attention. As these are sub-partitions, that I am going to create, in case of re-installation, all will be washed? Am I right?

I tried installing using the **Something else** method, twice, the installation ended in an error. So, I went ahead with the auto partition method. But, I will try it again now, with the links you shared. need to carefully study them before I start. 

I think, I did not create the EFI standard partition, I had no knowledge that I should. I did created 4 partitions in the **Something else **mode: 20GB root + 50 MB boot loader + Swap 2.5 GB + Home <100 GB.  This probably created the error, at the end of the installation process. It fails to load/start certain modules.

---

### Post by CelticWarrior on 2020-09-01
You want them washed, as commented before, if you do a re-installation. There's really no point in using an almost 40 years old partition scheme in a new UEFI computer. You want GPT.

> [COLOR=#000000]in the live session, prior to installing, open GParted, select the target drive (if more than one), Device menu > New partition table and select "GPT" **(this will remove all the existing partitions)**[/COLOR]

---

### Post by mastablasta on 2020-09-02
12 year old laptops probably doesn't have UEFI. you can do manual (something else) MBR install. there is no need for boot partition there.

also separate home is not needed. although it has some benefits, might have some cons as well. i know it saved my OS once, though i could probably save it with a live boot anyway. it's kind of like having My Documents (or user folder) on separate partition.

---

### Post by sabyuntu on 2020-09-02
Hi,

I was trying to reinstall. But I am not getting the "**efi system partition**" option in the **Use as** menu, when trying to create the boot partition. 

Can you enlighten me here?

---

### Post by sabyuntu on 2020-09-02
Installed by creating a FAT32 partition for boot. Now, it is not booting after installation. Probably, the original partition method that I used is the only way. [https://ibb.co/0jrxm3v](https://ibb.co/0jrxm3v)

---

### Post by Dennis N on 2020-09-02
> **sabyuntu said:**
> Hi,

I was trying to reinstall. But I am not getting the "**efi system partition**" option in the **Use as** menu, when trying to create the boot partition. 

Can you enlighten me here?
For the FAT 32 partition, you don't specify how it's to be used from that menu. Instead, you set the boot flag on the partition, which automatically also sets an esp flag:

Menu Bar > Partition > Manage Flags

---

### Post by sabyuntu on 2020-09-02
Okay. Solved. This is for the record. 

During installation go into **Something else** > On an empty drive, there will be two partitions. One is the FAT 32 partition slightly > 500mb ,  Keep this one.** Do not delete**  > Delete the other partition and convert it to free space and then make the Home partitions etc. This worked. Verified after installation. Everything works fine. 

I guess this happens to older laptops only. I found many references/ forum discussions at many places. People often face this issue.

---

### Post by CelticWarrior on 2020-09-02
> [COLOR=#000000]12 year old laptops probably doesn't have UEFI. you can do manual (something else) MBR install. there is no need for boot partition there.[/COLOR]


And yet it shows a UEFI mode installation. UEFI computers predate the mass adoption of GPT/UEFI that only happened around 2012 with Microsoft forcing it to the manufacturers for the preinstalled Windows 8.

---

### Post by mastablasta on 2020-09-03
> **CelticWarrior said:**
> And yet it shows a UEFI mode installation. UEFI computers predate the mass adoption of GPT/UEFI that only happened around 2012 with Microsoft forcing it to the manufacturers for the preinstalled Windows 8.

UEFI was around since about 2003 and it is different from secure boot. 

however, it still hasn't appeared massively on home PCs and laptops until about after 2011 or 2012 when windows 8 came out. so a laptop from 2008 will probably boot with MBR and have the old BIOS on it or have an option to do that. 

but of of course there were a few that already used UEFI in 2008 and some had UEFI with BIOS compatibility modules.  i am not sure how the installer determines the install type (is it manual or auto?). default is now likely UEFI.

in any case as long as we resolved the issue and the user can now use the hardware. :D

---

### Post by CelticWarrior on 2020-09-03
> [COLOR=#000000]i am not sure how the installer determines the install type (is it manual or auto?). default is now likely UEFI.[/COLOR]

It is determined on boot. If you have UEFI with CSM and the installation media can boot in both modes it'll appear duplicated in the list of bootable devices. One probably with "UEFI:.." and the other without it. It can also happen that the installation media has been made to boot only in one mode - typically what happens with Rufus, depending on the settings - so, in those cases, "BIOS" media will boot and install in Legacy mode with CSM enabled or not boot at all with "UEFI only".

---

