---
title: "Need to fix GRUB but Ubuntu doesn't load"
date: 2008-07-27
forum: General Help
---

### Post by gsb521 on 2008-07-27
I messed up my linux partition with GParted, and I need to edit GRUB to make my Windows Vista partition the default rather than Ubuntu (it loads until the logon screen, at which point it says it can't find /home).

(I'd also like to try Xubuntu in place of Ubuntu, so how can I make sure I fix the partition before I install another OS on it?)

---

### Post by nbayiha on 2008-07-27
It's a kind of impossible to understand what you mean dude.
So from what i understood , you were trying to make a clean instalation of ubuntu ? Or what ? this think about can't find /home .... 
Maybe you didnt create a home partition while installing Ubuntu. 
Just to let you know , while installing Ubuntu u need to create three partition , 
- /swap partition one (no more than 1giga )
- /     partition , this one is where your system is going to be put (10 giga will be fine )
-/home  partition this is the one where you will keep your file. 
So my first question is did you do this while installing Ubuntu ?

And about this grub messed up. Why don't you just reinstall it :) ? 
And what do you mean by your windows Partition the default ?
Actually if you have grub installed normally , you should have to choice between two system at you boot on your system.

Try to be more specific , cause it's hard to understand what you mean.
Tell us what you were trying to do , and what didn't work :lolflag:.

---

### Post by gsb521 on 2008-07-27
Here's the details of what I did:

Before, I had a Windows Partition (sda1), a Ubuntu Partition (sda2), a documents partition (sda3), and a swap partition (sda4).  I was running low on space in my Ubuntu partition, and I had enough RAM that I had never used swap, so I deleted the swap partition and I wanted to expand my Ubuntu partition (sda2) to include swap as well as take some of the Windows partition:

Before:
[  Windows  ][Ubuntu][Swap][Documents]

After:
[Windows][  Ubuntu  ][Documents]

To modify the partitions I used GParted off a Xubuntu 8.04 disk I had around.  GParted gave me an error, and I can't get into my Ubuntu desktop (on sda2), though it seems I can get into a terminal.

So, I have two questions:
1) Before I played around with the partitions, GRUB was set to default to loading Ubuntu, with 2 seconds' delay for me to make a change if I wanted.  Now that Ubuntu is not loadable, I want to change the default to Windows.  The problem is, I don't know how to edit the GRUB config file because I can't log into Ubuntu.

2) I would like to reinstall Ubuntu or possibly try Xubuntu in place of my ruined Ubuntu partition.  Do I need to be concerned that the partition is messed up so even if I install a new OS it won't work?  If so, how can I repair the partition.

Fortunately, my Windows and documents partitions were not affected by the partition failure.  I don't want to do anything that may compromise them.

---

### Post by confused57 on 2008-07-27
You should be able to select "Manual" partitioning and install Xubuntu on the partition that Ubuntu is on.  Set the mountpoint as / , format as ext3, primary partition.  As long as you don't select to format your Windows or Data partition, you shouldn't have any problem.

---

### Post by gsb521 on 2008-07-27
Thanks.  Is there any way to fix GRUB before I install a new OS?

If I install Xubuntu, will that detect and automatically work with the existing GRUB installation?

---

### Post by confused57 on 2008-07-27
Xubuntu will install it's own grub over top of Ubuntu's grub on the mbr of the drive.

---

### Post by nbayiha on 2008-07-27
Ok i will tell you how to fix your grub having the Ubuntu live CD.

first just get to Ubuntu with your live CD.
And then open a terminal and do this.

1- ```
sudo grub
``` 
then you should have something like this
 the grub> (...). 
for (...) enter 

2- ```
find /boot/grub/stage2
```

now you should have grub root , meaning something with (hdx,y)
ps: x,y are number , they can be 0,0 or 0,1

3- ```
root (hdx,y)
```
x,y been the number you receive from the last command.

4-```
setup (hd0)
quit
```

And reboot and you should have it fine.
If not let me know . I am going to the shower :lolflag: so i may answer with some delay.

---

### Post by gsb521 on 2008-07-29
Thanks to everyone for their help.

If anyone experiences the same problem, this is how I handled it.  I ran a Live CD of Ubuntu, and I was actually able to access the /home partition (it was only partially messed up, I guess).  From there, I modified the GRUB list and made Windows the default.  After that, I installed Xubuntu over the partition.  It worked fine with GRUB - it replaced each old Ubuntu entry with a new Xubuntu version.

---

