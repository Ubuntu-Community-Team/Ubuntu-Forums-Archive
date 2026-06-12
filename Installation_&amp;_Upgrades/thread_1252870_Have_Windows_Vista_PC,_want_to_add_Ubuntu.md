---
title: "Have Windows Vista PC, want to add Ubuntu"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by tblom on 2009-08-29
Hi everyone,

I have used Ubuntu for a while but have no experience with the installation of any OS. 

I just bought a new PC and it has Windows Vista preinstalled on a 1 TB hard drive. I would like to do the following:

- Keep the Windows Vista installation
- Install Ubuntu as well
- Be able to dual boot
- Make the Ubuntu partition as large as possible and the Vista partition as small as possible.

I should therefore shrink my Vista partition. This is my problem. Windows Vista 's partition shrink tool is not doing the job at all as it only lets me shrink the partition by a few gigabytes. This seems to be a known problem. I read on these forums that using GParted would cause problems for booting Vista. I don't know any other freely available tools that can shrink the partition while not messing up the Vista installation.

Another possibility I read is to make two partitions and reinstall first Vista and then Ubuntu from scratch. However, since I 'm new to this, this is too vague for me, especially the part where I have to partition and format a drive with Vista already installed on it. I would need step-by-step instructions on how to do this. 

Thank you very much for any help. It would be greatly appreciated.

---

### Post by stlsaint on 2009-08-29
I would suggest using Gparted as it is very compatible with all filesystems under windows...or since you said your not comfortable with that due to forum post you could try [EASEUS ]("http://www.partition-tool.com/personal.htm")for free...its third party but i have had and heard of much success with it for TB hdd's.

---

### Post by tblom on 2009-08-30
Thank you very much! Using Easeus I managed to shrink my Vista partition to 40 GB, exactly what I needed. I now have 876 GB of free space.

Eventually I would like 4 more partitions:

- Windows data(NTFS)
- Ubuntu /  (ext3)
- Ubuntu /home (ext3)
- Ubuntu swap (ext3)

Will I be able to create all of these during Ubuntu installation, or should I create the Windows data partition now using Easeus?

Also, will I be able to install dual boot?

Best regards and thanks again!

---

### Post by ad_267 on 2009-08-30
I would suggest setting up all of your partitions using Gparted before running the installer. Gparted can create an NTFS partition so you don't have to use Windows for that. When you install Ubuntu you can select the manual partitioning option and select the partitions you've created. Ubuntu will automatically install the GRUB bootloader and add an entry for Windows so you can dual boot.

Also, if you want to access your Windows data drive from Ubuntu remember to specify a mount point for it (eg /windowsdata).

---

### Post by tblom on 2009-08-30
Thanks! Could you please explain why you would use GParted rather than creating the partitions during Ubuntu installation? Isn't it possible to create an NTFS partition during Ubuntu installation?

Sorry for the n00b question, I 'm just curious :)

---

### Post by ad_267 on 2009-08-30
Hmm I guess I just prefer getting the partitions sorted out before hand. There's probably no real reason not to do it during the installation though, I think the installer just loads gparted.

So no it's not a noob question. :)

---

### Post by gavshouse on 2009-08-30
> **ad_267 said:**
> Hmm I guess I just prefer getting the partitions sorted out before hand. There's probably no real reason not to do it during the installation though, I think the installer just loads gparted.

So no it's not a noob question. :)

i agree, i would use ext4 for / instead of ext3 though should boot faster.

also for your /home you can install this driver for windows to view your home folder in windows if you want might help moving files from windows to ubuntu 

[http://www.fs-driver.org/](http://www.fs-driver.org/) Windows ext driver (i dont think it supports ext4 though)

---

### Post by tblom on 2009-08-31
Thanks guys!
I managed to create the necessary partitions for Ubuntu, I installed Ubuntu, I can dual boot AND my Vista installation is still alive. Worked like a charm!

The only thing I should mention is that it is NOT possible to create an NTFS partition during Ubuntu install. So I will create this one using Windows now and pray for good luck that I will still be able to mount it in Ubuntu :-)

---

