---
title: "Need some guidance to be able to go on my own: BIOS and partitions"
date: 2019-05-14
forum: Hardware
---

### Post by Pedro_Teixeira_Spinola on 2019-05-14
Hi there!,

I don't have much knowledge of os, bios, hardware, etc.. So I got help from a tech support specialist (and some friends by the side), to build and buy and build my new rig. As I also don't have that much time, I hired the tech guy to set up Windows 10 alongside Ubuntu, which he did successfully. But he told me couldn't go further into configs, as he wasn't comfortable with linux beyond install. No problem, I'll deal with it myself from now on. And  did: have just dealt with getting nvidia driver to work on ubuntu. :). But I have some new challenges. I'm not asking for the full answer here, but for some advice or some idiomatics so I can search google and get the responses I need. Any help will be much appreciated! 

My rig: i9-9900K 3.6, motherboard: msi meg z390 ace, 32gb(2 cards) RAM, 2 SSD Nvme(one with 150gb and one with 500gb). I use ubuntu for natural language studies and general programming, and windows for other kinds of work aswell as gaming.
When I go into partitions screen, what I see is:
/dev/nvme0n1
p1 ntfs 29/575MB Win
p2 ext4 8035/9457MB Ubuntu
p3 ext4 2387/94999MB 
free space 15GB
/dev/nvme1n1
p1 ntfs 163/512GB

My current challenges:
 -The tech guy told me there is a difference between what slot you choose to install each one on the motherboard. What was he talking about exactly? Why is it important? Where can I know more about this?
