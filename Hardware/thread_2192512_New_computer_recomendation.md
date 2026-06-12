---
title: "New computer recomendation"
date: 2013-12-08
forum: Hardware
---

### Post by johnu1960 on 2013-12-08
Hello all.

I will be upgrading to a new desktop computer in 2014 and was looking for recommendations for the best Ubuntu computer hardware for someone who is starting from scratch.  My primary use of the computer will be for database management and statistics/data mining.  My first thoughts are to get a computer with 8 or 16GB memory Intel I7 processor and an SSD boot drive.  (I am surprised by how few new computers feature SSD boot drives.  What am I missing?)   I currently have a 3TB Seagate USB 3.0 drive that I plan to plug in for data storage.  My budget is in the $1000-1500 range plus maybe $500 for a good graphics monitor.   

I want to use the R statistical package.  As a fairly inexperienced Ubuntu Linux user,  I know how to download and install the R package through the Ubuntu software center, but this is not the _most current _version of R available for Ubuntu.  How do I install the latest version of R as opposed to the one installed by Ubuntu and what is the best Ubuntu version to use?       

In addition to using R I will be using the SAS system under Windows with a dual boot configuration on this same machine.  Some day I hope to completely get away from Windows but this is not possible currently.     

I looked at the certified hardware section of the Ubuntu site and some of the content seemed to be older models.  Is it safe to purchase a newer model in the same product line even if it is not in the certified list?  (This reminds me of Consumer Reports whose reviews always seem to be one model number behind what is currently available.)

Any guidance that people can provide would be greatly appreciated.  Happy Holidays to all!

---

### Post by oldfred on 2013-12-08
Do not know about R, but you should ask that as a separate thread.

Since willing to install your own hard drive have you thought about building your own system? 
You do not really save any money but have better components and know & understand system better. Also bit more work as you do want to research all the components.

If not doing much gaming, the built in video with the new Haswell processors is very good. But a high end nVidia card with the proprietary drivers outperforms Intel or the open source drivers.
       Ubuntu 13.04 Desktop Comparison: 6 Desktops, 5 Driver/GPU Combinations
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1)
        Open Source only drivers - 16-Way Graphics Card Comparison On Open-Source Linux
