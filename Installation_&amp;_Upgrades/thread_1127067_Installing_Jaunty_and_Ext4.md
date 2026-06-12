---
title: "Installing Jaunty and Ext4"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by Scubdup on 2009-04-16
I know there have been some posts on this before but I can't find a clear answer.

How do I install Jaunty and Ext4?

When I install from the LiveCD it automatically creates an Ext3 partition. At no point do I have an option for Ext4.

Thanks for any help.

---

### Post by digitalmonk on 2009-04-16
> **Scubdup said:**
> I know there have been some posts on this before but I can't find a clear answer.

How do I install Jaunty and Ext4?

When I install from the LiveCD it automatically creates an Ext3 partition. At no point do I have an option for Ext4.

Thanks for any help.
I installed jaunty from the alternate cd,by default it selects ext3, however there is an option which allows you to go back,once you select go back,you have the option to change ext3 to ext4

---

### Post by Scubdup on 2009-04-16
> **digitalmonk said:**
> I installed jaunty from the alternate cd,by default it selects ext3, however there is an option which allows you to go back,once you select go back,you have the option to change ext3 to ext4Ah. I'm *pretty* sure I explored every avenue on the regular LiveCD. So maybe I need to download the Alternative LiveCD to do it...

---

### Post by bvanaerde on 2009-04-16
> **Scubdup said:**
> Ah. I'm *pretty* sure I explored every avenue on the regular LiveCD. So maybe I need to download the Alternative LiveCD to do it...

I'm quite sure it is located on the regular LiveCD too.
At least it was like that on the alpha5 CD :)

When the installer asks:
*"How do you want to partition the disk?"*
you have to select **manual**.

Here you can add partitions and select the partition type (ext3, ext4, ...)
It looks something like this:

---

### Post by Scubdup on 2009-04-16
Hmmm. I'll have another look. Thanks bvanaerde.

Can/should I make all of them ext4 to see the full benefits?

What do people recommend?

---

### Post by Scubdup on 2009-04-16
Anyone?

I've shoved in an old 200Gb drive so no data to lose.

I don't know anything about the essential partitions for Ubuntu.

From bvanaerde's picture I would guess SDA1 and SDA6 can be formatted as Ext4 and SDA5 needs to stay as "swap". Is that right?

---

### Post by bvanaerde on 2009-04-16
You need at least 2 partitions:
[LIST]
[*]root partition (/)
[*]swap
[/LIST]
Some prefer to put their home directory on a different partition though.

About the amount of swap, there are different opinions on this matter. I found [some good advice]("http://www.cyberciti.biz/tips/linux-swap-space.html"):
Swap space == Equal RAM size (if RAM < 2GB)
Swap space == 2GB size (if RAM > 2GB)

Unless you want to use e.g. hibernation: then the swap space needs to be at least the RAM size.

---

### Post by scott1541 on 2009-04-16
i think the selection thing you want is in about step 4 of the installation, where you select the drive you want to use and how you want to partition the drive(s), there is a list of file systems on the next page if you choose manually partition drive(s)(page 3,4 or 5) - Also you don't need any swap space (well i don't have any) to add to that i am only using one drive

---

### Post by bobmatino17 on 2009-04-16
the only disadvantage of ext4, which i found out the hard way, is that cd's with rescue modes cant fix a grub error, because they only support ext3. at least i had the live cd. i still use ext4, soon they will all understand it.

---

### Post by Scubdup on 2009-04-16
Thanks for the replies. That's cleared up some of my confusion.

I think I'll go for what I mentioned earlier:

Root - Ext4
Swap - N/a
Home - Ext4

scott1541, I'll go for the swap partition like bvanaerde suggested just because it's what the standard installation sets up IIRC. I'm a bit of a novice, so the closer I can get to the bog-standard the better IMO!

Same reason for having a separate home partion.

Am I right in thinking I can format Root and Home in Ext4 and the Swap partition is an option.#

I'm trying to get as much of the speed benefits from Ext4 as possible.

---

### Post by SuperSonic4 on 2009-04-16
Yes, that configuration is fine and similar to what I use (I have /var formatted to reiserfs too).

If you've got enough disk space it won't hurt to have swap :D, I've got 4gb of ram and I've still needed swap when ripping video to an ISO file

---

### Post by Scubdup on 2009-04-16
Thanks SS4. I've got 5gb (so I'll definitely use a swap partition) and you've just reminded me [I need to test for a  memory-hole-remapping/hoisting problem I experienced when I tested a 64-bit LiveCD where only 3.2gb was showing]("http://ubuntuforums.org/showthread.php?p=6921492#post6921492").

---

### Post by digitalmonk on 2009-04-16
Perhaps the question might appear silly,still i would be glad if someone throws some light on this

any idea what is the difference between ext3 and ext4.
what i understand is there ext4 is faster, master in terms of what, say a hard disk is sata and 7200 rpm, how will ext4 better the speed??

---

### Post by scott1541 on 2009-04-16
it's not the speed of the drive spinning its the speed of data transfer or something like that. As an answer to the actual question look [here]("en.wikipedia.org/wiki/Ext4") (it may or may not help

---

### Post by Scubdup on 2009-04-16
Errrr.

I tried to reinstall and had some problems.

The default setup was for a swap partition and an ext3 partition.

After selecting a manual partition configuration I have a few options.

I tried to change the ext3 to ext4 and continue and I get an error message "No root file system is defined. Please correct this from the partitioning menu".

Not sure how to go forward. Any suggestions.

---

### Post by bvanaerde on 2009-04-17
> **Scubdup said:**
> I tried to change the ext3 to ext4 and continue and I get an error message "No root file system is defined. Please correct this from the partitioning menu".

You need to define the mount point. If you want Ubuntu installed on that partition, select "root" as mount point. It is normally described as a forward slash (/), but I'm not sure how it's shown in the jaunty installer.

---

### Post by cb951303 on 2009-04-17
Set the mount point for root partition to "/" and for home partition to "/home"

---

### Post by Scubdup on 2009-04-17
Thanks for the replies. Really helpful.

---

### Post by aenesias on 2009-04-23
Hi,
I have vista in my comp i have a ntsf partition D and a raw space which i reserved for 9.04. Till this release,i used the automatic installation using the largest continuous space one which is always easy to use however i want to try ext4 which i should make a manual installation. As for as i know i have to make an extended partition and make swap root partitions on it. the thing i am cofused is that i dont know how to set mount points when doing it manually. Can somebody please help me on that ?

---

