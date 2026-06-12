---
title: "How do I set up raid 0 with onboard controller?"
date: 2008-06-26
forum: Hardware
---

### Post by slope on 2008-06-26
I have an Asus P5N E SLI motherboard and have no idea how to set up raid 0 with 2 x 'cuda SE using the onboard. In the world of windows Iused a cd to install drivers for the onboard raid and then i could set it up. But I can not find any drivers for linux. So I guess there must be a way to get this working without drivers in ubuntu? I have roamed the net to figure out to do this woithout luck. The thing is I downloaded the manual for my mb and it says that for the nvidia raid it only supports windows. I am certain I have seen people running raid 0 with ubuntu on this very motherboard.

Is there a smart guide I can use or a tutorial maybe?
Maybe only changes are made in BIOS and linux handles the rest?

Pls help as I would like to get as much grunt as possible out of me system.

---

### Post by slope on 2008-06-27
Surely someone knows how to get me started here? What is different when setting up 2 x Hdd raid 0 w/ onboard nvidia.

A step by step guide would be right-on.

---

### Post by Odrodzona-Sarmacja on 2008-06-27
Searching on google for "ubuntu +tutorial +raid" gave me this page:
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)
Does it help somehow?

---

### Post by slope on 2008-06-27
Hmm this link covers software based raid. As far as I know there are often issues booting from softwarebased raid. So my plan was to set up hardware raid 0 based on the onboard nvidia raid on my asus p5n e sli board.

Are the problems with software raid and booting old and fixed maybe?

If there are no more boot problems with software raid, will I gain anything using software rather then hardware raid?

-thx

---

### Post by Odrodzona-Sarmacja on 2008-06-27
If you have set hardware, then you need just to set up device for raid and then mount it. I searched this forum for "raid" and got this result:
[http://ubuntuforums.org/showthread.php?t=835361&highlight=raid](http://ubuntuforums.org/showthread.php?t=835361&highlight=raid)
Have a look at how someone did succeeded at creating himself a raid device for raid on his Ubuntu and then how he used it for mounting it. Maybe this will be of some help to you.

---

### Post by slope on 2008-06-30
I can not make the onboard raid [adapter] work with linux. If I set up the bios for raid with a windows on hardisk windows boots and has detected the raid. Trying this in ubuntu and it will ot work. When bios settings are correct I am not able to boot. Changing bios settings back to normal and <unable> raid lets me boot system. I am giving up on hardware raid until I have cash for dedicated raid controller. But as the are expensive that will have to wait. Meanwhile I will try out sw raid.

I am not sure if it is at all possible to boot into ubuntu from a software raid 0? Cause I have seen people saying both yes and now on the forums. Anyone actually made raid 0 with sata drives working with ubuntu? Remember I will use the raid 0 a system disk with both data and os in the raid.



For added security I will set up rsync to care for backup to nas.

---

### Post by slope on 2008-07-01
Gave up running hardware raid with onboard controller. Too much hazzle and I could not get it working nor find any usable solutions.

I started with software raid using the xubuntu alternate 64 bit cd.
Before I started I watched the raid guide video; [screencasts.ubuntu.com/20070910_installing_ubuntu_part_2_968x544.html]("screencasts.ubuntu.com/20070910_installing_ubuntu_part_2_968x544.html") 

Installation process went well and I was able to set to two 750 drives as raid 0. When I was almost done with the install I can not get GRUB to install. Neither could I get LILO working. 

Any tips how I can solve this?

---

### Post by slope on 2008-07-01
Here is an overview over my currently configured partitions and mount points:

```

RAID0 device #0 1.5 TB Software RAID device
      #1 1.5 TB F ext3          /
SCSI1 (0,0,0) (sda) - 750.2 GB ATA ST3750330NS
      #1 primary  745 GB K raid 
      #2 primary  5.2 GB F swap         swap
SCSI2 (0,0,0) (sdb) - 750.2 GB ATA ST3750330NS
      #1 primary  745 GB K raid 
      #2 primary  5.2 GB F swap         swap 

```

What I suspect is that GRUB do not see this raid 0, so installer does not know where to write the bootsector or what it is called. Do I maybe need to do something else to get a boot sector?

What I see from this is that I have RAID 0 1.5 TB that will be formatted filesystem ext and this is where the root goes. So why does not GRUB install nicely for me?

---

### Post by Tumbledown on 2008-07-02
I'll be keeping an eye on this post.

I have 3 500GB SATA II drives in RAID 0 with vista no problems,
tried various tutorials and how-to's to get this working with
ubuntu, but no joy.

I have looked about for support and I often see the comment that
"RAID" fake or H/W, "is sufficiently supported".

In my humble opion, this is not so in the case of fakeraid!
(i.e. most mobo's with onboard RAID)

I've been "playing" around with linux for some years now, 
tried various flavours, starting with the then new Red Hat 6.0 
SUSE 6/7.0, even still I classify myself as a linux newbie.

I have reciently tried fedora core 8 and it detected my RAID
(with Vista installed) and worked a treat, even setting up
grub to boot vista, and all without any input from me 
as an end user (Sweet).

I'm currenty trying to move my graphics and animation workflow
to linux and fedora sucks in the updates department, espacially
when you compair how easy and smooth this is in Ubuntu.
None of this hunting for dependencies of dependencies etc.

Ubuntu Studio would be my preffered platform, if i could get it working! :(

So come on guys, if the Fedora project can get this working out
of the box, so should Ubuntu, after all, isn't is supposed to
be linux for humans?

Sorry, rant over - keep us posted on how you get on, and mabe a
how-to as to you solution. I for one would love to ditch M$ ASAP

Good Luck and keep us posted on your progress

---

### Post by slope on 2008-07-02
I will surely keep you posted on the progress.
What i have learned so far is that i might have had a to laidback attitude going for the switch from MS to linux :-)

It seems by all articles I have read upon now that I will also get extra performance by partitoning the disks correctly. I was going to use /root + swap and ext3. But there seems it can be advantages choosing wiser.

As I dig deeper into this I will keep you posted with this as well on how i manage to solve the raid issue.

surely we can not be the only 2 that woul like to benefit from raid 0 ;-)

---

### Post by slope on 2008-07-07
@Tumbledown
Ok I must admit. Gave upon running the system from hardware raid 0.
No matter what I tried there was no way i could finalize installation or get all drives detected. Just problems all the time. 

I followed tips from this forum and went for software raid. Without any testing done to back my view I can say that I now have a much more responsive system. And this is specially true for my guests os in vmware.

What I did was having /boot +/root from singel drive no-raid.
Then /home + vmware runs from 2 disks in raid 0.
I put /tmp + /swap on a singel drive as well.

With SSD prices dropping and becoming highly available I think in order to really enjoy great I/O and performance one will need to work out raid 0 setup issues and Linux. It is just a matter of maybe months if we are lucky before we can stack up 4-9 SSD and have them running raid 0 :lolflag: Imagine the speed, read/write performance and stunning I/O.

So I guess I will need to find time to work something out during summer.

---

