---
title: "after installation: hangs on grub"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by mvoepo on 2009-11-02
Hi All,

I have just installed ubuntu 9.10 using the grub.
After finishing installation, the system reboots but it hangs in the grub
**sh: grub>**

I checking on my windows, and i am missing **C:\ubuntu\disks\boot\grub\menu.lst** file

when in grub editor i did

[B]ls
search -f /boot/grub/grub.cfg -> result loop0
configfile (loop0)/boot/grub/grub.cfg[/B]
i get a blank screen, and there the **sh: grub >** comes back

anyone have a solution

using win vista x64

thanks in advance

---

### Post by jjcv on 2009-11-02
Was this a fresh install.  If so then you would now be using grub 2 so things are in a different place.

Cannot help much more but do a search on **grub** in these forums should find you some help.

---

### Post by mvoepo on 2009-11-02
Yes, it was a fresh install.

How do i install grub2 on wubi then ?

---

### Post by lildevild on 2009-11-02
I'm having the same problem on a Windows 7 x64 install using wubi.  After reboot I get the grub prompt.  Any answers to this problem yet?

---

### Post by desiindc on 2009-11-02
> **lildevild said:**
> I'm having the same problem on a Windows 7 x64 install using wubi.  After reboot I get the grub prompt.  Any answers to this problem yet?

I am seeing a similar issue too on XP with 32bit ISO. After install system reboots and stops at grub shell prompt. Pressing insert rapidly did not show any error message. This was for a reinstall of wubi. The previous installation did not have any problems.

EDIT: One issue I found is that currently I have only one drive F: on windows. But Wubi creates an entry 'C:\wubildr.mbr="Ubuntu"' in F:\boot.ini though all it really is in F. Bug? When I change it to F:\wubildr.mbr="Ubuntu" I get disk failure message when booting. Any suggestions?

---

### Post by melgrim on 2009-11-02
It seems I'm stuck in the same place :(
By the way, I'm also using vista x64.

I installed xubuntu 9.10 the day it was released to test it and everything worked the way it was supposed to.
Now I have no idea if this is a problem only with ubuntu or if it was the xubuntu install I made previously that messed things up :confused:

I guess I'll just wait and see if some solution comes up, if not, I'll give xubuntu another try. :|

---

### Post by kamlesh30rao on 2009-11-02
Facing same problem.  I am using Windows 7 64-Bit.  On my Hard Drive, I created 180GB NTFS Free Partition.

After inserting the Ubuntu 9.10 (i386) Bootable CD, I choosed "Install inside Windows" options.  The setup wizard copied some files and rebooted.

After reboot, I choosed Ubuntu option from the menu.  The setup continued with some more automated copying/installing stuff. It again asked for reboot.

After reboot, I still get Win7 and Ubuntu options in boot menu.  But when I choose Ubuntu, it goes to a Command Line prompt.

Any of you guys solved this problem?

---

### Post by BeStanly on 2009-11-03
Hi all!
this is my first aport to this site. i hope to do it well.
The same problem happen to me. The problem is (aparently) is wubi Because this:
I had the same problem when i used the iso image wubi.
I downloaded the .iso image from the official site and wubi 9.10 ([wubi-installer.org/]("http://wubi-installer.org/")). Then I used (in my case) daemon tools for the image only for putting it in the virtual device but i didnt installed. then i used wubi and it reconized the image from the device. next wubi did the instalation normally AND THAT IS IT!!
if you do it you will notice that after you reboot, the installation will be in a elegant grafic user interface. thanks!!! i hope that this fix your problem up.

ps: My native language is spanish.excuse me if i did grammar mistakes;)

---

### Post by melgrim on 2009-11-03
Not solved yet but I'm already using Ubuntu 9.10. :-k

It seams that the problem only occurs in a 64 bit install. I tried the 32 bit iso and everything worked the way it was supposed to.

Tried what BeStanly suggested but with the 64 bit install the problem remains.

---

### Post by desiindc on 2009-11-03
> **melgrim said:**
> Not solved yet but I'm already using Ubuntu 9.10. :-k

It seams that the problem only occurs in a 64 bit install. I tried the 32 bit iso and everything worked the way it was supposed to.

Tried what BeStanly suggested but with the 64 bit install the problem remains.I see the problem with the 32bit ISO. (that was downloaded separately and placed in the same folder as wubi)

---

