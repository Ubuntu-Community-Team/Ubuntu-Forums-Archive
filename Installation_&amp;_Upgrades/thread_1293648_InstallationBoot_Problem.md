---
title: "Installation/Boot Problem"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by AMadDog on 2009-10-17
Hi I having a problem with the boot up after installing linux, I have a PC with a completly blank Hard drive (I had wiped it to use in another PC) and I recently decided to install Linux on to it so I downloaded it from the site Burned the iso Image onto a disk (the disk had the recommended specs) and put it into my PCs drive first I went to try ubuntu then I double clicked Install on the desktop it installed and I clicked restart when I was prompted to do so, It booted up and loaded the disk again and I clicked on boot from first hard drive like the guy in the youtube video I was watching did and when I did It almost immediately came up with an error message on a black screen In White BIOS like text saying: 
Booting from local disk...
isolinux: Disk error 01, AX = 0201, drive 80

Boot failed: press any key to retry...


Please help me 
Cheers

---

### Post by oldfred on 2009-10-17
When you made the CD did you use the slowest speed possible, it makes for better or more reliable burn of the CD.

Did you try running the liveCD to test that it worked ok with your system?

If you fully installed on your hard drive you should not need the CD anymore. Your system should boot to the Grub menu.

---

### Post by AMadDog on 2009-10-18
when  I try without the CD I get this message 
Searching for Boot Record from SCSI..Not Found

Boot Failure 
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot Device
Press any key when ready

And no I didn't burn it at the slowest speed. I pretty sure the disc works because I went on try Ubuntu and that work perfectly, I also did the CD check thing and the Memory check.
I really want to use ubuntu but I really need help to get past this hopefully minor setback 
Cheers AMadDog

---

### Post by oldfred on 2009-10-18
From the liveCD lets see how your hard drive looks:

run this command in the terminal and post the results:

```
fdisk -l
```

that is - small L not 1 or I.

---

### Post by AMadDog on 2009-10-19
whats the LiveCD? is it the: Try Ubuntu without any changes to your computer. Beacause if it is then yes It works fine.

---

### Post by AMadDog on 2009-10-19
ok yes I googled Ubuntu LiveCD and will post the results shortly

---

### Post by AMadDog on 2009-10-19
is there supposed to be a space in there before the -l or not? I tried with and without, 
with results: nothing it just went down to a new ubuntu@ubuntu:~$ 
Without space results: bash: fdisk-l: command not found
Thats all, I don't know if Im doing right:confused: it is the terminal under: applications, accessories? I think its the only one?

---

### Post by oldfred on 2009-10-19
We post terminal commands as it is easy to copy and paste them into the terminal either from your Ubuntu install or the liveCD. Many things can be done from a menu item but it is more difficult to explain and the results are graphical so not as easy to paste back.

sudo fdisk -l    #fdisk space dash small L not I or  1

If in a live Cd the sudo for superuser is not required.

---

### Post by AMadDog on 2009-10-19
so I type:
(space)fdisk(space)-l

---

### Post by AMadDog on 2009-10-19
oh wait i type:
sudo fdisk -l (small L)
don't I
Results I will post In a minute or two
Cheers

---

### Post by AMadDog on 2009-10-19
And the results are in:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbe509a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  83  Linux
/dev/sda2               7          37      249007+  82  Linux swap / Solaris
/dev/sda3              38        4270    34001572+  83  Linux
/dev/sda4            4271        4865     4779337+   5  Extended
/dev/sda5            4271        4865     4779306   83  Linux

