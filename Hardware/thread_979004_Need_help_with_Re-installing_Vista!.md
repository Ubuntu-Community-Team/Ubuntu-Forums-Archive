---
title: "Need help with Re-installing Vista!"
date: 2008-11-11
forum: Hardware
---

### Post by cvanelswijk on 2008-11-11
Hello Readers,

Ok, so I was very  curious about the new ubuntu 8 version and wanted to give it a try. I downloaded it, mounted it on a cd, and restarted my laptop.
Ran the install, got everything installed.
Now... Here comes the problem.
I installed ubuntu alright, but meanwhile i was doing it i was being distracted by my friend here, and i just pressed forward the whole time.
Which was a terrible mistake. Ubuntu itself got installed and reformated both of the hard drives that i had.
So i was like...
I want to get vista back and see if i can just dual boot ubuntu along with it. 
This is where everything went wrong, apparently ubuntu saved the harddrives as another type of 'system' instead of ntfs, and when i launch the vista installer it cant find the C drive anymore.
I tried the windows xp cd too.
If you happen to know a solution for this please tell me!
I really want my vista back since i miss some programs, this was my own mistake, but i want to solve it too.
I dont know alot of how ubuntu works, i just hope someone knows what i can do to solve this.

Thank you.

---

### Post by JinStevens on 2008-11-11
You'll have to fdisk the drives / partitions created by Ubuntu and then recreate them using the Windows CD.  During the install, Windows will give you the option of recreating your partitions...that's when you delete the Ubuntu created drives and create Windows recognized partitions.  Format the drives you create and then install Windows normally.

---

### Post by cvanelswijk on 2008-11-11
Im new with ubuntu, could you explain in steps how to 'fdisk' the drives? 
i would really apreciate this.

---

### Post by JinStevens on 2008-11-11
> **cvanelswijk said:**
> Im new with ubuntu, could you explain in steps how to 'fdisk' the drives? 
i would really apreciate this.

Fdisk is a Windows/DOS utility and not a part of ubuntu. Fdisk just allows you to add/remove/change partitions. In Windows Vista, it may be called something else now.  Just boot up with your Windows CD and you should have the ability to change your partitions...make sure you don't choose automated options for your Windows installation, otherwise, the screen to redo partitions won't come up.

---

### Post by sirebral on 2008-11-11
You want to install Linux after you install Windows because Windows wrecks the Grub installer.

Just use your Vista install CD, reformat you HD so that Vista erases the Linux install, then after you get Vista up and running, install Ubuntu onto a partition.

---

### Post by cvanelswijk on 2008-11-11
the thing is, when i try to re-install vista or xp, both cant find the main disk, meaning i have no idea how to get vista to reformat the drive or the windows xp.

---

### Post by caljohnsmith on 2008-11-11
If you can boot up your Live CD, how about going to System > Admin > Partition Editor, and you can use that to delete all the existing partitions on the HDD you want to install Windows to, and you can also use it to set up your partitions the way you want them. In other words, you would want to create a primary NTFS partition at the beginning of the drive for Windows, and then you can create any other partitions for Ubuntu if you want Ubuntu on that same drive. Or you could create a few data partitions or whatever you want for that matter. Once you have a primary NTFS formatted partition, the Windows Install CD should be able to recognize it and use it. Let me know how that goes or if you need more info.

---

