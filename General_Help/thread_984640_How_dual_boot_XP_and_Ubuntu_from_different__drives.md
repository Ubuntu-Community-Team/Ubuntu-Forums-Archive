---
title: "How? dual boot XP and Ubuntu from different  drives"
date: 2008-11-16
forum: General Help
---

### Post by mooncaptain on 2008-11-16
I installed 8.4 last Spring on a drive in my old computer. I pulled the XP os disk at that time and put it on a shelf. Now I want to dual boot the system from the original XP disk and my current Ubuntu disk. How can I do that?

---

### Post by jimmy the saint on 2008-11-16
do a quick search on the forum for dual boot and you will find 100s of threads on this exact topic.  as long as xp is installed first and you keep track of which disk is which during the installation you will be fine.

for example:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot+xp](http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot+xp)

and

[http://ubuntuforums.org/showthread.php?t=980108&highlight=dual+boot+xp](http://ubuntuforums.org/showthread.php?t=980108&highlight=dual+boot+xp)

---

### Post by Marius Derekus on 2008-11-16
Well, you could do a wubi install. First install windows, then your ubuntu disk should give you the option to install ubuntu as a windows application (if you already know this stuff then please inform me). It doesn't matter what hard drive you install ubuntu on. This would be another dual booting option.

---

### Post by TeXtonyx on 2008-11-16
Put the XP as master or first drive (drive 0).
Download Bootpart and install it on XP (free).

Reinstall grub on the Ubuntu /boot partition.
Boot to XP and run Bootpart which will add Ubuntu to boot.ini

Download Super Grub Disk, SGD. Then you can boot either XP or
Ubuntu independently of each, so that if one fails, it doesn't
leave the other OS temporarily dysfunctional, you with no OS.

---

### Post by caljohnsmith on 2008-11-16
All you need to do is set your BIOS to boot the Ubuntu drive, and then you can add an entry in your Grub menu to boot Windows on the other drive. It's actually really simple; once you get your other drive hooked up, how about opening a terminal (applications > accessories > terminal), and post:
```
sudo fdisk -l
```
And we can work from there if you want. :)

---

### Post by Marius Derekus on 2008-11-16
Can this be done for fedora as well. I saw a post where someone had ubuntu and windows ont the grub menu and was trying to get fedora on his grub menu. If it can be done, will you please show me how?

---

### Post by caljohnsmith on 2008-11-16
> **Marius Derekus said:**
> Can this be done for fedora as well. I saw a post where someone had ubuntu and windows ont the grub menu and was trying to get fedora on his grub menu. If it can be done, will you please show me how?
Did you install Grub with Fedora so that Fedora has its own menu.lst? If Fedora has a menu.lst, you can boot Fedora from Ubuntu by adding the following to Ubuntu's menu.lst:
```
title Fedora Grub Menu
configfile (hdX,Y)/boot/grub/menu.lst
```
And change (hdX,Y) to the Fedora drive/partition. If you want help, how about posting:
```
sudo fdisk -l
```
And identify your partitions. Also check if you have a menu.lst in your Fedora partition, and we can work from there.

---

### Post by Marius Derekus on 2008-11-16
Sorry for the misunderstanding but i don't have this information. I was trying to help someone else on this forum with the problem. If you want help him here is the thread [http://ubuntuforums.org/showthread.php?t=984597](http://ubuntuforums.org/showthread.php?t=984597) but if you don't have time I think he'll be ok because he's had other people help him on that thread. Thanx anyways

---

### Post by mooncaptain on 2008-11-16
Thanks for the offer. Here's the output from sudo fdisk -l
is:

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ccd2289

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4142    33270583+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e3f3ed9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4679    37584036   83  Linux
/dev/sdb2            4680        4866     1502077+   5  Extended
/dev/sdb3            4867        9729    39062047+   b  W95 FAT32
/dev/sdb5            4680        4866     1502046   82  Linux swap / Solaris

