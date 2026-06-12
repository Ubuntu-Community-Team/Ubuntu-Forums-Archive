---
title: "corrupted XP and Partitioning woes"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by RustyOrbit on 2009-09-01
Hello, First of all, I will describe my computer knowledge level, I know my way around windows, and can bluff DOS, but am not an enthusiast (though i did assemble my current PC). I have had a passing interest in Linux, but never really put the time into learning or installing it.

to start at the begining, I bought an HP Pavillion a few years ago with a preinstalled win XP Media center edition, I then realized that Integrated graphics sucked, and needed to upgrade, so i saved the processor (P4 3.06 GHz)  Ram (1GB ddr2 400) and HD (200GB seagate)  and replaced the MOBO and PSU and added a GFX card (nvidia 7600gt) 
Windows then installed Genuine advantage and told me that i had pirated windows. I called Microsoft tech support and they were able to bypass that, but i dont think that the same routine would work again. 

anyway fast forward a year: I reboot windows and i get NTLDR is missing error, only fix involves boot CD that I don't have. anyway I say screw it, I've always wanted to learn Linux, now's as good a time as any, and get Ubuntu 9.04. I boot it from CD and am attempting to install to my 200GB HD

Problem is that I have an 8GB Fat32 "Recovery" Partition (useless) and a 178.3 GB NTFS partition with all my files on it.  I dont have anything that I absolutely can't lose on my HD, but i would much prefer not to wipe the thing. 

so i did some googleing, booted up GParted, freed up just shy of 50 Gigs, and attempted to shrink the 178 GB NTFS partition by about 40 GBs, then create an ext3 partition for Ubuntu and a small swap Partition. But GParted returns an error when I tried to execute the resizing. some more googleing suggests that defraging my NTFS partition may help, but i cand find a utility to do it from within linux and I cant access windows. 

I guess that the point of this novel is that I don't know what to do next. 


also, here is logfile of GParted
GParted 0.4.3
 Libparted 1.8.8
    ```
Move /dev/sda2 to the right and shrink it from 178.30 GiB to 139.78 GiB  00:01:28    ( ERROR )             calibrate /dev/sda2  00:00:00    ( SUCCESS )             path: /dev/sda2
start: 16798320
end: 390715919
size: 373917600 (178.30 GiB)          calculate new size and position of /dev/sda2  00:00:00    ( SUCCESS )             requested start: 16803990
requested end: 309942044
requested size: 293138055 (139.78 GiB)       new start: 16803990
new end: 309942044
new size: 293138055 (139.78 GiB)          check file system on /dev/sda2 for errors and (if possible) fix them  00:00:11    ( SUCCESS )             ntfsresize -P -i -f -v /dev/sda2             ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 191445807616 bytes (191446 MB)
Current device size: 191445811200 bytes (191446 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 140432 MB (73.4%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :    183838 MB             0
Multi-Record       :    190769 MB         77382
$MFTMirr           :         1 MB             1
Compressed         :    191405 MB         22159
Sparse             :    191346 MB        233777
Ordinary           :    191446 MB        144682
You might resize at 140431781888 bytes or 140432 MB (freeing 51014 MB).
Please make a test run using both the -n and -s options before real resizing!
            shrink file system  00:01:05    ( ERROR )             run simulation  00:01:05    ( ERROR )             ntfsresize -P --force /dev/sda2 -s 150086684159 --no-action             ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 191445807616 bytes (191446 MB)
Current device size: 191445811200 bytes (191446 MB)
New volume size    : 150086676992 bytes (150087 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 140432 MB (73.4%)
Collecting resizing constraints ...
Needed relocations : 6896840 (28250 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1048 > 1024), not yet supported!
Please try to free less space.
               check file system on /dev/sda2 for errors and (if possible) fix them  00:00:11    ( SUCCESS )             ntfsresize -P -i -f -v /dev/sda2             ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 191445807616 bytes (191446 MB)
Current device size: 191445811200 bytes (191446 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 140432 MB (73.4%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :    183838 MB             0
Multi-Record       :    190769 MB         77382
$MFTMirr           :         1 MB             1
Compressed         :    191405 MB         22159
Sparse             :    191346 MB        233777
Ordinary           :    191446 MB        144682
You might resize at 140431781888 bytes or 140432 MB (freeing 51014 MB).
Please make a test run using both the -n and -s options before real resizing!
            grow file system to fill the partition  00:00:01    ( SUCCESS )             run simulation  00:00:01    ( SUCCESS )             ntfsresize -P --force /dev/sda2 --no-action             ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 191445807616 bytes (191446 MB)
Current device size: 191445811200 bytes (191446 MB)
New volume size    : 191445807616 bytes (191446 MB)
Nothing to do: NTFS volume size is already OK.
            real resize  00:00:00    ( SUCCESS )             ntfsresize -P --force /dev/sda2             ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 191445807616 bytes (191446 MB)
Current device size: 191445811200 bytes (191446 MB)
New volume size    : 191445807616 bytes (191446 MB)
Nothing to do: NTFS volume size is already OK.
               ========================================

```

---

### Post by matsuzine on 2009-09-01
I'm not sure, but this may have to do with the windows pagefile.  

