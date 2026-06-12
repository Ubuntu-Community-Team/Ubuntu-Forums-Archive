---
title: "[SOLVED] Newbie needs help dual booting Ubuntu and XP"
date: 2008-10-01
forum: General Help
---

### Post by Padre Joshua on 2008-10-01
I have been researching this topic for days, but I just cannot figure out how to accomplish what I want to do.

Here's the deal:
I have been running Windows XP Home SP3 for some time now.  I have two HDDs, and last week I decided to install Ubuntu on one of them to test out the new OS.  I downloaded the Hardy Heron 8.04 ISO file, burned it to CD, backed up my data, and then removed the XP HDD from the computer.*   I of course fixed the jumper on the remaining drive, popped the cd in the drive, and installed with no problem.

I decided that I really like Ubuntu, so I put the Windows HDD back in the computer as the master, with the Ubuntu HDD as the slave.  So far, so good.  I have been able to boot into the OS of my choice by changing the boot order in the BIOS.

Now I want to be able to configure and run GRUB so that XP is my default OS, and so that if I want to use Ubuntu I can select it from the menu.  I want to be able to boot straight into XP on startup without having to do or select anything.

Another option I find very attractive (more so, actually) is configuring a boot CD or USB drive that will boot the computer into Ubuntu.

Thanks in advance.  I really appreciate the help.  If this has already been answered, would you be so kind as to point me in the right direction?

--Joshua

_________________
*The reason I did this is that the last time I tried installing a new OS with both drives still attached, I lost everything on both drives.  Twist of fate? User issues? The world may never know.

---

### Post by Forbees on 2008-10-01
i'm pretty sure grub is only for dual booting on a single drive

as for booting linux off a flashdrive it can be done

one of my friends did it

you need to like copy all files from the ubutnu ISO to the flash drive and make sure the computer your going onto run off the flashdrive has the ability to USB boot

only problem is if this worked (since i'm only guessing on how to do it)

you can't really save anything unless you mod it like crazy >,<

---

### Post by virtuallinux on 2008-10-01
The easiest way to make grub work will probably be to reinstall it.  [_This_]("http://ubuntuforums.org/archive/index.php/t-24113.html") thread explains several ways to do that; I prefer the one in the fifth post down.

_[This]("http://www.linuxquestions.org/questions/ubuntu-63/how-to-make-xp-boot-as-default-os-in-winxp-ubuntu-dual-boot-system-481631/")_ thread explains how to edit the boot menu order.

---

### Post by kokkus on 2008-10-01
In Ubuntu, install QGRUBEditor for add/remove.
GO to system tools to run it, there you can change default os, how grub runs, and costumize the grub list.
Like I have Ubuntu as do.1, winxp as no.2 and ubuntu recovery mode as no.3.
You can also use the program to turn off the grub so u have to click escape to change OS so it doesn't take that much time.
Btw, I too have windows on one hdd and ubuntu on another.

---

### Post by caljohnsmith on 2008-10-01
If you want help making a USB drive to boot your Ubuntu, I can help you do that, but it really isn't necessary; just change your BIOS to always boot your Ubuntu drive, we can add an entry to your Grub menu to boot Windows, and then we can make Windows the default OS to boot unless you choose Ubuntu. Does that sound like what you want? 

If that sounds good, then open up a terminal in Ubuntu (applications > accessories > terminal), and do:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
Then find the line in the file that says:
```
### BEGIN AUTOMAGIC KERNELS LIST

```
And put the following before that line:
```
title Windows XP
rootnoverify (hd1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```
Also, at the top of your menu.lst file, make sure the "default" line looks like:
```
default 0
```
Make sure the "hiddenmenu" does not have a pound sign # in front of it:
```
hiddenmenu
```
And lastly, make the timeout line:
```
timeout 3
```
Save, reboot, and you should automatically boot Windows unless you press ESC at start up to get the Grub menu. If you run into problems, please post: 
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
Let me know how it goes. :)

---

### Post by Fc1032 on 2008-10-01
hello!!