### Post by soma123 on 2009-11-03
I  am also facing the same problem. It seems it is problem with wubi 9.10. Is it a bug? Anybody any idea when it is going to get fixed.

As of now I installed wubi 9.04 and then upgraded it to 9.10. It is working fine except some I/O errors while restart/shutdown

---

### Post by mozkill on 2009-11-04
I have Windows7x64 .  I installed Wubi.exe v9.10.   Everything went ok.  I get the boot loader error on system start.  COmplains about hd0, then it waits about 30 seconds until it finally tries hd1 which works .  It boots and everything is great.  I think I am going to use suns box though intead... sounds easier to me.  I hate it when things mess with my boot sector (or they seem to be).

---

### Post by melgrim on 2009-11-06
I've been kind of away from the forum since I managed to install a working Ubuntu 9.10 but since today that changed I wonder if a solution to this problem has been found yet.

Today I installed the available updates and I noticed at least one of them was for GRUB. Next reboot and it's not working :mad:

Seems like the day for me to go back to 9.04 is getting near ](*,)

---

### Post by kaelonlloyd on 2009-11-06
> **melgrim said:**
> I've been kind of away from the forum since I managed to install a working Ubuntu 9.10 but since today that changed I wonder if a solution to this problem has been found yet.

Today I installed the available updates and I noticed at least one of them was for GRUB. Next reboot and it's not working :mad:

Seems like the day for me to go back to 9.04 is getting near ](*,)

I've got the same problem as you, damn update broked my linux :(

---

### Post by devi59 on 2009-11-06
> **mvoepo said:**
> Hi All,

...reboots but it hangs in the grub
**sh: grub>**

I checking on my windows, and i am missing **C:\ubuntu\disks\boot\grub\menu.lst** file...



I acutally have the same problem and I started a thread but I tried copying all the files from inside the .disk files using the LiveCD and it didn't help. Mine now trys to boot if I manually do the linux and initrd commands followed by boot but then I get a kernel panic at the end saying none of the partitions can be mounted properly and it hangs with VPS or something like that.

---

### Post by OuldeFauder on 2009-11-07
> **devi59 said:**
> I have the same problem and I started a thread but I tried copying all the files from inside the .disk files using the LiveCD and it didn't help. Mine now trys to boot if I manually do the linux and initrd commands followed by boot but then I get a kernel panic at the end saying none of the partitions can be mounted properly and it hangs with VPS or something like that.
I have the same problem using 9.10 server and it is on a clean install. No windows. During the install before writing Grub to disk I was informed that Vista was on the drive. Is not and never has been. Weird.

---

### Post by reynardine on 2009-11-11
> I have just installed ubuntu 9.10 using the grub.
After finishing installation, the system reboots but it hangs in the grub
sh: grub>

I had this same problem - after several unproductive days trying to get Ubuntu 9.10 to install with Wubi I gave up and installed Kubuntu 9.10 instead - it worked first time. Not tried Xubuntu yet - you could try installing Xubuntu and then installing the gnome desktop. From all the comments I've seen lately there seems to be a serious problem with the Ubuntu wubi install process.

---

### Post by melgrim on 2009-11-11
> **reynardine said:**
> I had this same problem - after several unproductive days trying to get Ubuntu 9.10 to install with Wubi I gave up and installed Kubuntu 9.10 instead - it worked first time. Not tried Xubuntu yet - you could try installing Xubuntu and then installing the gnome desktop. From all the comments I've seen lately there seems to be a serious problem with the Ubuntu wubi install process.

I thought about doing this but I fear updates will ruin it like they did with my 32 bit install.

By now, I just don't have the time to risk it. I liked 9.04 and for now I'm back to it.

---

