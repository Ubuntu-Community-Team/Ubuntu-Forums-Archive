---
title: "Disk Activity Slooows Down Computer"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by kommissar on 2005-05-09
Hello.  I currently have Ubuntu 5.04 installed on my computer.  I have SATA and am using the Intel ICH5R controller on my motherboard to connect the drives, but not using the "hardware" (or emulated hardware) RAID supported by the chip.  Instead, I have the drives setup as software raid with ~180 Gigs on one drive and 200Gigs on the other.  The extra space on the first drive is 10Gigs of unpartitoned space, a boot partition and some swap space.

My problem is that whenever there is heavy disk activity, such as copying large files or creating an image to write with my cd burner, my computer slows down a lot.  This was never a problem under Windows, and should not be a problem for any OS with the proper configuration.  The computer is very up to date, running a Pentium 4 at 3.0 Ghz.  When this activity occurs, opening even Gnome Terminal window will take a long time.  The top utility reports that there is only ~36% CPU usage by all programs.

So what is slowing down my computer?  Do you think that the software RAID in Linux is the cause of the slowdowns?  The only other thing I can think of is that perhaps the Intel ICH5R chip is not well supported under Linux.

Thanks.

---

### Post by movery on 2005-05-10
I get a similar problem on my laptop when copying files to my USB harddrive.  If I try and rsync some files for backup then Ubuntu literally hangs for one second out of ~7 whilst the file is copying and the mouse behaviour becomes erratic.  The CPU freq also scales up to 100%.

If I nice -n 5 the rsync process then the CPU usage does stay down but it doesn't cure the hangs.  I shouldn't have to even do this though, it should just work.. :)

Anyone got any thoughts on why this happens?

---

### Post by Magnes on 2007-01-26
Well, I have the problem now with my new hard drive. Anyone found the answer to that problem? My system even crashes sometimes when I for example copy one file with krusader and one with nautilus. It's only happening on my new hard drive (320GB Seagate, I tested default and optimised hdparm settings - both the same).

---

### Post by movery on 2007-01-27
Found the answer to my problem...  Despite the manufacturer claiming the USB ports were powered they clearly weren't powered enough for my external hard drive.  A powered USB hub did the trick and now it works perfectly.

---

### Post by RandomJoe on 2007-01-27
Can't say what might be causing your slowdown, but I _can_ say that software RAID isn't the problem.  I've been using it for a long time, in both RAID5 and RAID1 configurations, and can't even tell it's operating.  

My server is a 2.4GHz P4 that has cpufreq running, it idles at 600MHz when serving files via NFS, the only time it ever comes off that is when I use scp to move files, and that's due to the encryption overhead.  I have also used sofware RAID on older/slower machines with no issue.

---

