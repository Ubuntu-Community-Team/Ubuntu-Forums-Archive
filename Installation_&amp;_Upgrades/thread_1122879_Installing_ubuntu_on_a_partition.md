---
title: "Installing ubuntu on a partition"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by acethedragon on 2009-04-11
trying to install Ubuntu 8.10 on a dell 6400/e1505.I had it installed in windows before. But since then. I have wiped the hard drive so there is no recovery sector ie; (no dell). I have the divided the HD into 3 partitions. the hard is as follows 
80 gig sata
C:/ 25gig. formatted NTFS.. nothing installed
E:/ 25 gig formatted NTFS ..Win Xp Pro 
F:/ remaining drive free unformatted

The question how do I manual install Ubuntu on the last partition? 

I have tryed reading, but instead of scabbing material together to do this. I thought I just ask.

---

### Post by acethedragon on 2009-04-11
BTW my Ram is 1.5 gig.

---

### Post by coffeecat on 2009-04-11
> **acethedragon said:**
> BTW my Ram is 1.5 gig.

Plenty! :wink:

> **acethedragon said:**
> 80 gig sata
C:/ 25gig. formatted NTFS.. nothing intalled
E:/ 25 gig formatted NTFS ..Win Xp Pro 
F:/ remaining drive free unformatted

The question how do I manual intall Ubuntu  on the last partition?


That leaves about 25-30GB unformatted which is also plenty. By the way, Linux doesn't refer to C:, D: drives and so on. I tell you this so you don't get confused later. Also, the unformatted space is not a partition because it's unformatted. And it's possible it may be split. Dell have a habit of sprinkling small partitions all over the hard drive, so there may be unformatted space 'before' and 'after' your Windows C: and E: partitions.

Anyway, the easiest way is to boot up with the live CD. I presume you've got a live CD. Once you get the desktop loaded, double-click on the installer and when you get to the partitioning stage (about page 3 or so), choose 'Guided - Use largest continuous free space'. The installer will set up partitions for you and set up a dual-boot menu. Please do take a note of the username and password you choose. You'll need it! We get people coming on these forums complaining that they are being asked for a username and password at login and don't know what to put in. :-k

Before you start the installer, go to System > Adminstration > Partition Editor. You don't need to create any partitions - the installer will do that for you - but just have a look to see how your unformatted space is distributed. If you have any doubts about this, just post back.

**Edit:** the 'Guided' section in Ubuntu 8.04 is slightly different from what I described (8.10). Which version were you thinking of installing?

Also - you've probably been warned about this. Whenever you use a partitioner there's always the (slight) risk of a catastrophic corruption of the partition table. Backup all data first.

---

### Post by ronparent on 2009-04-11
Format your remaining drive as an extended partiotion. You can do this from your ubuntu live cd. Install ubuntu into that extended partition. You should select manual format when you get to the partitioning step of the install. Make sure to select a mount point for the system before proceeding to create the linux (and swap) partition - select / as mount point. Other than that in is pretty much a matter of following directions as you proceed through each step.

---

### Post by acethedragon on 2009-04-11
thanks for both of your replys. 
  Coffeecat: > **coffeecat said:**
> Which version were you thinking of installing?

     Yes Ubuntu 8.10  
> **coffeecat said:**
> I presume you've got a live CD.

         Yes.. Ubuntu 8.10 iso  i386

> **coffeecat said:**
> 
 Once you get the desktop loaded, double-click on the installer and when you get to the partitioning stage (about page 3 or so), choose 'Guided - Use largest continuous free space'. The installer will set up partitions for you and set up a dual-boot menu.
 It hangs if I try to install from the live CD GUI. I am able to get the install, by just running the CD. Trying to run "guided" use the largest. I get " Some of the partitions you created are too small. Please make partitions at least this large(in bytes)--
/2053140992 if you do not go back to the partitioner and increase the size the intall may fail"
Sorry I cant seem to get the attach file to work or I would just post a screen shot.

and last but not least I just wiped this hard drive and thought this would be a  good time to Install Ubuntu on it's own partition. Unstead of running it from within a windows intallation.
Thanks

ronparent:> **ronparent said:**
> --------------------------------------------------------------------------------

