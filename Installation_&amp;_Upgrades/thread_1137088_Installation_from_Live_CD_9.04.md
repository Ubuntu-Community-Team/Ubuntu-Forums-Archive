---
title: "Installation from Live CD 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by blues2use on 2009-04-25
I am posting this via the 9.04 Live CD on my laptop so I know that my wireless connection works as do my wireless usb mouse, sound, screen resolution, etc.

ubuntu@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

Hardware: Lenovo R61e, 2.5gb RAM, 80gb HD, 128MB video ram, CDR/CDRW, usb mouse, 802.11b/g Atheros chipset

My question: is performing the installation from the Live CD the preferred method?

Also, during the installation, when I create the partition for Ubuntu, do I need to specify sizes for /swap, /home, /user and so forth or is that done automatically?

Lastly, can I completely remove Ubuntu by booting to my XP Pro CD, recovery console and run "fixboot" and "fixmbr" (to remove grub) and then, after booting into XP, run Disk Management to remove the Ubuntu partitions and then run Easeus Partition Manger to reclaim and add the space back into the existing XP partition?

Sorry to be so wordy but I would like to know what steps are proper to insure a good installation and (if necessary) a clean and complete removal.

Your suggestions and advice are greatly appreciated.

Thanks in advance

---

### Post by blues2use on 2009-04-25
Sorry, forgot to ask about a couple of things...

Do I need to install updates as soon as I have completed the installation?

Is 30GB drive space sufficient for the installation and for future software installs? I tend to keep my software installs to a minimum, even under XP.

I have a lot to learn but I have been reading everything I can about ubuntu and Linux in general and still remember quite a bit from my old "Redhat" days.

Thanks

---

### Post by Therion on 2009-04-25
> **blues2use said:**
> My question: is performing the installation from the Live CD the preferred method?
Yes.

> **blues2use said:**
> Also, during the installation, when I create the partition for Ubuntu, do I need to specify sizes for /swap, /home, /user and so forth or is that done automatically?
You can manually partition if you want but you don't have to.  
The default option will install a "dual-boot" setup if the installer detects the presence of another OS on the install drive.

> **blues2use said:**
> Lastly, can I completely remove Ubuntu by booting to my XP Pro CD, recovery console and run "fixboot" and "fixmbr" (to remove grub) and then, after booting into XP, run Disk Management to remove the Ubuntu partitions and then run Easeus Partition Manger to reclaim and add the space back into the existing XP partition?
That sounds about right.  I can't promise you it will work (it's an imperfect world we live in) but that sounds like a good plan.  
You'll be doing backups as well, of course.

> **blues2use said:**
> Do I need to install updates as soon as I have completed the installation?
Yes.

> **blues2use said:**
> Is 30GB drive space sufficient for the installation and for future software installs?
Yes, generally speaking.  I mean sure, it's possible to exceed that if you try, but for the "average" user I would think 30GB would be fine.

---

### Post by agnitio on 2009-04-25
Never mind [Therion]("http://ubuntuforums.org/member.php?u=388980") said it better

---

### Post by blues2use on 2009-04-25
Therion,

Thanks for the quick reply...I'll be installing later today...

Looking forward to using Ubuntu for as much as I can...I'll be installing Audacity for sure as I edit tracks for my wife's dance classes...as for burning CD's, I'm still looking for something close to Nero...

Thanks again

---

### Post by aysiu on 2009-04-25
Actually, in a situation like yours, I think installing with Wubi would be the preferred method.

It sets up a dual-boot without repartitioning, and if you decide you don't like Ubuntu, you can remove it as you would any Windows program (Start > Control Panel > Add or Remove Programs > Ubuntu). No need to bother with *fixmbr* and all that.

---

### Post by blues2use on 2009-04-25
> **aysiu said:**
> Actually, in a situation like yours, I think installing with Wubi would be the preferred method.

It sets up a dual-boot without repartitioning, and if you decide you don't like Ubuntu, you can remove it as you would any Windows program (Start > Control Panel > Add or Remove Programs > Ubuntu). No need to bother with *fixmbr* and all that.

Thanks for the suggestion...I did try 8.10 with WUBI and it was okay but I'd rather just do a dual boot system. Not really keen on running WUBI or VurtualBox...

---

### Post by aysiu on 2009-04-25
> **blues2use said:**
> Thanks for the suggestion...I did try 8.10 with WUBI and it was okay but I'd rather just do a dual boot system. Not really keen on running WUBI or VurtualBox...
You're obviously entitled to choose what you want. I just want you to make an informed choice.

What advantages are you hoping to get out of a traditional dual-boot, as opposed to a Wubi one?

---

### Post by blues2use on 2009-04-25
I'd rather not run it as an installed program within XP. 

I'd rather install it so as to be able to use my laptop's hardware in the most efficient manner and to keep it separate from XP. I would likely browse my XP files and folders for different things, but I think having the OS'es reside on totally different partitions would be best for me.

Thanks for the suggestion, though...I appreciate it...

At the moment I'm running the Kubuntu Live CD...I think I'm going to be a Gnome guy...it took forever to get my wireless connection up and running...took about 20 seconds in Gnome...Konqueror is not my cup of tea either...I'm still evaluating the overall operation but it looks like Gnome will likely be my choice...

---