this is my latest attempt (Also failed) I partitioned the Hard drive myself (I had Instructions from a PC shopper magazine)
[COLOR=#888888]
[/COLOR]

---

### Post by dhavalbbhatt on 2009-10-19
Have you tried re-installing all over again? If you are going to just install Ubuntu on the whole 40GB disk, I am thinking you don't even need to partition your HDD (I think the partioner, at the time of installation will partition a small portion of the disk for swap, but that should be extent of partitioning that will happen - all automated). I am no expert, but looking at the fdisk output, it seems that there are a lot of partions on your disk, an installation issue I am guessing, if so, doing a clean re-install should solve your issues.

Thanks,
DB

---

### Post by AMadDog on 2009-10-19
My first install I selected entire disk and I have reinstalled it about 10 times with no success, however I will once more reinstall and then if it dosen't fix it I will post the results of the fdisk -l code

---

### Post by AMadDog on 2009-10-19
I don't suppose it would make any difference that I have a AMD proccessor would it?

---

### Post by oldfred on 2009-10-19
Processor should make no difference. 

As dhavalbbhatt says it looks like you have created several duplicate partitions are part of your installs. I also thought use entire disk was a choice as opposed to side by side, but I always separately make partitions and use manual install telling it which partition to use for what. I had a new 640GB HD and did not want it to use the entire disk and there was nothing for side by side.

If use entire disk does not work, then I would use gparted to delete all the partitions before reinstalling just to make sure it uses the entire disk.

---

### Post by AMadDog on 2009-10-19
I tried to reinstall but get this message :
 
[Errno 5] Input/output error 

It said that it is often due to a faulty cd or hdd :mad: It also says that it might help to burn the disc again
so im gonna burn it again
fingers crossed it works 
wish me luck!!:(

---

### Post by AMadDog on 2009-10-19
don't I need an OS on it to use gparted
remeber that I had wiped the hard drive for use in my other pc

---

### Post by AMadDog on 2009-10-19
ok I have burned a new disc and am about to try It Iwill post results in 30 minutes or tommorow UK time:) wish me luck

---

### Post by bulldog on 2009-10-19
If you have a working live-cd,you can boot it and use gparted to partition your hdd.
As suggested,remove all partitions one by one till you have a disk with only unallocated space,you'll have to delete the logical in the extended partition first,before you can delete the extended partition!

Create a primary partition 10GB for /
Create a primary for swap 2GB
Create a primary as big as the remaining space for /home
When you install ububtu and the partition manager comes up,choose the manual option!
Select the 10GB partition set it to format ext3 and mountpoint /
Select the 2GB and mount it as swap [formatting is default if I'm correct]
Select the last primary set it to format ext3 and mount point /home

Continue the install.

---

### Post by dhavalbbhatt on 2009-10-19
> **AMadDog said:**
> don't I need an OS on it to use gparted
remeber that I had wiped the hard drive for use in my other pc

During the installation process, Ubuntu will format whatever portion of the disk you are allocating to Ubuntu (for example: on a 40GB HDD, if you are installing Ubuntu on 30GB, then Ubuntu installation will format 30GB of your HDD before installing the OS). If you are not going to use the HDD for anything else, then you can use the entire 40gigs and Ubuntu will format the disk for you, you won't have to manually use GParted. 

Also understand, a lot formating/re-formatting of the HDD may corrupt the disk. I have lived through that. If your problems persist, I would suggest getting a new HDD and installing Ubuntu on that.

DB

---

### Post by AMadDog on 2009-10-19
ok thanks to the two of you above I do have another 40gig hdd I might try if this dosen't work

---

### Post by AMadDog on 2009-10-19
um Gparted wouldn't let me delete /dev/sda2 which also has a sub folder thing /dev/sda5 (also unable to delete)

---

### Post by AMadDog on 2009-10-19
but I have 36.66 of 37.27 unallocated

---

### Post by AMadDog on 2009-10-19
> **bulldog said:**
> If you have a working live-cd,you can boot it and use gparted to partition your hdd.
You'll have to delete the logical in the extended partition first,before you can delete the extended partition!

How do I do that?
Sorry I'm a complete 13 year old linux noob

---

### Post by AMadDog on 2009-10-19
Im just gonna use the installation partitioner for now

---

### Post by bulldog on 2009-10-19
First you have to be sure all partitions are not mounted,if there's a locker behind a partition,it means it's mounted.

Device Boot Start End Blocks Id System
/dev/sda1 * 1 6 48163+ 83 Linux <---remove this one step 5
/dev/sda2 7 37 249007+ 82 Linux swap / Solaris <---remove this one step 4
/dev/sda3 38 4270 34001572+ 83 Linux <--- remove this one step 3
/dev/sda4 4271 4865 4779337+ 5 Extended <---then remove this one step 2
/dev/sda5 4271 4865 4779306 83 Linux <---remove this one first step 1

If you cant remove swap sda2 it's no problem we can use it again.

Create a primary partition 10GB for /
Create a primary for swap 2GB <--- don't create this one if step 4 fails
Create a primary as big as the remaining space for /home
When you install ububtu and the partition manager comes up,choose the manual option!
Select the 10GB partition set it to format ext3 and mountpoint /
Select the 2GB and mount it as swap [formatting is default if I'm correct]
Select the last primary set it to format ext3 and mount point /home

---

### Post by AMadDog on 2009-10-19
ok I will do that tommorow

---

### Post by AMadDog on 2009-10-20
Im sorry to say it didn't work](*,)

---

### Post by dhavalbbhatt on 2009-10-20
> **AMadDog said:**
> Im sorry to say it didn't work](*,)

What didn't work? The deletion of various partitions or the re-install on the current HDD or the re-install on a new HDD?

---

### Post by AMadDog on 2009-10-20
reinstall on current HDD

---

