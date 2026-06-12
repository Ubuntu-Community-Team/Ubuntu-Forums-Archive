---
title: "Dual disk external docking station, should this work?"
date: 2021-02-23
forum: Hardware
---

### Post by watson524 on 2021-02-23
Hi all,

I have 20.04 running and am trying to organize years of files and such into a better system for storage/backup. I have a thermaltake external drive station with 2 slots where you can put internal drives into it (I also have a WD passport I'll be using tho not entirely sure where that'll fit in yet as I'm thinking of ditching the 2 internal/external drives altogether and save on a power cord for the drive station but in the meantime....).

One of the drives is a 2.0TB and the other is a 1.5TB. Both Western Digital. It seems like the system got confused in that when the 1.5TB is in, it's showing it as a 2.0 but seems to have the right model number with it. I guess my first question is SHOULD the OS see both slots separately in the thermaltake drive station? It doesn't seem to matter that they're in the same slot they were when they were set up, if I take one out and then the other, they show differently in the disks utility. Also, I can't seem to get the system to show them both at the same time anymore.

I'm wondering if something just got goofed up in fdsk (I did it all through the gui disks utility) but before I start looking into how to wipe things out and start over (I can completely wipe and format both drives if need be as I have all my data elsewhere), SHOULD this work as expected?

thanks!

---

### Post by TheFu on 2021-02-23
I have a BlacX duel dock with eSATA and USB2 connections [https://www.amazon.com/Thermaltake-External-Enclosure-Docking-ST0014U-D/dp/B002MUYOLW/](https://www.amazon.com/Thermaltake-External-Enclosure-Docking-ST0014U-D/dp/B002MUYOLW/) .  The eSATA requires an eSATA-pm card in the connected system to work with more than 1 HDD.  USB2 is slow, so using that for backups would be painful.  i've had 4TB HDDs in this dock and it saw all the space.

> SHOULD the OS see both slots separately in the thermaltake drive station?
Yes, assuming you are using an eSATA-pm eSATA connection.  IF you are not, then no. Only one disk will be seen. With USB connections, both disks are seen.
> It doesn't seem to matter that they're in the same slot they were when they were set up, if I take one out and then the other, they show differently in the disks utility. Also, I can't seem to get the system to show them both at the same time anymore.
The placement of the HDDs doesn't matter, unless the connected device controller cares. It isn't something the BlackX dock controls.

I don't trust most GUIs when it comes to disk management, except **gparted**. Use that.  **sudo -H gparted** is the command you need to use. DO NOT FORGET THE -H!!!

Inside gparted, set different LABELS for the disks and each partition. Humans can deal with LABELs easier. Don't use any spaces - or mixed case.  Setup both with GPT partition tables.

As for needing more power connectors ... amazon sells thick 1-plug to 4-plug quad-power connector 3-pak for $20. These are perfect for low-power devices like HDDs, small switches, perhaps a KVM switch or powered USB hub, but don't use them for devices with high-power draw like desktops or servers or laser printers.  Obviously, the 1-plug would go into a reputable UPS or power strip with surge protection.

I should say that I've had 3 other USB3 docks as well, 2 of those died after just over a year of seldom use. The BlacX duel is what I've used the most and had the longest. It is part of my sneaker-net video recorder xfer workflow and gets used a few times every week.

---

### Post by watson524 on 2021-02-23
> **TheFu said:**
> I have a BlacX duel dock with eSATA and USB2 connections [https://www.amazon.com/Thermaltake-External-Enclosure-Docking-ST0014U-D/dp/B002MUYOLW/](https://www.amazon.com/Thermaltake-External-Enclosure-Docking-ST0014U-D/dp/B002MUYOLW/) .  The eSATA requires an eSATA-pm card in the connected system to work with more than 1 HDD.  USB2 is slow, so using that for backups would be painful.  i've had 4TB HDDs in this dock and it saw all the space.


Yes, assuming you are using an eSATA-pm eSATA connection.  IF you are not, then no. Only one disk will be seen. With USB connections, both disks are seen.

The placement of the HDDs doesn't matter, unless the connected device controller cares. It isn't something the BlackX dock controls.

I don't trust most GUIs when it comes to disk management, except **gparted**. Use that.  **sudo -H gparted** is the command you need to use. DO NOT FORGET THE -H!!!

Inside gparted, set different LABELS for the disks and each partition. Humans can deal with LABELs easier. Don't use any spaces - or mixed case.  Setup both with GPT partition tables.

As for needing more power connectors ... amazon sells thick 1-plug to 4-plug quad-power connector 3-pak for $20. These are perfect for low-power devices like HDDs, small switches, perhaps a KVM switch or powered USB hub, but don't use them for devices with high-power draw like desktops or servers or laser printers.  Obviously, the 1-plug would go into a reputable UPS or power strip with surge protection.

I should say that I've had 3 other USB3 docks as well, 2 of those died after just over a year of seldom use. The BlacX duel is what I've used the most and had the longest. It is part of my sneaker-net video recorder xfer workflow and gets used a few times every week.

Mine is a blackX as well and I'm using a USB connector. So it sounds like I have something fudged up somewhere in that it can't keep track of what's where. I have the labels of 20tbext and 15tbext but it still seems goofy. I mean I guess the good news is it SHOULD work.

---

### Post by TheFu on 2021-02-23
> **watson524 said:**
> Mine is a blackX as well and I'm using a USB connector. So it sounds like I have something fudged up somewhere in that it can't keep track of what's where. I have the labels of 20tbext and 15tbext but it still seems goofy. I mean I guess the good news is it SHOULD work.

How do you mount it?  Use the label in the fstab or via autofs?
Any other method would likely have terrible performance.

---

### Post by watson524 on 2021-02-23
> **TheFu said:**
> How do you mount it?  Use the label in the fstab or via autofs?
Any other method would likely have terrible performance.

Kind of new at all this so I'm not sure I can answer that. The "disks" GUI sort of took care of all that for me. Tho I was just reading through this 
[https://www.answertopia.com/ubuntu/adding-a-new-disk-drive-to-an-ubuntu-system/](https://www.answertopia.com/ubuntu/adding-a-new-disk-drive-to-an-ubuntu-system/)

for the proper way to do it. I just checked /etc/fstab and it doesn't seem to have them in there so.... What's weird is I now noticed I see the 15tbext drive, tho it has a 2tbext subfolder (nothing in it) and when I go to the 2tbext it says there's an issue with one file and it needs cleaning??

Definitely seems like something is crossed up good.

---

### Post by TheFu on 2021-02-23
Be careful where you find answers when you are new.  While 90% of all Linux systems are similar, there are differences between releases and to get the best help, really should stay with places that have "ubuntu" in the domainname, not just the title.

Always start with help.ubuntu.com and maybe go to wiki.ubuntu.com. Those are the most official places.  After that, ubuntuforums, askubuntu, and almost any domainname website with "Ubuntu" in the name, as I've said before.  There are a few long time posters here (check their bean counts) that happen to have blogs with some answers too.  Why I'm I suggesting being careful?  Because it is nearly impossible for you to tell whether the other person knows 0.0001% more than you or 1000x more when you are really new.  There are a few exceptions, of course.  Almost always if someone posts a link here any they have 500+ beans, you can trust it for advice.

That link suggests using XFS. There are a few reasons to use xfs, but on Ubuntu, there are many reasons NOT to use XFS, especially for relatively small disks like you have. Stick with ext4, unless there is a compelling reason to use something else.  There are things that ext4 can do that XFS cannot do. Best not to become trapped.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) explains setting up the fstab to mount stuff.  Always remember, we mount file systems that are created on partitions. We do not mount drives.  BTW, Windows doesn't mount drives either, but they've been calling a partition a "drive" for 30+ yrs, incorrectly.

---

### Post by watson524 on 2021-02-23
Point well taken! I shouldn't say I'm a total newbie, I have a degree in Comp Sci (mainly unused but it helped with processes, critical thinking blah blah) and in college had to work on Sun Sparc stations and have dabbled here and there over the years. Because I always think I need to maybe use drives with my windows machines, I tend to use FAT systems, I mean, do I need to? Well, I do map them from 2 other windows machines so yeah..... but I won't be using the link for their XFS and all (I've never even heard of it). 

Right now I'm starting from scratch on the 1.5TB drive to see if I can get that to behave properly. Then I'll have to figure out what on the 2.0TB drive it thinks needs to be "cleaned". I can get to it from my windows machine and read/write files, but it won't show the files on the linux machine, which seems bizarre to me.

---

### Post by watson524 on 2021-02-23
It looks like it's sorted out. I started from scratch with the 1.5 drive (and learned windows can access ext4 drives!) and then on the 2TB drive, I ended up stopping samba services, unmounting, running e2fsck to fix whatever it didn't like about a file that wasn't even there anymore, and brought it back up and all is fine. I can access from my phone and from a windows laptop. 

One thing I did notice is that I still can't see the 2.0TB drive in the disks GUI. I see 3 things on the left, my OS drive 160GB, the CD drive in the machine and the 1.5TB drive, BUT I noticed at the top of disks, it actually has /dev/sdb /dec/sdc so it's like it's showing both at once (it's not) but still very odd. Not going to worry about it tho, I'm just glad to have all my drives doing what they're supposed to.

---

### Post by TheFu on 2021-02-24
Is Windows set to disable fast startup and hibernation?  Those can leave a file system open and Linux will refuse to access open file systems.

**sdb** is the whole disk.
sd**b1** is the first partition created on the disk. That is where you'd format a file system. Of course, you can have over 100 partitions, if you like. Most of them time, I use 1-4 partitions on any disk.  Some systems like to go crazy with partitions - ChromeOS (which is used by chromebooks) used 11 partitions, I think. Chromebooks have 2 copies of the OS, so about half of the partitions are for the "A" copy and the other half are for the "B" copy. OS updates are pushed (and cannot be stopped) into the currently unused version of the OS.  So if an OS update fails, there's always a fallback OS and the update can be attempted later.

FAT is mostly a bad memory and avoided here.  If Windows needs access to storage I have on Linux, I use the network to transfer files. Moving physical connections around only happens when the network cannot be used for whatever reason, which is extremely seldom.  That's why we have **sftp** and NFS.  Usually there is no need to leave any Windows file system on any storage that isn't always connected to a Windows machine.

I have a SPARC IPX in a closet here, somewhere. Think is has a 1GB HDD. Where I worked, they had hundreds of them stacked to be trashed - with a sign on them - "Please take some home".  I was using an UltraSPARC 1/140 for my workstation at the time, so I didn't really understand how slow an IPX was. Took about 2 weeks to learn that lesson.  I'd always had access to lots of Unix workstations and servers after my mainframe programming job was over.

---

### Post by watson524 on 2021-02-24
That's likely what happened. Since it's my work laptop, it's locked down in what settings I can even see, let alone change but I know things stop when it goes to sleep so..... And until last nite I didn't realize that a network connection and a physical connection meant 2 different needs as far as file systems and since I'd never plug the drive into anything but my linux machine and just access from wherever, it's all ext4 from here on out.

If I ended up getting rid of one of these drives, what is the preferred method for "cleanup"? i.e. let's say sdb as a whole goes away (the 1.5tTB drive). Should I work to take it out of fstab? I'm just wondering if I decommissioned it, then put in say a WD Passport in circulation, would the system try to give that sdb or would it just skip and go to sdd?

---

### Post by TheFu on 2021-02-24
I was always cautious to keep work and personal things separate. Everything connected to the work PC/laptop/phone wasn't mine. It was property of the company. They'd used Bluecoat and MiTM certs to see all the traffic on the network and took periodic screen captures daily from all systems to ensure we weren't doing anything "bad".  A few day traders were caught that way.  People think they aren't being watched when the login banner clearly says the company does.  Also, all phone calls were recorded.  BTW, I worked in the IT architecture team and saw all the different systems which did this.  They were running on everybody's laptop/desktop. No exceptions. It wasn't like I was a customer representative and "the phone calls were being recorded for quality control."  ALL phone calls were recorded. All conference lines, all video chats, all text chats ... all recorded.  GPS tracking on the company provided phone and all those conversations and all data on those devices was recorded too.

I even used a separate mp3 player rather than having headphones and using the audio of the laptop. 
Keep work stuff separate from personal stuff.

sda, b, c, d, e, f, g should never be used in system settings or scripts. Those names are never guaranteed and often change names based on the order that each device is discovered.  Always use either the UUID or LABEL in those.  I don't really understand what you mean by cleanup?

Drives that aren't used by Linux shouldn't be in the fstab.

Be cautious with WD Passport devices. In the past, some were not compatible with Linux for some reason. I never had that issue, but you never know. The only reason I'd buy an external drive w/ enclosure now that I have a few docks is to shuck the drive. For some reason, WD has a habit of putting expensive HDDs inside their cheap USB enclosures and selling them for 30% less.  I ended up with 2 8TB "Red" drives by shucking. The drives had the red label on them still.  
Learn more about shucking: [https://www.reddit.com/r/DataHoarder/comments/9zmbph/tutorial_on_shucking_wd_elements_drives/](https://www.reddit.com/r/DataHoarder/comments/9zmbph/tutorial_on_shucking_wd_elements_drives/)

If the eject from Windows doesn't close the file system properly, then in Windows, just format the drive and eject it.
I really hope someone else will jump in with their greater knowledge on this.

---

