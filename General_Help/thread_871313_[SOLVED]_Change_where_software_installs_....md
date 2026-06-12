---
title: "[SOLVED] Change where software installs ..."
date: 2008-07-26
forum: General Help
---

### Post by OzCDN on 2008-07-26
I've just put Ubuntu on an Acer Aspire one. I am somewhat familiar with linux but have never 'lived' in it.

Anyway, because of the space limitations of the solid state hard drive, I want to get software installing to the secondary storage (8GB HCSD). When I use the package manager to install I don't get any options for where the software installs and I'm not sure if I move the software, if the startup icons will break?

Anyone got a moment to give me some details on how this works?

Thanks,
Dave

---

### Post by jonian_g on 2008-07-26
As far as I know this can't be done with .deb installers(choosing the folder where a software installs). You can do that only with software that come with a .bin installer.
The folder when installing with package manager or .deb files is /usr. When you installed ubuntu you could have choosen your flash card to be mounted on "/usr" and software would go there.

I have an Asus eeepc with 4GB SSD and never needed more space to install software. My setup is this:

4GB SSD mountpoint "/" - System and software
8GB FC  mountpoint "/home" - User data and configuration

I don't use a swap partition because SSD drives have a limited life time and flash cards are slow. With 512MB of ram I don't think you will need a swap partition.

---

### Post by OzCDN on 2008-07-28
Thanks for the info. I haven't done many manual installs except for a couple that had step by step walkthrus.

I took your advice and dumped my 1GB swap partition. I was able to extend the main partition from the Ubuntu Live CD to recover the space.

I am also planning on buying a 1GB sodimm tonight to bring the RAM up to 1.5gb ... so even less chance of needing swap.

Dave

---

### Post by jonian_g on 2008-07-28
512 ram are fine for my eeepc, I never had problems. 1,5 GB even better :)

---

### Post by OzCDN on 2008-07-29
> **jonian_g said:**
> 512 ram are fine for my eeepc, I never had problems. 1,5 GB even better :)

I did the memory upgrade last night. Since the empty sodimm slot is on the bottom of the motherboard and you have to go in through the top, it is not for the feint-hearted. I messed up my keyboard connector as it releases in a way that I had never seen before (a flip-up bar (quite nice actually)). Took me two hours to fix up. The case takes a lot of fiddling to crack it open even after all the screws are out.

Anyway, the bios recognized the new ram without any issues and I am typing this on my 'one' :).

Dave

---

### Post by jonian_g on 2008-07-29
Very nice. I see that everythibg works fine for you.
Don't forget to mak the thread as [SOLVED] ;)

BTW. Do you see any performance change with the additional ram? I'm thinking to put 1GB to my eeepc.

---

### Post by OzCDN on 2008-07-29
> **jonian_g said:**
> Very nice. I see that everythibg works fine for you.
Don't forget to mak the thread as [SOLVED] ;)

BTW. Do you see any performance change with the additional ram? I'm thinking to put 1GB to my eeepc.

It is one of those things where I can't be sure. I didn't do any before / after tests. All I can say for sure is that I am really happy with the performance right now.

---

### Post by derrick81787 on 2008-07-29
> **OzCDN said:**
> I've just put Ubuntu on an Acer Aspire one. I am somewhat familiar with linux but have never 'lived' in it.

Anyway, because of the space limitations of the solid state hard drive, I want to get software installing to the secondary storage (8GB HCSD). When I use the package manager to install I don't get any options for where the software installs and I'm not sure if I move the software, if the startup icons will break?

Anyone got a moment to give me some details on how this works?

Thanks,
Dave

Typical user programs installed from .deb packages are installed in /usr/bin.  Some programs that are special cases or especially important to the operating system may be installed in /bin or /usr/sbin, but /usr/bin is definitely where most programs go.  I don't know a way to change the folder (and I'm not sure if it would be good even if we did), but you could just create a partition on your other drive and use /usr/bin as the mount point.  Technically, I guess you could create one partition per folder and make /usr/bin, /bin, and /usr/sbin all on the other drive.

You wouldn't want to just partition the drive and mount it at /usr/bin, though, because you would lose all your programs (they wouldn't actually be gone, but would be invisible to the operating system).  You'd first have to create a partition and mount in in your home folder (or elsewhere) and copy all the files from /usr/bin to the new drive.  Once you have all the files on the new drive, you could set your /etc/fstab to automatically mount the new partition at /usr/bin at boot time, and optionally delete the files in the old /usr/bin.

If something goes wrong, and you find yourself with an empty /usr/bin folder because the new drive didn't mount correctly (possibly due to a typo in /etc/fstab, or something) your system might not be usable until the files are restored.  They could be restored pretty easily with a LiveCD, though.

I hope this helped.  Let me know what you think.

- Derrick

*****Edit: ** Didn't read all the post and just noticed that the thread is solved.  I still think that this is a pretty fancy solution, though. ;-)

---

