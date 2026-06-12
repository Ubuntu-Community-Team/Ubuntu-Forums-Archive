---
title: "Rescuing hard disk on Dell Laptop with Testdisk"
date: 2010-03-30
forum: Hardware
---

### Post by bejo on 2010-03-30
Hello! This is my first post ever in this site. 

I have problems with a Dell D600, with a solitary OS - just XP! I am migrating to a new desktop right now on which I run Kubuntu, and that is why I try to repair my laptop with an Ubuntu rescue_remix bootable CD. 

I have come quite far in analysing the problem but I get stuck when using the Testdisk utility which is on that CD. I am trying to extract an image of my faulty C: partition (NTFS) on /dev/sda to an external USB harddisk, but when I reach the step where I am to choose the destination disk, which is correctly identified by the Testdisk program in the beginning, as /dev/sdb (although it is external), nothing happens. When I try to make that choice I first arrow down in the /dev directory and then I put the higlight bar on sdb and press enter, but absolutely nothing happens, and I cannot get out of that state without pressing ctrl-C and start over. 

I am very new to Linux and try to learn, but many texts are to brief to make me really understand the details. What I have understood is that mounting of a volume is important, but on the other hand - and this is explicit in the texts - the faulty disk should not be mounted in the rescue CD installation, but it says nothing about any external disk. My impression is that Testdisk should manage the situation as it correctly identifies the disk in the beginning. This is however the only thing I can think of myself as a possible cause for my problem. Or there is something else completely out of my world! Please help if you think you can identify my problem, and see what needs be done. 

If I cannot make it, what would be the best utility (or standard command) to rescue singular files on the NTFS disk to an external USB-disk? They seem to be there! 

TIA

---

### Post by 2hot6ft2 on 2010-03-30
In the Tutorials & Tips section
You'll just have to adjust it for your version of ubuntu

[How to: Recover data with testdisk!]("http://ubuntuforums.org/showthread.php?t=387922")

---

### Post by bejo on 2010-03-31
Thanks for the tip! 

Went there but found not the details I need. The howto was informative but covered not my special problem. 
Regarding Ubunto versions I have presumed this is already attended to, as I downloaded a full bootable Ubuntu CD for rescuing, ubuntu_rescue_remix-9.04, as an ISO image file and burnt it. The tools are thus already included - I have not put it together myself. At least I find nothing about any config process for that CD.
So I still get nowhere...?

---

