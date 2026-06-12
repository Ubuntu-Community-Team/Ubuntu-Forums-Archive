---
title: "Can Windows XP and Ubuntu Linux work on the same computer?"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by Amit G on 2007-03-26
I have got an Ubuntu Linux 6.06 LTS but have not started using it yet. I am planning to get a laptop in a couple of months and wanted to know whether I could use both Windows XP and Ubuntu Linux on the same Laptop? Actually a friend of mine told me that I can have both by partitioning the hard disk but it will lead to system instability and even computer crashes. Can both Ubuntu and Windows be used on a 160 GB Hard Disk by partitioning the hard disk? or would it be better to have a laptop with 2 hard disks with one OS on each??? Right now I have Windows XP on my desktop and my family is keen on using it while I wish to use Ubuntu and Windows both and am getting a laptop pretty soon. Please help me!!!!!

---

### Post by BrianK on 2007-03-26
Your friend has no idea what he's talking about.  You can run them both on the same computer on different partitions, and it's amazingly simple to do so.  Just be sure to install Windows first & leave half or so of your disk unpartitioned during the windows install.  Once windows is up & running, install ubuntu on the remainder of the disk (this is one of the options when you install) & Ubuntu will automagically setup a dual boot menu for you.

I've been doing this for years (along with half the population of Ubuntu users, I would imagine) - there is 0 issue with stability.  One OS doesn't know about the other and vice versa (while they're running anyway)

---

### Post by Moordrik on 2007-03-26
Brian is right, there is absolutely no issues with building a dual boot XP/Linux box.  I'm writing this from one right now. Like Brian said install Windows on the first partition and Ubuntu on the second partition, grub (the boot loader) will automatically create a boot menu that you will see at start up giving you the option to boot Ubuntu or Windows.

---

### Post by Amit G on 2007-03-26
Thanks BrianK,
    so now pretty soon I would also be amongst half of the population of Ubuntu Users.I'm looking forward to it.

---

### Post by Amit G on 2007-03-26
Hi Moordrik,
       what's grub(boot loader) ?

---

### Post by Amit G on 2007-03-26
Thanks BrianK and Moordrik,
                 I'll start using it as soon as I get my new laptop. Take Care. Bye .

---

### Post by aysiu on 2007-03-26
Your friend is clueless on this issue but may be knowledgable about other areas of life.

Here's a dual boot guide for you:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by crane on 2007-03-26
I am guessing that the lasptop will have XP preinstalled? If so don't worry. Ubuntu (edgy and Feisty) come with the option to resized the windows partition so you can install Ubuntu. Be sure to clean and defrag Windows before installing.
 Windows can duel boot with absolutly no problems. This machine I am on actually has 4 Operating systems on it. One is XP which I  runs fine.

Basicly a boot loader is software that manages what boots up when you start the computer. When you install Linux you will be presented with a list of options to boot.
 When you install Ubuntu on your laptop you should see the option to start windows or Ubuntu.

---

### Post by zorkerz on 2007-03-26
It is not even necissary to install windows first (though deffinitely cuts out a step)  I reinstall windows all the time because it slows down and i cant take it.  My ubuntu install has been intact after each install. It just requires reinstalling the grub bootloader after windows so you can boot in ubuntu again.

---

### Post by windigofer on 2007-03-27
Not only is it possible, it's very easily doable :D

I am with others in that if you're going to put both on a laptop to install Windows first and then Ubuntu (if only because so many PC manufacturers can't be bothered to supply an *actual* Windows CD and give restore disks); Gparted actually does a fairly painless job of partitioning the drives.  (You will want to make sure your Windows partition is defragged first just in case; with a fresh Windows install this should not be an issue, but if you've been running Windows for a while this could be more of one.)

Presently I am running both Windows XP and Ubuntu Edgy on what I lovingly call the FrankenLaptop (Compaq Presario 2190US motherboard installed in HP ZE4500 laptop with most of the components from the latter--both laptop models actually use the same motherboard, it's the BIOS which has minor differences--think Ford vs. Mercury :D).  I set things up to have the Windows partition (which was pre-existing from their system restore, which in fact is just a PartImage disk image), then set up a dedicated partition for Ubuntu and a FAT32 partition to be shared between operating systems (writing to NTFS is still touchy at this point, hence the desirability for a communal FAT32 partition).

One can even use Ubuntu in a dual-boot system without using ext3 (which is the default anymore for Ubuntu)--I actually up and put ReiserFS on here, all is quite well behaved :D  (In fact, the Linux partition tends to behave better than the WinXP one, quicker at any rate)

---

### Post by Obywan on 2007-03-27
yes you can put 2 Operating Systems on one HD (i acvtually have 3) FIRST you MUST put in Win XP, load it up like normal, tehn you put Ubuntu in it will split up the HD space in half exactly... :)  hope that helped!!!

P.S. i think that if you split up you HD into partitions with boot magic or fdisk, tehn you can have one partition split (say 20 gigs), then the rest can be common space between the t OS's.



                      -Oby

---

### Post by aysiu on 2007-03-27
> **Obywan said:**
> 
P.S. i think that if you split up you HD into partitions with boot magic or fdisk, tehn you can have one partition split (say 20 gigs), then the rest can be common space between the t OS's. Ubuntu's installer comes with its own graphical partitioning utility. You don't need to use another program to split partitions.

---

### Post by Amit G on 2007-03-27
Thanks all you guys for helping me out.I was actually in a fix of how to make it work and here in my city it seems no one uses Linux, everyone is Windows fanatic and if somehow they come to know I have a Linux they look down upon me and were not assisting me or even telling me properly how it works or can two OS work on the same computer- in fact my mom told me, if you wish to do it, do it on your laptop, not my desktop computer cause' the computer engineer who came to repair somehow dissuaded her from using it saying she will have a lot of technical problems. I had one more question to ask , actually is it possible that I have 2 internal hard disks on the same laptop which I asked these guys and they said no, it's only possible with desktop computers and have one hard disk with Ubuntu Linux 6.06 LTS and another with Windows XP? and I can use both and if somehow Windows Crashes it will not affect the entire computer and Ubuntu will still keep working? And while I have two internal hard disks, I can have one external hard disk to save all documents,spreadsheets, presentations, favorites and bookmarks whether it be from MS Office or OpenOffice?

---

### Post by BrianK on 2007-03-27
> **Amit G said:**
>  I had one more question to ask , actually is it possible that I have 2 internal hard disks on the same laptop which I asked these guys and they said no, it's only possible with desktop computers and have one hard disk with Ubuntu Linux 6.06 LTS and another with Windows XP? and I can use both and if somehow Windows Crashes it will not affect the entire computer and Ubuntu will still keep working? And while I have two internal hard disks, I can have one external hard disk to save all documents,spreadsheets, presentations, favorites and bookmarks whether it be from MS Office or OpenOffice?
Most laptops only have room for one hard drive.  There are a few that hold two, but it's pretty uncommon.

If you were to have two hard drives, you could certainly install windows on one and ubuntu on another without issue. Again, grub will take care of this for you.

That said, windows crashing will have no effect on the hard drive or ubuntu.  Windows will not cause hard drive failure, nor will any OS - hard drive failure is exactly and only that - a physical hard drive failure. (I'm sure, someone will argue something about windows memory management and swap files and viruses and so forth, but, for the most part hard drive health is OS independent.)

Finally, yes, you could still attach another external drive to store documents if you so desire.  I don't know if there is even a realistic limit to the number of drives that you can attach to your machine.

---