### Post by Larry_G on 2009-11-14
Same problem with fresh 9.04 install!!  Here’s my experience from a first time installer that’s not a total idiot about computers, been writing software and installing IBM mid-range computers for 20 years but mostly just “use” PC’s.
   
  My first attempt at loading Ubuntu hasn’t been very encouraging.  Don’t care for Windows at all but if this is how things go in Ubuntu land, I’ll live with Windows or switch to Mac.
   
  A few weeks ago I downloaded the .iso file and burnt the CD for 9.04 and kept having problems when the computer would be in the middle of booting from the CD.  Decided I would wait until a weekend day and try the online install using my FIOS connection.
   
  This morning I went to the “Download Ubuntu Installer for Windows” page at [http://www.ubuntu.com/getubuntu/download-wubi](http://www.ubuntu.com/getubuntu/download-wubi) and noticed the new version was available, cool…figured everything would be the latest.  Clicked on the “Begin Download”, and because I’m using Firefox it saved to disk and then I clicked on it.  Really expected it to download from the Internet as the documentation on the website said but instead I got a pop-up window saying there’s an error because I don’t have a disk in my F: drive, which is the CD/DVD.  Well wait a minute, I thought this was the download install for Windows???  So I tried to get the pop-up warning to go away and that won’t happen, “Cancel” doesn’t work, clicking on the “X” in the upper right corner of the box doesn’t work and neither did trying to end it immediately from the Windows Process Explorer, it just kept duplicating itself into a new occurrence like a bad virus does.  Now I’m starting to get worried.  Am I really sure I want to try a new operating system when even a little installer is this whacked????  
   
  But I decided to give it a shot and figured installing from the 9.04 CD I had burned earlier would be acceptable and then would upgrade later if I liked the OS.  Put the CD in the drive and it installed and then said it had finished, would reboot and I should select the Ubuntu option.  When the options came up I selected Ubuntu and it went through the finalizing of the install and unpacking of files and then rebooted again.  Again I selected Ubuntu, which is the 2nd option and not the first as I’ve read in other documentation) and all it does is stop at the “Grub>” prompt and leaves me hanging their.  Then I come to this site and see all of these posts about the same thing.  Tried an install of Linux several years ago and had lots of problems and figured I should wait until the kinks got ironed out and starting to feel they aren’t gone yet.  I know they won’t all every go away, after all they are computers, but can’t we at least get to a point where there might be some clue or hint of the problem, maybe even write out a simple text file or display it on the screen instead of just showing “Grub>”?  
   
  Is there a solution to this or should I just walk away as before and come back in a couple more years?  Trying to get away from Windows and don’t want to give up so quickly but also look at my computer as something for me to use and really not the kind of person that wants to be messing with it all the time to keep it working as that’s what I do at work all day and is also why I’m trying to get away from Microsoft in the first place.

---

### Post by LuisPT on 2009-11-16
**Well you can boot into Ubuntu following the steps below.**

