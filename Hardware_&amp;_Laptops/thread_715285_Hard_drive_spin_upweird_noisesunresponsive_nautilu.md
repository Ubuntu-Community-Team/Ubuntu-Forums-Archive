---
title: "Hard drive spin up/weird noises/unresponsive nautilus"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by 00arthuryu on 2008-03-04
heya
I've been having this problem since gutsy was released and I have been forced back to running feisty, as this problem does not occur on feisty.
Whenever i view a partition on nautilus or other file managers, the hard disk seems to spin up and down, with a extremely weird eerie noise, ones that you hear when you turn a sound system/speakers on. It also makes nautilus unresponsive. On larger partitions (100GB), the drive spins for about 15seconds before it reads anything and for nautilus to become responsive again. On Feisty, this took about 1 second (about).This problem has also corrupted one of my previous Hard disks (400GB Seagate) Although i cannot say that this is the definite issue that caused it to die but my doubts remain. :(
I have 2 hard disks in my system
500GB Seagate SataII
250GB Seagate SataII

i'm running on an AMD 5600+ with a ASUS motherboard, 

please help
Arthy

---

### Post by 00arthuryu on 2008-04-27
okay, this is now solved in ubuntu 8.04
cheers 
:popcorn:

---

### Post by sroland81 on 2008-05-28
hello, i'm running Hardy-amd64 on Presario F700 laptop and the hard drive once a while makes a huge CLICK, like somthing broken down... very weird, but i don't see any performance issue, just the noise... what it could be? it keeps me nervious. I researched in ubuntu forums and heard about smartctl and hdparm and i algo changed the power managment to -B 254 with hdparm. But the noise still happening and it is only in ubuntu, in XP never heard it. the click sound is like when you shut down the machine, but without the slowdown, just the huge click.... i thought about the current adapter i'm using, that does not have the "ground" in the plug... could be this? thank you very much.

---

### Post by krlhc8 on 2008-06-05
As a quick fix, try editing /etc/acpi/power.sh.  Below I have a snippet of the code that needs to be [COLOR="Red"]**changed**[/COLOR], which is highlighted in red and bolded:

```


function laptop_mode_enable {
    $LAPTOP_MODE start
    
    for x in /sys/bus/ide/devices/*/block*; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S $SPINDOWN_TIME /dev/$drive 2>/dev/null
	$HDPARM -B [COLOR="Red"]**128**[/COLOR] /dev/$drive 2>/dev/null
    done
    
    for x in /sys/bus/scsi/devices/*/block*; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S $SPINDOWN_TIME /dev/$drive 2>/dev/null
	$HDPARM -B [COLOR="Red"]**128**[/COLOR] /dev/$drive 2>/dev/null
    done
}


```

The key here is to change the $HDPARM -B 1 to $HDPARM -B 128.  There's no need to restart if you were wondering; it should work right off the bat.

---

