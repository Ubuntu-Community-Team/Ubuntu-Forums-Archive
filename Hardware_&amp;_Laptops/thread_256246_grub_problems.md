---
title: "grub problems"
date: 2006-09-12
forum: Hardware &amp; Laptops
---

### Post by Rubbing Alcohol on 2006-09-12
I had a working Breezy install dual-booting with WinXP. I reinstalled XP and lost my MBR. Nothing unexpected so far. Problem is that now I can't reinstall grub for the life of me](*,) 

The patitions are still there, but I can't always see them. I followed a few different guides but none worked. Closest I got was using the install CD in rescue mode. I can use it to get myself to a shell prompt, but grub-install keeps saying it can't read /boot/grub/stage1.

I've tried the Super Grub Disk as well, but I don't think I understand how it works. The guide I read seems to indicate there should be a menu interface but when I load it up, I get the grub shell (which I don't know how to use).

Any help would be greatly appreciated.

jul

---

### Post by Herman on 2006-09-14
Hello, Rubbing Alcohol,
Normally, you should be able to install Grub 'Natively' using a Linux Live CD with Grub on it. Ubuntu Dapper Drake Live/Install CD is a popular choice.

When I do it, I boot my CD operating system and open -->Applications -->Accessories -->Terminal and type 'sudo grub', to enter a grub shell. When you have a grub shell, you will have a grub > prompt instead of your regular username @ hostname:~$ prompt. ```
sudo grub
```The next command is 'find /boot/stage1' and that should tell you which partition numbers in grub notation are Linux partitions that contain a copy of grub. ```
find /boot/grub/stage1
``` Next. you use the answer or one of the answers you got from the previous command to 'root' grub to the partition that contains the grub you want represented in your MBR. The command looks like 'root (hdx,y), where: X is the hard drive number and y is the partition number, for example ```
 root (hd0,1)
``` Then, you can either write Grub's 'IPL' (stage1) to MBR of the first hard disk with 'setup (hd0)', or to the first sector of a partition with 'setup (hdx,y). Where x is a hard disk and y is a partition number. ```
setup (hd0)
``` You should see some feedback from the above command to let you know that your Grub install of stage1 to MBR has succeeded. You can quit the grub shell ```
quit
``` and exit yout terminal and reboot, removing your Live CD to make sure it has worked.
Here are some illustrations to make sure, [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

I wanted to see if you are able to try that method first, and let me know how you go. I don't know which other how-tos you might have been trying. There are a lot of good ones and some that are out-of-date for Dapper and a few that that I wouldn't recommend.
The method I described above has proven quite reliable for me and others who I have given it to. It is possible to have some other problems that seem to prevent Grub from being written to MBR though.

I have noticed some people feeling that it's necessary to 'chroot' into their Ubuntu partition to install Grub, but I don't know where that idea comes from. It isn't mentioned at all in the Grub Manual, and I have only seen it being recommended lately. I have never needed to do that. However, if you find you cannot install Grub the normal way, chrooting might be worth a try.  I'm rather skeptical about the need for it myself. > The patitions are still there, but I can't always see them. What partitioning software can you see your partitions with, and when can you see them or not see them?  
What is the output from 'sudo fdisk -lu' from teh Live CD? ```
sudo fdisk -lu
```> I've tried the Super Grub Disk as well, but I don't think I understand how it works. The guide I read seems to indicate there should be a menu interface but when I load it up, I get the grub shell (which I don't know how to use). Yes, well you should be getting an orange language selection menu, here's the Super Grub Disk Documentation page, [Click Here]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html").
 Using Super Grub Disk should look something like the illustrations shown with the examples on the page, or maybe something has gone wrong with your .iso download, or the way you burned it to disk or something. There are Super Grub .iso.tar.bz2 files for making CDs with, or img.bz2 files, I think those are for floppy disks, I really should test one.
Here's a link that should help you with Grub's Command Line Interface, which can be interesting and fun once you get the idea of it, [Click Here.]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

Rubbing Alcohol, I hope something here helps you get your laptop booting normally with Grub again, I'll keep an eye on this thread for any news. 
Good luck with it, Regards, Herman :D

---

