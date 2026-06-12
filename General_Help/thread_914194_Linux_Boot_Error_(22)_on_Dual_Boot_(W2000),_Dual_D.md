---
title: "Linux Boot Error (22) on Dual Boot (W2000), Dual Drive PC..."
date: 2008-09-08
forum: General Help
---

### Post by casparov on 2008-09-08
Hi, Everyone...

I dual boot Heron and W2000 using separate disk drives. I want to copy my Windows disk to a new hard drive for use in a new (dual boot) PC.

My Ubuntu disk is the slave disk. In order to copy my master drive I removed the slave disk--and, therefore, the Linux partition--to make room for the new drive for copying. GRUB produced the loading error (22), and my PC was useless, at that point.

Could anyone please explain how I go about bypassing or removing GRUB so that I might copy my master drive? Also, could anyone explain how I could then reinstall GRUB to renew my dual boot system. (My Ubuntu slave drive will be swapped into the new machine as a slave disk for dual booting.)

Many thanks for any help,

Casp

---

### Post by caljohnsmith on 2008-09-08
What's happening is that you have Grub installed to the master boot record (MBR) of the Windows master HDD, yet the Grub system files (such as menu.lst) reside on your slave HDD. Thus when you disconnect your slave HDD, you get that Grub error since it can't find the files its needs. 

Anyway, to fix your problem, you could temporarily reinstall the Windows MBR to the master drive so you can boot directly into Windows. To do this, if you have some sort of Windows 2000 install CD/disk, you can run the command:
```
fdisk /mbr
```
Or if you don't have the Windows CD/disk, there are ways of writing a Windows MBR with Linux. 

