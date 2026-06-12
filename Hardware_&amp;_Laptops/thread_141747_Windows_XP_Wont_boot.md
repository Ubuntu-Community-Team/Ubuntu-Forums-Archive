---
title: "Windows XP Wont boot?"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by nismoskys on 2006-03-08
.. i didnt know where to post this.. so i decided ill put it here.

i've been using linux steadily for a while and i know i booted xp probably since january... but i tried today, and it wont work.. i see grub, it shows ubuntu and windows, i go 2 windows, select windows again, and then i just get a black screen. if i try F8 for safe mode, i get a black screen. (Also the activity light in front of my box just stays orange when that happens). 

Eh.. its okay, i guess im better off without windows.. but still.. anyone know what could be causing this?.

---

### Post by SoggyCornflake on 2006-03-09
[I]anyone know what could be causing this?.

[/I]

Any number of things I suppose.  If you type dmesg into a command prompt after booting into Linux, it may give you a place to point. 

I think the first place I'd try is to see if you can read any files from your XP partition(s) while you're in Linux.  If you can, then first back up your XP partition. Or at least the files you want to save.  If your Windows partition is NTFS (which it probably is), then you're probably out of luck when it comes to changing anything on your XP partition.  The Linux kernel has limited support for NTFS.  (Admittedly, I don't know the current level of support in the kernel.)

If you can't read the partition that could mean a couple of things, it's corrupted, or maybe the kernel you're using doesn't support the partition type.  Before assuming it's corrupted, make sure you do have NTFS as part of the kernel or a module.

Windows XP uses a boot.ini file to start it's loading process.  I don't know how Grub works when you boot into Windows.  When lilo is used, the computer boots into Windows XP's partion and finds the boot.ini file in windows XP and follows that for bootup.  If that got corrupted, then you have to edit that file.  You might be able to use a program called something like NTFSDOS or DOSNTFS to edit the ini file. 

The computer I'm using right now lost it's system.config file for XP and as a result, it would start to boot then dump out to an error message.  The only way I was told that I could recover from that was to re-install XP  :cry:   In my case I saved the data files and installed Linux.  It's been a linux box ever since and My wife & kids can still use the files I saved from the Windows XP partition.   \\:D/   Of course that Ice Age hunting game we played in XP errors out in Wine  when we tried it 
:-|

---

### Post by nismoskys on 2006-03-09
hmm.. well i know it cant be the drive itself (i have windows on a seperate disk nd linux on a seperate disk) because i can read the (NTFS) drive fine. all my files are accessible without a problem.. but yes, i cant write to them. I have GRUB..  but yeah.. same problem, start up, windows xp-- blank screen.. eh i guess ill just have to live without xp for a while (2 other comps in my house have it though).. ive been wanting to reinstall ubuntu anyways so i guess now's my chance. thanks for the help though

-later

---

### Post by SoggyCornflake on 2006-03-09
The program I was mentioning earlier might help if you need to edit a file on your NTFS partition:  NTFSDOS.

You can find it here:[http://www.sysinternals.com/Utilities/NtfsDos.html](http://www.sysinternals.com/Utilities/NtfsDos.html)

If you boot up with a DOS Boot disk with this program, you can use it to change files on an NFTS partition.  It's a good tool to have in your utility belt if  you know what I mean.

---

### Post by nismoskys on 2006-03-10
cool, thanks.

---

