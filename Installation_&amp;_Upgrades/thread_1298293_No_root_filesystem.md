---
title: "No root filesystem?"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by GimmeCoffe on 2009-10-22
Okay, I have downloaded Ubuntu 9.04 x64 and I am trying to dual-boot it with Wubi. However, when I boot into Ubuntu, it gives me a message saying "No root filesystem specified. Please use the partition manager to fix this error." or something like that. :confused: Please help! I am running Windows XP, and I have three partitions:


[LIST]
[*]Recovery partition
[*]XP Partition
[*]Data Partition
[/LIST]
I am trying to install onto Data partition.

~Mr. Coffe with one "E" :guitar:

---

### Post by earthpigg on 2009-10-22
hi,

it sounds like during the ubuntu install you manually partitioned, but did not set anything with the mount point of "/" and having the "bootable" flag?

well, that is what i would think on a true ubuntu install. im not sure what level of oddness WUBI may have added....

---

### Post by GimmeCoffe on 2009-10-22
Nope, I just did a regular install on my data drive...

~GimmeCoffe

---

### Post by a7j_72 on 2009-10-22
Recovery and Xp partitions are both part of WINDOWS, right?

If this helps... Its for installing Ubuntu next to windows, but pick out what u need from it.
IF someone knows a better/easier way let us know. thnx

*******************
As if you were installing for the first time, when you get to PARTITIONS 
select: Maually select/assign Partitions.
Make sure that the "Data Partition" is not a formatted but instead: free space.

Now we are ready to designate/format "Swap Partition" and "Filesystem Partition"...
-Select appropiate type & sizes for each partition.

-Make sure that both are using "/" mount point. 

continue with installation.
***********************

someone, please fill in if I forgot to mention something. (as Im typing from what I remember )

---

### Post by GimmeCoffe on 2009-10-22
> **a7j_72 said:**
> Recovery and Xp partitions are both part of WINDOWS, right?

If this helps... Its for installing Ubuntu next to windows, but pick out what u need from it.
IF someone knows a better/easier way let us know. thnx

*******************
As if you were installing for the first time, when you get to PARTITIONS 
select: Maually select/assign Partitions.
Make sure that the "Data Partition" is not a formatted but instead: free space.

Now we are ready to designate/format "Swap Partition" and "Filesystem Partition"...
-Select appropiate type & sizes for each partition.

-Make sure that both are using "/" mount point. 

continue with installation.
***********************

someone, please fill in if I forgot to mention something. (as Im typing from what I remember )

1. How do you get to PARTITIONS?
2. How do i set mount point?

~Thx, GimmeCoffe

---

### Post by a7j_72 on 2009-10-22
When you reboot with the Ubuntu CD, (and It boots from CD)... so that you get the options menu, You can select Install Ubuntu. 
After completing all the time zone settings and keyboard layout...
At some point it will ask you where in your hard drive do u wish to install...
That is the Partitions Menu.

 -Select "Manually select Partitions"
and you should choose the** free space** (make sure its not formatted) where Ubuntu will be installed.
- First select the free space and make a new partition, a menu should pop up
  -under type select "swap area" 
  - Select the appropriate size... 1-3GB ??? (I have 4GB)...
  - And for mount point:    "/"
OK 

Now in the remaining free space...
 Create new partition... (this one will be ubuntu OS)...
 - leave all  other settings as they are. 
 - Select what size would u like the partition to be.(I suppose whatever you have left.)
 - Make sure for Mount Point:  " / "
OK

Proceed with Ubuntu Installation.

I suppose if you plan on installing Wubi you might need to leave appropriate free space left. I have never used Wubi but I assume its a similar if not identical process.

---

### Post by GimmeCoffe on 2009-10-23
> **a7j_72 said:**
> When you reboot with the Ubuntu CD, (and It boots from CD)... so that you get the options menu, You can select Install Ubuntu. 
After completing all the time zone settings and keyboard layout...
At some point it will ask you where in your hard drive do u wish to install...
That is the Partitions Menu.

 -Select "Manually select Partitions"
and you should choose the** free space** (make sure its not formatted) where Ubuntu will be installed.
- First select the free space and make a new partition, a menu should pop up
  -under type select "swap area" 
  - Select the appropriate size... 1-3GB ??? (I have 4GB)...
  - And for mount point:    "/"
OK 

Now in the remaining free space...
 Create new partition... (this one will be ubuntu OS)...
 - leave all  other settings as they are. 
 - Select what size would u like the partition to be.(I suppose whatever you have left.)
 - Make sure for Mount Point:  " / "
