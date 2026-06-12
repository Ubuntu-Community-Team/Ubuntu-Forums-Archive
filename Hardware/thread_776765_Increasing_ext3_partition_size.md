---
title: "Increasing ext3 partition size"
date: 2008-04-30
forum: Hardware
---

### Post by hulio40 on 2008-04-30
hello all i wanted to increase my ext3 ubuntu partition size with gparted livecd


first i unallocated 20gb of size from my windows xp ntfs partition
to the end 

now i want to increase my ubuntu partition by 20gb but it doesnt let me it says max partition size 5185mb (i first wanted to test ubuntu)


please help me i give a thank to te one who gives me the solution [-o<

---

### Post by PauGNU on 2008-05-01
Are you doing that from your ubuntu partition or from a livecd?. I think it is not possible to resize linux partitions when those partition are active and working.

Try using a livecd.

---

### Post by mtonsbeek on 2008-05-01
> **hulio40 said:**
> hello all i wanted to increase my ext3 ubuntu partition size with gparted livecd


first i unallocated 20gb of size from my windows xp ntfs partition
to the end 

now i want to increase my ubuntu partition by 20gb but it doesnt let me it says max partition size 5185mb (i first wanted to test ubuntu)


please help me i give a thank to te one who gives me the solution [-o<


Yes I think PauGNU is right. I couldn't manipulate the partitions either until I booted from the LiveCD. No problem afterwards.

That is assuming you have hard drive capacity of course.

---

### Post by hulio40 on 2008-05-01
yes i have the ard drive capacity and yes i ran it from the gparted livecd

---

### Post by pytheas22 on 2008-05-01
What does the geometry of the drive look like?  If it's like:

|---Windows---| |---unallocated---| |---ext3----|

then it might be difficult because I'm not sure if you can expand a partition by merging with empty space in front of it.  It would be better if the unallocated partition came after the Linux one.  But I'm not sure.  It's possible that you might be able to move the ext3 partition so that you would have a setup like:

|---Windows---| |---ext3---| |---unallocated---|

then you would be able to add the unallocated space into the ext3 partition without a problem.

Another solution is to create a new ext3 partition with the unallocated space and use it for /home if you need more space for data storage, or for /usr if you're running out of space for Ubuntu applications.  You would need to edit /etc/fstab for this to work but it's not hard.

Or you could just reinstall Ubuntu.

---

### Post by pytheas22 on 2008-05-01
Also as a word of caution...I should have mentioned this early...be sure to back up any important data on all partitions of your hard disk before trying to modify the partition structure.  Nothing should go wrong, but editing the partition table is inherently unstable so you should take precautions.

---

### Post by akroev on 2008-05-01
> **pytheas22 said:**
>  Nothing should go wrong, but editing the partition table is inherently unstable so you should take precautions.

Inherently unstable is a misnomer: Inherently dangerous is a better description.

Generally, backups are warranted whenever the words "partition" or "filesystem" are involved in the discussion (as well as whenever you have done some work on your data/files that you'd rather not have to do again).

-akr
(Occasional prophet; always a Picker of Nits)

---

### Post by hulio40 on 2008-05-01
my gemotry is like this  |------ntfs-------||-ext3-||swap||---------ntfs------||unallocated|

---

### Post by Can+~ on 2008-05-01
> **hulio40 said:**
> my gemotry is like this  |------ntfs-------||-ext3-||swap||---------ntfs------||unallocated|

Wow, that's a huge mess you got there. I used to have something similar:

hda: |----ntfs----|
sda: |-----------ntfs----------||--ext3--||swap|

This happend when I was just strating with ubuntu, then I liked it and did:

hda: |----ntfs----| (For windows, slow hard disk 5600rpm)
sda: |-----ext3------||swap||-------ntfs-------|

So I had windows running on the old hard disk, ubuntu running with a nice amount of space and a "common" section, on ntfs, for both OSs to read/write to.

How I did that change? I just formatted everything :KS, you can buy an external hard disk and backup everything there, or burn dvds like crazy.

Windows, after a clean install runs a lot faster and you can install essential apps with a fresh start, and just use ubuntu everyday, and leave windows for those crucial things.

gparted can move partitions (apparently), but I have never done it before. I just would say a clean reinstall, plus, you make a big backup for the future, and a clean install of windows.

---

### Post by hulio40 on 2008-05-01
ha never..... would take me months and i dont have an external hd

maybe someone can find a solution? all this is on the same hd...

---

### Post by akroev on 2008-05-01
> **hulio40 said:**
> my gemotry is like this  |------ntfs-------||-ext3-||swap||---------ntfs------||unallocated|

Adding the sizes of each partition might have been a good idea, too. But regardless, the only way you can make _one_ ext3 partition from several non-adjacent pieces, is by the use of what's known as Logical Volumes. However, these are somewhat finicky in setup (IMHO, others may disagree), and (AFAIK) the resultant filesystems will not be available from anywhere other than inside the given Linux installation. Depending on sizes here, I might consider making the existing ext3 partition your /boot (or /home) partition, and make a new / partition in the unallocated space.

But before you do anything, please come back with a post including the sizes of the partitions, so we can take that info into consideration.

-akr
(asking himself why someone wants just _one_ partition for Linux)

---

### Post by hulio40 on 2008-05-01
or i could just backup my ubuntu partition stuff and then delete it and with both unallocated spaces i would do a fresh ubuntu install? but then it would be like this

|--ntfs--||unallocated||--swap--||--ntfs--||unallocated|

---

### Post by akroev on 2008-05-01
> **hulio40 said:**
> or i could just backup my ubuntu partition stuff and then delete it and with both unallocated spaces i would do a fresh ubuntu install? but then it would be like this

|--ntfs--||unallocated||--swap--||--ntfs--||unallocated|

Yes, that would be roughly what I outlined as a potential solution. However, in this case there is one potential problem that I am too ignorant to consider: What would happen to the Windows setup if you changed the number of partitions between the two NTFS partitions ? I'm thinking that if you do, the system ID of the second NTFS partition would change, potentially confusing Windows, and since I haven't used Windows since its name was "Windows 3.11", I have no idea whether this would become a problem or not.

But for us to consider this more fully, _please_ tell us the sizes of these partitions, and add the size of your RAM. And regardless of what OS you are running, harddisks are prone to failure, and should be backed up regularly, so that part is relevant, anyway.

Another point is that it is generally recommended to keep /home on its own partition, so that it is somewhat isolated from the rest of the system, and so that it can be kept as is from one installation to the next (assuming you do a reinstall at some future point).

(sidenote: The next two/three days I'll be busy somewhere off the net.)
-akr

---

### Post by hulio40 on 2008-05-02
umm is there a command to show the partition sizes and empty spaces etc

---

### Post by pytheas22 on 2008-05-03
> is there a command to show the partition sizes and empty spaces etc 

Install gparted (sudo apt-get install gparted) and run it with sudo gparted.  It will show all the stuff you need to know.

---

### Post by hulio40 on 2008-05-03
no space on my ext3 partition its 5gb big....

---

### Post by pytheas22 on 2008-05-03
If you can't come up with the two megabytes to install gparted, run it from a live CD.

---

### Post by hulio40 on 2008-05-03
Oh sorry i thought gparted was about 120mb as from the livecd but forgot it included fluxbox anyways

i got a screenshot of it and my ram is 256 mb   dont laugh lol its a 5-6 year old computer it cost me 1500$ back then lol n  im planing to buy a new one this summer

---

### Post by hulio40 on 2008-05-07
anyone? :(

---

### Post by bdoe on 2008-05-07
I agree, that is quite a mess you have there. Personally, I would just back up everything important within all OSs you have on that thing, then format and reinstall. However, as long as you already have everything backed up, you have nothing to lose by trying to move the partitions around so that the ext3 and unallocated partitions are next to each other, and then expand the ext3 partition to fill the unallocated space.

Short of that, the best solution is to format the unallocated partition, then use it for /home.

---

### Post by hulio40 on 2008-05-07
and how do i use it for home after i format it to ext3

---

### Post by hulio40 on 2008-05-08
or how can i move the ubuntu partition to the end near the unallocated space?

---

### Post by hulio40 on 2008-05-09
bump

---

### Post by hulio40 on 2008-05-15
BUMP halp!

---

### Post by hulio40 on 2008-05-20
whatever ill just erase the ubuntu partition and get my partitions back as they were 2 ntfs's

i wasted my time with this os all it got me is problems

---

