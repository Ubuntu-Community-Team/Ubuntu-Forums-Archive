---
title: "dual os with vista?"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by rchubcitywihwy1480 on 2009-07-21
Hi

What do i need to do to experiment with  the latest Ubuntu to see if i  can do it?
I have AMD 64 Athlon X2 4600,  3drives- 160, with vista home premium 32 bit, 160 for storeage and an external 250, the 250 has 198 free,  the 160 c has 41.6 free now of 160, the s has 102 free of 160.

Running spybot, lavasoft, computer assoc av,   scanner printer 4 port usb hub 

Not sure what else  i should tell you?

Thanks

---

### Post by philcamlin on 2009-07-21
you want to duaboot?

you just pop in the live cd/usb and install 

and install :)

---

### Post by nmaster on 2009-07-21
try wubi first.  its simple, easy, and you can see if all your hardware will work before doing a full install. [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by lisati on 2009-07-21
It can be done - I currently dual-boot with Vista on my laptop, and don't anticipate any major problems on your machine.

The first thing I'd recommend, if you haven't already done so, is make a backup of your recovery partitions, "just in case". My laptop came with software preinstalled that let me do it.

The next thing I'd suggest before installing is try the "try Ubuntu without installing" option a "Live CD". Although it will run slightly slower than installing, it will help give you an idea if you can use your machine, e.g. will networking work?

---

### Post by nmaster on 2009-07-21
if you resize a vista partition using gparted you may need to use this:
 [http://neosmart.net/blog/2008/window...disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

vista has a partitioning tool, but it may restrict the amount by which you can shrink the parition.

---

### Post by rchubcitywihwy1480 on 2009-07-21
Thanks for all the prompt relies.

I understand  some of you are saying not to install and using  wubi also, can i put anything on the "s" drive, which is the internal one opposite the c,  with the most free space? then the stupid question/// dual boot is 2 os on 1 pc?   when you start up they both start or  only the one you designate?

thanks,.
i'm down for the count now, so won't see any replies till tomorrow night,tks

---

### Post by lisati on 2009-07-21
> **rchubcitywihwy1480 said:**
> Thanks for all the prompt relies.

I understand  some of you are saying not to install and using  wubi also, can i put anything on the "s" drive, which is the internal one opposite the c,  with the most free space? then the stupid question/// dual boot is 2 os on 1 pc?   when you start up they both start or  only the one you designate?

thanks,.
i'm down for the count now, so won't see any replies till tomorrow night,tks

I can't speak for the others who have responded, but my recommendation is for a "taste and try before you buy" approach, using the "try Ubuntu without installing" option to get an idea of what problems (if any, hopefully none) you are likely to encounter. This can be a useful part of the planning process if you decide to go ahead and actually install Ubuntu.

---

### Post by perito on 2009-07-21
> **rchubcitywihwy1480 said:**
> Thanks for all the prompt relies.

I understand  some of you are saying not to install and using  wubi also, can i put anything on the "s" drive, which is the internal one opposite the c,  with the most free space? then the stupid question/// dual boot is 2 os on 1 pc?   when you start up they both start or  only the one you designate?

thanks,.
i'm down for the count now, so won't see any replies till tomorrow night,tks

After you install ubuntu successfully. When you start your PC, you'll get to a menu like this

[IMG]http://taqeem.files.wordpress.com/2007/11/xp_ubuntu_09article-width.jpg[/IMG]

(With your Operating Systems instead of the ones above)
You will choose an operating system and it will start. As simple as that.

---

### Post by rchubcitywihwy1480 on 2009-07-21
Thanks

does that window appear whether you have installed it or" tried one of the other  options"?
tks

---

### Post by Mark Phelps on 2009-07-22
The post clearly says that appears "after you install ubuntu successfully".  Also, while either an Wubi install or separate dual-boot install is likely to produce the same menu, the dual-boot might need some additional work.

---

### Post by rchubcitywihwy1480 on 2009-07-22
> neal.m.master  	
Re: dual os with vista?
try wubi first. its simple, easy, and you can see if all your hardware will work before doing a full install. [http://wubi-installer.org/](http://wubi-installer.org/)

I  gues this is where i was coming from, this is not a complete install?

---

### Post by nmaster on 2009-07-22
> **rchubcitywihwy1480 said:**
> I  gues this is where i was coming from, this is not a complete install?

you get all of ubuntu (except hibernation), but you don't need to worry about partitioning your disk.  wubi is an executable that you can remove from the control panel if you want to.  it is a full install, but runs off of a virtual disk in a folder rather than a seperate partition.  its a great way to try ubuntu without any risks.  read the faqs section of that site for a lot more info.

---

### Post by rchubcitywihwy1480 on 2009-07-22
Thanks

I did order the cd or dvd for Ubuntu, but when i would install that i can put it on the s  drive i have, not the c drive?
The s  has 198 free where the c presently has 40+. i could increase that easiyl.

Just wondered if they both  have to be on the same?
tks

---

### Post by dk06 on 2009-07-22
> **rchubcitywihwy1480 said:**
> 
What do i need to do to experiment with  the latest Ubuntu to see if i  can do it?


All you need to do to experiment -or- try Ubuntu is just download & burn the Live CD (Desktop Edition)

You don't need to install it to try it out, just put the Live CD in , Reboot, & boot from the CD

when you get the menu, 

select:
"Try Ubuntu without making any changes to my computer"
____________________________________________________________________
If you decide you like it, dual-boot or try it with Wubi

---

### Post by rchubcitywihwy1480 on 2009-07-22
Maybe i am not asking it right, so one more try,  does it make any difference which drive i  put Ubuntu on should i install it?  The c drive my s drive or my external drive?  vista is om my c drive.
tks

---

### Post by dk06 on 2009-07-28
> **rchubcitywihwy1480 said:**
> Maybe i am not asking it right, so one more try,  does it make any difference which drive i  put Ubuntu on should i install it?  The c drive my s drive or my external drive?  vista is om my c drive.
tks
________________________________________________

If you want  to dual-boot  ubuntu with windows, 

***Do a FULL BACKUP of Windows***

Then:
1) boot from the Ubuntu CD 
(I recommend installing it on your internal HDD, External installs can cause issues)

2)Select your language then select "Try Ubuntu without changing your computer"
(You can use the Live Installer with the option above)

3)Select "Install Ubuntu" from the desktop icon & follow the prompts