Once you are ready to reinstall Grub, connect your Ubuntu slave drive, boot your Live CD and do the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hd1,X), use that:][/COLOR]
grub> root (hd1,X)
grub> setup (hd0)
grub> quit
```
That will put Grub back in the MBR of your master HDD. Let me know how it goes or if you need more help/info. :)

---

### Post by casparov on 2008-09-08
CalJohn... 

You are a genius. 

Yes, I have a W2000 disk knocking around.  However, will this boot me to a prompt where I can enter "fdisk /mbr"? 

All Regards, 

Casp

---

### Post by caljohnsmith on 2008-09-08
> **casparov said:**
> 
Yes, I have a W2000 disk knocking around.  However, will this boot me to a prompt where I can enter "fdisk /mbr"? 

All Regards, 

Casp
I've never had to use Windows 2000, so sorry but I wouldn't know the details of getting to a command prompt. If it ends up being too difficult, like I mentioned before, there are ways of installing a Windows MBR from Linux. Let me know how it goes. :)

EDIT: I just realized that Windows 2000 might be recent enough that it uses "fixmbr" instead of the old "fdisk /mbr" command; "fdisk /mbr" may only be for Windows 98 or earlier. Anyway, one of those commands should work. :)

---

### Post by casparov on 2008-09-09
CalJohn... 

Thanks so much for your assistance...  Since I have reinstalled the Linux (slave) drive so that I can boot into Windows.  This will allow me to hit the F8 key and get to a C:\ .

A Question: will a C-prompt acquired in this way do the trick?  

Thanks again, 

Casp

---

### Post by caljohnsmith on 2008-09-09
> **casparov said:**
> CalJohn... 

Thanks so much for your assistance...  Since I have reinstalled the Linux (slave) drive so that I can boot into Windows.  This will allow me to hit the F8 key and get to a C:\ .

A Question: will a C-prompt acquired in this way do the trick?  

Thanks again, 

Casp
At least for Windows XP, I don't think the fixmbr program is put on the HDD with the Windows install, so it is probably the same for Win 2000. You certainly have nothing to lose by trying "fixmbr" at the C:\ prompt (or "fdisk /mbr" if that doesn't work), but I think it will tell you the command is not found. Most likely you'll need to run it from your Win 2000 CD/disk.

---

### Post by casparov on 2008-09-09
CalJohn...  

You were right--I couldn't get to a command prompt through the GRUB option; all that I could achieve was a normal W2000 boot. 

I changed my boot sequence to my CD-ROM and got the W2000 to take over.  However, I saw no good option there, nothing for a command prompt.  All that is offered is a W2000 repair or a W2000 setup. 

Could you explain the steps to get to a W2000 command prompt booting from the W2000 disk?  (I looked through a Google search for this information and couldn't get past all the entries which were devoted to making a W2000 boot disk, which is not what I want.  (Or is it?) 

All Regards, 

Casp

---

### Post by casparov on 2008-09-10
CalJohn...  

Thankfully, I restored the Windows MBR and copied my W98 and W2000 on my master drive to a new master drive to be fitted into the new machine.  You were correct about everything, including the command from within the Windows restore function.  (Ubuntu will be the slave drive in the new system.)

I have a couple of questions that relate to Windows formatting.  The new drive is a 360GB Seagate ATA.  The Seagate disk wizard formatted and copied my Windows partitions using its "proportional" copying system.  I.e., when the new drive is larger than the original source drive then the original partitions will occupy proportionally larger segments of the new target drive.  However, when the procedure finished, the partitions were no larger, at all.

Could you please provide any insight into how one copies partitions to a new, larger drive in such a way as to take advantage of the larger capacity.  Must one do this through fdisk?  I.e., must one create, manually, a large FAT32 (for my W98 partition) and a large NTFS then copy from the source drive to the new destination partitions?  Do you know an easy way to copy the drives over?  

Anyway, we're gaining on it. 

All Regards and many thanks,

Casp

---

### Post by caljohnsmith on 2008-09-10
> **casparov said:**
> 
I have a couple of questions that relate to Windows formatting.  The new drive is a 360GB Seagate ATA.  The Seagate disk wizard formatted and copied my Windows partitions using its "proportional" copying system.  I.e., when the new drive is larger than the original source drive then the original partitions will occupy proportionally larger segments of the new target drive.  However, when the procedure finished, the partitions were no larger, at all.

Could you please provide any insight into how one copies partitions to a new, larger drive in such a way as to take advantage of the larger capacity.  Must one do this through fdisk?  I.e., must one create, manually, a large FAT32 (for my W98 partition) and a large NTFS then copy from the source drive to the new destination partitions?  Do you know an easy way to copy the drives over?  

Anyway, we're gaining on it. 

All Regards and many thanks,

Casp
If your Seagate disk wizard was at least able to copy the Windows partitions on your old drive to your new HDD, have you tried booting from your new HDD and using Windows on it yet? If you can do that successfully, then I'm thinking all you would need to do is use gparted (Ubuntu's partition editor) to expand the size of those partitions to fill the entire disk. I don't have a lot of experience trying to image one HDD to a larger HDD, so I don't know off-hand of software that will automatically "expand" it or copy it "proportionally" so you can fill the HDD in one step. But like I mentioned, if your Windows on that new HDD boots fine, I would just expand the partitions with gparted. I think that is all it would take. Let me know how it goes or what you decide to do.

---

### Post by casparov on 2008-09-10
CalJohn... 

Wow, thanks for the heads up re gparted.  The copied disk will successfully boot so, once I get the new machine ready (it will be so in a few days) I will attached the Ubuntu slave disk and restore GRUB.  At that time I will also try to expand the partitions using your suggestion.  

I wonder, could I contact you once I get things ready?  You were the only responder to my original questions over a few posts.  

Thanks so much,  

Casp

---

### Post by caljohnsmith on 2008-09-11
> **casparov said:**
>  
I wonder, could I contact you once I get things ready?  You were the only responder to my original questions over a few posts.  

Thanks so much,  

Casp
I'm usually around most days, so if you just post to this thread again, I'll surely notice it. Good luck and let me know how it goes. :)

---