Format your remaining drive as an extended partiotion. You can do this from your ubuntu live cd. Install ubuntu into that extended partition. You should select manual format when you get to the partitioning step of the install. Make sure to select a mount point for the system before proceeding to create the linux (and swap) partition - select / as mount point. Other than that in is pretty much a matter of following directions as you proceed through each step.

  Ok like I said I am new so Linux terms are slow to sink in. I am at the manual format stage and need to learn "a mount point". Could you break that down a bit?

Thanks

---

### Post by coffeecat on 2009-04-11
> **acethedragon said:**
> and last but not least I just wiped this hard drive and thought this would be a  good time to Install Ubuntu on it's own partition. Unstead of running it from within a windows intallation.

Do you mean that you've removed the former Windows C: and E: partitions so that there's now nothing on the drive? If so, it's quite straightforward. You don't need to set up partitions manually, and you don't need the 'Manual' install. (Which can be a bit intimidating if you're not used to partitioning or to Linux.)

If you really want only Ubuntu on that machine with Windows wiped into oblivion, simply choose the first 'Guided' option - 'use whole disc', or something similar.

The most likely reason you got the "partitions too small" error is that the free space was spread over the drive, probably before, between and after the C: and E: partitions. Which is why I suggested you looked in the Partition Editor before proceeding.

I don't understand what you mean by "Unstead of running it from within a windows intallation." That sounds like a wubi install which wasn't what I was describing at all, with Windows and Ubuntu having their own discrete partitions.

---

### Post by acethedragon on 2009-04-11
> **coffeecat said:**
> The most likely reason you got the "partitions too small" error is that the free space was spread over the drive, probably before, between and after the C: and E: partitions. Which is why I suggested you looked in the Partition Editor before proceeding
I did look at the partition before trying to install
ok so I hope this explains what I am trying to do.
C:/ = /dev/sda1 (boot)  25gig  ntfs    nothing installed 
the rest are extended
E:/ = /dev/sda5   25gig  ntfs    Win Xp Pro is installed here

F:/ = /dev/sda6   25 gig ntfs  this is where I want ubuntu 8.10
unallocated 1.41 gig

I want to format 26082 mb of this part (/dev/sda6)of the harddrive in what format. In manual / edit partition (below are my choices)
a)Ext3 journaling file system
b)Ext2 file system
c)ReiserFS journaling file system
d)JFS journaling filing system
e)XFS journaling file system
f)fat16
g)fat32
h)ntfs
i) Do not use this partition

Then have a small 1500mb swap partition?

what i am trying to do is learn to manually intall Ubuntu, on a portion of my hard drive. create a dual boot. Not just install Ubuntu but learn to manually install.

---

### Post by coffeecat on 2009-04-11
> **acethedragon said:**
> F:/ = /dev/sda6   25 gig ntfs  this is where I want ubuntu 8.10
unallocated 1.41 gig

Ah! Now I understand you. Sorry for not catching on before. Unformatted is often used loosely to mean a space with no partitions, which is why I misconstrued your first post. My mistake. Anyway, you have a partition which you need to reformat. Choose the ext3 filesystem. This will be your Linux root partition, which you will see referred to as the '/' partition.


> **acethedragon said:**
> Then have a small 1500mb swap partition?

Yes, you'll need a swap partition. 1.5GB will be fine. Or that 1.41 will do nicely.

> **acethedragon said:**
> what i am trying to do is learn to manually intall Ubuntu, on a portion of my hard drive. create a dual boot. Not just install Ubuntu but learn to manually install.

Yes, if you format sda6 as ext3 and create a swap partition in that unallocated 1.41G space, then go for the manual choice at the partitioning stage of the installer. The installer will pick up the swap partition automatically - you don't have to worry about that. Designate sda6 as your root partition by specifying '/' as the mount point. It should be the first choice in the little drop down menu here.

A little bonus. If you want Ubuntu to mount your two NTFS partitions at boot up so that you can read/write to them, at this same mount point part of the installer, simply specify mountpoints, but obviously make sure they are not marked for reformatting. Your mountpoints could be of the form:

```
/media/winC
/media/winE
```Or winC and winE can be anything you want: Fred, Bill, StrangleBillGates, whatever you want. By mounting in /media, you get desktop icons to click on.

Alternatively, if you do not want these partitions mounted at bootup, they will still be mountable on the fly, so to speak, from the Places menu.

---

### Post by acethedragon on 2009-04-11
Thanks. 
 well it is asking me to make the swap drive. So question here is ,what choices do I make.
