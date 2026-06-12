---
title: "&quot;Install inside Windows&quot; - Stuck with GRUB Command Line Prompt"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by kamlesh30rao on 2009-11-03
I am using Windows 7 64-Bit.  On my Hard Drive, I created a new additional 180GB NTFS Partition.

After inserting the Ubuntu 9.10 (i386) Bootable CD, I choosed "Install inside Windows" options.  The setup wizard copied some files and rebooted.

After reboot, I selected Ubuntu option from the boot menu.  The setup continued with some more automated copying/installing stuff. It again asked for reboot.

After reboot, I still get Win7 and Ubuntu options in boot menu. I get this screen for very few seconds:

[http://www.twitpic.com/o3jfn](http://www.twitpic.com/o3jfn)

And finally it shows the GRUB command line and nothing happens further!  Command line screenshot here:

[http://www.twitpic.com/o3jng](http://www.twitpic.com/o3jng)

Anyone else faced similar problem?

---

### Post by Mark Phelps on 2009-11-03
From the posts here, LOTS of folks are having problems with the combination of Windows 7, Wubi install, and Ubuntu 9.10 -- with no one posting any solutions yet.

Also, Wubi installs INSIDE an existing Windows partition.  If you want it in its own partition, you need to do a traditional dual-boot installation instead.

---

### Post by kamlesh30rao on 2009-11-03
Thats right Mark. I too noticed few posts with this problem.

Yes, you are right about Wubi.  Since I had some unpartitioned space, I created a seperate drive for the same.

Are you also facing this issue?

---

### Post by hakkon on 2009-11-03
I have the same problem. I also run windows 7 64-bit and used wubi. i didn't make a seperate partition, but after the ubuntu install it asked me to reboot, and then when i choose ubuntu, i get the second screen that you have postet a pic of. let me know if you find a solution!

---

### Post by Na$$im on 2009-11-25
Hi there , 
having the same problem on my laptop , i installed Windows 7 32 bit ...then ubuntu 9.10 , grub worked fine for the first few boots ...and now i'm having a prompt command line Sh : grub>

---

### Post by phillw on 2009-11-25
Wubi and Win7 don't seem to be getting along very well. The project for Wubi is VERY good, but they are somewhat hampered by a different operating system actually behaving - And, let's face facts, that suite of operating systems are not the best behaved ones on the planet.

If you have 'dipped your toe' into Ubuntu and it has whetted your appetite, putting on a dual boot system is quite painless (Very scary for new-comers, yes) - There is a great suite of HowTo's over here --> [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Don't worry that some are for previous incarnations of Ubuntu, that only affects people puttin Win on AFTER Ubuntu as 9.10 is on Grub2. Taking & keeping both Win & Ubuntu boot master records is handled here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Get a backup, and give Ubuntu a dual boot - you'll love it that way, it will even 'look after' your Win installation for you. :p

Oh, and by the way ... Ubuntu can do unto widows what Wubi does unto Ubuntu - except that the Ubuntu virtualisation system doesn't cough or stutter to a juddering halt. It's over here --> [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)  - It's only a short thread on the subject (lol)

Regards,

Phill.

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

### Post by Na$$im on 2009-12-05
hey guys, 
here's the command list to access your ubuntu... but the problem is that you have to repeat these steps every time you boot up ubuntu, hope it will help you saving your data , or maybe let you fixing grub issue :


sh:grub> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
sh:grub> initrd /boot/initrd.img-2.6.31-14-generic
sh:grub> boot

PS. on the first command I put "sda2" : because my ubuntu folder is on sda2 .make sure you'll change it if necessary.

---

### Post by phillw on 2009-12-05
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
 		 		  		  		 		 			 				 				* 					 						Last edited by drs305; 1 Hour Ago at 06:24 PM*

That is a known working solution - you will have to pay attention to your initrd as here ...

# Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
 
Regards,


Phill.

---

### Post by tsaunders on 2009-12-18
> **Na$$im said:**
> hey guys, 
here's the command list to access your ubuntu... but the problem is that you have to repeat these steps every time you boot up ubuntu, hope it will help you saving your data , or maybe let you fixing grub issue :


sh:grub> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
sh:grub> initrd /boot/initrd.img-2.6.31-14-generic
sh:grub> boot

PS. on the first command I put "sda2" : because my ubuntu folder is on sda2 .make sure you'll change it if necessary.

I did this and then it starts to boot up and gets to the end and says:

Alert! /host/ubuntu/disks/root.disk does not exits. Dropping to a shell!

---

### Post by darkod on 2009-12-18
> **tsaunders said:**
> I did this and then it starts to boot up and gets to the end and says:

Alert! /host/ubuntu/disks/root.disk does not exits. Dropping to a shell!

From windows check whether in the ubuntu folder, the file /disks/root.disk exists. That is the image of your root disk. According to that message, it's not there in which case you can't continue to run wubi.

---

### Post by tsaunders on 2009-12-18
> **darkod said:**
> From windows check whether in the ubuntu folder, the file /disks/root.disk exists. That is the image of your root disk. According to that message, it's not there in which case you can't continue to run wubi.

It's there, but it seems it's looking for host/ubuntu

I am assuming host is just sda1 though.

I am in the process of just dual booting Ubuntu with Windows 7.  I was trying to avoid this as I have heard bad things with Window 7 and Ubunut as a dual boot.  I shrunk the partition first so we will see.

---

### Post by darkod on 2009-12-18
> **tsaunders said:**
> It's there, but it seems it's looking for host/ubuntu

I am assuming host is just sda1 though.

I am in the process of just dual booting Ubuntu with Windows 7.  I was trying to avoid this as I have heard bad things with Window 7 and Ubunut as a dual boot.  I shrunk the partition first so we will see.

Yes, host is the host. Not sure if it would be the same message if your host is not actually sda1. Remember, win7 sometimes creates small 100MB boot partition that has no letter assigned and is not visible in Computer. So C: can be /dev/sda2, D: can be /dev/sda3, etc. Try few options.
As for dual booting with win7, from what I have seen wubi creates much more issues than the proper dual boot. Which is what I would expect, because wubi is trying to make linux work inside windows, not a natural environment.
I am dual booting 9.10 with win7 on both my netbook and desktop. No serious issues at all.

---

### Post by tsaunders on 2009-12-18
I am updating Ubunutu right now.  I haven't tried to get back into Windows yet.

I would get rid of window entirely but I enjoy gaming to much.

---

### Post by dokluch on 2010-01-07
> **phillw said:**
> That is a known working solution - you will have to pay attention to your initrd as here ...

# Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
 
Regards,


Phill.

completed all the steps.
got this message

No filesystem could mount root, tried: ext3 ext2 ext3 fuseblk
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
Pid: 1, comm: swapper Not tainted 2.6.31-17-generic #54-Ubuntu

some more lines and everything stops (((

---

### Post by Newbie6 on 2010-01-08
I have exactly the same problem...... :( It starts to boot and then stops with the same message:

.... unable to mount root fs on unknown-block (8,5)
 
 ......2.6.31-17-generic-pae swapper not tainted #54 Ubuntu
 
I have tried to run the command ls and get this:

(loop0) (hd0) (hd0,6)  (hd0,5)  (hd0,4)  (hd0,2)  (hd0,1) 

When I run ls /boot I get this:

2.6.31-17-generic-pae

Can anyone please help me please? Thanks.

---