```
The sda disk has XP on it. I guess the next step is getting it into grub...

---

### Post by TeXtonyx on 2008-11-16
"All you need to do is set your BIOS to boot the Ubuntu drive, and then you can add an entry in your Grub menu to boot Windows on the other drive."

> **Marius Derekus said:**
> Can this be done for fedora as well. I saw a post where someone had ubuntu and windows ont the grub menu and was trying to get fedora on his grub menu. If it can be done, will you please show me how?

This thread has two drives. The other thread has fedora and ubuntu
on one drive, so there is no other drive to set bios to boot to. 

Of course this can be handled by grub. And it must be handled by
grub if Linux is the only dual (multi) boot OS's involved.

But if one is dual(multi) booting Windows and Linux the situation
is much different. 60% of Ubuntu users dual boot Windows and Ubuntu.
Some of those 60% are capable of handling problems. But the vast
majority are inept with Windows and very inept with Ubuntu the
new OS, to most of them. It's rare to have Linux users who are
first time Windows users.

Most of the new users to Ubuntu who dual boot Windows and ubuntu
are in the dabbling stage. They are the ones most likely to have
a problem with grub. Many of them have never used the command line
interface before. Now, for the more complicated menu.lst entries,
for more than one hard drive, figuring out the correct configuration
is largely a matter of trial and error. At least 50 threads a 
month have 4 or more pages with "experts" offering 8-12 different
grub configurations. I think that is a frustrating experience for
a new user who the Ubuntu community wants to convert. 

In quite a few (but probably less than half) it turns out that
the problem is not even with the grub configuration! Do you think
that makes a good impression on the new user? It seems to me that
early in a new Ubuntu user's career is the wrong time to establish
a priority for learning grub.

I don't think that reaches the most frustrating experience which
results from having grub installed in the MBR. What happens when
the user decides to get rid of Ubuntu or Linux in general. The
grub support files get deleted. The user can no longer boot into
the Windows OS which he is most reliant upon. This can be fixed
if you have the right Windows install cd in order to run Recovery
Console. But users have misplaced these cds. Or on some desktop
and most laptops, they ship with an OEM recovery cd which doesn't
have Recovery Console on it. Now they have to resort to other
more difficult measures. What for??!! This problem is created
when grub is installed to the MBR, and there is no need to do that.
Besides removing Ubuntu, the information in the grub files can
get corrupted in a few ways. Then the new to Ubuntu user can't
boot Windows because grub in the MBR can't work. Back to using
the Windows Recovery Console or spending a few days figuring out
how to fix grub. This problem never needs to occur, when the
two OS's are kept separate. Windows standalone and Ubuntu stand-
alone. I installed Ubuntu again last night and in Step 7, Advanced
I chose to install grub to the /boot partition. That takes about
5 extra seconds. It would take a little longer if you had two
Linux OS installed, to run sudo fdisk -l first to see your ext3s

Then I rebooted to XP and it took me 10 seconds to add Ubuntu to 
boot.ini and put the 512 byte boot sector segment in C:\ root.
The first time it might take 5 minutes to figure it out, it's 
simple. So besides being easier or certainly just as easy as grub
in the MBR it saves tons of frustration to inexperienced dual
booting, Windows and Linux, users. Now, if XP doesn't boot you
know it isn't grub but a Windows problem. No need to come to this
conclusion by trying various menu.lst entries which don't work
until forced to realize that this is a Windows problem not a
Ubuntu grub problem. And when Windows works and ubuntu doesn't
you know that it can be a grub problem, so troubleshooting is aided.

So you might have been undereducated and not known about the benefit
for windows/ubuntu/linux dual booters that prevents many of these
grub problems from ever happening. I think there is a big plus on
the side of /boot partition for grub installation, especially with XP,
and a very small advantage for grub in the MBR for advanced users. 
And there is Ubuntu nepotism (ist) somewhat like a soccer fan.
And there are old people not open to changing the old way of doing
things. Objectively, which approach do you think is best?

So you don't think I'm all out on a limb, here are some urls
including Ubuntu forum, which advocate putting grub in the /boot 
partition with an alternate bootloader. You can still use grub there.

[http://www.linux.com/feature/113945](http://www.linux.com/feature/113945)

[http://forums.majorgeeks.com/showthread.php?t=108021](http://forums.majorgeeks.com/showthread.php?t=108021)

[http://ubuntuforums.org/archive/index.php/t-499904.html](http://ubuntuforums.org/archive/index.php/t-499904.html)

[http://ubuntuforums.org/showthread.php?t=899222](http://ubuntuforums.org/showthread.php?t=899222)

[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

---

### Post by mooncaptain on 2008-11-17
> I installed Ubuntu again last night and in Step 7, Advanced
I chose to install grub to the /boot partition. That takes about
5 extra seconds. It would take a little longer if you had two
Linux OS installed, to run sudo fdisk -l first to see your ext3s
So after the fact of already having an Ubuntu install - since last last spring and I have a pretty big investment in development tools on it and I have my XP install, which has been around for years, what is the best path to getting Ubuntu to boot up from the XP boot.ini without reinstalling either OS on their separate drives?

---

### Post by caljohnsmith on 2008-11-17
> **mooncaptain said:**
> So after the fact of already having an Ubuntu install - since last last spring and I have a pretty big investment in development tools on it and I have my XP install, which has been around for years, what is the best path to getting Ubuntu to install from the XP boot.ini without reinstalling either OS on their separate drives?
So can you go into your BIOS and set the Ubuntu sdb drive to boot on start up? If you can do that, your problem is 90% solved, because all you need to do is add an entry in the Grub menu to boot Windows like I mentioned earlier. The only reason you would ever need to modify boot.ini in Windows is if you have no way of booting the sdb drive directly on start up, and if that is the case, I think that using Grub4DOS in Windows is a better alternative than modifying the Windows boot loader to boot Ubuntu. If you modify boot.ini, you have to go through two boot menus to see your Ubuntu entries, whereas with Grub4DOS you just have one menu with all your OS choices. Also boot.ini doesn't have the error handling capability of Grub4DOS; you won't get any Grub errors if you modify boot.ini, so it can be really difficult to troubleshoot booting problems that might arise when booting Ubuntu. I think TeXtonyx was replying to Marius Derekus's post, as he quoted, so I don't think he meant that advice specifically for you, but I might be wrong. :)

Anyway, it's up to you, let me know what you decide to do. :)

---

### Post by mooncaptain on 2008-11-17
I can change the drive I boot from in the bios so I know that each system will boot by itself. In any case I don't mind a Linux centered solution I have, with a lot of help from this forum, been able to get through all the issues I have needed to.

---

### Post by caljohnsmith on 2008-11-17
> **mooncaptain said:**
> I can change the drive I boot from in the bios so I know that each system will boot by itself. In any case I don't mind a Linux centered solution I have, with a lot of help from this forum, been able to get through all the issues I have needed to.
OK, to boot Windows from Grub, how about first opening a terminal (Applications > Accessories > Terminal), and do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the very bottom add:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Then reboot, make sure your BIOS is set to boot the Ubuntu drive, and then let me know how it goes when booting Windows from the Grub menu. If you have any problems, please explain in detail what happens when you boot Windows from the Grub menu, and we can work from there. :)

---

### Post by TeXtonyx on 2008-11-17
> **mooncaptain said:**
> So after the fact of already having an Ubuntu install - since last last spring and I have a pretty big investment in development tools on it and I have my XP install, which has been around for years, what is the best path to getting Ubuntu to boot up from the XP boot.ini without reinstalling either OS on their separate drives?

You are a competent Ubuntu user and have two hard drives which
gives you more options that a new user with one hard drive. I 
don't think you have to reinstall any OS, I mentioned the grub
reinstall to the /boot partition.

I look upon having two boot menus for booting as a plus, like a 
backup. If you boot to XP you can change the timer to 2 seconds
and the default OS from XP to Ubuntu. My other computer has
XP and Ubuntu on first drive and Vista and Ubuntu on the second
drive. I control all of this from XP on the first drive and I
use grub installed on the /boot partition of first drive ubuntu
to boot Vista. Or I can change bios to boot Vista directly. I 
think it is best to maximize your flexibility.

Since I think you want to boot XP I'm most concerned about whether
XP will boot from the second or slave drive position. Grub is
not my strong suit but I think this entry in menu.lst may work.

# on /dev/sdb1
title Windows XP Professional
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

EDIT: I later noticed that your XP is on (hd0,1)not (hd1,0) as above.

Write down the jumper settings on the back of the XP drive and
I use tweezers to change them if the drive is installed. Try it 
first with no jumper. Then try it with the jumper set to slave.
I'm not sure that XP will boot from second drive like Vista does.
Perhaps it has to be set to Master, Ubuntu doesn't care about it.

I just noticed your fdisk report and it seems you already have
it hooked up. Did you pay attention to the jumper settings? I
also see that caljohnsmith's menu.lst suggestion looks like mine.
If XP doesn't boot check to see if you can mount if from Ubuntu.
sudo mount -t ntfs /dev/sda1 /mnt
cat /mnt

Well if you can boot from XP and it may have to be set as master.
Download free Bootpart. Unzip bootpart.exe into C:\
run bootpart.exe and it reports the ntfs and ext3 of the drives,
with a number. Suppose the number for ubuntu ext3 is 3, then
bootpart 3 ubuntu.bin "Ubuntu" writes ubuntu.bin to C:\ and 
makes an entry Ubuntu in boot.ini and it shows up on the XP boot 
menu. I don't think it works with grub installed to the MBR, but 
try it. Bootpart reports two drives as C and D.

Otherwise you have to write grub to the /boot partition.
sudo grub
grub>find /boot/grub/stage1
root (hd1,0) [use what the find command reports]
setup (hd1,0) 
quit

With XP reported as sda1, if the jumpers are set to master,
XP should boot up right now because XP should still be written
to the MBR. Have you tried that? And if bios is changed to
second drive then Ubuntu should boot up. Both drives have a *
by them which means they should both be bootable.

---

### Post by TeXtonyx on 2008-11-17
> **caljohnsmith said:**
> OK, to boot Windows from Grub, how about first opening a terminal (Applications > Accessories > Terminal), and do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the very bottom add:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```