But first, my hard disk configuration is: one disk with 3 partitions:
- 1st one (sda1): is laptop recover data NTFS (came from factory and it's hidden)
- 2nd one (sda2): is where I have Windows (Vista) NTFS installation and from where I installed Ubuntu inside using WUBI.
- 3rd one (sda3): just a data backup NTFS partition

[COLOR="Navy"]To boot up Ubuntu, just restart computer and choose "Ubuntu" at windows boot menu. When it drops to prompt "sh:grub>" enter the following 4 (four) commands (change it according to your hard disk configuration):[/COLOR]

> [B]set root=(hd0,2)
linux (loop0)/boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd (loop0)/boot/initrd.img-2.6.31-14-generic
boot[/B]

[I][U]Remember:
1. that you can press TAB key after "(loop0)" and "loop=" to get completion help/guidance.
2. at prompt "sh:grub>" you can type the command 'ls' to list the partitions.
3. (hd0,1) equals to /dev/sda1, (hd0,2) equals to /dev/sda2, (hd0,3) equals to /dev/sda3, ... [/U][/I]


**You should now be able to boot to Ubuntu.** :p


Once inside Ubuntu, open a console and try to resolve the grub/wubi problem with the following commands (this part I can't confirm that will work):

sudo update-grub
sudo update-grub2
sudo grub-install /dev/sda
sudo grub-install /dev/sda2  


I hope this will help you guys.

Regards.

---

### Post by 5of0 on 2009-11-18
LuisPT, thanks!  Your instructions got my 9.10 Wubi install to boot again.  However, the grub updating didn't solve the problem - a reboot still falls into the grub shell and requires the manual boot entry.  Any ideas?

---

### Post by LuisPT on 2009-11-21
> **5of0 said:**
> LuisPT, thanks!  Your instructions got my 9.10 Wubi install to boot again.  However, the grub updating didn't solve the problem - a reboot still falls into the grub shell and requires the manual boot entry.  Any ideas?

I'm also trying to figure out to fix the grub.

I've being reading close the bug reported in [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/477104](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/477104), and it seems that problems points to fact that grub2 for some reason loses the ability to read EXT4 loop device block.

**I supose wubi and grub2 developers should take this bug as extreme serious bug.**

Regards.
LuisPT

---

### Post by ncmncm on 2009-11-24
> **LuisPT said:**
> I'm also trying to figure out to fix the grub.

I've being reading close the bug reported in [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/477104](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/477104), and it seems that problems points to fact that grub2 for some reason loses the ability to read EXT4 loop device block.

**I supose wubi and grub2 developers should take this bug as extreme serious bug.**

Regards.
LuisPT

Is it possible to  replace grub2 with the old grub?

---

### Post by a_ch on 2009-11-25
I'm new to Ubuntu and all these grub/grub2 discussions confuse me alot. I just started to use and like Ubuntu, but after system update yesterday i've stuck with a black screen and sh:grub> and have no idea what to do... 

Looking forward to the solution!

---

### Post by Canaryguy on 2009-11-25
Hello,

I had the same problem with the installation of Ubuntu with wubi. Once I installed the updates I saw grub and the system couldn't lunch the graphical interface. But I did something that helped me.

1º Install Ubuntu inside Windows with wubi

2º Install all the updates for Ubuntu when they appear or do it yourself manually

3º After installing the updates when the system asks you to reboot don't do it. Go to the Terminal (Applications/Accessories/Terminal)

4º In the Terminal write: sudo update-grub2 (press enter and write your password if required)

5º Now restart

And that's all

That worked for me.

Good luck.

---

### Post by aschlosberg on 2009-11-25
> **LuisPT said:**
> Once inside Ubuntu, open a console and try to resolve the grub/wubi problem with the following commands (this part I can't confirm that will work):

sudo update-grub
sudo update-grub2
sudo grub-install /dev/sda
sudo grub-install /dev/sda2  


Thanks Luis! The manual grub booting worked perfectly. There are a few more steps involved in updating.

With sudo edit /etc/default/grub - if your GRUB menu isn't displaying then comment out the lines GRUB_HIDDEN_TIMEOUT and GRUB_HIDDEN_TIMEOUT_QUIET by adding a # to the beginning.

After this run sudo update-grub

With regards to LuisPT's post, depending on your hard drive setup you'll have to change (hd0,2) and sda2 to (hd0,X) and sdaX where X is appropriate to your system.

---

### Post by aschlosberg on 2009-11-25
Another point regarding /etc/default/grub

I have found that the easiest way to set the default kernel is to change GRUB_DEFAULT=0 to GRUB_DEFAULT=saved and then each time you boot it will default to the last choice.

---

### Post by Larry_G on 2009-11-27
No progress yet but still trying...

Tried the following steps where it said [COLOR=Navy]"When it drops to prompt "sh:grub>" enter the following 4 (four) commands (change it according to your hard disk configuration):" [/COLOR]and the commands listed don't exist within Grub, or at least what is loaded on my computer.  I have 1 hard drive on a Dell (actually 2 running mirrored) with 3 partitions as:
-1st one is Fat16 - Original from factory and shows 0xDE (EISA Configuration)
-2nd one is NTFS - This is the C: drive where XP is installed and where I installed .Ubuntu using WUBI.
-3rd one is NTFS - This is the D: backup drive from the factory.

Here's what I did and what happened by trying to follow the steps below where it specifies the 4 commands that can be run from the "sh:grub>" prompt.
  **[FONT=&quot]set root=(hd0,2)  ([/FONT]**Got an error that "set" wasn't a command.  Found that "root" was valid so entered the "root=(hd0,2)" portion and it accepted that.)
**[FONT=&quot]linux (loop0)/boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  [/FONT]****[FONT=&quot]([/FONT]**Got an error as "linux" also isn't a command and really couldn't see where I could strip off part of the command as I did with the "set root" potion.)

[B][COLOR=Red]So are the 4 commands listed below really valid or ???  Not really sure what to make of all this....
[/COLOR][/B] 
Thanks in advance, appreciate any help I can get as folks at work are waiting to see if I can get this up and running as they'd like to also move away from MS...

> **LuisPT said:**
> **Well you can boot into Ubuntu following the steps below.**

But first, my hard disk configuration is: one disk with 3 partitions:
- 1st one (sda1): is laptop recover data NTFS (came from factory and it's hidden)
- 2nd one (sda2): is where I have Windows (Vista) NTFS installation and from where I installed Ubuntu inside using WUBI.
- 3rd one (sda3): just a data backup NTFS partition

[COLOR=Navy]To boot up Ubuntu, just restart computer and choose "Ubuntu" at windows boot menu. When it drops to prompt "sh:grub>" enter the following 4 (four) commands (change it according to your hard disk configuration):[/COLOR]

  [B][FONT=&quot]set root=(hd0,2)
linux (loop0)/boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd (loop0)/boot/initrd.img-2.6.31-14-generic
boot[/FONT][/B]

[I][U]Remember:
1. that you can press TAB key after "(loop0)" and "loop=" to get completion help/guidance.
2. at prompt "sh:grub>" you can type the command 'ls' to list the partitions.
3. (hd0,1) equals to /dev/sda1, (hd0,2) equals to /dev/sda2, (hd0,3) equals to /dev/sda3, ... [/U][/I]


**You should now be able to boot to Ubuntu.** :p


Once inside Ubuntu, open a console and try to resolve the grub/wubi problem with the following commands (this part I can't confirm that will work):

sudo update-grub
sudo update-grub2
sudo grub-install /dev/sda
sudo grub-install /dev/sda2  


I hope this will help you guys.

Regards.

---

### Post by phillw on 2009-11-27
drs, the writer of most of the HowTo's for Grub, has a proposed solution for Wubi.

> **Re: sh:grub > desperation** 			
 			 			 		   		 		 		[SIZE=3][COLOR=DarkRed]WUBI Installs Only[/COLOR][/SIZE]

I tried wubi when it first came out a few years ago but am no longer familiar with exactly how it works. There were enough problems recently that I rearranged my laptop's partitions so I could once again install wubi. Once I got wubi installed, I experimented until I could boot from a grub prompt. 

This is how I am able to manually boot from the Grub 2 prompt *in wubi*. My Windows partition is on [COLOR=DarkRed]**sda1**[/COLOR], which would be fairly standard.

Lines starting with a # are explanatory only. Do not type them.

 	Quote:
 	 	 		 			 				# Add the ntfs module
**[COLOR=Navy]insmod ntfs[/COLOR]**
# Set root (normally would be sda1, or hd0,1  Change as necessary
[B][COLOR=Navy]set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk[/COLOR][/B]
# Yes, set root for a second time. I don't know why...
**[COLOR=Navy]set root=(loop0)[/COLOR]**
# Set the kernel. You can (and should) use Tab (twice) to complete entries such as the kernel when possible - type vml and then TAB twice and it will autocomplete to the point where there are two possibilities. Tab complete ensures the path/file names as typed exist. Additionally, if you suspect the new kernel is the problem, you might want to select an earlier one. vmlinuz.... should be a complete kernel entry such as "vmlinuz-2.6.31-15-generic-pae" *
**[COLOR=Navy]linux /boot/vmlinuz.... root=/dev/sda1  loop=/ubuntu/disks/root.disk ro[/COLOR]**
# Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
[COLOR=Navy]**initrd /boot/initrd/initrd.img... **[/COLOR]
[B]# Boot.
[COLOR=Navy]boot[/COLOR][/B] 			 		 	 	 


* If this line scrolls off the screen as you type it, due to its length: To make it easier type "linux root=/dev/sda1 /ubuntu/disks/root.disk ro" and *then cursor back before "root=" to type/tab in the kernel name*.


If you successfully boot, run "sudo update-grub". Also inspect your /etc/default/grub file, which contains menu timeout and default kernel selections and determine if there is a problem with the menu.
 		                   		  		  		 		 			 				__________________
				[GRUB2]("https://help.ubuntu.com/community/Grub2") : [G2-Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") [G2-Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
[G2-Tasks]("http://ubuntuforums.org/showthread.php?t=1302743") [DiskSpace]("http://help.ubuntu.com/community/RecoverLostDiskSpace")  
[Expand /]("http://ubuntuforums.org/showthread.php?t=1219270") [SUM]("http://ubuntuforums.org/showthread.php?t=818177") 			
 		 		  		  		 		 			 				 				* 					 						Last edited by drs305; 1 Hour Ago at 06:24 PM.* 			 		 	 	 We do need someone to try this out & report back if it works.

Please post back how you get on with it.

Regards,

Phill.

---

### Post by fishie on 2009-12-11
this works for me to get into ubuntu, but everytime i tried to restart i get the same problem...

---

### Post by fishie on 2010-02-19
anyone add anything else? this is annoying to have to do everytime turn on my netbook

---

### Post by meierfra. on 2010-02-19
This should take care of it:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

