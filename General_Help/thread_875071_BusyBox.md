---
title: "BusyBox"
date: 2008-07-30
forum: General Help
---

### Post by Deldo on 2008-07-30
Hello.

I have installed something, I think, so that now when I open Ubuntu, BusyBox open before Ubuntu.

It writes that it is BusyBox - a built-in shell. And write <initramfs> below where I can type.

How do I remove it, exit it or get in to Ubuntu again?

Rune Eriksen

---

### Post by Deldo on 2008-07-30
Hmm, I could open Ubuntu again, but only one time. I'm stocked again with BusyBox.
I really need some help.

---

### Post by bks on 2008-07-30
> **Deldo said:**
> Hello.

I have installed something, I think, so that now when I open Ubuntu, BusyBox open before Ubuntu.

It writes that it is BusyBox - a built-in shell. And write <initramfs> below where I can type.

How do I remove it, exit it or get in to Ubuntu again?

Rune Eriksen

Are you able to get all the way into your desktop?

---

### Post by Deldo on 2008-07-30
No, I'm not. Only to the terminal with BusyBox?

---

### Post by bks on 2008-07-30
> **bks said:**
> Are you able to get all the way into your desktop?

On second thought it might be easier to just reinstall, unless you have valuable data you don't want to loose.

---

### Post by bks on 2008-07-30
> **Deldo said:**
> No, I'm not. Only to the terminal with BusyBox?

I found a Wikipedia page on BusyBox and it sounds like it is meant to replace a lot of the GNU Core utilities/libraries. You may have already replaced too many files to just remove BusyBox.

[Article link]("http://en.wikipedia.org/wiki/BusyBox")

---

### Post by Deldo on 2008-07-30
I have a lot of data inside Ubuntu that I can't do live without.

---

### Post by bks on 2008-07-31
> **Deldo said:**
> I have a lot of data inside Ubuntu that I can't do live without.

There may be another way, but I'm not that familiar with BusyBox. So with that said, what I'd do is, load up a LiveCD and back up all the data you don't want to loose (either on removable media or another partition) and then reinstall Ubuntu. I would think that you should be able to find all your important info using the LiveCD or maybe you could even remove BusyBox while in LiveCD. Just a thought.

---

### Post by justleen on 2008-07-31
busybox is a very nifty tool for smaller distro's. It has a whole buch of shell commands baked into the busybox binary, so you dont need a lot of seperate binaries for seperate actions anymore. (as a rule of thumb, you can say that /bin/ is packed into 1 binary). If you do a "ls" it will not execute /bin/ls, but it will let busybox parse the command... the effect is the same though.

I wouldnt start reinstalling just yet.
you didnt replace any files just yet, your old install is still there.
you should be able to bootstrap to the old install, and just remove busybox

[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-03/msg00709.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-03/msg00709.html)

---

### Post by Deldo on 2008-07-31
justleen, you need to explane that a little bit more precise. I'm not very good at Ubuntu.

---

### Post by Deldo on 2008-07-31
I will reinstall Ubuntu, but I would like to know what I did to get this problem?

---

### Post by Martje_001 on 2008-07-31
Before you do that, pop a live-cd in and mount your hard disk (just by going to 'Computer' in GNOME) and copy your files to an other partition / hard disk / USB-drive.

It might help yo try another kernel. If you only have installed ubuntu you can select another kernel by pressing ESC when booting.

---

### Post by geirha on 2008-07-31
When you see the busybox prompt, then some important driver has failed to load, and it gives you this tiny shell to give you a chance to straighten things out. Of course, you need a bit of knowledge to figure out what's wrong and how to fix it. If you see any error messages, please post them here, and someone might know what it means.

Anyway, my guess is that the thing that caused this was an update with a new kernel. It's possible that it has some sort of bug that fails to load the harddrive drivers for example. If that is the case, you should be able to simply boot the previous kernel from the grub menu (You might see a message that says hit ESC to show menu or something if the option to hide the grub menu is on. Press Esc if you see it) Choose the previous kernel, should be the third menu-entry.

---

### Post by drs305 on 2008-07-31
I agree with geirha - don't reinstall until you try this step. Let the computer start its boot. After the BIOS loads (your computer may beep) start hitting the ESC key. Hopefully that will display the grub menu. Then select an older kernel on the menu. If you don't have an older kernel listed, you can edit the menu manually from this point. We can talk you through it if necessary.

---

### Post by Deldo on 2008-08-01
Thank you. I'm sorry that I already have reinstalled Ubuntu.
But I back-upped my important files. And while I did that, I expierenced that some files wouldn't be copied. It was .mp3, .odt and many other files. So I just reinstalled Ubuntu, because it seemed to be the most easy thing to do.

---

### Post by ingeva on 2008-08-01
> **Deldo said:**
> Hello.
It writes that it is BusyBox - a built-in shell. And write <initramfs> below where I can type.

How do I remove it, exit it or get in to Ubuntu again?