-He also told me that after installing the cards, there was a difference about choosing exactly on what SSD should I install each OS. And that I shouldn't install both OS at same card, or something. He was really confused about it, and I am even more. lol
-As I understand, he configured it this way: Windows root, Ubuntu root and Ubuntu home are at the 150GB SSD, with 15GB freefloating for some reason. The other 500GB SSD card is being used only for windows files. Is this the optimal manner? If not, how could I go about changing it without comitting a lot of hours to it? (I mean: OS operations takes a lot of time when I'm a complete newbie to this point yet). Should I have a swap partition, considering my rig?
-What is the difference between a partition and a drive? What I don't understand is: when I'm inside windows, C: contains both SYSTEM (root?) files, and my files like Downloads, Pictures, etc.. Ain't that strange considering partitions as they are right now?
-Everytime I reboot into windows or ubuntu, the clock is wrong by 3 hours. The guy was not particularly savvy about BIOS configuration at all, and less am I, but I have learned that the clock problem should be a BIOS problem as it affects both OS. How can I correct that? More generally, how should I go about getting the best bios configuration I possibly can for my purposes?
-Even though I have a cooling system that should be good, the computer seems to be hot when I touch it. How can I check if it was properly installed, configured, whatever? I can use cpu-z or something like that to check temperatures, but what should I consider much high? Any tips?


Thanks a lot!

---

### Post by him610 on 2019-05-14
Welcome to the forums, Pedro_Teixeira_Spinola

Don't know your level of computer literacy so I began with basics. Feel free to skip if you already know subjects in links.
Start here, [chrome-extension://oemmndcbldboiebfnladdacbdfmadadm/https://taosnet.com/assets/help/ComputerBasics101.pdf]("chrome-extension://oemmndcbldboiebfnladdacbdfmadadm/https://taosnet.com/assets/help/ComputerBasics101.pdf")
Continue with this, [https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)
Finally, study and become familiar with your User Manual. Can be downloaded here, [https://www.msi.com/Motherboard/support/MEG-Z390-ACE#down-manual](https://www.msi.com/Motherboard/support/MEG-Z390-ACE#down-manual)

More help, [http://linuxcommand.org/tlcl.php]("http://linuxcommand.org/tlcl.php")

Additional questions - feel free to return - one question at a time.

---

### Post by oldfred on 2019-05-14
It looks like your tech guy is not very knowledgeable. It looks like your Windows is BIOS/MBR.
Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012. Not the now 35 yr old BIOS/MBR configuration which a user can use, but really only for backward compatibility on old equipment or large users with many systems who want all same configuration.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Microsoft for years has confused drives & partitions. Think of a drive as a file cabinet and partitions as the drawers in the cabinet. But Microsoft always has called a partition as a "drive".  Linux clearly separates drives from partitions. You have the very new NVMe drives and one is nvmen0 and other is nvmen1 and then partitions will be p1, p2, p3 on each actual drive. 
Windows probably calls your nvmen0p1 as the c: drive and nvmen1p1 as d: drive.  When clearly in Linux seen as first partition p1 on two different drives.

If it was my system, I would reinstall Windows correctly in UEFI boot mode to gpt partitioned drive. But if you have spent hours configuring it, it may not be easy to backup your data & configuration and reinstall. With Windows just about impossible to convert in place. And Windows install is a lot more complicated than installing Ubuntu, even when you have some experience in installing systems.

---

### Post by cruzer001 on 2019-05-14
> -The tech guy told me there is a difference between what slot you choose to install each one on the motherboard.
Probably talking about the PCIe slots.  They can have different speeds from 1x to 16x, may even go higher these days, I don't know.
> 
-He also told me that after installing the cards, there was a difference about choosing exactly on what SSD should I install each OS. And that I shouldn't install both OS at same card, or something.
There are many ways to configure a system.  I have used single boot, dual boot, bios boot, ssd, hdd, ssd+hdd, ubuntu inside windows.  They all work, what you need to do is decide what is best for you.

I see oldfred has chimed in, he's a tough act to follow so I'll end my two cents here :D

---

### Post by oldfred on 2019-05-14
> I see oldfred has chimed in, he's a tough act to follow so I'll end my two cents here

Please do not stop helping. Sometimes oldfred gets too detailed or techy for new users. 
New users often need more than one explanation to fully understand details.

---

### Post by TheFu on 2019-05-14
Lots of good wisdom above.

Since this is a new system, getting it setup with lots of flexibility today should be the main goal.  That means UEFI booting for all OSes and partitioning to allow for upgrades over the next 5 yrs with as few hassles as possible.
GPT disk partitioning will simplify things going forward 10x. Use GPT, not MBR. This is important to have a flexible system. MBR has enough negative to be worth changing.

I built a new system 6 months ago. It has 2 NVMe slots on the motherboard and 6 SATA ports. NVMe can be 10x faster than SATA, but only if used/configured correctly. On my board, there are tradeoffs.  If I use any NVMe, I loose 2 SATA ports.  The PCI lanes get used.  Also, if I use the 2nd NVMe slot, then the 2nd GPU PCIe slot can only work at 4x speed, not 8x and the 2nd NVMe storage works at 2x speeds, not 4x speeds.  It is about reassigning PCI lanes by the motherboard.  Trade-offs.  Every motherboard version from each vendor is a little different.
There are also PCIe NVMe expansion cards. Those cards have different throughput capabilities which are dependent on the PCIe slot speed used and the configuration of other PCIe slots and on the capabilities of the NMVe storage.  It gets complex. My Asus motherboard has a table to help explain.  Of course, the box and advertising for it never mention anything except the fastest possible speeds for each slot as if they were used 1 at time in the most-bestest configuration possible for that single device.  The fact that this is impossible in the real world never is mentioned in the advertising.  Read the specific motherboard manual for these aspects.

As with your money and retirement planning, nobody cares about your computer (money/retirement) as much as you do.  For any non-trivial setup, I've never seen someone else configure a system in the most flexible, safest for upgrades, way.  When I configure someone else's setup, I try to keep it as simple as possible at the expense of flexibility.  I tiny problem that takes me 3 minutes to fix, thanks to a flexible setup, would be insurmountable for someone without the necessary knowledge. So to avoid that issue, I'd waste 2x the storage "just in case", even though it would likely NEVER be needed.
For example, it might seem to be smart to allocate 100G to Linux on a single partition, but that isn't the way experts do it.  The way I allocate storage is mostly about having the best backups possible and being able to easily install another Linux in a few years, while not risking my personal data.  How to best allocate a Linux setup is well covered in these forums already.

And I love the **tlcl** link above.  Linux people don't usually post images/screen shots. We use the shell tools so only text needs to be posted. 150 bytes replaces a 10Kb image, easily.

For example, to show us your partition tables on both disks, use **sudo fdisk -l**, then copy/paste the text here and wrap it in "[code tags]("http://blog.jdpfu.com/code_tags")" so the columns line up. If you post output here and it doesn't look the same as it did in a terminal, then please fix it.
To show the used storage, use **df -Th | grep /dev |grep -v loop** .  That line shows the mounted storage, file systems, for the important partitions, but not the funky pseudo-devices that don't matter.

---

