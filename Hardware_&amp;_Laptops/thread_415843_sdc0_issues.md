---
title: "sdc0 issues"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by chuckt3hnoob on 2007-04-20
i am using Ubuntu 7.04 server set and i was just about to start my configuration of a LAMP server when i apt-get to install openssh it asked me for the install CD and i complied only to find that it was just repeating the message again and again each time i pressed enter and not accessing the CDROM *no blinking lights for me* :( ... check to see what i have mounted and... CDROM is not there check the fstab file and it is set to mount as follows

/dev/sdc0 /media/cdrom0

but when i ls the same file (/media/cdrom) there is nothing in it and when i try to mount i manually....

special device /dev/sdc0 not found

so... i have been searching these threads trying to find the right combination of words to find the solution because i know it has been long since dealt with,  but i cant find it so to sum it up;

Can someone provide me with a solution (most grateful) or a link to the solution (equally grateful :D )

btw i would copy my fstab file in here but alas i cant install openssh so i have to do everything at the terminal and go easy with me for this is first time with ubuntu (eps as server)

thanks

---

### Post by Compyx on 2007-04-20
What you should probably do is edit your /etc/apt/sources.list file, there should be a line which tells apt to get files from the CD: either change it to point to the correct mount point of your CD, or comment it out to get files from the internet. You might also try to remove the 0 from '/dev/sdc0' to see if that helps, it seems a little odd to me that a CD-rom would have multiple partitions.

---

### Post by chuckt3hnoob on 2007-04-20
since i cant find where (if at all) my cdrom is getting mounted how would i comment it out to get the files from the internet?

and after doing the mod that you suggested no change;

mount: special device /dev/sdc does not exist

---

### Post by Compyx on 2007-04-20
If you look at /etc/apt/sources.list, there will be a line containing "/dev/sdc0" or "/media/cdrom" or something similar, try commenting that out. I don't know how such a line would like exactly, since I immediately remove these after installing the base system.

---

### Post by chuckt3hnoob on 2007-04-20
thaks XD 

I commented the line

deb cdrom:[Ubuntu-Server 7.04 _Feisty Faun_ -release i386 20070415 feist$

then tried the apt-get again

it seemed to have worked but i got a strange message after apt-get completed

# apt-get install ssh openssh-server
  Reading package list.... Done
  Building dependency tree
  Reading state information... Done
  the package ssh is not availible, but is refered to by another package.
  this may mean that the package is missing, has been obsolete, or is only availible from anther source.
  However the following packages replace it
     openssh-client
  E: package ssh has no installation canidate
#

something tells me that i dont yet have ssh-server... nor can i get it :/

---

### Post by Compyx on 2007-04-20
It appears ssh is a transitional package, it has been replaced by openssh-client and openssh-server. So you can just do what apt tells you: install openssh-client, not ssh.

---

### Post by chuckt3hnoob on 2007-04-20
thanks alot for that information but i am still at my original problem... how am i going to get my CDROM back in mounting condition, but i am well on my way to configuring this server so i am happy right now :) but should i need to mount a future CDROM i will need to resolve this problem and just a fyi I install from CD so i know it works :)

---

### Post by Compyx on 2007-04-20
Perhaps the mount point of your CD-rom would be /dev/hdc or /dev/hdd, like on my system? My system uses IDE-drives, so my hard disk is /dev/hda, my DVD-writer /dev/hdc and my old CD-writer is /dev/hdd. Try that or look through the /dev directory if anything looks like a CD-rom drive and try to mount it. Trial and error, but it might work ;)

I had a similar problem installing Debian a few years ago, the mount points of my drives had shifted somewhat and I also got this 'mount point does not exist' message. So maybe try /dev/sdd(0) or similar mount points?

---

### Post by chuckt3hnoob on 2007-04-21
that is the thing that confuses me, I have 2 hard drives on IDE 0 and my CDROM is the slave on my IDE 1 but Ubuntu current release uses SCSI drivers for all devices IDE or SCSI so even though i have a (technically) hda1 hda2 hdb1 and hdd devices i instead have the SCSI versions for titles, but unfortunately I will not be able to attempt you suggestion because this is a test server at my office untill Monday

but thanks again for the quick responces XD

---

### Post by Robin T Cox on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm not sure if yours is the same fault as mine, but I discovered a bug in Feisty (now 7.04) that intermittently prevents my Kubuntu recognising the CD burner.

Check your dmesg to see whether your problem is similar.

---

### Post by chuckt3hnoob on 2007-04-23
Well I found that my CDROM was bad so I replaced it only to find that I am still getting the same problem :( 
But looking through that error report I am not sure how to read it per say, I am not understanding if it was fixed and if so what is it that I have to do

sadly all I am trying to do is install open-ssh server and if I could get a online repository that would suffice for the CDROM not being present that would get things moving again.  

So should I revert back to the 2.6.20-11 kernel to solve this issue?

---

### Post by Robin T Cox on 2007-04-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You could try adding the word 'irqpoll' (without quotes) to the kernel line in /boot/grub/menu.lst thus:

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash irqpoll

See:

[http://ubuntuforums.org/showthread.php?t=414002&page=2](http://ubuntuforums.org/showthread.php?t=414002&page=2)

The mount point of my CD writer is /dev/sdc0.

---

