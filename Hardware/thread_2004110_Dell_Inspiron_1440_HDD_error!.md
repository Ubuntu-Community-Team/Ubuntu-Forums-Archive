---
title: "Dell Inspiron 1440 HDD error!"
date: 2012-06-15
forum: Hardware
---

### Post by nipunshakya on 2012-06-15
Hi forums.
Recently, my harddisk ran into a problem which has made me worried. Please refer the pictures attached and suggest what should i do?

I have dual boot win 7 and ubuntu 12.04. The only thing i did new in my laptop was  run virtualbox and try to share a ntfs partition d: in winxp host ran on the virtualbox. Rest stuffs were normal things like surfing and others... 

I assume there is something to do with virtual box for my harddisk to generate the error... or maybe i am wrong... 
Im planning for a clean format of all the drives and beginning from zero level by installing win 7 and ubuntu again... will that help solve my problem??

Its the first time i've experienced the error and its freaking me out... Please help.. :(

Regards, WinuxUser

---

### Post by nipunshakya on 2012-06-15
mate that links provide a webpage in language i don't understand...:( but i appreciate ur help though...

---

### Post by sikander3786 on 2012-06-15
Those pictures clearly express that the HDD is failing and it is a hardware failure. It was just a co-incidence that the HDD decided to fail when you were trying to run Virtualbox stuff otherwise there isn't any relation between the two. It simply can't be like that.

I don't think re-formatting would help here. Still, you can try your luck.

But before doing anything else, backup any important data that is contained on that HDD. Things would keep getting worse as you keep using that HDD and it might well leave you in a state when accessing that data becomes impossible.

The bottom line, in my opinion, your laptop needs a new HDD.

---

### Post by nipunshakya on 2012-06-15
> **sikander3786 said:**
> Those pictures clearly express that the HDD is failing and it is a hardware failure. It was just a co-incidence that the HDD decided to fail when you were trying to run Virtualbox stuff otherwise there isn't any relation between the two. It simply can't be like that.

I don't think re-formatting would help here. Still, you can try your luck.

But before doing anything else, backup any important data that is contained on that HDD. Things would keep getting worse as you keep using that HDD and it might well leave you in a state when accessing that data becomes impossible.

The bottom line, in my opinion, your laptop needs a new HDD.

so it clearly means that there is no way my hard-disk can be either repaired, or re-transformed to its normal working behavior even after a format... :(

---

### Post by sikander3786 on 2012-06-17
> **WinuxUser said:**
> so it clearly means that there is no way my hard-disk can be either repaired, or re-transformed to its normal working behavior even after a format... :(
Yeah, probably.

But trying your luck with a re-format won't be offensive before you go for the HDD replacement. ;)

---

### Post by nipunshakya on 2012-06-17
Im on it...will report back soon... :)

---

### Post by nipunshakya on 2012-06-18
A start from zero didn't help me...
i ran the following in the terminal....
```

winuxuser@MagicBox:~$ sudo fdisk -lu
[sudo] password for winuxuser: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9f7139f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2046   239996927   119997441    5  Extended
/dev/sda2       239996928   625141759   192572416   83  Linux
/dev/sda5            2048     7999487     3998720   82  Linux swap / Solaris
/dev/sda6         8001536    45600767    18799616   83  Linux
/dev/sda7        45602816   239996927    97197056   83  Linux
winuxuser@MagicBox:~$ 


```
any chances of me getting ditched by the HDD soon?? coz i am still need the HDD to work for me....:(

---

### Post by ahallubuntu on 2012-06-18
"Zero" the hard drive means erase everything on it by writing zeros to every sector, then checking the S.M.A.R.T. status again and see if those bad sectors have been cleared.  You would have to do this by booting a Linux live CD - you can't zero the drive while you are running an operating system from it.

This CAN work on drives with just a few pending sector errors in my experience.  But your drive already has 533 reallocated sectors.  That means 533 sectors have already failed and been replaced by the drive firmware - and at some point (if not already) your drive runs out of spares. And then it is not usable anymore, because you will keep creating files in areas with failed sectors.

I would give up on your hard drive and replace it - sorry.  Hard drives do fail all the time. Sad fact of computer life.

---

### Post by nipunshakya on 2012-06-19
> **ahallubuntu said:**
> "Zero" the hard drive means erase everything on it by writing zeros to every sector, then checking the S.M.A.R.T. status again and see if those bad sectors have been cleared.  You would have to do this by booting a Linux live CD - you can't zero the drive while you are running an operating system from it.


Can you elaborate a bit in detail about this method please... i can't give up on my HDD right now because i can't have another one... :(

---

