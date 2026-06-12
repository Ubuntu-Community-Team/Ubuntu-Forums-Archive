---
title: "Bootit Ng + Raid 0 + ubuntu installation"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by OldandGrim on 2009-10-16
I am trying to install Unbuntu on a raid 0 configuration with Bootit Ng a partion manager [https://terabyteunlimited.com/bootit-next-generation.htm](https://terabyteunlimited.com/bootit-next-generation.htm). From what I can read I have to use the alternative install and from bootits documentation install in expert mode ([https://terabyteunlimited.com/kb/article.php?id=279](https://terabyteunlimited.com/kb/article.php?id=279)) but during the installation of Ubuntu when reaching where to install the Grub it has no option to install it anywhere else except to hd0 it gives the oportunity not to install grub and warns me where it intends to install it but no opportunity to choose where to install as apposed to the knowledge base articles install using the live cd advanced options after setting up partitions where it has a list of places to install grub this path would be great except it does not reconigse the raid
 
I am still trawling the ubuntu forums reading community documentation researching google resaults and reading bootits documentation where they do have a lot of info with regards to installing ubuntu and linux distros in general. I am sure that amongst all this the answers are there and I will eventually get my head around it and solve the problems myself but after two long days and nights I thought I would ask here. :P
 
I am installing on a Asus p6t Deluxe v2 i7 920 two 1tb Western Digital hard drives set up as raid 0 BootIt NG is installed as not to limit the number of partitions with the EMBR on the front of the HD followed by a 80 gig partition for Win7, followed by Partitions for Ubuntu, 15 gig for root, 12 gig for swap, 250 gig for home 
 
To simplify what I am asking during the alternate install can I choose where to install the Grub (expert mode?)
 
I appreciate any help available

---

### Post by OldandGrim on 2009-10-17
Well I am still going from what I can find on the net and within these forums all I need to do now is to install grub which I have tried like so
 
grub> setup (hd0,0) which returns an error of "Error 17 cannot mount selected partition" which I have found many posts and answers to here and on google. But as of yet I am unable to get my head arround it or solve the problem. 
 
Please someone help I feel I am so close and was so looking forward to dropping windows like a stone and joining Linux !!!!

---

### Post by tosk on 2009-10-17
You can choose to install GRUB to the MBR or to the partition that contains your /boot directory.

ie...

**(hd0)** is the MBR of the first drive.
**(hd0,0)** is the first partition of the first drive.

The error you got from GRUB was telling you that GRUB can't read from the first partition on the first drive. Or rather that it's not of a type that it can read.

With everything I've seen and read though, RAID shouldn't be possible with linux using the Intel ICH10R chipset.

---

### Post by OldandGrim on 2009-10-17
> **tosk said:**
> With everything I've seen and read though, RAID shouldn't be possible with linux using the Intel ICH10R chipset.
 
Please tell me this is not so ? Surly !!. The chipset is common hardware and a raid 0 setup is common this would deny large portions of the pc comunity who are desperate to leave windows ???

---

### Post by tosk on 2009-10-17
ICH10R is a relatively new chipset. The driver in Linux just doesn't support RAID for that chipset at this time.

I had a similar problem: Ubuntu couldn't see my "storage" array which consisted of 3 250GB drives. It saw each drive individually but not the array as a whole.

---

### Post by OldandGrim on 2009-10-17
> **tosk said:**
> ICH10R is a relatively new chipset. The driver in Linux just doesn't support RAID for that chipset at this time.
 
I had a similar problem: Ubuntu couldn't see my "storage" array which consisted of 3 250GB drives. It saw each drive individually but not the array as a whole.
 
Well many thanks for your reply
 
I have waited five years sinse I first looked at linux I guess I will have to wait a little bit longer, shame I think with the release of win7 now is a great time to be bringing as many people to the linux party as possible. :(

---