4)[COLOR=Red]**Partitioning:**[/COLOR]
---It should default to"**Resize Windows & Install Ubuntu in unused space**" 
    (if not select that option -**or**- whichever option best suits you)

5) Follow the rest of the prompts & you are done

-Reboot & Test them out, you can select which one to boot when you power on your machine- 

Have Fun:)

[B]
EDIT:[/B] I highly recommend disconnecting your external drive for the install unless you are installing it on your external
& You can also Run Ubuntu from a Flash Drive <-fyi

---

### Post by rchubcitywihwy1480 on 2009-07-28
Thanks

the cd/dvd is not here yet, be aweek or so yet i'd assume, so the flash drive  will work better than the ext hdd, nothing on it?  what brand of  f dr, is best?

tks

---

### Post by dk06 on 2009-08-08
> **rchubcitywihwy1480 said:**
> Thanks

the cd/dvd is not here yet, be aweek or so yet i'd assume, so the flash drive  will work better than the ext hdd, nothing on it?  what brand of  f dr, is best?

tks
______________________________________________________________________

Here is what I'd do:

boot from the ubuntu disk & select the "Resize Windows & Install Ubuntu in empty space " option (during partitioning), click next-click next-click next-click next-done-
______________________________________________________________________

For a portable Ubuntu, put it onto a USB stiick

---

### Post by Mark Phelps on 2009-08-08
[QUOTE=dk06]... boot from the ubuntu disk & select the "Resize Windows & Install Ubuntu in empty space " option ... [/QUOTE]

Please do NOT do this!! Using Ubuntu to resize the Vista OS is risking corrupting the OS partition such that it renders is unbootable -- which you can repair if you have A Vista DVD.

If you're going to dual boot (separate partition for Ubuntu), use the Vist Disk Management utility to shrink the Vista OS partition to make room for Ubuntu.  

You can also use the same utility to shrink the "S" volume -- but since that does not contain the OS, you can also use the Ubuntu partitioner (GParted) to do that.

If you just want to try out Ubuntu for a while, use Wubi to install side-by-side (NOT shrinking) into your "S" drive.  Later, if you decide you like it, you can either remove the Wubi install and reinstall dual-boot, or you can "move" the Wubi install to its own Linux partition.

---

### Post by rchubcitywihwy1480 on 2009-08-08
TKS
the cd is here but i will wait  and look at your suggestions
tks

---

### Post by presence1960 on 2009-08-08
> **Mark Phelps said:**
> Please do NOT do this!! Using Ubuntu to resize the Vista OS is risking corrupting the OS partition such that it renders is unbootable -- which you can repair if you have A Vista DVD.

If you're going to dual boot (separate partition for Ubuntu), use the Vist Disk Management utility to shrink the Vista OS partition to make room for Ubuntu.  

You can also use the same utility to shrink the "S" volume -- but since that does not contain the OS, you can also use the Ubuntu partitioner (GParted) to do that.

If you just want to try out Ubuntu for a while, use Wubi to install side-by-side (NOT shrinking) into your "S" drive.  Later, if you decide you like it, you can either remove the Wubi install and reinstall dual-boot, or you can "move" the Wubi install to its own Linux partition.

+1

A lot of us have had Vista become unbootable after using gparted from either the Ubuntu Live CD or gparted Live CD. IT is a well documented issue. Use the Vista disk management utility from within Vista to shrink the partition with Vista OS on it.

---

### Post by rchubcitywihwy1480 on 2009-08-08
Thank you very much.  Sometime if my head should become clearer, and my patience better, i will try Wubi.  

After that is on the s drive, am i given a prompt as to what to boot to when i boot the pc?  I am very GREEN  on how you run one os and not the other?????

I am far from a geek stage!
tks
:p

---