Then reboot, make sure your BIOS is set to boot the Ubuntu drive, and then let me know how it goes when booting Windows from the Grub menu. If you have any problems, please explain in detail what happens when you boot Windows from the Grub menu, and we can work from there. :)

I have a question. If Windows XP is installed on sda1, shouldn't
the root entry above "(hd1,0)" instead be (hd0,1) ?

------------------------------------

earlier posted fdisk report

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ccd2289

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4142    33270583+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e3f3ed9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4679    37584036   83  Linux

---

### Post by caljohnsmith on 2008-11-17
> **TeXtonyx said:**
> I have a question. If Windows XP is installed on sda1, shouldn't
the root entry above "(hd1,0)" instead be (hd0,1) ?

I assume you mean (hd0,0) instead of (hd0,1), is that true? :)

But that's a good question, TeXtonyx, because it reveals one the most confusing aspects of Grub for most people, because nowhere in the official Grub manual does it explicitly explain the difference between Grub on start up vs. Grub when you are in Linux. Basically, think of it this way: the Grub on start up is not the same as the Grub that you use in Ubuntu when it comes to how the drives are ordered. 

When you use Grub in Ubuntu, Grub works through the kernel, so Grub's drives are ordered the same as Ubuntu orders them in the /dev directory; the drives are generally ordered as IDE, SATA, USB, etc:
```
(hd0) = sda
(hd1) = sdb
(hd2) = sdc
...etc.
```
But on start up, Grub must use BIOS to access the drives, so Grub on start up sees the order of drives as the *same as the BIOS boot order* (and you can change the BIOS boot order); that means the drive order Grub sees on start up has nothing to do with how the drives are ordered in /dev once you boot into Ubuntu. Therefore, on start up, Grub sees:
```
(hd0) = 1st boot drive (the drive you boot on start up)
(hd1) = 2nd boot drive
(hd2) = 3rd boot drive
...etc.
```
So to answer your question, if mooncaptain boots from his Ubuntu sdb drive on start up, then sdb is (hd0) or the first boot drive, and since he doesn't have any other drives, the Windows sda drive would be (hd1) or the 2nd drive in the BIOS boot order. 

