---
title: "No Partitioning Options when installing from alternate CD"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by sadafrasheed on 2009-01-03
Hello,, 
i have windows xp installed on my system. i am trying to installed ubuntu 8.10 from my hard disk. i dont want to lose data on windows partition. i have freed up / deleted 40 GB partition. i have downloaded image of alternate CD and followed the instruction provided at 

[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

when installing ubuntu, the installer does not ask me how to partition disk, instead it showed me a screen with options saying "help on partitioning", two blank line then "Undo Changes on Partitions" and "Finish Partitioning & write changes to disk"

since all of the options does not seem to be right to me,, i ctrl+alt+del to abort setup.


i searched net and found this..
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) 

but this is not what i got...
i was not presented with screen shown in fig 19


what have i done wrong :confused:
how do i specify my partition options.. i dont want to delete my windows partitions.


i have hp dv6000 and i have downloaded ubuntu-8.10-alternate-amd64.iso 


following are the lines i have specified in my menu.lst file


title Install Ubuntu
kernel (hd0,0)/boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd (hd0,0)/boot/initrd.gz

---

### Post by sadafrasheed on 2009-01-03
i have viewed the screen case from [http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2](http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2) but cant figure out the problem

---

### Post by sadafrasheed on 2009-01-03
seems like no one has got solution for this propblem :confused:

haven't any body ever faced this problem??

i cant find any answer on net as well :(

---

### Post by Kintwa on 2009-01-03
I have this exact same problem. I just finished downloading Intrepid today - the same iso as you are using. I've installed Ubuntu via the alternate install before and this is the first time I've come across this issue.

I'm still searching for a solution.

Just curious, is there a reason you are using the alternate install? The normal GUI install seems to be working fine for me. (except I need to use the alternate for RAID.)

---

### Post by sadafrasheed on 2009-01-04
my cd writer is not working properly,, i cant write cd so i find this alternate method of installing ubuntu but i think i have to stick with xp although i am sick of virus attacking windows :(

---

### Post by Pumalite on 2009-01-04
[https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD](https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD)
You can also use Gparted Live CD and prepare the partitions ahead of time

---

### Post by sadafrasheed on 2009-01-04
i have studied it but cannot get any solution for my problem :(

Live CD,, not an option,, my cd writer is not working,, i cannot create live CD

---

### Post by Pumalite on 2009-01-04
Burn the iso to disk and boot from it
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by sadafrasheed on 2009-02-06
Thankyou everyone for showing concern :)

i installed ubuntu using alternate cd,, i downloaded iso,, copied it to usb and booted my system using usb..

now enjoying ubuntu on my system

---