Create partition:

Type for the new partition; 
a)primary
b) logical

New paritions size... we will just use the 1.41 gig
location for the new partition
a)beginning
b)end
use as ... i am assuming ext3?
Mouunt point..... '/'??

---

### Post by acethedragon on 2009-04-11
retract the last 2 choices 

ext3 and '/' I figured that one out "swap area"

---

### Post by coffeecat on 2009-04-11
It probably doesn't matter whether your swap is primary or logical. A couple of tips here - excuse me if you know them. You are limited to 4 primary partitions only - an old msdos limitation. Instead of one, and one only, primary partition you may have one extended partition. An extended partition is merely a container for a number of logicals.

Now to the linux bit: You can tell by the number. sda1,2,3,4 are either primaries or extended. sda5,6,7,8,etc are logicals. So, your partitions:

> C:/ = /dev/sda1 (boot)  25gig  ntfs    nothing installed 
the rest are extended
E:/ = /dev/sda5   25gig  ntfs    Win Xp Pro is installed here

F:/ = /dev/sda6   25 gig ntfs  this is where I want ubuntu 8.10
unallocated 1.41 gigsda1 must be a primary. sda5 and sda6 are logicals. (By the way, I thought Windows couldn't boot from a logical - can you boot that WinXP on sda5?) There must also be an extended. When you open the live CD Partition Editor, do you see sda2,3 or 4?

Now the tricky bit: that spare 1.41gig. Without seeing the layout, I can't say what's best. Creating a small primary would be easiest (I imagine) but a bit untidy. But if there is 1.41 unused in the extended partition, you would have to make the 1.41G swap a logical. Or, you could increase the size of the extended to swallow the 1.41G, but ONLY if the 1.41 is contiguous with the top end of the extended.

Anyway, I hope this helps and that I haven't misunderstood anything again. I'm afraid I've got to hit the sack now, so that's it from me for a few hours.

Good luck!

---

### Post by coffeecat on 2009-04-11
> **acethedragon said:**
> retract the last 2 choices 

ext3 and '/' I figured that one out "swap area"

Just so we're clear. Your root partition (/) will be ext3 filesystem. Linux needs a dedicated swap partition - you choose 'Linux swap' as the filesystem -  which you create with the partitioner. I just wanted to emphasise that because I was uncomfortable with your "swap area". Windows uses a swap file, Linux a swap partition. Important point that.

---

### Post by acethedragon on 2009-04-11
Well It is loading, we will see if that is a good sign.

> **coffeecat said:**
> By the way, I thought Windows couldn't boot from a logical - can you boot that WinXP on sda5?) 
Yes it boots no problems, I have been doing that for years. Only problems is some programs wont let you choose what drive to install on, they automaticaly choose C:/. So you have to do a little changing later on. 
 AS you probaly figured out I like to tweek things. It is how I learn.

> **coffeecat said:**
> just wanted to emphasise that because I was uncomfortable with your "swap area". Windows uses a swap file, Linux a swap partition. Important point that.

"swap area" was the term right there in the drop down box, Explain swap partition?
Enjoy your rest, I look forward to learning more.
Thanks

---

### Post by acethedragon on 2009-04-11
What was that name and password again?

Well it seems to be working, YAAA !

---

### Post by coffeecat on 2009-04-12
> **acethedragon said:**
> "swap area" was the term right there in the drop down box, Explain swap partition?

I didn't realise they used the term 'swap area'. I didn't notice. Well, basically a swap partition is a dedicated partition for - um - swap. :wink: It has its own filesystem. When you get to setting up multiboots - that is several Linux distros on different partitions - you can have just one swap partition. The same one gets used by all the distros - obviously one at a time. The traditional rule of thumb was to make the swap partition twice the size of your RAM. That was OK in the days of 256-512 MB RAM, but is a bit out of date now - it could lead to unnecessarily huge swap partitions. The only thing that is important is that if you rely on suspend or hibernate (whichever it is - I can never remember - the one where the contents of RAM are dumped to the HD) you need a swap partition at least equal to your RAM. So, depending on whether those 1.5 and 1.41 values were both or differently GB or GiB, you might need to take care with suspend. Hibernate? :?
 
> **acethedragon said:**
> What was that name and password again?

:lol:

> **acethedragon said:**
> Well it seems to be working, YAAA !

Excellent. Enjoy!

---