[http://www.phoronix.com/scan.php?page=article&item=haswell_linuxgpu_16way&num=1](http://www.phoronix.com/scan.php?page=article&item=haswell_linuxgpu_16way&num=1)

Even if not doing a build, I might look at some of the sites to see the comparisons of components. And then see if a vendor will give you options to come close to what seems good at your price point.
Lots of performance tests of Linux systems
[http://openbenchmarking.org/](http://openbenchmarking.org/)
These are mostly gaming and then use very high end video which makes each build more expensive. But the reviews are informative. Not really Linux but most parts work with Linux.
[http://www.tomshardware.com/reviews/bestconfigs-forum-builds,3692.html](http://www.tomshardware.com/reviews/bestconfigs-forum-builds,3692.html)
      
 [URL="http://lifehacker.com/5840963/the-best-pcs-you-can-build-for-600-and-1200"]http://lifehacker.com/5840963/the-best-pcs-you-can-build-for-600-and-1200
[http://pcpartpicker.com/](http://pcpartpicker.com/)
[/URL]
Now older thread, so parts not current, but shows what you need to do for a build.
[http://ubuntuforums.org/showthread.php?t=1179877](http://ubuntuforums.org/showthread.php?t=1179877)

---

### Post by mörgæs on 2013-12-08
Regarding SAS: It runs well on Buntu, but the setup takes some time. Here are some old but still valid threads:

[http://ubuntuforums.org/showthread.php?t=641448&page=8](http://ubuntuforums.org/showthread.php?t=641448&page=8)
[http://ubuntuforums.org/showthread.php?t=1303357](http://ubuntuforums.org/showthread.php?t=1303357)

---

### Post by drmrgd on 2013-12-08
With regard to installing R, I used to do it the manual way, following the instructions at the CRAN website here:

[http://cran.r-project.org/bin/linux/ubuntu/README](http://cran.r-project.org/bin/linux/ubuntu/README)

However, there's always this business of manually fixing the PGP Key for this repository, and since then I've learned that the repository from which this Key comes is a better way to get the latest versions of R:

[https://launchpad.net/~marutter/+archive/rrutter?field.series_filter=precise](https://launchpad.net/~marutter/+archive/rrutter?field.series_filter=precise)

I've not yet tried it as I have a working install of R.  But the next machine I install R on, will be configured using this PPA.  In short, though, it's as simple as just adding the repository to your list, updating the package cache, and installing r-base.

Once you get to that point, post back in a separate thread and we'll get you fixed up.

---

### Post by mkmanifesto on 2013-12-08
If you don't plan on building your own computer you should check out [http://www.system76.com](http://www.system76.com). If you take the $699 desktop model and add a 4th Gen i7 with 240 SSD, 2tb physical hdd, as well 8 gigs memory your still under the $1500 price tag. I would honestly recommend them over any other company if you don't plan on building your own mainly because they don't offer Microsoft Windows on their systems and the systems they make are really nice.

---

### Post by johnu1960 on 2013-12-10
Thanks for all the informative posts and the many links.  I will probably forgo building my own computer due to time constraints.  I will ask the R question on another thread if I am still having trouble after trying drmrgd's suggestions.  On the hardware end it seems like adding higher end gaming video is what really drives up the price, so I can save by just having a decent modern basic video system.  I am in the process of checking out mkmanifesto's and oldfred's links.  I will almost certainly stick with runnning SAS in Windows since this has been my bread and butter for the last 20+years.

---

### Post by mkmanifesto on 2013-12-11
Good luck! Let us know how it turns out.

---

### Post by johnu1960 on 2014-01-20
Just purchased a Dell XPS 8700 with i7 and 8GB RAM.  It has an NVIDIA GT635 video card with 1GB memory.  I also bought the Dell U2713HM 27" monitor (for my old eyes).  Do I need to go to the NVIDIA site to get the video driver or would Ubuntu installer recognize the card and install the driver? 

I was able to figure out how to update the R package and the RStudio GUI by going to the R Project website and also to Jason French's site here: [http://gradstudents.wcas.northwestern.edu/~jaf502/blog/2013/03/11/installing-r-in-linux/](http://gradstudents.wcas.northwestern.edu/~jaf502/blog/2013/03/11/installing-r-in-linux/)

I know there are issues with Linux and UEFI on the new computers.  I have been reading up on that.

---

### Post by oldfred on 2014-01-21
With nVidia you will need nomodeset to boot, unless you have dual video and are really booting with the Intel video chip.

Best to use the nVidia drivers from the repository. You will have to boot with nomodeset parameter in grub menu until you install the driver. If you install directly from nVidia, you have to reconfigure it on every kernel update, where the versions from Ubuntu will auto reconfigure to work with a new kernel.

Lots of info on UEFI in links in my signature. First several are vital.

Is this the new Haswell chip, or 4th gen? That may require some UEFI/BIOS settings also.

---

### Post by johnu1960 on 2014-01-25
[SIZE=2]Thanks for the info Fred.  It is the 4th gen i7 4770 chip. I have disabled Secure Boot and also "Fast Startup".  Windows 8.1 still works fine.  I guess the startup takes a bit longer now though.  
I will keep your advice in mind with the nVidia card.  

I am planning to purchase a small SSD and install Ubuntu on to that disk.  Then I can just change the boot priority in the bios when I want to switch between Win and Ubuntu.  Is this a feasible and reasonable way to do it?  Surely a dual boot system would be preferable, but I hope to be in Ubuntu a lot more than Windows.  At some point down the line I can completely purge windows from the computer and use the drive for storage.    [/SIZE]

---

### Post by Yellow Pasque on 2014-01-26
No, do not install nvidia drivers directly from their website. Use the nvidia-319 package in the repo.

---

### Post by C.S.Cameron on 2014-01-26
> **johnu1960 said:**
> [SIZE=2]I am planning to purchase a small SSD and install Ubuntu on to that disk.  Then I can just change the boot priority in the bios when I want to switch between Win and Ubuntu.  Is this a feasible and reasonable way to do it?   [/SIZE]

When in Ubuntu do a "sudo update-grub", then you will have the option to boot Windows from grub and not need to go to BIOS.

---

### Post by oldfred on 2014-01-26
Dell's seem to be common across models. Not sure about desktops vs. laptops.

 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

Note the Dell techcenter link as it also discusses some Haswell issues that seem common to all Intel based systems.

---

### Post by johnu1960 on 2014-02-09
Here's an update.  

I have switched to Debian Wheezy on the new computer.  One reason for this is that I corrupted the Ubuntu install (it's a long story.  I basically went to another website and followed configuration directions that were either wrong or outdated.) and when I attempted to re install, the Ubuntu program would not allow me to install GRUB for some unknown reason.  I guess the SSD drive still had remnants of the old system on it.  At any rate I am happy with the current setup and appreciate very much everyone's attempts to help.  

The Debian install program allowed me to completely reformat the drive and install GRUB with no problem.  I am using the GNOME classic desktop environment and it is amazingly fast and stable so far.  I did have trouble installing the NVIDIA video driver but I was able to get help from the folks at the Debian forums.  

I continue to run Ubuntu on my older COMPAQ and it's been running great for a year.

---

