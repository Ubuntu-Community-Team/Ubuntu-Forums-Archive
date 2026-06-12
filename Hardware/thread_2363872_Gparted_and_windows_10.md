---
title: "Gparted and windows 10"
date: 2017-06-15
forum: Hardware
---

### Post by wickette on 2017-06-15
[EDIT: SOLVED, scroll down]

Hi, 


I know gparted is a little buggy but ive neve rhad this much trouble.   

Im need to resize my laptop ntfs windows 10 partition - its got 220gb of 465g b free, Im trying to shrink it 35gb ubuntu can read and write to the partition when its mounted but when its unmounted in gparted I get a message the partition cannot be read. If i mount again, it can be read/written to but gparted cant modify it while its mounted- its NOT giving me this problem with the other ntfs partitions on that drive. 


Kubuntu live cd dolphin said i don't have read or write permission to access the  partition (I can see all my folder behind the message), I tried opening as root, same message, I tried "[COLOR=#111111][FONT=Consolas]sudo mount -o ro /dev/sda4 /mnt"[/FONT][/COLOR]   just to see if i should go through the effort of fixing the permission thing.  but even the read only command did nothing so back to Ubuntu

---

### Post by oldfred on 2017-06-15
Is fast start up off?
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

Always best to use Windows to resize NTFS partitions and immediately reboot, so it can run chkdsk which is required after any resize.
And then use gparted to create or resize Linux partitions.

---

### Post by wickette on 2017-06-15
Fast start off is already disabled, you cant mount a windows partition if its hibernating.

I needed to shrink the windows partition to install ubuntu, windows only lets me shrink it 2.3 gb, I didnt realize using ubuntu to resize a windows partition was no longer an option.

Looking up instructions on who to shrink a windows 10 partition with a unmovable file at the end of the volume... its not worth the hassle, i guess no ubuntu for me

---

### Post by Bucky Ball on 2017-06-15
> **wickette said:**
> ... I didnt realize using ubuntu to resize a windows partition was no longer an option.

Welcome. It has never been an option. Always strongly discouraged. Win for Win resizing, Linux for Linux resizing. 

Did you defragment your Win partition several times before trying to shrink? You will reclaim space, sometimes a lot, by doing this and more so by using a non-generic Win app. Try something like PowerDefragmenter (I think it's called that, been awhile) as the non-Win defraggers are generally more powerful and will gain you more space than the Win default Disk Management tool. PowerDefrag certainly will. 

If you defrag a few times you will get more than 2.3Gb. Maybe a little, maybe a lot, depends on the last time you defragged. Good luck. ;)

PS: Not quite with you here:
> 
Looking up instructions on who to shrink a windows 10 partition with a unmovable file at the end of the volume...

Could you please elaborate on the 'unmovable volume'? If Windows is in a separate partition, then that partition can be shrunk. Perhaps post a link to where you read what you're reading and post a screenshot from Gparted (Go Adv or Adv Reply button then use the paperclip icon in the taskbar to attach pic).

---

### Post by oldfred on 2017-06-15
Some of this goes back to Vista,but same issues in newer Windows.
 Windows Vista - partition your hard drive using Disk Management, if XP use Gparted
30GB at an absolute minimum and you want at least 30% free inside the NTFS partition for Windows to work well
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
Hiberfile in Windows 7 & 8 often prevents shrink
[http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)

---

### Post by wickette on 2017-06-16
Using gparted to resize a windows partition was always possible, it always ran the risk of windows not being bootable after but it was always able to resize the partition.

How about I rephrase the question:  I want to install ubuntu on my laptop, and never use windows again.
 I think I backed up all of my personal files, but I cant be 100% sure because some programs i used either store in-progress work in custom incomplete folders, or are so old they dont save to "my documents","my pictures",etc. I want to keep the windows file system to remain intact as a separate partition on the drive for ubuntu to be able to access.



Also, Windows built in tool said it can only shrink it 4.2 gb, I ran a defrag, no change optimized degrag made things worse (can only shrink 2.3gb now), hibernation and page file were both off before I tried the resize. Im sure t here is one stubborn files towards the end of the volume thats mucking everything up. but these posts are already  more time than i had planned on spending on this part of the process =P

---

### Post by efflandt on 2017-06-16
I don't know it that is still the case with Window's own Disk Management (I don't think so), but at one time (in my case originally a WinXP system from 2004) you could not shrink an NTFS partition much unless you temporarily disabled virtual memory (similar to Linux swapfile) that Windows put near the end of main Win partition. But not knowing that I originally used ntfsresize in Linux to shrink the partition, and without disabling virtual memory in Windows, I could only free up about 25 GB of my 200 GB drive. So at that time I split that up into about 12 GB for SuSE 8.2 and 12 GB for 64-bit WinXP Pro beta. Years later once I knew about the virtual memory thing, I could have shrunk Windows down to 50 GB, but I think I left it at 100 GB which gave me 50 GB each for separate 32 and 64-bit Ubuntu 10.04 on that old early Athlon64 3200+ (2.0 GHz).

But more recently I had no trouble at all using Disk Management in Win10 to free up 230 GB on a 1 TB laptop drive to install Ubuntu 16.04 with 8 GB swap. The laptop still defaults to Win10 unless I hit Esc on the HP laptop to get into the UEFI menu to select grub. But everything works fine (albeit somewhat slowly on 4 core Pentium). I would not have bought such a low end laptop, but bought it to set up for a friend who decided they did not have the money to pay me for it yet. So it comes in handy for viewing WebEx sessions while doing other things on my desktop PC and to give me some experience with UEFI which I do not have on any other computer.

---

### Post by yancek on 2017-06-16
I just got a low end HP laptop with windows 10 and using Disk Mgmt on windows, was only able to shrink to about 465GB.  Has a 1TBdrive so not a problem.  I have had mixed sucess with Linux partition managers and windows filesystems so I generally use windows to do it.  One should be able to do the resizing though using GParted, probably less of a problem if dealing with data partition.

     	 	 	 	   
What I did to get the system to boot both Ubuntu and windows 10 without using the Esc key with the HP, copied bootmgfw.efi from EFI/Microsoft/Boot to EFI/Microsoft.  Moved bootx64.efi from EFI/ubuntu to /EFI/Microsoft/Boot and renamed it bootmgfw.efi.  After doing that I changed the path for windows to the correct location as below

 
 
   chainloader /EFI/Microsoft/bootmgfw.efi 

 
This booted windows 10 as well as Ubuntu 16.04 from the Grub menu.  I believe I found this info here or possibly at askubuntu.

---

### Post by wickette on 2017-06-17
Hi everyone, 

Should anyopne have the same issue, I did find some easy solutions (not that the above solutions would not have worked)   EaseUS Partition Master was free, I told it how much to shrink, it rebooted and ran it in a b&w text screen  before starting windows, it was fast it didnt need a checkdisk or anything after, great!  

Since I was curious, I did boot into a live usb session of manjaro kde, the kde tool there was able to shrink the windows partition as well, NOT fast, LONG startup repair ran when I tried to get into windows, but it worked as well.

This laptop is a Toshiba Satelite with EFI bios that CANNOT be turned off (legacy bios mode), not sure if it was a factor just info for the next beginner who gets stuck  =)

Thank you all for replying.

---