I recently asked a similar question to you, but I only had one hard drive to use. I couldn't find my question but I can give some links that I used.

I used this to learn how to partition my drives (if you need the info)
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")

For the XP information, same site
[URL="http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm"]http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm
[/URL]

Then to set up the master OS as windows, you download '**startup manager**' from the programs. From there open System> Administration> Startupmanager, you can configure the boot options so that that windows is the master and ubuntu the slave. (Credit of this information goes to the person who answered my question, sorry i couldn't find you name...) 

Hope that helped! It helped me!

---

### Post by WWSmith36 on 2008-10-01
If you would have installed ubuntu with you winXP drive attached, it would discovery you winXP and automatically put an entry in menu.lst.

Don´t worry I did the same thing when I installed Ubuntu.  I wanted to make sure my winXP drive would not be touched.  My work around was this

In you bios choose the ubuntu drive to be the primary.  Then you just have to update your /boot/grub/menu.lst file.

Open a terminal with the menu Applications-> Accessories-> Terminal and type

```
gksudo gedit /boot/grub/menu.lst
```

You will have to add some remapping to fool windows to think that it is the primary drive.  Assuming that you had standard windows install, it will look something like this.

title		Microsoft Window XP
		rootnoverify (hd1)
		map (hd0) (hd1)
		map (hd1) (hd0)
		chainloader +1

If you put this add the end of the file, you should be able to boot to windows now.  If this works you can change make an addition edit to make it the default OS that´s loaded.  Look at the following line

default 0

You will probably have to change that to 3.  If this works, it will also have to be modified after kernel updates, since you menu.lst is modified.

Hope this help

---

### Post by TeXtonyx on 2008-10-01
You can add line(s) to the boot.ini  to boot from XP first as usual.
C:\ubuntu.bin="UbuntuA"
C:\UbuntuB.bin="UbuntuB"
I had XP on first drive with Ubuntu installed on that partition and 2nd drive all Ubuntu.
Free Bootpart copies the first 512 bytes of the Ubuntu boot partition and writes to boot.ini
and makes the Ubunt*.bin file; run Bootpart from C:\.
To do this reinstall grub to the Ubuntu boot partition not MBR. The advantage of this is
that XP is always available even if you uninstall Ubuntu. If the XP drive goes down, then
one can use Super Grub disk to boot the grub installed to the Ubuntu boot partition.
Later I installed Vista to the second drive and kept Ubuntu on the XP second partition.
Since Vista has that new bootloader it doesn't fit into the boot.ini scheme. So now the XP 
boot.ini runs XP by default and the Ubuntu .bin entry points at both Ubuntu and Vista. So 
that if you lose your first drive (XP) one can still boot Vista by changing to 2nd drive in Bios

[http://www.swerdna.net.au/linhowtoboot1.html](http://www.swerdna.net.au/linhowtoboot1.html)  This is an expert's preference. 
This was written for Suse, but just substitute Ubuntu for OpenSuse (.bin).

---

### Post by caljohnsmith on 2008-10-02
> **TeXtonyx said:**
> You can add line(s) to the boot.ini  to boot from XP first as usual.
C:\ubuntu.bin="UbuntuA"
C:\UbuntuB.bin="UbuntuB"
I had XP on first drive with Ubuntu installed on that partition and 2nd drive all Ubuntu.
Free Bootpart copies the first 512 bytes of the Ubuntu boot partition and writes to boot.ini
and makes the Ubunt*.bin file; run Bootpart from C:\.
To do this reinstall grub to the Ubuntu boot partition not MBR. The advantage of this is
that XP is always available even if you uninstall Ubuntu. If the XP drive goes down, then
one can use Super Grub disk to boot the grub installed to the Ubuntu boot partition.
I agree that if Ubuntu is on the same drive as Windows, it can be an advantage to add the Grub boot loader to the Windows boot.ini file so that if Ubuntu goes down, you can still easily boot Windows. But Padre Joshua did say that Ubuntu is on an entirely separate HDD, so I think a better solution in his case is to keep the Windows drive untouched (as he did when he installed Ubuntu), make the Ubuntu drive the first to boot on start up, and then he can simply add an entry in his Grub menu to boot Windows. That has the same advantage (as with your setup) that he will still be able to boot his Windows drive if anything happens to his Ubuntu drive. Does this sound reasonable or would you disagree? :)

---

### Post by TeXtonyx on 2008-10-02
"But Padre Joshua did say that Ubuntu is on an entirely separate HDD, so I think a better solution in his case is to keep the Windows drive untouched (as he did when he installed Ubuntu), make the Ubuntu drive the first to boot on start up, and then he can simply add an entry in his Grub menu to boot Windows. That has the same advantage (as with your setup) that he will still be able to boot his Windows drive if anything happens to his Ubuntu drive. Does this sound reasonable or would you disagree?"

TeX: It is reasonable if you know that the situation will remain static and that there is no
need to build in some flexibility. PJ kept his Windows drive untouched because he was 
afraid of mistakenly overwriting the partition. There is nothing to fear from writing a
512 byte file to Windows, the file is already named so it can't overwrite some key file. 
Initially it takes about 2 minutes to download Bootpart, bootpart.exe = 44,544
and after one grasps the very intuitive report it takes about 30 seconds to write copy
the 512 bytes from the Linux boot partition and write to boot.ini

I mention that because PJ said he wanted to edit menu.lst so that XP was the default.
It takes time to type gksudo gedit /boot/grub/menu.lst and then edit it so XP is default
and if you test it and you made a mistake, you have to type it again because the up arrow
key doesn't retain the previous keystrokes. Now lets suppose you have to actually edit
menu.lst. I saw an example earlier of a proposed entry:
title Microsoft Window XP
rootnoverify (hd1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
TeX: That is not at all intuitive to a Linux newcomer. I see no reason to add any degree 
of steepness to the learning curve that isn't necessary. Let him learn grub when the 
need arises. C:\UbuntuB.bin="UbuntuB" seems much easier to understand to me.
I feel that it is more elegant, but I've agreed that in a static situation, which method 
is used is not significant and/while I don't give the, windows is untouched ploy, much 
credence. Writing to the Windows MBR or resizing the Windows partition has risk,
but not copying a 512 byte .bin file to Windows. 

It takes about 10 seconds longer to install to boot partition rather than the MBR using
the live cd, so not a factor. Now to flexibility and Windows is less compromising than
Linux. One can write Ubuntu to the MBR as PJ did or to a boot partition. Windows
wants to go to the MBR. So suppose he wants to add Ubuntu to his XP drive. You've
agreed that on the first drive, grub is better off in the first partition. So if he makes that
choice it is more consistent and organized to have started with the Ubunt*.bin method.

Suppose  the more likely event where he chooses to add Vista to his second hard drive.
Vista will overwrite the MBR and grub. So now you have to reinstall grub, and if you
reinstall it to the MBR, if Vista doesn't start, you don't know whether grub is at fault
or Vista. Thus, if one originally installed grub to the boot partition, one doesn't have
to reinstall grub at all, because grub was not in the MBR in order to be overwritten.
If Vista doesn't start with grub in the boot partition, one doesn't have to wonder if the
problem is Vista or grub you know its Vista. This way Vista will boot all on its own
from the MBR if UbuntuB is damaged and again Ubuntu is bootable by SuperGrub. 

In my case I did install Vista. Then I did reinstall grub to the boot partition and it
picked up on the Vista bootloader. When I ran bootpart, it captured the Ubuntu grub
and with it the option to boot Vista all from XP. I like the idea of all OS under control
of one bootloader, boot.ini, and because doing it this way doesn't sacrifice any OS if
any one part breaks down. If something gets corrupted on the partition you've written
the controlling grub entries from and into the MBR, you'll lose both Windows OS
at least for awhile. That doesn't happen with my method. People newly coming from
Windows would find such an event scary because they want to keep Windows as a
crutch for at least a year and they have plenty to learn. I don't see why learning arcane
grub configuration and troubleshooting has to have a priority and be introduced early on.  
The boot sector method is the most likely method to delay having to learn grub
and I think that is the best way for the new user to proceed; let them do more fun stuff
first like configuring Nvidia two monitor video cards :) My philosophy is to obtain the
best Windows/Linux result, 60% of Ubuntu users dual boot, while perhaps your 
philosophy emphasizes teaching the Ubuntu way of doing things as the first priority.
Just to recap, in this situation if nothing changes, either MBR or boot partition works,
but I think newcomers like to dabble by adding OS's so flexibility is a larger concern. 
I mean safest, clearest, most flexible method, not that grub is not capable of doing it.
[http://www.swerdna.net.au/linhowtoboot.html](http://www.swerdna.net.au/linhowtoboot.html)
[Yast will often default to booting from the root or boot partition 
rather than from the MBR but that's for experts only ...]
TeX: From his other howto, it doesn't seem that hard to me.

[http://linux.ioerror.us/2006/01/where-should-you-install-grub/](http://linux.ioerror.us/2006/01/where-should-you-install-grub/)
If you intend to dual-boot Windows, then you should avoid installing 
GRUB to the MBR. The reason for this is that Windows occasionally 
overwrites the MBR, for instance, when you reinstall it, and that 
could be quite often. When that happens, your Linux system will seem 
to disappear as your system starts booting directly into Windows, 
bypassing the boot menu altogether. To avoid this, install GRUB to 
the boot sector of the active partition instead.

TeX: One can dual boot on both drives. If you have only Linux on 
the second drive now, you can put a 512 byte piece of that Linux
on the first drive now and allow for the future good practice of
not having grub in the MBR if you decide to later dual boot Windows.
That is why I said it isn't yet crucial to do this, but a good idea.


[http://www.terabyteunlimited.com/kb/article.php?id=279](http://www.terabyteunlimited.com/kb/article.php?id=279)
3. The consequences of allowing the Ubuntu installer to install 
Grub to the MBR will be that both the MBR and EMBR on HD0 will be 
overwritten. In all cases, this will require that the Grub boot 
loader be reinstalled to the Ubuntu root partition, and will also 
require that BootIt NG itself be reinstalled. In addition, if your 
BootIt NG installation was not limiting primaries, you may lose 
some partitions on HD0. If this happens, the KB article mentioned 
in item 2 above should be followed to recover as best possible.

TeX: BootIt NG is a third party bootloader. It also allows a user
to overcome the 4 primary partitions to a drive limitation. And
someday PJ may need that. It doesn't hurt to allow for that option
now, by installing to the boot partition, rather than having to 
change it later. The choice maximizes your options which is why I
have called it more flexible. It's not like their is any improved
performance for Ubuntu by installing to the MBR rather than boot.
One would have to know that PJ is never going to change things in
order for the MBR and boot partition methods to have equal potential.

---

### Post by Padre Joshua on 2008-10-02
First, I want to say "Thank You" to everyone who posted.

**TeXtonyx**, I didn't read your post in time to use that method, but I have printed the thread off and will keep it in my notebook for future reference.

**WWSmith36** and **caljohnsmith**, I tried your idea first.

At first, I put
> title Windows XP
rootnoverify (hd1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
immediately before the
> ### BEGIN AUTOMAGIC KERNELS LIST
line in menu.lst.  This did not work; Grub got confused and kept repeating itself until I hit esc and chose Ubuntu on the menu.

Next, I moved the above to the end of the document.  This was better, except that when Grub handed off to Windows, the Windows Recovery ran.  No good.

I finally found on another thread that I would need to change the entry to something else.  I'm in Windows at the moment, so I can't access the file and can't remember what it said.  I'll edit this post later and quote it.  The gist of it was that I had to specify hd1,1 and add a couple extra commands to make it work.

Thanks again for the help and advice. :D

ETA:
Here's the quotation from menu.lst as promised:
> ### END DEBIAN AUTOMAGIC KERNELS LIST

title  Windows XP
rootnoverify (hd1,1)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by TeXtonyx on 2008-10-02
I'm glad you got it working. Getting everything working with Ubuntu actually turns into
fun if you like Star Trek and crossword puzzles :) The position I take isn't very popular 
because people learned to do it the MBR way. But the boot partition method for grub
takes 15 minutes, and that's counting 2 minutes to download Bootpart and 3 minutes 
for booting up XP in order to run Bootpart. I'll bet you spent at least an hour on this. 
I've seen other people spend hours fixing the situation by having to learn grub 
mechanics. Grub needing to be repaired doesn't happen all the time of course.

It's not so intuitive because in Linux hd0 means the first hard drive and hd1 is the 2nd
hard drive. hd1,1 means the second partition of the second hard drive. It strikes me as
odd that both your partitions for XP or Ubuntu aren't a 0 but one is a 1. Hmm, I'm glad 
I don't give grub advice. sudo fdisk -l is very handy for these situations.  Hasta la Vista.

---

### Post by Padre Joshua on 2008-10-03
**TeXtonyx**:

Thanks again.  I actually don't like crosswords, but I do like Star Trek.  I grew up using MSDOS, so I am actually more comfortable with a text-based interface like the Ubuntu Terminal.  Once I get the codes memorized, I'll be good to go.

I'm not sure what the deal is about Windows being in hd1,1 instead of 1,0.  It came from the store like that, so I would assume it's a factory install.  1,0 is the recovery.  Windows sees the recovery partition as D: and the main partition as C:, so I assumed that C:=1,0 and D:=1,1.  Oh, well.  All's well that ends well.

Thanks again for your help.
--Joshua

---

### Post by caljohnsmith on 2008-10-03
> **Padre Joshua said:**
> 
**WWSmith36** and **caljohnsmith**, I tried your idea first.

At first, I put

immediately before the
> ### BEGIN AUTOMAGIC KERNELS LIST 
line in menu.lst.  This did not work; Grub got confused and kept repeating itself until I hit esc and chose Ubuntu on the menu.

Next, I moved the above to the end of the document.  This was better, except that when Grub handed off to Windows, the Windows Recovery ran.  No good.

If you set your BIOS to boot directly from your Windows HDD now, does it still boot correctly? From the behavior you describe above when trying to boot the Windows HDD with Grub (using the entry that WWSmith36 and I gave), it makes me suspicious of whether you can boot your Windows HDD directly or not. Your solution to boot the Windows partition (hd1,1) instead of the HDD (hd1) will certainly work from Grub, but in case anything happens to your Ubuntu drive, I would assume you would want to be able to boot your Windows drive with no problem. Also, since your Windows recovery partition (hd1,0) was booted when you had Grub boot the drive with (hd1), that could be because the recovery partition was marked active instead of the Windows partition (hd1,1). Anyway, in case it matters to you whether your Windows HDD is bootable or not, I would check it if I were you. If you run into problems let us know. :)

---

### Post by TeXtonyx on 2008-10-03
"I'm not sure what the deal is about Windows being in hd1,1 instead of 1,0. It came from the store like that, so I would assume it's a factory install. 1,0 is the recovery. Windows sees the recovery partition as D: and the main partition as C:, so I assumed that C:=1,0 
and D:=1,1. Oh, well. All's well that ends well."

Yes, I got this book about Dos 5.0 which had a chapter on batch files and another on
Assembly programming! I like Bash. I think when computers are shipped with recovery 
partitions they are usually at the front of the drive. So 1,0 is the first partition as you 
said and it could well be the recovery. That makes the next partition, the second
partition 1,1 which is your C:\ Windows drive. Usually the recovery partition is
hidden so doesn't have a drive letter assigned to it. That is why sudo fdisk -l can be
handy because it may well report a partition before your much larger NTFS partition.
Then you can tell that grub should use 1,1 (2nd partition) if that's the case. 
I'm glad it's solved, now you can get going like sixty :) See you later, alligator.

---

