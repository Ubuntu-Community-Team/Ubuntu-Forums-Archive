---
title: "Dual boot with WinXP"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by Zanoah on 2009-03-06
I already got windows XPSP2 installed on my main C:\ drive, and I want to install Ubuntu on totally different physical drive D:\ which is on the same machine. Both disks are working under xp and both are NTFS format. My question is, can I install Ubuntu, on drive D:\ without compromising any of the windows installation and files, and then after installation make dual boot system? So that both systems are totally independent of each other but got dual boot on any command prompt.

Thanks in advance :)

---

### Post by Whorehay on 2009-03-06
You can just install Ubuntu and GRUB on the second drive and GRUB will only need you to point out where Windows is (in case you want to boot XP).

To edit GRUB:
```
sudo nano /boot/grub/menu.lst
```

There seems to be more information on **_[[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?p=677880#post677880")_** thread as well as **_[COLOR="Red"][[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=179902")[/COLOR]_** one if you need more details.

---

### Post by Zanoah on 2009-03-06
Thanks for swift reply, but something else is bothering me. I read all the treads that is to be, but I am afraid if I start Ubuntu installation with CD/DVD drive as first boot device, that Ubuntu installation can reformat windows drive, and how can I be sure, that it will install itself on D:\ and not touch C:|? Maybe it is better that I unplugged C:\ and install it to D:\, but what will happen when I turn C:\ on again without removing jumpers, and it will take master boot again? Lots of questions, I know, but I am Ubuntu n00b and really need detail help, all the threads I saw and have read, don't explain exactly how can I reroute master or slave to do boot sequence together?

thnx in advance :)

---

### Post by howefield on 2009-03-06
> **Zanoah said:**
> .but I am afraid if I start Ubuntu installation with CD/DVD drive as first boot device, that Ubuntu installation can reformat windows drive,

You are correct to be cautious, many people have wiped out the wrong partition. But as long as you read what is on your screen you should not go wrong.

Boot from the live cd and go to system > administration > partition editor and delete the disk you want to use for Ubuntu. Then when you are in the Ubuntu installation process, tell it to use the largest free space.

This presupposes that you know the difference between your disks and would know which one to delete ? 

> ..Maybe it is better that I unplugged C:\ and install it to D:\..

Yep, that would work, but you would need to tell the bios which drive to boot from depending on which operating system you wanted to load.

---

### Post by Roob on 2009-03-06
Hi Zanoah,

> how can I be sure, that it will install itself on D:\ and not touch C

If I understand correctly, if you leave the C-drive in as boot, Grub will edit the mbr of your boot drive (which is C). I was so unlucky that after installing (X)Ubuntu on a different drive [I lost my WinXP partition]("http://ubuntuforums.org/showthread.php?t=1084528"). I found this is exeptional though. It is more common that after installing Ubuntu you can't boot into one (WinXP) or both OS-es, and you'll have to boot into the LiveCD to do some editing in order to be able to restore things. This is not very difficult and you should be able to get some good advice in this forum.

If you want to play it safe, disconnect your C-drive, boot from the liveCD and install Ubunto on "D". After this you'll have to do some editting in order to be able to boot into both OS-es (your boot-HD will be "D" then).

Of course this is more work, and I guess in 95% of the cases everything works just fine if you install Ubuntu on "D" without disconnecting "C", no matter which drive is set to boot. I would certainly advice you to defrag and check both disks in WinXP before doing this. I think in some defrag apps (PerfectDisk?) it is possible to defrag the mbr as well. And if it's possible, it can never hurt to make an image of your WinXP-partition and store it in a different place (you'll have to have a rescue CD in order to put the image back in case you need it). 

Good luck and let us know how you fared!

---

### Post by Pumalite on 2009-03-06
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by Whorehay on 2009-03-06
> **zanoah said:**
> *i am afraid if i start ubuntu installation with cd/dvd drive as first boot device, that ubuntu installation can reformat windows drive, and how can i be sure, that it will install itself on d:\ and not touch c:\?*

I understand what you mean, but don't be scared!  The only way you could overwrite Windows is if you format over it when you are setting up the partitions.  If you ONLY want your second hard drive to have Ubuntu, you can let the partitioner take over the whole thing and format it to whatever Linux filesystem you prefer.   **You HAVE to be careful when choosing your hard drives.**  They won't be referred to by C, D, or any labels you've assigned to them.   There's a little info on that [**_[COLOR="Red"]here[/COLOR]_**]("http://www.yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html").

[**[COLOR="Red"]_Here_[/COLOR]**]("http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml") is a step-by-step guide of how the installation process goes.  I'm assuming you're installing 8.10, but it's pretty much the same thing for the most recent versions.   There's an example of the GRUB settings in [**_[COLOR="Red"]this wiki[/COLOR]_**]("http://wiki.archlinux.org/index.php/Windows_and_Arch_Dual_Boot#Dual_Booting_from_Multiple_Hard_Drives").

It is always a good idea to back up your data and print out any information you might need while you are installing.  Good luck!

---

### Post by Zanoah on 2009-03-06
Thank you all for help and fast reply, I installed 7.10. Now I am downloading necessary updates and will upgrade it to newest (I think it's 8.something version). I will surely inform you of my progress and if needed write some installation tricks (that is, If I learn something out of this experience). I like to explore and learn as I go doing things in Linux. 

read you soon :)

---

### Post by Pumalite on 2009-03-06
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by Whorehay on 2009-03-13
@ Zanoah
Any luck?

---

### Post by Zanoah on 2009-04-15
No, still ripping cables out physically, when I need to log on Ubuntu or Win, no luck... :(

too much info, must start Linux hyper-basic course...

---