OK

Proceed with Ubuntu Installation.

I suppose if you plan on installing Wubi you might need to leave appropriate free space left. I have never used Wubi but I assume its a similar if not identical process.

all right, I got into the PARTITIONS, but it does not recognize XP OS.

Help??? :confused:

~GimmeCoffe

---

### Post by a7j_72 on 2009-10-23
I am assuming winXP is currently operable? right?

When you get to Partitions Menu... 
 what partitions exist?

Let me switch computers, so I can re-create and see what ur seeing.:P

---

### Post by GimmeCoffe on 2009-10-23
Sorry for the late reply.

> I am assuming winXP is currently operable? right?
Yes, I am using XP to type this post! :)

> When you get to Partitions Menu... 
what partitions exist?
When I get there, there are no partition tables! Just /dev/sda.


However, when I am in Windows, I can see all the partitions.
I have tons of important data (mostly homework) and I can't format. Any ideas?

~GimmeCoffe

---

### Post by GimmeCoffe on 2009-10-23
AArgh!!  My data partition is hidden!

---

### Post by GimmeCoffe on 2009-10-23
Bump! Anybody?

---

### Post by a7j_72 on 2009-10-24
I am not familiar to Wubi... 
but I was reading on another forum, 
It seems that 
"Wubi installs Ubuntu on the same file partition as Windows"

Is this what you are trying to do?

---

### Post by andrew0002 on 2009-10-25
Yeah, I'm getting the same issue. I'll let you know if a find a fix.

-Andrew

---

### Post by andrew0002 on 2009-10-25
I think I might be on to something.... Details pending....

---

### Post by a7j_72 on 2009-11-03
ok... I ran into a page on accident. which taught me a lot of how wubi worked... I had incorrectly assumed that Wubi was just a different distro of ubuntu like kubuntu, etc...

If you are still having the same problem... 
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
might help just in case you havent read it.

I would suggest using Windows' Control panel to uninstall Ubuntu.
should the uninstall fail, use [URL="https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe"]this uninstaller
[/URL]
Then install, using the wubi-guide mentioned above.


[I]If the default settings are not working for you, 
"Verbose Mode" might provide some logs that if not I, then someone knowledgeable 
might be able to interpret, and help u further. 

"Verbose Mode" is dicussed in the wubi-guide under "[SIZE=1]Wubi Support Forum[/SIZE] section"[/I]

---

### Post by GimmeCoffe on 2009-11-06
Ok, thanks. I'll give it a try

---

### Post by GimmeCoffe on 2009-11-07
Aha!  Found out what was the problem. This should work if you have a SATA drive, Andrew0002.  I needed to set SATA mode to AHCI. Thanks for all the help!

---

### Post by a7j_72 on 2009-11-08
Great to hear that you solved it! :p


Ps: As creator of this thread, you can mark this thread as SOLVED (under "thread tools") so that others having this problem might find a fast solution. ;p

---

### Post by GimmeCoffe on 2009-11-08
Shoot, now I'm screwed. It still doesn't detect my partition table, even when I boot from Cd. It just says "No operating systems installed." Any ideas?

---

### Post by a7j_72 on 2009-11-08
uh oh! 
"The problem is that if you installed Windows in IDE mode (ie you didn't use F6 and supply a driver disk), then simply changing the BIOS setting to AHCI mode and rebooting will cause Windows to fail and will require a repair install. Most people have been advising to reinstall Windows if you want AHCI enabled."

I have never tried this...
_*not even sure if its possible.*_
 but MAYBE If you reverse it to IDE you can log in, back up files, make the switch to AHCI, then install Windows+Wubi??? maybe?
Best wishes.

---

### Post by GimmeCoffe on 2009-11-09
> **a7j_72 said:**
> uh oh! 
"The problem is that if you installed Windows in IDE mode (ie you didn't use F6 and supply a driver disk), then simply changing the BIOS setting to AHCI mode and rebooting will cause Windows to fail and will require a repair install. Most people have been advising to reinstall Windows if you want AHCI enabled."

I have never tried this...
_*not even sure if its possible.*_
 but MAYBE If you reverse it to IDE you can log in, back up files, make the switch to AHCI, then install Windows+Wubi??? maybe?
Best wishes.

Yes!!! It worked! :p Thank you so much, aj7_72.  Now I have Ubuntu up and running!

---

