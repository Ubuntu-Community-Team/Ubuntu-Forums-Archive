---
title: "About adding NAS to Intranet"
date: 2014-09-04
forum: Hardware
---

### Post by satimis on 2014-09-04
Hi all,

I have 2 PCs connected via a router.

PC1 - Running Orcale VirtualBox with about 40VMs installed, Ubuntu/Fedora/LinuxMint/SUSE Linux/Debian etc., and a 1TB hard drive for storage.  Host-Ubuntu 12.04 64bit

PC2 - Running Oracle VirtualBox with about 20VMs installed, Ubuntu/Fedora/LinuxMint/Debian/Win7/WinServer etc., and a 640G hard drive for storage.  Host-Debian7 64bit

Router - TPLink (150MB) with 4 ports

Periodically running "rsync" via the router transferring newly added data from PC1 to PC2 and PC2 to PC1 respectively.  Now I'm considering to add NAS to the network making use of the storage HDs (1TB SATA3 WD Black Label HD)(640G SATA3 Seagate HD) and the spare port on the router.


I have following questions please shed me some light sharing me your experience.  This is my 1st time purchasing a NAS.

1) Can the mentioned storage HDs of different brand and specification be used in the same NAS box?
2) Both storage HDs are running ext4. Can I change the file system to NTFS (Windows), copying all data back afterwards?  (please see my explanation below)
3) Suggestion on selecting a NAS box


Explanation:
===========
1) Configuration
PC1 - OS (Ubuntu 12.04 64bit - host) running on 120G SSD.  VMs on a 2TB HD (SATA3 WD Black Label)

PC2 - OS (Debian 7 64bit - host) running on 120G SSD.  VM on a 1.5TB HD (SATA3 WD Black Label)

There are sufficient space coping all data on the storage HDs to the HDs abovementioned for temporary storage.

2)
Recently I encountered a problem on scanning color negatives on my old scanner Epson Perfection 3490 photo.  I can't make it to work on Ubuntu.  Finally I digged out an old HD (160G Maxtor SATA) on shelves, attached it to PC2 and installed Windows 7 64bit on it.  After installing the FREE software from Espon, now my old Epson scanner can scan color negatives nicely.  However another problem popup, sharing data between Windows and Linux.  The former can't read ext4.  On googling I found many suggestion, installing ext4 reader software on Windows 7.  I don't know how good they are?  For such a reason I'm considering changing the file system on NAS to NTFS (Windows system)

3)
There is no problem sharing data amongst host and VMs.


I'm prepared;
1) purchasing a NAS, installing the old storage HDs (mentioned above) on it.

2) purchasing a 500G SSD to replace the 120G SSD on PC2 (recently the price of SSD has been dropped)

3) making use of 120G SSD on PC2 installing Windows 7.


Thanks in advance.

Regards
satimis

---

### Post by TheFu on 2014-09-04
Most NAS devices that support important protocols you want (NFS) will be picky about specific hard drive models.  Definitely read their suggestions on drives.

Most NAS devices trade convenience for high price.  It is amazing what a $200 PC can do compared to a $900 NAS. Just sayin'.  Plus the PC won't be as picky about matching HDDs, won't store files in a proprietary format that can't be accessed from normal Linux PCs, etc....   Convenience has a price and it isn't just $$$.

Just setup samba to allow Windows to see/access Linux data ... or store it in NTFS partitions which can be available to everyone. This is for data, not programs. I wouldn't use alpha-software that reads ext2/3/4 from Windows. It just isn't necessary.

Sorry didnt carefully read the rest of the post.

Why use vbox when it is clear that KVM is what you want for that number of VMs?  Performance will be better, that is certain - unless the VMs are disk IO bound.

---

### Post by satimis on 2014-09-04
> **TheFu said:**
> Most NAS devices that support important protocols you want (NFS) will be picky about specific hard drive models.  Definitely read their suggestions on drives.

Most NAS devices trade convenience for high price.  It is amazing what a $200 PC can do compared to a $900 NAS. Just sayin'.  Plus the PC won't be as picky about matching HDDs, won't store files in a proprietary format that can't be accessed from normal Linux PCs, etc....   Convenience has a price and it isn't just $$$.
Hi,

Thanks for your advice.

Most important to me are;
1) Matching HDDs.  I'm not prepared duming the old HDDs.
2) Change of file system for data from ext4 to NTFS (this is not so important as 1) above)

I have no pre-set budget.


> 
Just setup samba to allow Windows to see/access Linux data ... or store it in NTFS partitions which can be available to everyone. This is for data, not programs. I wouldn't use alpha-software that reads ext2/3/4 from Windows. It just isn't necessary.

Oh, yes.  Good suggestion.  I almost forget "samba"

Can data on ext4 partition be copied back to NTFS partition without problem?


> 
Why use vbox when it is clear that KVM is what you want for that number of VMs?  Performance will be better, that is certain - unless the VMs are disk IO bound.
Good question.

I used KVM before VBox.  I changed to the later because easier to maintain and configure.

I may go back go KVM on the new 500G SSD, if the exported VMs from VBox can be imported back to KVM.  From my recollection it might be possible.  Because I encountered the same problem on switching from KVM to VBox several years back.  But I'm not sure.  Googling may throw me some light.

Regards
satimis

---

### Post by TheFu on 2014-09-05
virt-manager is the tool you want to manage  server KVM VMs.

---

### Post by satimis on 2014-09-05
Hi TheFu,

A further thought on your advice;
> 
Just setup samba to allow Windows to see/access Linux data ... or store it in NTFS partitions which can be available to everyone. This is for data, not programs. I wouldn't use alpha-software that reads ext2/3/4 from Windows. It just isn't necessary.

The data HDD is solely for storge without OS.  Besides when Windows 7 is running other HDDs is not working which is cotrolled by BIOS.

Regards
satimis

---