I had a similar problem when I wanted to install Ubuntu on my new computer. I was told to enter setup and change the hard-disk settings from IDE to RAID. My two disks are still seen and operated like two separate HDs, but this made things work as they should.

I have two SATA disks, and my theory is that if the system doesn't find them, it attempts to initialize a ramdisk file system (initramfs).

---

### Post by Deldo on 2008-08-03
Now I get the problem again. But I'm not sure that I can get inside Ubuntu again to back-up my files.

---

### Post by daleus on 2008-08-03
I fixed this problem by changing the BOOT option in GRUB to REMOVE the word "QUIET" and add "all_generic_ide".

---

### Post by Deldo on 2008-08-03
Try to explaine that a bit more?

---

### Post by Deldo on 2008-08-03
I wonder.
When I see the Ubuntu map in Windows it has a few files. 
Is it possible to copy some of the files, reinstall ubuntu and then replace the files in ubuntu with the copied files?
The files should give me my documents, music, video and desktop back. 
Is this possible or will I get the problems with me if I do that?

---

### Post by Deldo on 2008-08-04
Sorry for the double posts. But I need an answar soon. I have a meeting about the lauch of a website. But the files is placed in my documents.
I hope someone see this thread.

---

### Post by ingeva on 2008-08-04
> **Deldo said:**
> I wonder.
When I see the Ubuntu map in Windows it has a few files. 
Is it possible to copy some of the files, reinstall ubuntu and then replace the files in ubuntu with the copied files?
The files should give me my documents, music, video and desktop back. 
Is this possible or will I get the problems with me if I do that?

That should be possible. If you have a memory pin that's large enough you may be able to use that -- or an external disk on a USB interface.

---

### Post by Deldo on 2008-08-04
The space for the copied files is no problems. I just need someone to tell witch files I shall backup and replace after reinstallations.

---

### Post by geirha on 2008-08-04
By default all files will be stored under you homefolder at /home/yourusername/, so that's the directory you want to copy. If you boot the liveCD and mount your backup-drive and the filesystem where your homefolder is, then dragging the files between the two.

There is one catch, and I suspect that's what you experienced last time. If the drive you are backing up to has NTFS or FAT, you may experience that some files will not copy. That is because linux's ext3 file system accepts virtually all symbols in filenames. NTFS and FAT does not. You cannot have ?, * and : on FAT drives for instance. And I'm afraid nautilus will give you a bit of a cryptic message if this is the case.

If you do experience problems, I recommend you archive either parts or all of your home-folder to avoid having to rename the files. You do this from the live CD by right-clicking a folder or group of files and choose "Create archive" or something along those lines. (.tar.gz archive is a good choice, .zip is ok too)

---

### Post by Deldo on 2008-08-04
geirha, as I explaned, I can NOT get into Ubuntu to my /home/username/
The only thing I can do is acces ubuntu inside windows. Which means that I can see:
[img]http://img3.imagebanana.com/img/iq9w5ndu/Unavngivet.JPG[/img]

---

### Post by geirha on 2008-08-04
I'm unfamiliar with this, is it wubi? What's inside disks?

---

### Post by Deldo on 2008-08-04
Is Wubi the installions inside Windows?
If yes, then this i how Ubuntu looks like when you install it like any other program in Windows.

[img]http://img3.imagebanana.com/img/ikxeo3oz/Unavngivet.JPG[/img]

---

### Post by geirha on 2008-08-04
I see, I didn't realize that earlier. That's a bit vital information. Reading up on wubi, it says the following about backing up the system:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
> Can I back up the installation files?

Yes just copy C:\ubuntu\disks\root.disk somewhere else (in 7.04 the relevant files are called C:\wubi\disks\*.virtual.disk). Old installation files can be mounted within Ubuntu and any relevant data can be copied over the new installation.

So if you have a root.disk inside d:\ubuntu\disks\, that should contain all your documents and the likes.

It also explains how to find the /home-folder using the liveCD.
[https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7)
(That is, once /vdisk is mounted, you should find your home under /vdisk/home/yourusername/ )

Hope this helps.

---

### Post by Deldo on 2008-08-04
As you can see in my last picture there is not a root.disk inside the "disks", but I think it is swap.disk. It is the biggest file in the directory.

---

### Post by geirha on 2008-08-04
No, that's the swap partition, can't be it. It's not stored anywhere else on your system either? Try searching all your windows drives for "root.disk" or "*.disk"

If there is no matches, then I think we've found the reason why ubuntu won't boot.

---

### Post by Deldo on 2008-08-04
Hm, I'm sorry to hear that.
I would like to try this before I reinstall Ubuntu:
[https://wiki.ubuntu.com/WubiGuide#he...cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide#he...cef9e81cd675b7)
But can you explane the way more precise to me?

---

### Post by geirha on 2008-08-04
If you don't have root.disk anywhere, then that won't work either. Perhaps you should try to find some recovery software for windows, and see if you can recover that root.disk file. It must have been deleted somehow.

---

### Post by Deldo on 2008-08-05
I'm trying with a recover tool now.
If not, oh ****.

---