So bottom line, when you run Grub commands in Ubuntu, the first case above applies, but when you boot Grub on start up, the second case applies; and since Grub uses the menu.lst on start up, the second case applies when it comes to determining the correct OS entries in the menu.lst. :)

---

### Post by mooncaptain on 2008-11-17
> **caljohnsmith said:**
> OK, to boot Windows from Grub, how about first opening a terminal (Applications > Accessories > Terminal), and do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the very bottom add:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Then reboot, make sure your BIOS is set to boot the Ubuntu drive, and then let me know how it goes when booting Windows from the Grub menu. If you have any problems, please explain in detail what happens when you boot Windows from the Grub menu, and we can work from there. :)

So this is what happened:

I started out in Ubuntu. The BIOS is set to boot on the Ubuntu disk. I did a reboot after applying the above changes and I rebooted right back to Ubuntu. I tried it again tapping the esc key and got the grub menu, I selected XP and then I booted into XP. Very Good!

I guess it would be useful if I could get the system to pause in the grub menu or even wait there until I make a choice. This is especially true since the BIOS responds to the esc key too in the sequence of events during boot up and sometimes I will trigger its menu.

Definitely making progress.

Going back to work now...

---

### Post by TeXtonyx on 2008-11-17
First of all I'm glad its working and as they say the proof of the
pudding is in the eating. 

