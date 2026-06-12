---
title: "Hard Drive Recovery questions."
date: 2008-12-19
forum: Hardware
---

### Post by Plecebo on 2008-12-19
I have a 400GB hard drive that has crashed and I am needing to recover some data from it if possible. 

I have another 400GB hard drive (different manufacturer) that is the largest drive I have. This drive can be used however to aid in this recovery. 

I am following this tutorial: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) which is very useful. 

So my broke hard drive is /dev/sde with one NTFS partition /dev/sde1
My good hard drive is /dev/sda with no partitions on it. this drive is not mounted. 

I executed this command in a shell hoping to recover the bad drive to the good drive. 

```
sudo ddrescue -vr 5 /dev/sde /dev/sda /media/Archive/ddrescueLogFile
```

(/media/Archive) is another completely seperate drive in my computer that I am using to put the log file on. 

I'm wondering if I have made a mistake here? The command is executing and it looks like it could take a while to finish up. 

The guide indicates that I should run a fsck on the /dev/sda drive once the ddrescue is done. 

I'm wondering if a command like this will fail or not? 

```
sudo fsck -y /dev/sda
```

The reason I did not format and mount the good drive in ubuntu then do something more like this: 

```
sudo ddrescue -vr 5 /dev/sde /media/Backup/rescue.img /media/Archive/ddrescueLogFile
```

is that I was afraid that the whole 400GB would not fit on the drive. Am I mistaken? 

All I need is a few items from the drive, not even most of it... and the drive is likely mostly empty. 

Does anyone have suggestions on how I can proceed? Am I on the right track? Should I Format and write to an image? 

thanks in advance for all your help

---

### Post by stupid_user on 2008-12-19
I didn't know about that tutorial thank you.  

You are correct after using ddrescue, you will probably have to run a fsck, if it won't mount.  However since you are recovering an NTFS partition, you will have to run an NTFS version.  I know there is fsck.vfat for FAT, but I don't know about NTFS.

I know you are probably looking for a free way to do this... but just in case you have a windows machine laying around  this may help you...

The best tool I have found for recovering data from NTFS is getdataback.  Of course its not free but it only costs $79, (They offer a trial, so you can see it will even work before purchasing) and it doesn't require making an image of the drive.  It will scan the entire drive or partition, and then will display the files and folders for you just like the original, and you can just select the files you want to save.  It is very simple and easy to use, but very powerful.  I haven't used anything else to recover from NTFS drives because it works so well. 

Plus making a 400GB image will take a long time, and you need the space to store it, and then more space to store the data you are recovering.  So worse case you need a 800GB drive.  If you already have one laying around that is empty then you are luckier than me. I had to buy another drive.

I just had to recover my 250GB laptop drive (ext3) and using some of the tools in that post, I was able to get most of my data back.  But it was a very tedious process and I wished that getdataback worked on other file systems.  

I hope this is helpful.

links: [http://runtime.org/data-recovery-software.htm](http://runtime.org/data-recovery-software.htm)

---