See this:

[http://www.linuxquestions.org/questions/linux-software-2/gparted-ntfs-resizing-has-anyone-had-any-problems-with-it-459829/](http://www.linuxquestions.org/questions/linux-software-2/gparted-ntfs-resizing-has-anyone-had-any-problems-with-it-459829/)

[http://ubuntuforums.org/showthread.php?t=1224942](http://ubuntuforums.org/showthread.php?t=1224942)

Personally, I think I remember having some ntfs woes on a partition that had been used to hibernate as well.  

Can you resize to a less optimal size partition?  Maybe you could install ubuntu, boot to windows, clean it up, then go back and resize with gparted.  Or, boot manually from grub?

---

### Post by RustyOrbit on 2009-09-01
problem is that I can't boot windows at all, so I cant clean up the file system

---

### Post by oboedad55 on 2009-09-01
> **RustyOrbit said:**
> problem is that I can't boot windows at all, so I cant clean up the file system

Can you post a printscreen of your drive under Gparted? That would help to see what you're doing.

---

### Post by matsuzine on 2009-09-01
I guess what I was thinking is that if your boot problem is with the MBR, then you could install the GRUB bootloader in the MBR (which is the default when you install Ubuntu) and it will set up a dual-boot.  In theory, you could then use GRUB to boot into windows, assuming the problem doesn't lie elsewhere ( [other possible NTLDR errors]("http://www.computerhope.com/issues/ch000465.htm"))

As an alternative, I think it's possible to use a linux rescue live disk and use the command line to boot from grub, but I haven't tried it that way. It would be less invasive if you could clean up that windows partition.

For awhile, I had a windows machine booting from GRUB, with only a little ext3 partition with the boot files (before I got around to removing windows entirely...)

Finally, if you don't care about the windows installation, you could create a linux partition in whatever free space you can get, access the windows partition (hopefully!) from linux install / live cd and copy the data onto the linux partition.  In one case with an ntfs partition, I was able to access it from linux, but could not write to it.  That was fine to save my data!

Can't vouch for this, but it might be an option:

[http://www.linux-ntfs.org/doku.php?id=ntfsdefrag](http://www.linux-ntfs.org/doku.php?id=ntfsdefrag)

---

### Post by egirl723 on 2009-09-01
Hi,

i'm a newbie...my 1st post....I'm going through the same thing except I fixed the NTLDR missing with this:
[SIZE=5][http://ntldrismissing.com/](http://ntldrismissing.com/)[/SIZE]
but did not follow through with legitimizing the "recovery" and am presently dealing with some error message about missing the DLL kernels so I too cannot boot from XP and am using Jaunty Jack live for everything.  That link, however, will fix your issue (if it's just that the hidden boot files have been deleted/corrupted), just follow through with whatever it tells you to do after the fix.

I do still have the partitioning prob, but I'm going to try the links listed above for help and then come back here if i can't hack it.

---

### Post by Mark Phelps on 2009-09-01
You got the MS Windows validation message because your original copy of XP was tied to the BIOS on the motherboard (being an OEM version).  When you replaced the motherboard (I'm presuming NOT with an HP OEM motherboard), that BIOS code was no longer present so XP discovered that and flagged itself as invalid.  It was good that MS was willing to work with you on this.

Regarding recovering the files from an Ubuntu LiveCD, you can most certainly do that -- provided that the partition can be mounted.  If you can see it in Places and open the folder for it, then you should be able to copy all the files off that partition to somewhere else.  If the filesystem got corrupted, it won't mount -- and that poses different problems.

---

### Post by ronparent on 2009-09-01
The good news is that MS is not currently supporting xp and you can probably reinstall without having to clear with MS. The bad news is that MS is not currently supporting xp, so you are on your own.

---

### Post by RustyOrbit on 2009-09-02
Hey Guys, I solved it by formatting the 8GB recovery sector to an ext3 (thinking just bite the size bullet and install there, but when I ran the installer it gave be a dual-boot option that wasn't available before, and allowed me to resize the larger partition and I installed ubuntu with no issues, still can't boot windows, but I can and will cannibalise the files from there when I build a Win7/ubuntu machine later in the fall. I will just run ubuntu till then. and just try to figure WINE out. 

I have no idea what formatting the recovery partition had to do with resizing a diferent one, but it worked and i'm not going to complain. 

thanks for the help,
            Rusty Orbit:KS

---

### Post by oboedad55 on 2009-09-02
> **RustyOrbit said:**
> Hey Guys, I solved it by formatting the 8GB recovery sector to an ext3 (thinking just bite the size bullet and install there, but when I ran the installer it gave be a dual-boot option that wasn't available before, and allowed me to resize the larger partition and I installed ubuntu with no issues, still can't boot windows, but I can and will cannibalise the files from there when I build a Win7/ubuntu machine later in the fall. I will just run ubuntu till then. and just try to figure WINE out. 

I have no idea what formatting the recovery partition had to do with resizing a diferent one, but it worked and i'm not going to complain. 

thanks for the help,
            Rusty Orbit:KS

Woohoo! Way to go man.

---