"I assume you mean (hd0,0) instead of (hd0,1), is that true?"

Yes. I know why I got confused, I copied and pasted this from my
menu.lst where I boot to XP on first drive, where I select Ubuntu
from boot.ini and then it provides me a choice to boot Vista which
is on the second drive. I just booted up that machine and my
menu.lst doesn't even use "map" ! I thought that it did.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Original Windows XP Professional
root        (hd0,0)
savedefault
chainloader    +1

title        Vista 
root        (hd1,0)
makeactive
savedefault
chainloader    +1 

[This is menu.lst for Ubuntu on the first drive.]

------------------------------------------

caljohnsmith: I can't figure out why "map" is required for 
mooncaptain and why I don't have any mapping going on? Thanks 
for your previous detailed explanation which I recorded.

------------------------------------------

mooncaptain: do you have the timeout set to a few seconds, or 0?

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

---

### Post by caljohnsmith on 2008-11-17
> **TeXtonyx said:**
> 
caljohnsmith: I can't figure out why "map" is required for 
mooncaptain and why I don't have any mapping going on? Thanks 
for your previous detailed explanation which I recorded.

Your XP Grub entry uses (hd0,0), so fortunately it doesn't need any mapping since it is all ready on (hd0) or the first boot drive, which is where XP insists on being if you want to boot it. But your Vista uses (hd1,0), so normally that would require the mapping; but if you boot Vista without the mapping, then I believe what happens is Vista will just once give you the "hardware changes have been detected" type warning while it adjusts itself to booting from (hd1) or the second boot drive. But that means then if you change your BIOS to boot your Vista drive directly on start up so that it is now (hd0), Vista will complain again and give you the same warning if I'm not mistaken. So even though Vista is smarter than XP and can compensate in order to boot off of (hd1), it is better to just use Grub's mapping technique so that Vista still thinks it is on (hd0) and doesn't change anything. 

So the bottom line is, if Windows is on the first boot drive or (hd0), no mapping is necessary, but if it is on some other drive, then ideally mapping should always be used. :)

---

### Post by mooncaptain on 2008-11-17
Regarding timeout: the menu.lst file has a timeout 3 entry but the problem was the hiddenmenu command, which I commented out, after that all is good.

Thanks for everybody's help.

---

### Post by TeXtonyx on 2008-11-17
> **mooncaptain said:**
> Regarding timeout: the menu.lst file has a timeout 3 entry but the problem was the hiddenmenu command, which I commented out, after that all is good.

Thanks for everybody's help.

I think that installing the new hard drive so that both drives/OS's
could be booted was the hard part. After that Bootpart is a 3 minute
setup and it didn't very long in this case to find the right grub entry.

I get the message, Windows has found new hardware (after a partition has
been created for Ubuntu) and needs to be restarted, with both XP which is
installed on a first drive, and/or Vista, which is installed on a second drive.
[http://forums.majorgeeks.com/showthread.php?t=108021](http://forums.majorgeeks.com/showthread.php?t=108021)

---

