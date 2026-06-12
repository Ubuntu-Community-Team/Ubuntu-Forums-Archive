---
title: "? installing multiboot XP and Ubuntu"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by Nehmo on 2006-01-28
Let's say I have two HDs. One has Windows XP (sp1) on an NTFS-formatted 15 GB drive on it and is functioning okay. The second 80 GB drive is blank. 

I want to have a multi-boot system where I can boot to either:
A Fresh install of Windows XP (updated to sp2)

A copy of the current installation of Windows XP sp1

A new install of Ubuntu

I have my original upgrade CD for Windows XP. And I also have another 160 GB drive that's just for additional storage, but I'll leave that out of the discussion to keep it simple.

Ubuntu, I've downloaded the installation iso, ubuntu-5.10-install-i386.iso  

My understanding is that I have to get a boot loader to handle these multi-boots. And the boot loader will allow selection of OS's but will default to something, I'd like that to be the WinXP fresh install. 

So what are my steps? 

Do I use Windows XP computer manager to format the 80 GB drive to FAT32 before I install Ubuntu?

---

### Post by byen on 2006-01-28
Ok..here goes
You already have a version of xp installed correct? so lets leave that there! (as it seems you wanna keep it too)
Now, you want to install another version of Windows along with Ubuntu on the other drive? well if that  is what you want to do..first install windows while leaving some space for Ubuntu by creating a seperate drive. I suggest installing Ubuntu after installing Windows as things are easier that way.

And about choosing the default OS..It comes up during the install where you can select it..if at any point you wanna change it, you can do it later after install as well. Just remember to say "yes" when you get the question "would you like to install boot loader into the MBR" if you want to see multiple  OS boot options during boot.
Hope that helps.Goodluck and Welcome to Ubuntu.


Ok.. see if this link helps:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
It has all the necessary steps needed step by step pictures and might help you.Goodluck and welcome to Ubuntu.

---

### Post by Nehmo on 2006-01-29
Okay, so this means my first step to get a multiboot arrangement of
WinXPsp2 (default) , WinXPsp1 (existing), and Ubuntu 

