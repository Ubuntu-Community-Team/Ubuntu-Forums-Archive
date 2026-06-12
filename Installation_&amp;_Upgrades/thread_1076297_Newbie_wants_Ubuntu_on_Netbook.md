---
title: "Newbie wants Ubuntu on Netbook"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by Sebrof on 2009-02-21
Hi all,

Recently purchased Samsung NC10 as my primary machine (it's cheapish, powerful enough for my needs and seems ergonaomically accepatable) and I'm very keen to use the Ubuntu OS. 
Why? The ethos, the hope it will be a more resliiant OS than windows and because I would like to become more computer literate.

I am compleatly green when it comes to this type of OS, though a friend mentioned it is possible to partition the HD and load Ubuntu so that I could use either OS untill I felt comfortable with Ubuntu.

So my questions are: (considering the NC10 comes with a spartan version of Windows XP with SP3):

1. How easy is it to parition the HD and install Ubuntu ALONG with XP? (i.e. Would it be more stable to compleatly erase XP and plonk in Ubuntu)

2. The Samsung has already partitioned its HD using Samsung Recovery Solution III into two ~60GB sections - how would this impact on further partioning neccissary to install Ubuntu alongside XP?


I'm sure these questions are infuriatingly nieve for alot of the advanced users out there, but any help would be much appriciated :)  

Thanks in advance


(I have downloaded the Ubuntupocketguide, so I am trying to learn!)

---

### Post by wpshooter on 2009-02-21
You can, in theory, have multiple O/S on the same machine.  However, my personal preferences is to have either M/S O/S on the machine or have Ubuntu on the machine but not both at the same time.  If you attempt to install both on the same machine AND if they decide which one of them is going to be in control and they do have any conflicts regarding that matter, then you might be fine.  But **_IMO_**, there is too much that can and likely will go wrong when trying to have multiple O/Ss on the same machine.

---

### Post by Bölvaður on 2009-02-21
sorry for how long it took to answer but here is mine:

It is fairly simple to partition. There are 2 ways to do it:
[LIST=1]
[*]Partition from inside Windows
[*]Defragment the Windows partitions and manipulate them from the live cd via program named **G**nome** PART**ition **ED**itor (gparted)
[/LIST]

This is because of the ntfs file system Windows is probably installed on to avoid any dataloss.


Before you get down and dirty with the partitions you may want to learn what the different partitions on your Windy is used. And depending on that you should draw a simple partition scheme on a napkin (or anything really...).

I guess if you can provide detailed information about the partitions we can help you as far as the data you provide allows.


How you set up partitions normally should not have anything to do with the stability of the system.


It is very easy to do (please do it manually). Just make backups of your data before you begin.

---

### Post by pedja_portugalac on 2009-02-21
Ubuntu Netbook Remix (UNR) is great OS for netbooks.

[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

Now, it's possible to have windows and ubuntu on same netbook (your 60GB HDD is enough for that. The process is the same as installing dual boot on normal laptop but then I'll recommend to install regular ubuntu and then add extra packages for Ubuntu Netbook Remix: Desktop Switcher, Go Home Applet, Human Netbook Theme, Maximus, Ubuntu Netbook Remix Launcher and Window Picker Applet. 

Read this first: [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

---

### Post by Dalal on 2009-02-21
well !
I am a beginner like u so let me try ;)

if u are a biginner with ubuntu i think u need time to use it comfortably bacause with linux  u must know exactly what u want to do and how to do it ;)
so i think your friend suggestion is ok.(i still have both OSs).


if u intend to complete with ubuntu  u can give it larger  hard disk partition and to modify the disk partitioning 
to divide disk partitions as your needs 
u can go to
control panel ->administrative tools->computer managment-> storage->disk managment  to make free space for installing .

and when installing ubuntu choose to install it in the empty  space of your disk 

I do not know if this info is simple to u or not but I wanted to help

REGARDS.

---

### Post by Bölvaður on 2009-02-21
> **wpshooter said:**
>   But **_IMO_**, there is too much that can and likely will go wrong when trying to have multiple O/Ss on the same machine.

examples?


I have been triple booting for a year now and have "public" backup and data partitions accessible for them.
I can see how GRUB may be a pain, and perhaps resizing netfs partitions which is occupied by windy, but it's not likely to affect Sebrof you think?

---

### Post by Sebrof on 2009-02-24
Hey, thanks for all the advice guys!

Going to try and manually partition the drives and duel install Ubuntu. Now would be a good time as I have not transfered any old files onto the HD yet, so any disasters won't be disasterous.

I'll keep you posted ;)

---

