---
title: "Grub my axe and go berserk."
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by Deicider on 2009-11-11
Simple.
Installed KK on empty comp.
After i installed windoze on another partition.
As usual grub disappeared,so i installed kk again.
I reboot.
Says :loading Grub.
But unfortunately for everyone in the planet,It doesnt load.
Skips it and goes straight to karmic,although sometimes it actually LOADS but at the grub menu shows only Karmic(normal,recovery,mem test).
Tried to install through terminal(grub),did that,upgrade it.
Same.
Should i install it again? :$

---

### Post by paxmark1 on 2009-11-12
First.  Did you put Windows in the first partition?  If not you will have to learn about chainload I believe.  Windows always wants to be first, I install windows first usually, and then when I put in my linux flavour, grub (old fashioned) would find it.  

Yes, Windows always wipes the mbr (master boot record) and you have to reinstall grub.  You can use your live cd or a disk recovery cd or the alternative cd.

Important details are if your linux partitions are ext3 or ext4? 

Is this from an upgrade or a fresh install?
Are you running 32 bit or amd64 (which includes the intel 64 bit processors).

If it is a fresh install and you are using the default installation, you will get grub2, the new grub and ext4 partitions with 9.10.  

There are many,many people having difficulties with 9.10 for a variety of reasons, video drivers, the new grub, etc., palmipsest, nvidia name change to nv, etc.  I lucked out and it went very easy for my upgrade.  

A quick and simple temporary fix might be to just install the 6 month old 9.04.  Who knows what all might be going wrong with your system with the brand new 9.10. You haven't had the chance to get to know it yet, and it might throw some more curves at you.  If you will do hideous damage to innocent metal and silicon in a berserker viking mode if you encounter one more problem, that might be best.  (Yes, we all have been that angry at our computer at least once)

An even easier fix might be (if you are using grub2)
sudo update-grub2

Or search the forums for what others have had to slog through

(Hint adding "solved" to your search filters out ones that have not been marked solved) 

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=update+grub](http://ubuntuforums.org/showthread.php?t=1195275&highlight=update+grub)

[http://ubuntuforums.org/showthread.php?t=1323193&page=3&highlight=solved+update+grub](http://ubuntuforums.org/showthread.php?t=1323193&page=3&highlight=solved+update+grub)

[http://ubuntuforums.org/showthread.php?t=24113&highlight=solved+update+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=solved+update+grub)

peace mark

---

### Post by Deicider on 2009-11-12
> 
First. Did you put Windows in the first partition? If not you will have to learn about chainload I believe. Windows always wants to be first, I install windows first usually, and then when I put in my linux flavour, grub (old fashioned) would find it. 

Yes, Windows always wipes the mbr (master boot record) and you have to reinstall grub. You can use your live cd or a disk recovery cd or the alternative cd.

Important details are if your linux partitions are ext3 or ext4? 

Is this from an upgrade or a fresh install?
Are you running 32 bit or amd64 (which includes the intel 64 bit processors).

If it is a fresh install and you are using the default installation, you will get grub2, the new grub and ext4 partitions with 9.10. 

I suppose when u say first you mean the order of installation,and not the partition number(or maybe u meant both).
Ext4 it is.
32 for me.
I imagine it was grub 2.


Have 4 partitions(i dont know if the order of partitions count)
a 200 disk broken in:
48 -ntfs-empty-for future windows7(but the way things happens dunno)
39 -ntfs-windows xp pro-i installed it first
50-ext4- and then i installed karmic(that means windows was first and linux second)
Though the installation of karmic was "select the largest continues space" ,it was the 50gigs.
You u had a 200gig,and wanted to install those 2 OS,how would u form ur partitions?

Btw,grub still does same,it "loads" but it actually loads bs.and karmic start.
So that means,grub is already installed.
Any way,am going for pure installation of Both OS from scratch.
Any suggestions?

---

### Post by mikewhatever on 2009-11-12
> Grub my axe and go berserk.

:lolflag: ...

---

### Post by paxmark1 on 2009-11-13
wow.  so you have 

/sda1 empty for windows 7
/sda2 is for xp
/sda3 for /    for all of karmic.

I had a triple boot once upon a time, but I used the FreeBSD bootloader which some argued was much better than grub at the time.  I had my first partition for 98, then Mandrake, then FreeBSD and shared the swap space. 

I also used two hard disk drives  98 was done as /dev/sda1 and then moved to /dev/sda2 (or hdb in windowsland) and the unixes were on the new /dev/sda1.  windows is dumb and didn't know it had been moved to sda2. 

Possibly the empty partition on /sda1 is causing grub problems.  possibly not.

If you are triple booting, you very well might have to learn about chaining in grub.

search forums for triple boot grub2     add solved 
google triple boot grub2 xp windows7 karmic

user phillw posts  in [http://ubuntuforums.org/showthread.php?t=1316153](http://ubuntuforums.org/showthread.php?t=1316153)

 couple of pointers ....

[http://raviratlami1.blogspot.com/200...ws-7-with.html](http://raviratlami1.blogspot.com/200...ws-7-with.html)

another triple boot, although not win7.

[http://lifehacker.com/193474/hack-at...sta-and-ubuntu](http://lifehacker.com/193474/hack-at...sta-and-ubuntu)

Are by people who have done it.

The secret seems to be XP 1st, then Win7 (which will see XP) and then ubuntu (which will see them both)

Hope they are of help.

Phill.

You have selected a very challenging install with a triple boot and even more so with ubuntu 9.10 karmic koala being a little notorious for being fickle for failure for some.  It will require a bit of reading on the web to get it up.  I am sure it can be done.    

It might be easier to go with a dual install of xp and karmic or even jaunty and to install windows 7 on a seperate hard drive later.  If you have recent but not new machines (as guessed by the choice of 32 bit and a 200 gb hdd) 

My plans are to finally buy a new version of Windows again (it's been over a decade since I bought 98) and install it in a second hard drive and run my 32 bit windows XP (I upgraded in 2005) in virtualbox under Ubuntu. I did use the Windows7 RC for a bit in virtualbox and it is the first Windows worth buying in a long time. I am back in school online and they do like windows for distance learning. 

me, 200gb    30 gb for xp.  and then 
/dev/sda2 6gb /
/swap   1gb
/var 1gb
/tmp 2 gb
all the rest for /home

I would have windows 7 on a different disk.  

If it is a notebook, I would not have xp.  or else I would give windows 7 90 gb and ubuntu all the rest and run xp using virtualization.  I would first get windows 7 running.  Then I would install Jaunty 9.04 and then after the dust clears I would install or upgrade to 9.10.  

I never have and never will place my home under /  Some of the simplified ubuntu disk partitioning schemes have this, but if I wanted to do things like that, I would not be using linux.  

Enjoy learning

peace mark

---

### Post by Deicider on 2009-11-13
i actually finished.
But.
Installed:
WinXP and Karmic.

1.primary -ntfs-30 gigs for Xp-just to use some programs,and have fun (:
2.primary -ext4-15 gigs for /(Root) (made it primary just in case)
3.primary -ntfs-30 gigs -for now data-this is ntfs only to be readable by both OS,i made it a pri actually so that later i can have the option to make it an OS.
4.exteded-
 1-logical-ext4- 5 gigs for swap.
 2-logical -ext4- 70 gigs for home.

It took me time and i lost my appetite for win7.
Anywa,the correct order and good parition formations did the work.

---

### Post by paxmark1 on 2009-11-15
congrats,  please mark as solved.  

Kudos on giving / 15 gb.  I only have 6.g gb and I only have 1.4 gb left and that is with a seperate /tmp. 

Enjoy learning

---