Is first I must new install WinXP on the 80 GB drive.
(Should I do this drive in NTFS or FAT32? I suppose it must be FAT32 for the Ubuntu, but this will mean the old WinXPsp1 installation on the other drive will be in NTFS. That's not a problem, is it?)

And then I presume the BIOS will give me the option of which Windows to boot up to, but somewhere I can set one as default. Do I do this by setting in the BIOS
Advanced BIOS Features > First Boot Device > then set it to where WinXPsp2 is?

-- 
          (||) Nehmo (||)

---

### Post by lha on 2006-01-29
Take that 15GB drive out of your computer and plug that 80'er in. Make it primary master. Install Windows on it. Make sure to leave space for Ubuntu and maybe for a shared fat32 partition. You could make a ntfs partition of x GBs and install Windows there. Then make a fat32 partition if you want to share files between different os'es. 

Now, install Ubuntu using the remaining space. Try if you are able boot both Ubuntu and your new WIndows.

Now, plug in that 15GB drive. Make it a slave or secondary master, it doesn't matter.  Start Ubuntu. Open terminal (Applications->Accessories->Terminal) and type```

cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
Add following lines to the very end of that file.
```
title Windows XP sp1
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
Find a line that says
```
default 0
``` The number tells grub what menu item to use as default. Change it to suit your preference. Save and reboot. Try to boot every os.

Because you have a third hd, you might need to change those 'hd1's to 'hd2', depending on how you have set your hd's.

HTH

---

### Post by Nehmo on 2006-01-30
[QUOTE=lha] Take that 15GB drive out of your computer and plug that 80'er in. Make it primary master. Install Windows on it. Make sure to leave space for Ubuntu and maybe for a shared fat32 partition. [/QUOTE]

I only have a WinXP upgrade CD – not the full one. In order to work, the install program on it needs to find "qualifying media", which can be a previous copy of Windows. My understanding is that the install program can find that (the qualifying media) on C (the 15 GB drive) and then install the new XP on F (the 80 GB drive).

The F, 80 GB, drive is available for whatever I want. I haven't determined how I should partition it yet or in what file system (NTFS or FAT32). I think I want the whole thing to be in FAT32 to facilitate file sharing between the new WinXP and Ununtu. I suppose that makes sharing files between the two XPs difficult, but I'm not sure of the implications. I plan to primarily use the new XP and the Ubuntu. 

So the result should look like this:
C, 15 GB, NTFS, Original WinXP
F, 80 GB, 2 partitions, 
          40 GB, FAT32, New WinXP
          40 GB, FAT32, Ubuntu

But is this better?:

C, 15 GB, NTFS, Original WinXP
F, 80 GB, 3partitions:
          25 GB, NTFS WinXP
          25 GB, FAT32 shared space 
          30 GB, FAT32 Ubuntu 

Which is the better arrangement?

[QUOTE=lha]You could make a ntfs partition of x GBs and install Windows there. Then make a fat32 partition if you want to share files between different os'es. 

Now, install Ubuntu using the remaining space. Try if you are able boot both Ubuntu and your new WIndows. [/QUOTE]

Basically, I want to make certain I can boot to a Windows XP. I must always retain that.

[QUOTE=lha]Now, plug in that 15GB drive. Make it a slave or secondary master, it doesn't matter. [/QUOTE]  

I *could* actually remove and re-install the 15 GB drive. I could first clone the OS to the F drive. I have Ghost 2003 and I've successfully cloned before. In that way, I could use the WinXP install CD and it would find the qualifying media (the clone of the old install) right there on the F 80 GB drive. 

I'm working on understanding the last part of your post. It appears grub is something that comes with Ubuntu. And I can edit it… more later.

Apparently there's no need for boot managers like [http://www.osloader.com/](http://www.osloader.com/) ? Do those things give any advantage? 


[QUOTE=lha]Start Ubuntu. Open terminal (Applications->Accessories->Terminal) and type```

cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
Add following lines to the very end of that file.
```
title Windows XP sp1
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
Find a line that says
```
default 0
``` The number tells grub what menu item to use as default. Change it to suit your preference. Save and reboot. Try to boot every os.

Because you have a third hd, you might need to change those 'hd1's to 'hd2', depending on how you have set your hd's.

HTH[/QUOTE]

---

### Post by lha on 2006-01-30
> **Nehmo]I only have a WinXP upgrade CD – not the full one. In order to work, the install program on it needs to find "qualifying media", which can be a previous copy of Windows. My understanding is that the install program can find that (the qualifying media) on C (the 15 GB drive) and then install the new XP on F (the 80 GB drive).[/QUOTE]

I don't care how you install that other Windows.  said:**
> The F, 80 GB, drive is available for whatever I want. I haven't determined how I should partition it yet or in what file system (NTFS or FAT32). I think I want the whole thing to be in FAT32 to facilitate file sharing between the new WinXP and Ununtu. I suppose that makes sharing files between the two XPs difficult, but I'm not sure of the implications. I plan to primarily use the new XP and the Ubuntu. 

So the result should look like this:
C, 15 GB, NTFS, Original WinXP
F, 80 GB, 2 partitions, 
          40 GB, FAT32, New WinXP
          40 GB, FAT32, Ubuntu

But is this better?:

C, 15 GB, NTFS, Original WinXP
F, 80 GB, 3partitions:
          25 GB, NTFS WinXP
          25 GB, FAT32 shared space 
          30 GB, FAT32 Ubuntu 

Which is the better arrangement?

In fact, they are both bad. Something like the second option would be better, but: Do not install Ubuntu on a fat32 partition. It will not work! You should use a native linux filesystem. (Usually ext3.) Basically, make that NTFS partition, install Windows there. Somewhere down the road, make the shared fat32 partition. Use Windows' tools to do that. When you start Ubuntu installer, tell it to use the free space on you left on 80GB drive and to partition it automatically. I can't give you other advice on good sizes, but leave atleast 5GB free space for Ubuntu.

[QUOTE=Nehmo]

[QUOTE=lha]Now, install Ubuntu using the remaining space. Try if you are able boot both Ubuntu and your new WIndows.[/QUOTE]

Basically, I want to make certain I can boot to a Windows XP. I must always retain that.[/QUOTE]
Maybe I didn't make myself clear enough here. Before you install Ubuntu, unplug that 15GB'er from your computer. Ubuntu installer will have 0% change of doing anything to that hd, because it isn't attached to your computer. If something weird happens, you can put your 15GB drive back where it used to be, take out 80GB drive and boot to your former Windows configuration. Only if you trash your hd while (physically) fiddling with it, your ability to boot Windows may be endangered. (And as I told you before, if you trash your current Windows install when doing a new Windows install.)

[QUOTE=Nehmo]
I *could* actually remove and re-install the 15 GB drive. I could first clone the OS to the F drive. I have Ghost 2003 and I've successfully cloned before. In that way, I could use the WinXP install CD and it would find the qualifying media (the clone of the old install) right there on the F 80 GB drive.[/QUOTE]

Not sure what you are meaning here... :confused: 

[QUOTE=Nehmo]

I'm working on understanding the last part of your post. It appears grub is something that comes with Ubuntu. And I can edit it… more later.

Apparently there's no need for boot managers like [http://www.osloader.com/](http://www.osloader.com/) ? Do those things give any advantage?[/QUOTE]

A quick look on that website indicates osloader is an alternative to grub. Grub is a boot loader, it comes with Ubuntu. You will use it to do the thing that osloader would do if you used it. When you start your computer, grub is invoked. It will show you a list of operating systems and let you choose which one to boot.

Well, looks like a long post. Have fun.

---

### Post by DaBruGo on 2006-01-30
[QUOTE=Nehmo]Let's say I have two HDs. One has Windows XP (sp1) on an NTFS-formatted 15 GB drive on it and is functioning okay. The second 80 GB drive is blank. 

I want to have a multi-boot system where I can boot to either:
A Fresh install of Windows XP (updated to sp2)

A copy of the current installation of Windows XP sp1

A new install of Ubuntu

I have my original upgrade CD for Windows XP. And I also have another 160 GB drive that's just for additional storage, but I'll leave that out of the discussion to keep it simple.

Ubuntu, I've downloaded the installation iso, ubuntu-5.10-install-i386.iso  

My understanding is that I have to get a boot loader to handle these multi-boots. And the boot loader will allow selection of OS's but will default to something, I'd like that to be the WinXP fresh install. 

So what are my steps? 

Do I use Windows XP computer manager to format the 80 GB drive to FAT32 before I install Ubuntu?[/QUOTE]

nehmo,

I have a thread started that deals with dual booting XP (on an internal drive) and Ubuntu (on an external usb drive) that you may be able to adapt to your needs.

[http://www.ubuntuforums.org/showthread.php?t=80811]("http://www.ubuntuforums.org/showthread.php?t=80811")

Hope it helps some,
DAVE

---

### Post by Nehmo on 2006-02-02
I don't get around to installing OSs very often. I had a unpleasant experience on a couple of occasions, so I'm wary of the process. I have to be cautious because I only have one machine.

Anyway, my first step is to make a configuration with the two XPs. I think I just stick the CD in and go from there. I'm going to get to that phase of the operation tonight, hopefully.

---

