---
title: "Unacceptable!"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by Mieklol on 2009-04-13
I tried installing Ubuntu today to sort out my problem that Windows was having with linking to my HDTV.

Oh. My. God.

Ubuntu corrupted my Windows partition.

That's over 100GB of data...gone.

Don't tell me I should have backed up, I had nowhere to back up to, and I thought Ubuntu was reliable and user friendly.

Sorry, but this is unacceptable.

---

### Post by RedSingularity on 2009-04-13
What exactly is the problem?  The whole windoze install got deleted?

---

### Post by Mieklol on 2009-04-13
> **Shadow121 said:**
> What exactly is the problem?  The whole windoze install got deleted?

Windows, music, priceless photographs (hopefully I'll have these elsewhere), saved games, downloads, everything.

Sorry if I came across a bit harsh :( I love Ubuntu to bits, but I cannot live without my music!

---

### Post by RedSingularity on 2009-04-13
Did you chose the option in the Ubuntu install to "use the whole drive"?  Or did you have ubuntu automatically resize it?

---

### Post by Mieklol on 2009-04-13
> **Shadow121 said:**
> Did you chose the option in the Ubuntu install to "use the whole drive"?  Or did you have ubuntu automatically resize it?

I manually configured the drive to leave my Windows install alone: I told it to resize to 132GB out of 232GB. Just as it began 'Resizing Partition' it told me it had failed and the operation aborted.

---

### Post by OutOfReach on 2009-04-13
> **Mieklol said:**
> I manually configured the drive to leave my Windows install alone: I told it to resize to 132GB out of 232GB. Just as it began 'Resizing Partition' it told me it had failed and the operation aborted.

Did you defrag Windows before doing this?

---

### Post by Ravernomina on 2009-04-13
thats not ubuntu fault..... thats actualy the partitioners fault and did you take the requirements to partiton the drive as well?
Because if u didn't thats basicly the reason why it failed :l

whats u need to do befor you partition

1. Defrag the drive
2. empty recyle bin
3. clean windows drive 
4. virus scan
5. anti spy and ad scan
6. defrag again
7. partition and resisze.

if u didn't do any of these steps these could of ben one of the reasons....       so next time please do not auto-blame a OS :mad:

---

### Post by notwen on 2009-04-13
Resizing w/ partitions w/o backups is just asking for trouble.  I've had this same thing happen to me on multiple occasions.  After so many failed resizes/data lost I broke down and constantly back up files that mean a lot to me, every two weeks to a ext hdd that I keep in a fire-proof safe.  Sorry to hear about your loss of data, but you live and you learn.  Hope you can recover some, if not most of it.

---

### Post by Pasdar on 2009-04-13
Click Places in your panel up there... do you see your other partition there? and if you do... click on it... do you see your files? How are you sure that your files are gone?

---

### Post by Penguin Guy on 2009-04-13
Before you install Linux you should defrag' the disk. If you didn't defrag' then the good news is: You still have most of your data! Windows seems to prefer installing the OS in the centre of your disk - in this case you may have lost nothing but the operating system! Someone else may know how to go about recovering data, but for now, try not to loose the data that you already may have.

---

### Post by Mark Phelps on 2009-04-13
> **Mieklol said:**
> I tried installing Ubuntu today to sort out my problem that Windows was having with linking to my HDTV.

Oh. My. God.

Ubuntu corrupted my Windows partition.

That's over 100GB of data...gone.

Don't tell me I should have backed up, I had nowhere to back up to, and I thought Ubuntu was reliable and user friendly.

Sorry, but this is unacceptable.
There are two different "problems" with installing Linux in a dual-boot mode with Vista (I'm presuming you're using Vista):
1) Vista OS overwrite
2) Vista OS corruption

The first happens when folks choose the "whole disk" option, not realizing that Ubuntu will reformat the hard drive, effectively wiping out the Vista installation.

The second happens (sometimes) when folks choose to allow the Ubuntu installer to "shrink" the Vista OS partition to make room for Ubuntu.  This is nearly always repaired by booting from the Vista DVD and running Startup Repair.

A quick way to tell which one happened to you is (from Linux), open a terminal and type "fdisk -lu" (that's a lowercase L, not a one).  If you get info back indicating that you have NTFS partition(s) followed by Ext3 partitions(s), your Vista installation is still there.  If you have no NTFS partitions, it got overwritten by Ubuntu and is gone.

---

### Post by notwen on 2009-04-13
[Future reference]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") for Windows Vista users who wish to dual-boot, although the OP did not specify his version of Windows which was lost.

---

### Post by marks_linux on 2009-04-13
Sorry if it sounds harsh, but having 100GB of 'important' files that wasn't backed up was going to sting you one day anyhow. Yes Ubuntu is reliable, but disks and users aren't often! Vista stung me when 'disk clean up' decided to delete all my user files (it turned out later to be a bug that 'hid' the files, but too late as I had reinstalled). That was the last of several issues that moved me back to XP and Ubuntu.

Hope you gt it sorted

---

### Post by silentrebel on 2009-04-13
Have you tried boot into Ubuntu from the LiveCD, mounting your Windows partition and looking at the files that may still be there?  Have a look, if the partitioning failed so quickly, it may not have done much damage to your prized data...  If you need further help in this regard, let me know.

---

### Post by Therion on 2009-04-13
> **marks_linux said:**
> Sorry if it sounds harsh, but having 100GB of 'important' files that wasn't backed up was going to sting you one day anyhow. 

Agreed.  If you're not backing it up, it's not that important.  

Not when you can pick up [320GB drives for $50](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136098)

---

### Post by cariboo on 2009-04-13
I would suggest you give [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") a try to see if you can repair your partition. Like the others in this thread have said, if data is important to you back it up. I have my important files on at least three different hard drives in different computers, as well as on two external drive.

Jim

---

### Post by Mieklol on 2009-04-14
Right, sorry if I came across harsh, I was just distressed.

I stress to you that I had NOWHERE to back these files up to; the last place I backed them up to was unavailable.

The Vista install was relatively new, as was the partition, so defragging was not needed.

Partman reported that it was a full EXT3 partition.

---

### Post by cc8balla on 2009-04-14
> **Mieklol said:**
> Right, sorry if I came across harsh, I was just distressed.

I stress to you that I had NOWHERE to back these files up to; the last place I backed them up to was unavailable.

The Vista install was relatively new, as was the partition, so defragging was not needed.

Partman reported that it was a full EXT3 partition.

You can seriously buy an external hdd for $50 now, 320gb of backup goodness. 

And it dosen't matter that the partition was 'relatively' new. Defragging an existing partition is something that needs to be done, ESPECIALLY windows, since I don't think you have an idea how that file system works. It's a mess.

---

### Post by silentrebel on 2009-04-14
Is Partman reporting that your Windows partition is formatted as ext3?  If that is the case, I believe this isn't mere corruption; you inadvertently overwrote the Windows partition (chose the wrong partition for the installation).  I suppose that it may still be possible to recover data at this point, but I cannot help you in this endeavour...
Anyone?
Sorry

I'm afraid I don't believe Testdisk will be of much use in such a case...

---

